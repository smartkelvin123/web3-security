## [S-#] TITLE (Root Cause + Impact)
 variable  store in storage is  visibile to anyone, password can be seen by  anyone


## Description: **  
   all the data on-chain is visible to anyone, and can be read directly from the blockchain. the `passwordstore: is_password` variable is intended to be private varaible and only accessed throught the `passwordstore: getpassword` function, which is intended to be only called by the owner of the contract
 
 ## Impact:
    anyone can read the private password, severly breaking the functionality of the protocol
   

## Proof of Concept: 0r proof of code
   the below test case shows how anyone could read the password directly from the blockchain
    ```
    1. make a local running chain   // anvil
    2. deploy the contract
    3 run the contract

    ```
    cast storage <address_here> 1 --rpc-url http://127.0.0.1:8545

    ```
    you wiii get an output like this:
       `0x6d7950617373776f726400000000000000000000000000000000000000000014`

        ypu can parse the password with this:
           ```
           cast parse-bytes32-string 0x6d7950617373776f72640000000000000000000000000000000000000014
           ```
           you will get the password output 

           ```
           mypassword
           ```
       ```
    

## Recommended Mitigation:


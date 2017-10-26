# Acchain-HTTP Interface Specification
Table of Contents
=================

  * [Acchain-HTTP Interface Specification](#Acchain-http-interface-specification)
  * [Index](#index)
    * [<a href="#appendix-1-install-Acchain-js-library">Appendix 1 Install 'Acchain-js' library</a>](#-appendix-1-install-Acchain-js-library)
    * [1 API Usage Guide](#1-api-usage-guide)
      * [1.1 Request Process Overview](#11-request-process-overview)
    * [2 Interface](#2-interface)
      * [2.1 Accounts](#21-accounts)
        * [2.1.1 Login](#211-login)
          * [2.1.1.1 Login after locally encrypt (recommended)](#2111-login-after-locally-encrypt-recommended)
          * [2.1.1.2 Login without locally encrypt (not recommend)](#2112-login-without-locally-encrypt-not-recommend)
          * [2.1.1.3 Get secret of BIP39 format](#2113-get-secret-of-BIP39-format)
        * [2.1.2 Get Account Information](#212-get-account-information)
        * [2.1.3 Get Balance of Account](#213-get-balance-of-account)
        * [2.1.4 Get Account's Public Key](#214-get-accounts-public-key)
        * [2.1.5 Generate Public Key](#215-generate-public-key)
        * [2.1.6 Get Voting List by Address](#216-get-voting-list-by-address)
        * [2.1.7 Get the Fee of Given Delegate](#217-get-the-fee-of-given-delegate)
        * [2.1.8 Voting](#218-voting)
        * [2.1.9 Get the top 100 accounts](#219-get-the-top-100-accounts)
      * [2.2 Transactions](#22-transactions)
        * [2.2.1 Get the Transaction Detail Information](#221-get-the-transaction-detail-information)
        * [2.2.2 Get the Transaction Detail Information by Transaction ID](#222-get-the-transaction-detail-information-by-transaction-id)
        * [2.2.3 Get Transaction Detail by Unconfirmed Transaction ID](#223-get-transaction-detail-by-unconfirmed-transaction-id)
        * [2.2.4 Get Unconfirmed Transaction Detail Inforamtion (within all network)](#224-get-unconfirmed-transaction-detail-inforamtion-within-all-network)
        * [2.2.5 Create Transaction](#225-create-transaction)
        * [2.2.6 Exercise](#226-exercise)
      * [2.3 Blocks](#23-blocks)
        * [2.3.1 Get the Block Detail Information of the Given ID](#231-get-the-block-detail-information-of-the-given-id)
        * [2.3.2 Get the Latest Block](#232-get-the-latest-block)
        * [2.3.3 Get the Block Height](#233-get-the-block-height)
        * [2.3.4 Get the Transaction Fee](#234-get-the-transaction-fee)
        * [2.3.5 Get the Milestone](#235-get-the-milestone)
        * [2.3.6 Get the Reward Information of a Block](#236-get-the-reward-information-of-a-block)
        * [2.3.7 Get the Current Maximum Supply of the Blockchain](#237-get-the-current-maximum-supply-of-the-blockchain)
        * [2.3.8 Get Current Status of Blockchain](#238-get-current-status-of-blockchain)
      * [2.4 Delegates](#24-delegates)
        * [2.4.1 Get the Total Number of Delegates](#241-get-the-total-number-of-delegates)
        * [2.4.2 Check the Voters of Delegates by Public Key](#242-check-the-voters-of-delegates-by-public-key)
        * [2.4.3 Get the Delegate's Detail by Public Key or Name](#243-get-the-delegates-detail-by-public-key-or-name)
        * [2.4.4 Get the List of Delegates](#244-get-the-list-of-delegates)
        * [2.4.5 Get the Transaction Fee Set by Delegate](#245-get-the-transaction-fee-set-by-delegate)
        * [2.4.6 Get Forge Information by Public Key](#246-get-forge-information-by-public-key)
        * [2.4.7 Register Delegate](#247-register-delegate)
        * [2.4.8 Delegates enable forging](#248-delegates-enable-forging)
        * [2.4.9 Delegates disable forging](#249-delegates-disable-forging)
        * [2.4.10 Delegates forging status](#2410-delegates-forging-status)# Acchain-HTTP Interface Specification
Table of Contents
=================

  * [Acchain-HTTP Interface Specification](#Acchain-http-interface-specification)
  * [Index](#index)
    * [<a href="#appendix-1-install-Acchain-js-library">Appendix 1 Install 'Acchain-js' library</a>](#-appendix-1-install-Acchain-js-library)
    * [1 API Usage Guide](#1-api-usage-guide)
      * [1.1 Request Process Overview](#11-request-process-overview)
    * [2 Interface](#2-interface)
      * [2.1 Accounts](#21-accounts)
        * [2.1.1 Login](#211-login)
          * [2.1.1.1 Login after locally encrypt (recommended)](#2111-login-after-locally-encrypt-recommended)
          * [2.1.1.2 Login without locally encrypt (not recommend)](#2112-login-without-locally-encrypt-not-recommend)
        * [2.1.2 Get Account Information](#212-get-account-information)
        * [2.1.3 Get Balance of Account](#213-get-balance-of-account)
        * [2.1.4 Get Account's Public Key](#214-get-accounts-public-key)
        * [2.1.5 Generate Public Key](#215-generate-public-key)
        * [2.1.6 Get Voting List by Address](#216-get-voting-list-by-address)
        * [2.1.7 Get the Fee of Given Delegate](#217-get-the-fee-of-given-delegate)
        * [2.1.8 Voting](#218-voting)
        * [2.1.9 Get the top 100 accounts](#219-get-the-top-100-accounts)
      * [2.2 Transactions](#22-transactions)
        * [2.2.1 Get the Transaction Detail Information](#221-get-the-transaction-detail-information)
        * [2.2.2 Get the Transaction Detail Information by Transaction ID](#222-get-the-transaction-detail-information-by-transaction-id)
        * [2.2.3 Get Transaction Detail by Unconfirmed Transaction ID](#223-get-transaction-detail-by-unconfirmed-transaction-id)
        * [2.2.4 Get Unconfirmed Transaction Detail Inforamtion (within all network)](#224-get-unconfirmed-transaction-detail-inforamtion-within-all-network)
        * [2.2.5 Create Transaction](#225-create-transaction)
        * [2.2.6 Exercise](#226-exercise)
      * [2.3 Blocks](#23-blocks)
        * [2.3.1 Get the Block Detail Information of the Given ID](#231-get-the-block-detail-information-of-the-given-id)
        * [2.3.2 Get the Latest Block](#232-get-the-latest-block)
        * [2.3.3 Get the Block Height](#233-get-the-block-height)
        * [2.3.4 Get the Transaction Fee](#234-get-the-transaction-fee)
        * [2.3.5 Get the Milestone](#235-get-the-milestone)
        * [2.3.6 Get the Reward Information of a Block](#236-get-the-reward-information-of-a-block)
        * [2.3.7 Get the Current Maximum Supply of the Blockchain](#237-get-the-current-maximum-supply-of-the-blockchain)
        * [2.3.8 Get Current Status of Blockchain](#238-get-current-status-of-blockchain)
      * [2.4 Delegates](#24-delegates)
        * [2.4.1 Get the Total Number of Delegates](#241-get-the-total-number-of-delegates)
        * [2.4.2 Check the Voters of Delegates by Public Key](#242-check-the-voters-of-delegates-by-public-key)
        * [2.4.3 Get the Delegate's Detail by Public Key or Name](#243-get-the-delegates-detail-by-public-key-or-name)
        * [2.4.4 Get the List of Delegates](#244-get-the-list-of-delegates)
        * [2.4.5 Get the Transaction Fee Set by Delegate](#245-get-the-transaction-fee-set-by-delegate)
        * [2.4.6 Get Forge Information by Public Key](#246-get-forge-information-by-public-key)
        * [2.4.7 Register Delegate](#247-register-delegate)
        * [2.4.8 Delegates enable forging](#248-delegates-enable-forging)
        * [2.4.9 Delegates disable forging](#249-delegates-disable-forging)
        * [2.4.10 Delegates forging status](#2410-delegates-forging-status)
      * [2.5 Peers](#25-peers)
        * [2.5.1 Get all Peers' Information in the Whole Network](#251-get-all-peers-information-in-the-whole-network)
        * [2.5.2 Get the Version of Peer](#252-get-the-version-of-peer)
        * [2.5.3 Get the Peer Information of a Given IP Address](#253-get-the-peer-information-of-a-given-ip-address)
      * [2.6 Sync and Loader](#26-sync-and-loader)
        * [2.6.1 Get the local blockchain loading status](#261-get-the-local-blockchain-loading-status)
        * [2.6.2 Get the block syncing status](#262-get-the-block-syncing-status)
      * [2.7 Second Password](#27-second-password)
        * [2.7.1 Set the Second Password](#271-set-the-second-password)
        * [2.7.2 Get the Transaction Fee of Setting Second Password](#272-get-the-transaction-fee-of-setting-second-password)
      * [2.8 Multiple Signatures](#28-multiple-signatures)
        * [2.8.1 Set Normal Account to Multi-signatures Account](#281-set-normal-account-to-multi-signatures-account)
        * [2.8.2 Get the Detail Information of Pending Multi-signature Transaction](#282-get-the-detail-information-of-pending-multi-signature-transaction)
        * [2.8.3 Sign the Multi-signature Transaction (by non-initiator)](#283-sign-the-multi-signature-transaction-by-non-initiator)
        * [2.8.4 Get Detail Information of the Multi-signature Account](#284-get-detail-information-of-the-multi-signature-account)
      * [2.9 Peer to Peer Transportation(secure API)](#29-peer-to-peer-transportationsecure-api)
        * [2.9.1 Overview](#291-overview)
        * [2.9.2 Transaction](#292-transaction)
          * [2.9.2.1 Set the Second Payment Password](#2921-set-the-second-payment-password)
          * [2.9.2.2 Transfer Money](#2922-transfer-money)
          * [2.9.2.3 Register Delegates](#2923-register-delegates)
          * [2.9.2.4 Vote and Cancel the vote](#2924-vote-and-cancel-the-vote)
      * [2.10 User Identify Assets](#210-user-identify-assets)
        * [2.10.1 Get assets info](#2101-get-assets-info)
          * [2.10.1.1 Get all issuers](#21011-get-all-issuers)
          * [2.10.1.2 Get the issuers info](#21012-get-all-issuers-info)
          * [2.10.1.3 Get the issuer assets](#21012-get-the-issuer-assets)
          * [2.10.1.4 Get all assets](#21014-get-all-assets)
          * [2.10.1.5 Get info by asset name](#21015-get-info-by-asset-name)
          * [2.10.1.6 Get the applying assets](#21016-get-the-applying-assets)
          * [2.10.1.7 Get the applying issues](#21017-get-the-applying-issues)
          * [2.10.1.8 Get approved assets](#21018-get-approved-assets)
          * [2.10.1.9 Get the assets access control lists](#21019-get-the-assets-access-control-lists)
          * [2.10.1.10 Get all the assets info of gave address](#210110-get-all-the-assets-info-of-gave-address)
          * [2.10.1.11 Get UIA Exercise](#210111-get-uia-exercise)
      * [2.10.2 Create UIA Transaction](#2102-create-uia-transaction)
        * [2.10.2.1 Create Issuer](#21021-create-issuer)
        * [2.10.2.2 Register Assets](#21022-register-assets)
        * [2.10.2.3 Assets Issue](#21023-assets-issue)
        * [2.10.2.4 Assets Transfer](#21024-assets-transfer)
        * [2.10.2.5 Assets Exercise](#21025-assets-exercise)
      * [2.10.3 UIA Vote](#2103-uia-vote)
        * [2.10.3.1 Get voters by assets currency](#21031-get-voters-by-assets-currency)
        * [2.10.3.2 Get voters for issues](#21032-get-voters-for-issues)
      * [2.10.4 UIA Control](#2104-uia-control)
        * [2.10.4.1 Set acl mode](#21041-set-acl-mode)
        * [2.10.4.2 Update acl lists](#21042-update-acl-lists)
      * [2.10.5 Get Assets Category](#2105-get-assets-category)
        * [2.10.5.1 Get First Category](#21051-get-first-category)
        * [2.10.5.2 Get Category By id](#21052-get-category-by-id)
        
---

## 1 API Usage Guide

### 1.1 Request Process Overview
---
- **Generate request data:** according the interface specification provided by Acchain system, generate the request data as a JSON object. (In one case, if you write about secure peer to peer transportation, you may need a JS library called Acchain-js to create signature. see [2.9 Peer to Peer transportation](#29-peer-to-peer-transportation) for detail).
- **Send request data:** transfer the generated data object to acchain  platform through POST/GET Methods upon HTTP
- **Acchain system handles the data object:** after receiving the data object, acchain server will validate the data firstly, then deal with it.
- **Return the response data:** acchain system send the response data to client as a JSON object. See interface part for detail, like response data format and error code.
- **Client handles the response data**

## 2 Interface  
 
### 2.1 Accounts   
   
#### 2.1.1 Login   

##### 2.1.1.1 Login after locally encrypt (recommended)   
---
- Interface Address: /api/accounts/open2/   
- Request Type: post   
- Supported Format: json   
- Comment: Public key needs to be generated locally according to user's password (see Request Example)   

- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |acchain account public key       |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |Whether login is successful      |    
|account|json   |Account Information          | 
   
- Request Example:   
  
```js
var acchainJS = require('Acchain-js');  //For further information about Acchain-js, please see Appendix
var publicKey = AcchainJS.crypto.getKeys(secret).publicKey;  //Generate public key according to password 
// var address = AcchainJS.crypto.getAddress(publicKey);   //Generate address according to public key

// Submit the above data to acchain server through post Methods   
curl -X POST -H "Content-Type: application/json" -k -d '{"publicKey":"bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"}' https://testnet.acchain.org/api/accounts/open2/   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"account": {   
		"address": "16723473400748954103",   
		"unconfirmedBalance": 19480000000,   
		"balance": 19480000000,   
		"unconfirmedSignature": false,   
		"secondSignature": true,   
		"secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",   
		"multisignatures": [],   
		"u_multisignatures": []   
	},   
	"latestBlock": {   
		"height": 111923,   
		"timestamp": 4446270   
	},   
	"version": {   
		"version": "1.0.0",   
		"build": "12:11:11 16/08/2016",   
		"net": "testnet"   
	}   
```   
   
##### 2.1.1.2 Login without locally encrypt (not recommend) 
---
- Interface Address: /api/accounts/open/   
- Request Methods:post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |Whether login is successful      |    
|account|json   |Account information          |    
   
- Request Example: 
  
```bash   
curl -X POST -H "Content-Type: application/json" -k -d '{"secret":"fault still attack alley expand music basket purse later educate follow ride"}' https://testnet.acchain.org/api/accounts/open/   
```   
   
- JSON Response Example: 
  
```js   
{   
    "success": true,    
    "account": {   
        "address": "16723473400748954103",    
        "unconfirmedBalance": 19480000000,    
        "balance": 19480000000,    
        "publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",    
        "unconfirmedSignature": false,    
        "secondSignature": true,    
        "secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",    
        "multisignatures": [ ],    
        "u_multisignatures": [ ]   
    }   
}   
``` 
##### **2.1.1.3 Get secret of BIP39 format**  
---  
- Interface Address: /api/accounts/new   
- Request Methods: get 
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |     
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |    
|success|boole  |whether get is successful      |    
|secret| string  |secret information          |   
|publicKey| string  |publickey          | 
|address| string  |address          | 
   
- JSON Response Example:
 
```bash   
curl -X GET -H "Content-Type: application/json" -k https://testnet.acchain.org/api/accounts/new/   
```   
   
- JSON Response Example: 
  
```js   
{
   success: true,
   secret: "recipe faculty absorb leisure agree lecture syrup helmet fly airport cabin flag",
   publicKey: "5ca7efc2d1506739bc8719d16e7028dbe13d3de1f2680c7a00a0cf4e446eb366",
   privateKey:             "1516276d1875d10dbc5d706953f4c25495235bdd76ef18fcfdf9d4c25aad9c625ca7efc2d1506739bc8719d16e7028dbe13d3de1f2680c7a00a0cf4e446eb366",
   address: "AGXcBi7XG2qxesBBTHdHZiFPkYDUBWcxe1"
}  
``` 

####2.1.2 Get Account Information  
---
- Interface Address: /api/accounts   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether response data can be returned |    
|account|json  |account information      |    
|latestBlock|json  |latest block information      |    
|version|json  |version information      |    
   
- Request Example:  
 
```bash   
curl -k -X GET https://testnet.acchain.org/api/accounts?address=16723473400748954103   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"account": {   
		"address": "16723473400748954103",  //acchain address   
		"unconfirmedBalance": 19480000000,  //the sum of unconfirmed and confirmed balance, that should be larger than or equal to balance below.   
		"balance": 19480000000, //balance   
		"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",    //Public key   
		"unconfirmedSignature": false,   
		"secondSignature": true,    //second signature   
		"secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",  //second public key   
		"multisignatures": [],    
		"u_multisignatures": []   
	},   
	"latestBlock": {   
		"height": 114480,   //block height   
		"timestamp": 4471890   
	},   
	"version": {   
		"version": "1.0.0",   
		"build": "12:11:11 16/08/2016", //build date   
		"net": "testnet"    //blockchain type: main chain or test one   
	}   
}   
```   

#### 2.1.3 Get Balance of Account  
--- 
- Interface Address: /api/accounts/getBalance   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|balance|integer  |balance      |    
|unconfirmedBalance|integer|the sum of unconfirmed and confirmed balance, that should be larger than or equal to balance|   
   
   
-Request Example:  
 
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/getBalance?address=14636456069025293113'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"balance": 5281328514990,   
	"unconfirmedBalance": 5281328514990   
}   
```   
   
#### 2.1.4 Get Account's Public Key 
---  
- Interface Address: /api/accounts/getPublickey   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1     |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|publicKey|string  |public key      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/getPublickey?address=14636456069025293113'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7"   
}   
```   
   
#### 2.1.5 Generate Public Key
---   
- Interface Address: /api/accounts/generatePublickey   
- Request Methods: post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password     |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|publicKey|string  |public key      |    
   
- Request Example:  
 
```bash   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"fault still attack alley expand music basket purse later educate follow ride"}' 'https://testnet.acchain.org/api/accounts/generatePublickey'   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"   
}   
```   
   
#### 2.1.6 Get Voting List by Address   
---
- Interface Address: /api/accounts/delegates   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Voter's address      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegates|Array  |A list that contains detail information of those delegates who have already voted   |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/delegates?address=14636456069025293113'   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"delegates": [{   
		"username": "wgl_002",   
		"address": "14636456069025293113",   
		"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",   
		"vote": 9901985415600500,   
		"producedblocks": 1373,   
		"missedblocks": 6,   
		"rate": 1,   
		"approval": "98.54",   
		"productivity": "99.56"   
	},   
	{   
		"username": "wgl_003",   
		"address": "9961157415582672274",   
		"publicKey": "c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2",   
		"vote": 9891995435600500,   
		"producedblocks": 1371,   
		"missedblocks": 8,   
		"rate": 2,   
		"approval": "98.44",   
		"productivity": "99.41"   
	},   
	{   
		"username": "wgl_001",   
		"address": "1869971419039689816",   
		"publicKey": "c547df2dde6cbb4508aabcb5970d8f9132e5a1d1c422632da6bc20bf1df165b8",   
		"vote": 32401577128413,   
		"producedblocks": 969,   
		"missedblocks": 8,   
		"rate": 102,   
		"approval": "0.32",   
		"productivity": 0   
	}]   
}   
```   
   
#### 2.1.7 Get the Fee of Given Delegate 
--- 
- Interface Address: /api/accounts/delegates/fee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none  

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |fee setting      |    
   
   
- Request Example:
   
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/delegates/fee  
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"fee": 100000000   
}   
```   
   
   
#### 2.1.8 Voting   
---
- Interface Address: /api/accounts/delegates   
- Request Methods: put   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|N|acchain account's second password，minimum length：1，maximum length：100|   
|delegates|Array|a list that contains delegates' public key. put +/- in front of each public key, which means vote/abolish this delegate. |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |voting detail inforamtion      |    
   
   
- Request Example:  
 
```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"call scissors pupil water friend timber spend brand vote obey corn size","publicKey":"3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a","delegates":["+fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575"]}' 'https://testnet.acchain.org/api/accounts/delegates'     
```   
   
- JSON Response Example:   

```js   
 {
	"success": true,
	"transaction": {
		"type": 3,  //the type of vote is '3'
		"amount": 0,
		"senderPublicKey": "3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a",
		"requesterPublicKey": null,
		"timestamp": 5056064,
		"asset": {
			"vote": {
				"votes": ["+fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575"]
			}
		},
		"recipientId": null,
		"signature": "0bff58c7311fc59b3c8b3ffc236bbfece9850c334fb0c292ab087f78cf9a6c0f4d3e541c501887a2c2ec46294c777e8f7bf7dea9cb7c9a175fdec641bb684f08",
		"id": "5630629337798595849",
		"fee": 10000000,
		"senderId": "15238461869262180695"
	}
}  
```   

   
#### 2.1.9 Get the top 100 accounts
---
- Interface Address: /api/accounts/top    
- Request Methods: get  
- Supported Format: none      
- Request Parameter Description: if no parameters are passed, it will return top 100 accounts info
  
|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0,maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|json  |accounts info array, including "address", "balance", "publicKey" |    

- Request Example:

```bash
curl -k -X GET 'https://testnet.acchain.org/api/accounts/top?limit=5&offset=0'  //return 5 accounts info 
```

- Return JSON example:

```js
{
    "success": true,
    "accounts": [{
        "address": "355198157736313687",
        "balance": 4400099900000000,        //44000999 ACC
        "publicKey": "0b8e120db026d58cbf9d3f392f88eefe3a82a0a3023298b9466d7ed64ff05881"
    },
    {
        "address": "3196144307608101364",
        "balance": 3750000020000000,
        "publicKey": "988eb82a603dd033f94a4f3b6f9f9ef4a7d3d066607c433e5255d50ea7270720"
    },
    {
        "address": "9248745407080572308",
        "balance": 988703397029757,
        "publicKey": "02cedc56da08099532e312c5e563e2859bc5b93cc594eb3e5d350f368d681988"
    },
    {
        "address": "15745540293890213312",
        "balance": 498186229718623,
        "publicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3"
    },
    {
        "address": "8812460086240160222",
        "balance": 100704426831866,
        "publicKey": "0af92cc32f54d50dd83c4f7de14e71223a57843a40e993bc0813454aa9270053"
    }
}    
```


### 2.2 Transactions   
#### 2.2.1 Get the Transaction Detail Information  
--- 
- Interface Address: /api/transactions   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment： if there is no parameter in request data, all network transactions will be returned.    
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|blockId |string |N    |block id      |   
|limit |integer |N    |the limitation of returned records，minimum：0,maximum：100   |   
|type|integer  |N      |The transaction type, SEND: 0, SIGNATURE: 1,DELEGATE: 2 ,VOTE: 3, MULTI: 4, DAPP: 5,IN_TRANSFER: 6, OUT_TRANSFER: 7, APPROVAL: 8, UIA_ISSUER: 9, UIA_ASSET: 10, UIA_ISSUE: 11, UIA——EXERCISE: 12|   
|orderBy|string  |N      |sort with a field in the table，senderPublicKey:desc  |   
|offset|integer  |N      |offset, minimum 0  |   
|senderPublicKey|string|N|sender's public key|   
|ownerPublicKey|string|N||   
|ownerAddress|string|N||   
|senderId|string|N|sender's address|   
|recipientId|string|N|recipient's address, minimum:1|   
|amount|string|N|amount|   
|fee|integer|N|charge fee|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |A JSON object list containing multiple transactions' detail      |    
|count|int|the total number of retrieved transactions|   
   
- Request Example:  
 
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions?recipientId=16723473400748954103&orderBy=t_timestamp:desc&limit=3'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": [{   
		"id": "17192581936339156329",   
		"height": "105951",   
		"blockId": "15051364118100195665",   
		"type": 0,   
		"timestamp": 4385190,   
		"senderPublicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3",   
		"senderId": "15745540293890213312",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "98d65df3109802c707eeed706e90a907f337bddab58cb4c1fbe6ec2179aa1c85ec2903cc0cf44bf0092926829aa5a0a6ec99458f65b6ebd11f0988772e58740e",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "31802",   
		"asset": {   
			   
		}   
	},   
	{   
		"id": "7000452951235123088",   
		"height": "105473",   
		"blockId": "11877628176330539727",   
		"type": 0,   
		"timestamp": 4380147,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "dc84044d4f6b4779eecc3a986b6507e458cc5964f601ebeb4d3b68a96129813f4940e14de950526dd685ca1328b6e477e6c57e95aeac45859a2ea62a587d0204",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "32280",   
		"asset": {   
			   
		}   
	},   
	{   
		"id": "14093929199102906687",   
		"height": "105460",   
		"blockId": "2237504897174225512",   
		"type": 0,   
		"timestamp": 4380024,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "73ceddc3cbe5103fbdd9eee12f7e4d9a125a3bcf2e7cd04282b7329719735aeb36936762f17d842fb14813fa8f857b8144040e5117dffcfc7e2ae88e36440a0f",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "32293",   
		"asset": {   
			   
		}   
	}],   
	"count": 3   
}   
```   

#### 2.2.2 Get the Transaction Detail Information by Transaction ID
---
- Interface Address: /api/transactions/get   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|Id |string |Y    |transaction id      |   
    
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|json  |transaction detail information      |    
   
- Request Example: 
  
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions/get?id=14093929199102906687'   
```   
   
- JSON Response Example:
   
```js   
{   
	"success": true,   
	"transaction": {   
		"id": "14093929199102906687",   
		"height": "105460",   
		"blockId": "2237504897174225512",   
		"type": 0,   
		"timestamp": 4380024,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "73ceddc3cbe5103fbdd9eee12f7e4d9a125a3bcf2e7cd04282b7329719735aeb36936762f17d842fb14813fa8f857b8144040e5117dffcfc7e2ae88e36440a0f",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "34268",   
		"asset": {   
		}   
	}   
}   
```   
   
#### 2.2.3 Get Transaction Detail by Unconfirmed Transaction ID 
---  
- Interface Address: /api/transactions/unconfirmed/get   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|id|string |Y    |unconfirmed transaction id      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |unconfirmed transaction detail inforamtion      |   
   
   
- Request Example:
   
```bash   
curl -k -X GET https://testnet.acchain.org/api/transactions/unconfirmed/get?id=7557072430673853692  //Regularly, this unconfirmed transaction exist during an extremely short time, almost 0~10 second. 
```   
   
- JSON Response Example:
   
```js   
{
	"success": true,
	"transaction": {
		"type": 0,
		"amount": 10000,
		"senderPublicKey": "3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a",
		"requesterPublicKey": null,
		"timestamp": 5082322,
		"asset": {
			
		},
		"recipientId": "16723473400748954103",
		"signature": "3a97f8d63509ef964bda3d816366b8e9e2d9b5d4604a660e7cbeefe210cb910f5de9a51bece06c32d010f55502c62f0f59b8224e1c141731ddfee27206a88d02",
		"id": "7557072430673853692",
		"fee": 10000000,
		"senderId": "15238461869262180695"
	}
}
```   
   
   
#### 2.2.4 Get Unconfirmed Transaction Detail Information (within all network)
---
- Interface Address: /api/transactions/unconfirmed   
- Request Methods:get   
- Supported Format: urlencoded   
- Comment: If there is no parameter, all unconfirmed transactions in the whole network will be returned.
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|senderPublicKey |string |N    |sender's public key      |   
|address |string |N    |address      |   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |a list containing all unconfirmed transactions      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions/unconfirmed'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": []      //Currently there is no unconfirmed transaction in the whole network 
}   
```   
   
#### 2.2.5 Create Transaction   
---
- Interface Address: /api/transactions   
- Request Methods: PUT   
- Supported Format: json   
- Comment: recipient account must have already login in wallet on the web.  
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|amount|string|Y|amount，between 1 and 10000000000000000|   
|recipientId|string|Y|recipient's address, minimum:1|   
|publicKey|string|N|sender's public key|   
|currency|string|N|assets name, for example:"test.RET"|
|message|string|N|remark message|
|publicKey|string|N|sender's public key|   
|secondSecret|string|N|sender's second password (must fit the BIP39 standard), the length should be between 1 and 100|   
|multisigAccountPublicKey|string|N|the public key of multiple signature account|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |transaction id      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","amount":1000000,"recipientId":"16723473400748954103","currency":"test.RET"}' 'https://testnet.acchain.org/api/transactions'    
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "16670272591943275531"   
}   
```   





#### 2.2.6 Exercise  
---
- Interface Address: /api/exercises   
- Request Methods: PUT   
- Supported Format: json   
- Comment: recipient account must have already login in wallet on the web.  
- Request Parameter Description:  

|Name	|Type   |Required |Description|   
|------ |-----  |---  |----      |
|secret|string|Y| acchain account password |
|amount|string|Y| amount，between 1 and 10000000000000000|
|currency|string|Y| assets name, for example:"test.RET"|
|publicKey|string|Y| sender's public key|
|message|string|N | remark message|
|secondSecret|string|N| sender's second password (must fit the BIP39 standard), the length should be between 1 and 100|
|multisigAccountPublicKey|string|N| the public key of multiple signature account|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |transaction id      |  

- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","amount":1000000,"currency":"test.RET", "message":"hello"}' 'https://testnet.acchain.org/api/uia/exercises'        
```      

- JSON Response Example:   

```js   
{
    "success": true,
    "transaction": {
        "type": 12,
        "amount": "0",
        "senderPublicKey": "78e3bca480fc90ff149c1f538a332f540350ca19ac441bfee66cc29a076e62d9",
        "requesterPublicKey": null,
        "timestamp": 31408638,
        "asset": {
            "uiaExercise": {
                "currency": "test.RET",
                "amount": "10000"
            }
        },
        "recipientId": null,
        "signature": "ea12eee74a932c49863fb90493a90a942b95e9e39e2d5c6204d8cf651b6c3fee63309db17374c22a16a453a22f5f881c8af153119d81bc3401e5e80364c55502",
        "signSignature": "0577c15e9498fbcd0b84a70b80e7f10db3fb327dd7316868a427ec7bc917b15468f4cb8bcfb4cbe1897b9576275ff1430e78858fdbeebbc19a1ec0966e530d05",
        "id": "8a56a0f5c0b057f2e037b609ab829a8f15e9c581b43436c438063df3492eb6ce",
        "fee": 100000,
        "senderId": "APfs15A8KegKu1TtnJsWJvLoFxCKT7pRos"
    }
}    
```  
   
### 2.3 Blocks
#### 2.3.1 Get the Block Detail Information of the Given ID 
---  
- Interface Address: /api/blocks/   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|id |string |only choose one of these three parameters    |block ID      |   
|height|string|ditto|block height|   
|hash|string|ditto|block hash value|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|block|json  |the block detail information      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/get?id=6076474715648888747'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"block": {   
		"id": "6076474715648888747",   
		"version": 0,   
		"timestamp": 4734070,   
		"height": 140538,   
		"previousBlock": "16033230167082515105",    //previous block ID   
		"numberOfTransactions": 0,  //The number of transactions   
		"totalAmount": 0,   //the total transactions' amount   
		"totalFee": 0,   
		"reward": 350000000,    //reward   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "1d352950c8141e1b35daba4a974a604519d7a2ef3a1ec0a503ce2653646aa052",   
		"generatorId": "6656029629904254066",   
		"blockSignature": "a53de66922cdc2f431acd0a474beec7cf7c420a8460b7b7caf84999be7caebb59fb7fbb7166c2c7013dbb431585ea7294722166cb08bf9663abf50b6bd81cd05",   
		"confirmations": "2",   
		"totalForged": 350000000   
	}   
}   
```   
   
#### 2.3.2 Get the Latest Block  
---
- Interface Address: /api/blocks   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment: if there is no parameter, the detail of all the blocks in the whole network will be returned  
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit |integer |N    |maximum number of returned records, between 0 and 100   |   
|orderBy|string  |N      |sort by a field in the table, for example, height: desc  |   
|offset|integer  |N      |offset, minimum 0  |   
|generatorPublicKey|string  |N      |public key of the block generator  |   
|totalAmount|integer  |N       |total amount of transactions, from 0 to 10000000000000000 |   
|totalFee|integer  |N      |total fee of transaction, from 0 to 10000000000000000  |   
|reward|integer  |N      |the amount of reward, minimum: 0  |   
|previousBlock|string  |N      |previous block  |   
|height|integer  |N      |block height  |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|blocks|Array  |a list of JSON objects containing block detail|    
|count|integer|block height|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks?limit=2&offset=0&orderBy=height:desc'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"blocks": [{   
		"id": "12634047624004615059",   
		"version": 0,   
		"timestamp": 4708080,   
		"height": 137986,   
		"previousBlock": "3498191422350401106",   
		"numberOfTransactions": 0,  // the number of transactions   
		"totalAmount": 0,   // total amount of transactions   
		"totalFee": 0,  // transaction fee   
		"reward": 350000000,    // reward   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "44db7bec89ef289d0def257285675ca14f2a947dfd2b70e6b1cff4392ce42ada",   
		"generatorId": "4925169939071346193",   
		"blockSignature": "83a2124e3e8201c1a6099b2ac8ab1c117ad34867978add3a90d41a64df9d2ad8fabc9ec14d27a77cd34c08a6479ef684f247c11b1cbbcb0e9767dffc85838600",   
		"confirmations": "1",   
		"totalForged": 350000000   
	},   
	{   
		"id": "3498191422350401106",   
		"version": 0,   
		"timestamp": 4708070,   
		"height": 137985,   
		"previousBlock": "14078155423801039323",   
		"numberOfTransactions": 0,   
		"totalAmount": 0,   
		"totalFee": 0,   
		"reward": 350000000,   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "500b1ec025cd64d36008341ed8d2508473ecf559be213ca5f9580620a21a592c",   
		"generatorId": "16006295608945777169",   
		"blockSignature": "a0b5ed6c94b1f33c4d0f017f21a08357061493392b19e34eeedf274b77c751e3f86c92443280de09ea1754d62fe7ef00e02acbdc3bc0c1063cef344bacaa4f07",   
		"confirmations": "2",   
		"totalForged": 350000000   
	}],   
	"count": 137986   
}   
```   
   
#### 2.3.3 Get the Block Height  
--- 
- Interface Address: /api/blocks/getHeight   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height|integer  |block height      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getheight'    
```   
   
- JSON Response Example:   

```js   
{"success":true,"height":140569}   
```   
   
#### 2.3.4 Get the Transaction Fee  
--- 
- Interface Address: /api/blocks/getFee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee     |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getfee'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"fee":10000000}     //transaction fee is 
0.1 ACC   
```   
   
#### 2.3.5 Get the Milestone   
---
- Interface Address: /api/blocks/getMilestone   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|milestone|integer  |      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getMilestone'    
```   
   
- JSON Response Example:   

```js   
{"success":true,"milestone":0}   
```   
   
#### 2.3.6 Get the Reward Information of a Block 
---
- Interface Address: /api/blocks/getReward   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|reward|integer  |the reward of the block      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getReward'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"reward":350000000} //every single block you created will be rewarded by 3.5 ACC   
```   
   
#### 2.3.7 Get the Current Maximum Supply of the Blockchain

- Interface Address: /api/blocks/getSupply   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|supply|integer  |the total amount of ACC in the whole network      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getSupply'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"supply":10049222600000000} //There are totally 100492226 ACC in current testnet   
```   
   
#### 2.3.8 Get Current Status of Blockchain 
--- 
- Interface Address: /api/blocks/getStatus   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height|integer  |blockchain height      |    
|fee|integer  |transaction fee      |    
|milestone|integer  |      |    
|reward|integer  |block reward      |    
|supply|integer  |total amount of ACC in the whole network      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getStatus'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"height": 140649,   
	"fee": 10000000,   
	"milestone": 0,   
	"reward": 350000000,   
	"supply": 10049227150000000   
}   
```   
   
   
   
### 2.4 Delegates  
   
#### 2.4.1 Get the Total Number of Delegates 
---
- Interface Address: /api/delegates/count   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|count|integer   |total number of delegates      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/count'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"count":234}   
```   
   
#### 2.4.2 Check the Voters of Delegates by Public Key   
---
- Interface Address: /api/delegates/voters   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |public key of the delegate      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|Array  |a JSON object list of account    |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/voters?publicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"accounts": [{   
		"address": "2918354313445278349",   
		"publicKey": "4fde4c49f1297d5d3a24b1494204543c4281aff17917ff7ff8ff32da3b4b222f",   
		"balance": 1338227722727,   
		"weight": 0.013316660647014596   
	},   
	{   
		"address": "1523444724068322527",   
		"publicKey": "8a6a61c28dc47541aadf1eecec2175c8f768f2331eea3472b1593bf1aa4e1fb4",   
		"balance": 2109297623765,   
		"weight": 0.020989552213127274   
	},   
	{   
		"address": "14483826354741911727",   
		"publicKey": "5dacb7983095466b9b037690150c3edec0f073815326e33a4744b6d1d50953e2",   
		"balance": 5135815841470,   
		"weight": 0.051106336795243436   
	}   
	}]   
}   
```   
   
#### 2.4.3 Get the Delegate's Detail by Public Key or Name   
---
- Interface Address:  /api/delegates/get/   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment:Get the delegate's detail by his/her public key or user name      
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publickey |string |choose only one parameter of these two    |delegate's public key      |   
|username  |string |ditto    |delegate's user name      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegate|json  |the detail information of this delegate      |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/delegates/get?publicKey=bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9   
curl -k -X GET https://testnet.acchain.org/api/delegates/get?username=delegate_register   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"delegate": {   
		"username": "delegate_register",   
		"address": "16723473400748954103",   
		"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",   
		"vote": 0,   
		"producedblocks": 0,   
		"missedblocks": 0,   
		"fees": 0,   
		"rewards": 0,   
		"rate": 191,   
		"approval": 0,   
		"productivity": 0,   
		"forged": "0"   
	}   
}   
```   
   
#### 2.4.4 Get the List of Delegates 
---  
- Interface Address: /api/delegates   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment: if there is no parameter, all delegates in the whole network will be returned. 
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |N    |delegate's address      |   
|limit|int  |N       |maximum return records       |   
|offset|integer  |N       |offset, minimum: 0      |   
|orderBy|string  |N       |[field used to sort]:[sort type] e.g., address:desc      |   
   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegates|Array  |a list containing delegates' detail information      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates?orderby=approval:desc&limit=2' //the first two delegates order by approval vote, descendingly  
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"delegates": [{   
		"username": "wgl_002",  //delegate's user name   
		"address": "14636456069025293113",  //delegate's address   
		"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",    //delegate's public key   
		"vote": 9901984015600500,   //the number of vote   
		"producedblocks": 1371, //the number of generated blocks   
		"missedblocks": 6,  //the number of missed blocks   
		"fees": 12588514990,       
		"rewards": 276850000000,    //the gained reward   
		"rate": 1,   
		"approval": 98.54,  //the rate of approval votes   
		"productivity": 99.56,  //the productivity   
		"forged": "289438514990"    //All reward from forge   
	},   
	{   
		"username": "wgl_003",   
		"address": "9961157415582672274",   
		"publicKey": "c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2",   
		"vote": 9891994035600500,   
		"producedblocks": 1370,   
		"missedblocks": 8,   
		"fees": 12355148480,   
		"rewards": 275100000000,   
		"rate": 2,   
		"approval": 98.44,   
		"productivity": 99.42,   
		"forged": "287455148480"   
	}],   
	"totalCount": 233   
}   
```   
   
   
#### 2.4.5 Get the Transaction Fee Set by Delegate 
---
- Interface Address: /api/delegates/fee   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |delegate's public key      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/fee?publicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"fee":10000000000}  //0.1 ACC   
```   
   
#### 2.4.6 Get Forge Information by Public Key 
---
- Interface Address: /api/delegates/forging/getForgedByAccount   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|generatorPublicKey |string |Y    |block generator's public key      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fees|integer  |total amount of charged fee      |    
|rewards|integer|gained rewards|   
|forged|integer|total rewards comming from forge|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/forging/getForgedByAccount?generatorPublicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"fees": 12589307065,   
	"rewards": 285600000000,   
	"forged": 298189307065   
}   
```   
   
#### 2.4.7 Register Delegate
---
- Interface Address: /api/delegates   
- Request Methods: put   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|publicKey|string  |N      |public key|    
|secondSecret|string|N|acchain account's second password, minimum length:1 maximum length: 100 |   
|username|string|N|the delegate's user name|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |the detail of the registering process      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","username":"delegate_0821"}' 'https://testnet.acchain.org/api/delegates'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transaction": {   
		"type": 2,  //the transaction type of registering delegate is 2   
		"amount": 0,   
		"senderPublicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2",   
		"requesterPublicKey": null,   
		"timestamp": 4737615,   
		"asset": {   
			"delegate": {   
				"username": "delegate_0821",   
				"publicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2"   
			}   
		},   
		"recipientId": null,   
		"signature": "7f8417e8db5f58ddff887c86c789c26b32fd3f01083ef1e3c8d4e18ed16622bf766492d78518c6c7a07aada1c98b1efc36d40c8e09394989dbde229d8e3f8103",   
		"id": "16351320834453011577",   
		"fee": 10000000000,   
		"senderId": "250438937633388106"   
	}   
}   
```   
   
#### 2.4.8 Delegates enable forging
---
- Interface Address: /api/delegates/forging/enable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Descriptio|
|------ |-----  |---  |----  |  
|secret |string | Y   | acchain account secret|
|publicKey| string | N | publicKey|

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| address | string | delegate's address |

- Request Example:

```js
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"motion group blossom coral upper warrior pattern fragile sister misery palm detect"}' 'http://testnet.acchain.org/api/delegates/forging/enable'   
```

- JSON Response Example:

```js
{"success":true,"address":"16358246403719868041"}  
```

#### 2.4.9 Delegates disable forging

- Interface Address: /api/delegates/forging/disable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |  
|secret |string | Y   | acchain account secret|
|publicKey| string | N | publicKey|

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| address | string | delegate's address |

- Request Example:

```js
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"motion group blossom coral upper warrior pattern fragile sister misery palm detect"}' 'http://testnet.acchain.org/api/delegates/forging/disable'   
```

- JSON Response Example:

```js
{"success":true,"address":"16358246403719868041"} 
```

#### 2.4.10 Delegates forging status
---
- Interface Address: /api/delegates/forging/disable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |  
|publicKey |string | Y   | publicKey |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| enable | string | the status of delegates foring |

- Request Example:

```js
curl -k -X GET 'https://testnet.acchain.org/api/delegates/forging/status?publicKey=fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575'        
```

- JSON Response Example:

```js
{"success":true,"enabled":false}    
```


### 2.5 Peers 
   
#### 2.5.1 Get all Peers' Information in the Whole Network   
---
- Interface Address: /api/peers   
- Request Methods: get   
- Supported Format:  urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|state |integer |N    |peer's status: 0:,1:,2:,3:     |   
|os|string|N|Linux kernel version|   
|version|string|N|acchain system version|   
|limit |integer |N    |maximum return records, minimum:0, maximum: 100|   
|orderBy|string|N||   
|offset|integer  |N      |offset, minimum 0  |   
|port|integer|N|port number，1~65535|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|peers|Array  |a JSON array of peers' information |    
|totalCount|integer|the number of currently running peers|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/peers?limit=1'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"peers": [{   
		"ip": "45.32.19.241",   
		"port": 4096,   
		"state": 2,   
		"os": "linux3.13.0-87-generic",   
		"version": "1.0.0"   
	}],   
	"totalCount": ["54"]   
}   
```   
   
#### 2.5.2 Get the Version of Peer
---
- Interface Address: /api/peers/version   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|version|string  |version number     |    
|build  |timestamp |built time     |    
|net    |string  |if the peer is mainnet or testnet     |   
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/peers/version   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"version": "1.0.0",   
	"build": "12:11:11 16/08/2016",   
	"net": "testnet"   
}   
```   
   
#### 2.5.3 Get the Peer Information of a Given IP Address   
---
- Interface Address: /api/peers/get   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|ip |string |Y    |peer's IP      |   
|port|integer|Y|peer's port，1~65535|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|peer|json  | peer's information     |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/peers/get?ip=45.32.248.33&port=4096'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"peer": {   
	}   
}   
```   
   
### 2.6 Sync and Loader  
#### 2.6.1 Get the local blockchain loading status  
--- 
- Interface Address: /api/loader/status   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|loaded |bool    |          |   
|blocksCount|integer||   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/loader/status -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"loaded": true,   
	"blocksCount": 0   
}   
```   
   
#### 2.6.2 Get the block syncing status
---
- Interface Address: /api/loader/status/sync   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height |int    |block height          |   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/loader/status/sync -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"syncing": false,  // show whether in synchronising. if yes, it will be "true". if there is no data to synchronise, it will be "false" 
	"blocks": 0,   
	"height": 111987   
}   
```   
   
### 2.7 Second Password   
#### 2.7.1 Set the Second Password
---
- Interface Address: /api/signatures   
- Request Methods: put   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|Y|acchain account's second password，minimum length：1，maximum length：100|   
|multisigAccountPublicKey|string|N|the public key of multi signatures account|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |the detail information of setting transaction   |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","secondSecret":"fault still attack alley expand music basket purse later educate follow ride"}' 'https://testnet.acchain.org/api/signatures'    
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transaction": {   
		"type": 1,  //the transaction type of setting second password is 1  
		"amount": 0,   
		"senderPublicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2",   
		"requesterPublicKey": null,   
		"timestamp": 4872315,   
		"asset": {   
			"signature": {   
				"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"   
			}   
		},   
		"recipientId": null,   
		"signature": "e76d9b25ec0fdaa88b19d59c5a222b7efdc04f738ee05896f55f4e6959229d9b1600ca25aa92fbea176668f3be7c12c506f2091e2b38c52ef0ece7a5d35e240a",   
		"id": "1614688380530105232",   
		"fee": 500000000,       //the transaction fee of setting second password is 5 ACC   
		"senderId": "250438937633388106"   
	}   
}   
```   
   
#### 2.7.2 Get the Transaction Fee of Setting Second Password
---
- Interface Address: /api/signatures/fee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee     |    
   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/signatures/fee -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"fee": 500000000         //5 ACC   
}     
```   
   
### 2.8 Multiple Signatures 
#### 2.8.1 Set Normal Account to Multi-signatures Account
---
- Interface Address: /api/multisignatures   
- Request Methods: put   
- Supported Format: json   
- Comment: the return value is transaction ID only. To successfully set to multi-signature account still needs other's signatures. Every transaction after registered as multi-signatures account will be asked for multiple signatures. The minimum necessary signatures is defined by "min" (include sender itself) 
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|N|acchain account's second password, minimum length:1 maximum length: 100|   
|min|integer|Y|the minimum signatures that is required to each transaction for multi-signatures account. (When the transaction is to register multi-signature account, this parameter will not work since everyone needs to sign.) Minimum:2, maximum:16. This number must not be larger than keysgroup.length+1. |   
|lifetime|integer|Y|the maximum pending time of multi-signature transaction. Minimum:1, maximum:24. NOTE: this parameter is not available currently.|   
|keysgroup|array|Y|an array containing other signaturers' public key. There are plus/minus (+/-) in front of each public key, means add or delete multi-signature account respectively. Minimum length:1, maximum length:10.|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |the multi-signature transaction ID     |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"vanish deliver message evil canyon night extend unusual tell prosper issue antenna","min":2,"lifetime":1,"keysgroup":["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97","+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"]}' 'https://testnet.acchain.org/api/multisignatures'  //publickey = 2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "17620378998277022323"     //only transaction ID is returned. To successfully set to multi-signature account needs other accounts' signatures.   
}   
```   
   
#### 2.8.2 Get the Detail Information of Pending Multi-signature Transaction
---
- Interface Address: /api/multisignatures/pending   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey|string  |Y|public key      |    
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |a JSON object list containing those pending transactions      |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": [{      //the detail information of the setting multi-signature account transaction (see 2.8.1, transactionId: 17620378998277022323)  
		"min": 2,   
		"lifetime": 1,   
		"signed": true,   
		"transaction": {   
			"type": 4,      //4 means registering multi-signature account   
			"amount": 0,   
			"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
			"requesterPublicKey": null,   
			"timestamp": 4879978,   
			"asset": {   
				"multisignature": {   
					"min": 2,   
					"keysgroup": ["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
					"+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],   
					"lifetime": 1   
				}   
			},   
			"recipientId": null,   
			"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
			"id": "17620378998277022323",   
			"fee": 1500000000,   
			"senderId": "3855903394839129841"   
		}   
	}]   
}   
   
```   
   
#### 2.8.3 Sign the Multi-signature Transaction (by non-initiator) 
---  
- Interface Address: /api/multisignatures/sign   
- Request Methods: post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|secondSecret|string|N|acchain account second password. Minimum length:1, maximum length:100|   
|publicKey|string  |N|public key      |    
|transactionId|string|Y|transaction ID|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |multi-signature transaction ID      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"lemon carpet desk accuse clerk future oyster essay seminar force live dog","transactionId":"17620378998277022323"}' 'https://testnet.acchain.org/api/multisignatures/sign'   //signed by a user whose public key is eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "17620378998277022323"   
}   
// Now get the pending transaction again   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
{   
	"success": true,   
	"transactions": [{   
		"min": 2,   
		"lifetime": 1,   
		"signed": true,   
		"transaction": {   
			"type": 4,   
			"amount": 0,   
			"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
			"requesterPublicKey": null,   
			"timestamp": 4879978,   
			"asset": {   
				"multisignature": {   
					"min": 2,   
					"keysgroup": ["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
					"+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],   
					"lifetime": 1   
				}   
			},   
			"recipientId": null,   
			"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
			"id": "17620378998277022323",   
			"fee": 1500000000,   
			"senderId": "3855903394839129841",   
			"signatures": ["b38a161264db2a23e353d3fbc4983562f6343d5ee693144543ca54e2bc67c0f73d1c761b7bfa38b2bb101ac2ab0797b674b1a9964ccd400aaa310746c3494d03"]      //new multi-signature generated   
		}   
	}]   
}   
   
// a user whose public key is "d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb" sign this registering transaction   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"chalk among elbow piece badge try van round quality position simple teach","transactionId":"17620378998277022323"}' 'https://testnet.acchain.org/api/multisignatures/sign'   
{"success":true,"transactionId":"17620378998277022323"}   
// trying to get pending transaction again, but this time there isn't any of it.   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
{"success":true,"transactions":[]}   
// Check the detail of this transaction. (at this time, this transaction has been broadcasted to the whole network and been written to the blockchain) Now the account has already registered as a multi-signature account. 
curl -k -X GET https://testnet.acchain.org/api/transactions/get?id=17620378998277022323   
{   
	"success": true,   
	"transaction": {   
		"id": "17620378998277022323",   //the registering transaction ID   
		"height": "157013",   
		"blockId": "4680888982781013372",   
		"type": 4,   
		"timestamp": 4879978,   
		"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
		"senderId": "3855903394839129841",   
		"recipientId": "",   
		"amount": 0,   
		"fee": 1500000000,   
		"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "26",   
		"asset": {   
			   
		}   
	}   
}   
   
```   
   
#### 2.8.4 Get Detail Information of the Multi-signature Account
---
- Interface Address: /api/multisignatures/accounts   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |One of the participants‘ public key      |   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|Array  |the detail of this multi-signature account   |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/accounts?publicKey=eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"accounts": [{   
		"address": "3855903394839129841",       //the address of this multi-signature account   
		"balance": 18500000000,     //the balance of this multi-signature account   
		"multisignatures": ["eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
		"d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],    //the public key of this multi-signature account   
		"multimin": 2,  //minimum required signature  
		"multilifetime": 1,   
		"multisigaccounts": [{          //the detail of signer's account  
			"address": "13542769708474548631",   
			"publicKey": "eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
			"balance": 0   
		},   
		{   
			"address": "4100816257782486230",   
			"publicKey": "d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb",   
			"balance": 0   
		}]   
	}]   
}   
```   

### 2.9 Peer to Peer Transportation(secure API)
#### 2.9.1 Overview 
---
To request a peer related API, it is required to set a header like this:  

 - key=magic, and value=8e9b66ed  
 - key=version, and value=''  

#### 2.9.2 Transaction 
---
All the writing operations in acchain system are finished by starting a transaction.
The transaction data is generated through a JS library named "Acchain-js", and then broadcasted by a POST API.
The POST API specification is as follows:

payload: transaction data generated by Acchain-js
API Address: /peer/transactions  
Request Methods: POST   
Supported Format: JSON  

##### 2.9.2.1 Set the Second Payment Password
--- 
Request Parameter Description:  

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.signature.createSignature]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');    
var transaction = Acchain.signature.createSignature('measure bottom stock hospital calm hurdle come banner high edge foster cram','erjimimashezhi001')       
console.log(JSON.stringify(transaction))  
{"type":1,"amount":0,"fee":500000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5328943,"asset":{"signature":{"publicKey":"27116db89cb5a8c02fb559712e0eabdc298480d3c79a089b803e35bc5ef7bb7b"}},"signature":"71ef98b1600f22f3b18cfcf17599db3c40727c230db817f610e86454b62df4fb830211737ff0c03c6a61ecfd4a9fcb68a30b2874060bb33b87766acf800e820a","id":"15605591820551652547"}   

// submit above data of setting second password to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":1,"amount":0,"fee":500000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5328943,"asset":{"signature":{"publicKey":"27116db89cb5a8c02fb559712e0eabdc298480d3c79a089b803e35bc5ef7bb7b"}},"signature":"71ef98b1600f22f3b18cfcf17599db3c40727c230db817f610e86454b62df4fb830211737ff0c03c6a61ecfd4a9fcb68a30b2874060bb33b87766acf800e820a","id":"15605591820551652547"}}' https://testnet.acchain.org/peer/transactions   
```   
   
- JSON Response Example:   

```js  
{
    "success":true  //setting is successful
}	
``` 

##### 2.9.2.2 Transfer Money
---
- Request Parameter Description:   

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.transaction.createTransaction]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');   
var targetAddress = "16358246403719868041";  
var amount = 100*100000000;   //100 ACC
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';

// in above code, password is recorded when user logs in. meanwhile the second password needs to be input every time by user.
// To input or not depends on whether user has second password, which can be identified by "user.secondPublicKey" function.

var transaction = Acchain.transaction.createTransaction(targetAddress, amount, password, secondPassword || undefined);       
JSON.stringify(transaction)
'{"type":0,"amount":10000000000,"fee":10000000,"recipientId":"16358246403719868041","timestamp":5333378,"asset":{},"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","signature":"2d47810b7d9964c5c4d330a53d1382769e5092b3a53639853f702cf4a382aafcff8ef8663c0f6856a23f41c249944f0c3cfac0744847268853a62af5dd8fc90a","signSignature":"dfa9b807fff362d581170b41c56a2b8bd723c48d1f100f2856d794408723e8973016d75aeff4705e6837dcdb745aafb41aa10a9f1ff8a77d128ba3d712e90907","id":"16348623380114619131"}'

// submit above data of transfer to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":0,"amount":10000000000,"fee":10000000,"recipientId":"16358246403719868041","timestamp":5333378,"asset":{},"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","signature":"2d47810b7d9964c5c4d330a53d1382769e5092b3a53639853f702cf4a382aafcff8ef8663c0f6856a23f41c249944f0c3cfac0744847268853a62af5dd8fc90a","signSignature":"dfa9b807fff362d581170b41c56a2b8bd723c48d1f100f2856d794408723e8973016d75aeff4705e6837dcdb745aafb41aa10a9f1ff8a77d128ba3d712e90907","id":"16348623380114619131"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:  
 
```js  
{
    "success":true  //transfer success
}		
``` 

##### 2.9.2.3 Register Delegates   
---
- Request Parameter Description:  

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.delegate.createDelegate]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether transaction is success |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');   
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';
var userName = 'zhenxi_test';  

var transaction = Acchain.delegate.createDelegate(password, userName, secondPassword || undefined);   
JSON.stringify(transaction)  
'{"type":2,"amount":0,"fee":10000000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334485,"asset":{"delegate":{"username":"zhenxi_test","publicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f"}},"signature":"a12ce415d2d21ab46e4c1b918b8717b1d351dd99abd6f2f94d9a1a7e1f32b697f843a05b1851cb857ea45a2476dce592f5ddd612c00cd44488b8b610c57d7f0a","signSignature":"35adc9f1f37d14458e8588f9b4332eedf1151c02480159f64a287a4b0cbb59bfe82040dfec96a4d9560bae99b8eaa1799a7023395db5ddc640d95447992d6e00","id":"12310465407307249905"}'

// submit above data of registering delegate to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":2,"amount":0,"fee":10000000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334485,"asset":{"delegate":{"username":"zhenxi_test","publicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f"}},"signature":"a12ce415d2d21ab46e4c1b918b8717b1d351dd99abd6f2f94d9a1a7e1f32b697f843a05b1851cb857ea45a2476dce592f5ddd612c00cd44488b8b610c57d7f0a","signSignature":"35adc9f1f37d14458e8588f9b4332eedf1151c02480159f64a287a4b0cbb59bfe82040dfec96a4d9560bae99b8eaa1799a7023395db5ddc640d95447992d6e00","id":"12310465407307249905"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:   

```js  
{
    "success":true  //register successfully
}		
``` 

##### 2.9.2.4 Vote and Cancel the vote  
---
- Request Parameter Description: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.vote.createVote]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:  
 
```js   
var acchain = require('Acchain-js');   
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';
// the voting content is a list in which each item consists of a symbol (+ or -) and the delegate's public key. The "+" means vote, and "-" means cancel the vote.
var voteContent = [
    '-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7',
    '+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2'
];

var transaction = Acchain.vote.createVote(password, voteContent, secondPassword || undefined);
JSON.stringify(transaction)
{"type":3,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334923,"asset":{"vote":{"votes":["-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7","+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2"]}},"signature":"6036c2066a231c452a1c83aafd3bb9db3842ee05d5f17813f8264a4294cdec761faa89edf4a95f9b2e2451285807ab18aa9f989ad9a3165b95643179b8e4580f","signSignature":"a216ca739112e6f65986604b9467ccc8058138a7077faf134d6c4d673306cd1c514cc95bd54a036f7c602a56c4b4f2e4e59f6aa7c376cb1429e89054042e050b","id":"17558357483072606427"}

// submit above data of vote/cancel vote to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":3,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334923,"asset":{"vote":{"votes":["-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7","+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2"]}},"signature":"6036c2066a231c452a1c83aafd3bb9db3842ee05d5f17813f8264a4294cdec761faa89edf4a95f9b2e2451285807ab18aa9f989ad9a3165b95643179b8e4580f","signSignature":"a216ca739112e6f65986604b9467ccc8058138a7077faf134d6c4d673306cd1c514cc95bd54a036f7c602a56c4b4f2e4e59f6aa7c376cb1429e89054042e050b","id":"17558357483072606427"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:  
 
```js  
{
    "success":true  //transaction of vote/cancel the vote is success
}		
``` 

### 2.10 User Identify Assets

#### 2.10.1 Get assets info

##### 2.10.1.1 Get all issuers
---
- Interface Address: /api/uia/issuers
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|issuers|list  |element is dictionary, each dictionary represents a issuer, including "name", "desc", "issuerId" |
|count  | integer | count of issuers | 

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers?offset=0&limit=1' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "issuers": [{
        "name": "zhenxi",
        "desc": "this is a description",
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    },
    {
        "name": "speedtest",
        "desc": "speedtest",
        "issuerId": "AEVWQWAq3TEJkCPSDxXMP2uCRrL2xbQnsy"
    }],
    "count": 6
}       
```

##### 2.10.1.2 Get the issuers info
---
- Interface Address: /api/uia/issuers/:name
    - "name" could be the issuer's name or acchain account address.
- Request Methods: get
- Supported Format: urlencoded
- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|issuers|list  |element is dictionary, each dictionary represents a issuer, including "name", "desc", "issuerId" |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers/zhenxi' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "issuer": {
        "name": "zhenxi",
        "desc": "this is a description",
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    }
}
```

##### 2.10.1.3 Get the issuer assets
---
- Interface Address: /api/uia/issuers/name/assets
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name   | string | Y | issuer's name or acchain account address| 
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "name", ... |
|count | integer | the issuer's registered assets | 

- Request Example: 

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers/zhenxi/assets?offset=0&limit=2' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "assets": [{
            "currency": "BTC",
            "name": "zhenxi.UIA",
            "desc": "this is a description",
            "maximum": "10000000",
            "precision": 3,
            "strategy": "",
            "quantity": "1000000",
            "height": 301,
            "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
            "acl": 0,
            "writeoff": 1
    }],
    "count": 1
}   
```

##### 2.10.1.4 Get all assets
---
- Interface Address: /api/uia/issuers/name/assets
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |


- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "maximum", ... |
|count | integer | the issuer's registered assets | 

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets?offset=0&limit=2' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "assets": [{
        "name": "zhenxi.UIA",
        "desc": "this is a description",
        "maximum": "10000000",
        "precision": 3,
        "strategy": "",
        "quantity": "1000000",
        "height": 301,
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
        "acl": 0,
        "writeoff": 1
    },
    {
        "name": "speedtest.SPEED",
        "desc": "this is a description",
        "maximum": "10000",
        "precision": 1,
        "strategy": "",
        "quantity": "10000",
        "height": 380,
        "issuerId": "AEVWQWAq3TEJkCPSDxXMP2uCRrL2xbQnsy",
        "acl": 0,
        "writeoff": 0
    }],
    "count": 13
}       
```

##### 2.10.1.5 Get info by asset name
---
- Interface Address: /api/uia/assets/:name
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name | string | Y | asset name |

- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "maximum", ... |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets/zhenxi.UIA' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "asset": {
        "name": "zhenxi.UIA",
        "desc": "this is a description",
        "maximum": "10000000",
        "precision": 3,
        "strategy": "",
        "quantity": "1000000",
        "height": 301,
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
        "acl": 0,
        "writeoff": 1
    }
}
```


##### 2.10.1.6 Get the applying assets
---
- Interface Address: /api/uia/assets/applying
- Request Methods: get
- JSON Response Example:

```js
{
    "success":true,
    "assets":[
        {
            "currency":"A.AAA",
            "name":"A.sfsf",
            "desc":"sfasfsa",
            "maximum":"1000000000",
            "precision":1,
            "quantity":"0",
            "height":6931,
            "issuerId":"ACfjnjJtP9ZkprdLioohFS6Jp2CrAGfMS",
            "issuerName":"A",
            "category":"010912",
            "estimateUnit":"RMB",
            "estimatePrice":"100000000",
            "exerciseUnit":"sfasfsa",
            "extra":"{"productBrand":{"value":"sfasfsa"},"packingStandard":{"value":"sfasfsa"},"productIndex":{"value":"sfasfsa"},"productionInfo":{"value":"sfasfsa"},"otherInfo":{"value":"sfasfsa"}}",
            "unlockCondition":0,
            "approved":0
        }
    ],
    "count":1
}
```

##### 2.10.1.7 Get the applying issues
---
- Interface Address: /api/uia/issues/applying
- Request Methods: get
- JSON Response Example: 

```js
{
success: true,
issues: [
        {
            transactionId: "431dd812d00e2c7a9242b1b0f1bbf33b80b27e4a8bf333755673ab3ac0ff9d08",
            currency: "PuerBank.PEB",
            amount: "10000000",
            exchangeRate: "0.2",
            senderId: "A7KaYaLnWhSwCzrFVeE1TcXCQUY8WHB9hR"
        }
    ],
count: 1
}
```

##### 2.10.1.8 Get approved assets
---
- Interface Address: /api/uia/assets/approved
- Request Methods: get 
- JSON Response Example:

```js
{
    "success":true,
    "assets":[
        {
            "currency":"BTC",
            "name":"Bitcoin",
            "desc":"Bitcoin is a cryptocurrency and a digital payment system invented by an unknown programmer, or a group of programmers, under the name Satoshi Nakamoto. It was released as open-source software in 2009",
            "maximum":"21000000000000",
            "precision":6,
            "quantity":"50000000000",
            "height":1,
            "issuerId":"AGUaZUoJG5CYqPX32mWAcYQSKjvXu83V8o",
            "issuerName":"__SYSTEM__",
            "category":"1801",
            "estimateUnit":"RMB",
            "estimatePrice":"8000",
            "exerciseUnit":"1",
            "extra":"No extra information",
            "unlockCondition":0,
            "approved":1
        },
        {
            "currency":"asd.BUHG",
            "name":"asd.BUHG",
            "desc":"BUHG",
            "maximum":"1000000000",
            "precision":1,
            "quantity":"10000000",
            "height":6158,
            "issuerId":"APfs15A8KegKu1TtnJsWJvLoFxCKT7pRos",
            "issuerName":"asd",
            "category":"1717",
            "estimateUnit":"RMB",
            "estimatePrice":"100000000",
            "exerciseUnit":"BUHG",
            "extra":"{"productBrand":{"value":"BUHG"},"packingStandard":{"value":"BUHG"},"productIndex":{"value":"BUHG"},"productionInfo":{"value":"BUHG"},"otherInfo":{"value":"BUHG"}}",
            "unlockCondition":1,
            "approved":1
        },
        {
            "currency":"meiyingjugroup.RETSCHSR",
            "name":"RETSCHSR",
            "desc":"RET to House",
            "maximum":"6558750000",
            "precision":1,
            "quantity":"0",
            "height":7199,
            "issuerId":"ADfjWCQ6Ff5c2g62jzJbyQwHAe68TH1QWJ",
            "issuerName":"meiyingjugroup",
            "category":"1732",
            "estimateUnit":"USD",
            "estimatePrice":"655875000",
            "exerciseUnit":"220000",
            "extra":"{"productBrand":{"value":"Serene Country Homes"},"packingStandard":{},"productIndex":{},"productionInfo":{},"otherInfo":{}}",
            "unlockCondition":0,
            "approved":1
        }
    ],
    "count":3
}
```

##### 2.10.1.9 Get the assets access control lists
---
- Interface Address: /api/uia/assets/name/acl/flag
- Request Methods: get 
- Supported Format: urlencoded

- Request Parameter Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name | string | Y | asset name |
|flag | boole | Y | 0 or 1, 0: black lists, 1: white lists |
|limit	|integer  | N  |the limitation of returned records，minimum：0,maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|success | boole | success or failure  |
|list | list | the address list  |
|count | integer | the list count |

- Request Example:

```js
// get zhenxi.UIA white lists 
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets/zhenxi.UIA/acl/1' && echo
```

- JSON Response Example: 

```js
{
    "success": true,
    "list": [{
        "address": "15745540293890213312"
    },
    {
        "address": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    }],
    "count": 2
}       
```

##### 2.10.1.10 Get all the assets info of gave address
---
- Interface Address: /api/uia/balances/:address
    - `address` represents for user account address.
- Request Methods: get
- Supported Format: urlencoded
- Request Parameter Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|success | boole | success or failure  |
|balances | list | owned asset info list, each element is a asset, including some details  |
|count | integer |the assets count of this address   |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json" 'http://testnet.acchain.org/api/uia/balances/AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "balances": [{
            "currency": "zhenxi.UIA",
            "name":"UIA",
            "balance": "900000",
            "maximum": "10000000",
            "precision": 3,
            "quantity": "1000000",
            "writeoff": 1
    },
    {
            "currency": "speedtest.SPEED",
            "balance": "400",
            "maximum": "10000",
            "precision": 1,
            "quantity": "10000",
            "writeoff": 0
    }],
    "count": 2
}       
```

##### 2.10.1.11 Get UIA Exercise
---
- Interface Address: /api/uia/exercises
- Request Methods: get
- Supported Format: none
    - if no parameter passed, it will return all exercise record

- Request Parameter Description:  

|Name	|Type   |Required |Description              |    
|------ |-----  |---  |----              |   
|currency|string  |N      |exercise record of this currency   |
|id| string | N | account id |

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|boole  |success or failure |    
|exercises|json  |list of exercise，each contains transactionId, currency, timestamp..|
|count  |integer  | exercise count |
   
   
- Request Example:
   
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/uia/exercises?currency=TESTREAL.RET'  
// or
curl -k -X GET 'https://testnet.acchain.org/api/uia/exercises?id=3bf8892a33eadb2617dbc35934a4781bd0a50834524208a68faedb39fc12b510' 
```   
   
- JSON Response Example:
   
```
{"success":true,"exercises":[{"transactionId":"d5cf82f37a35537e73cb921f662b4fe162e7c4d715e4c397a4811db6cf949057","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29254858},{"transactionId":"086c912812c8b7ee0bd70cff80cbed83f0efa8a08230722fdf5b5502b1aa6238","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29254924},{"transactionId":"f7649cf70ad62203c7279be3e3cd0d8b7ecdf5e2073ab20546d521ca87a729ba","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29311954}],"count":3}
```


#### 2.10.2 Create UIA Transaction
---
Acchain system's every operation is raised by a transaction. The transaction is built by a framework called "AcchainJS", then POST the transaction.

##### 2.10.2.1 Create Issuer
---
- Interface Address: /peer/transactions
- Request Methods: get
- Supported Format: json
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createIssuer(name, desc, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
// issuer name, unique
var name = 'IssuerName'
// issuer description
var desc = 'IssuerDesc'
// create issuer
var trs = AcchainJS.uia.createIssuer(name, desc, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":9,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19395607,"asset":{"uiaIssuer":{"name":"IssuerName","desc":"IssuerDesc"}},"signature":"c6ed2a4bafe2b8aa31f4aaceacc2a96cb028abbabb2ed062937498c58e24ca5467a340ddd63b67f809a680ff91b83e685c64991eb695494ddb2fdc57e5761607","signSignature":"8eceacbd47c2b8ed335145ced19d7a3a51f99bdd6631d16ed214180c6f80e29bd6d572f45e7c7d685584e55cb5c303cf340406553ece28c9c0a2fa7a777aac0b"}

// http post the 'trs' to the server, register issuer name
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":9,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19395607,"asset":{"uiaIssuer":{"name":"IssuerName","desc":"IssuerDesc"}},"signature":"c6ed2a4bafe2b8aa31f4aaceacc2a96cb028abbabb2ed062937498c58e24ca5467a340ddd63b67f809a680ff91b83e685c64991eb695494ddb2fdc57e5761607","signSignature":"8eceacbd47c2b8ed335145ced19d7a3a51f99bdd6631d16ed214180c6f80e29bd6d572f45e7c7d685584e55cb5c303cf340406553ece28c9c0a2fa7a777aac0b"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true}  
```

##### 2.10.2.2 Register Assets
---
- Interface Address: /peer/transactions
- Request Methods: post
- Supported Format: json
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createAsset(name, desc, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var extra = {
    "productBrand": {
        "value":"ABC",
        "remark":"ABC",
        "link":"ABC"
    },
    "packingStandard": {
        "value":"BCD",
        "remark":"BCD",
        "link":"BCD"
    },
    "productIndex": {
        "value":"CDE",
        "remark":"CDE",
        "link":"CDE"
    },
    "productionInfo": {
        "value":"DEF",
        "remark":"DEF",
        "link":"DEF"
    },
    "otherInfo": {
        "value":" ",
        "remark":" ",
        "link":" "
    },
    "moreDetails":" "
}
var payload = {
    name: 'IssuerName.CNY',// assets name，issuer.assetsName，unique
    currency: "CNY",// currency: BTC,ETH..
    desc: 'this is a description',
    category: '',// assets category
    precision: 3,// precision，for instance: maximum = 1000000，precision = 3，and the IssuerName.CNY actual maximum is 1000.000
    maximum: '1000000',
    estimateUnit: '',
    estimatePrice: '',
    exerciseUnit: '',
    unlockCondition: 0,// unlock condition = 0 or 1
    extra: extra
}
// create assets
var trs = AcchainJS.uia.createAsset(payload, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":10,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19397444,"asset":{"uiaAsset":{"name":"IssuerName.CNY","desc":"this is a description","maximum":"1000000","precision":3,"strategy":""}},"signature":"c755587d331dd2eb62ef91dce1511d83a3e603c7cdc7548a16052519c21ea89c78364e35e5d46da0e2103fa2fb7f037eec55a5deba18826fa13e4252422d750e","signSignature":"1b7ed4c21c477b8ff3d2acfdfd7ff85617093f4c21de70938c46b61c9704b037dbcf7f9e5f5dd1a5dc8f22cf473aaa459e6e5b15ced388b8a1da1e307987a509"}

// http post the 'trs' to the server，register assset IssuerName.CNY
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":10,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19397444,"asset":{"uiaAsset":{"name":"IssuerName.CNY","desc":"资产描述","maximum":"1000000","precision":3,"strategy":""}},"signature":"c755587d331dd2eb62ef91dce1511d83a3e603c7cdc7548a16052519c21ea89c78364e35e5d46da0e2103fa2fb7f037eec55a5deba18826fa13e4252422d750e","signSignature":"1b7ed4c21c477b8ff3d2acfdfd7ff85617093f4c21de70938c46b61c9704b037dbcf7f9e5f5dd1a5dc8f22cf473aaa459e6e5b15ced388b8a1da1e307987a509"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true} 
```

##### 2.10.2.3 Assets Issue
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createIssue(currency, amount, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// 本次发行量=真实数量（100）*10**精度（3），所有发行量之和需 <= 上限*精度
var amount = '100000'
var trs = AcchainJS.uia.createIssue(currency, amount, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":13,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19475744,"asset":{"uiaIssue":{"currency":"IssuerName.CNY","amount":"100000"}},"signature":"32b01a18eca2b0dc7e2ce77ba4e758eaae2532f60844760a762cc20918e7439ac6ca585b921db6ede833ed0bf1c62e30cec545a928abafe0b679183a6ad02202","signSignature":"4fc290d7d7d788e9112a56233df0fe796cba39be3efa0cebf00cbc7e5bc5fd1369fad49e5698d967845b5c02e427926049cab25845d4d385e4a395791906f909"}

curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":13,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19475744,"asset":{"uiaIssue":{"currency":"IssuerName.CNY","amount":"100000"}},"signature":"32b01a18eca2b0dc7e2ce77ba4e758eaae2532f60844760a762cc20918e7439ac6ca585b921db6ede833ed0bf1c62e30cec545a928abafe0b679183a6ad02202","signSignature":"4fc290d7d7d788e9112a56233df0fe796cba39be3efa0cebf00cbc7e5bc5fd1369fad49e5698d967845b5c02e427926049cab25845d4d385e4a395791906f909"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true,"transactionId":"ffd7500b944451adfaea20578a9ecab382e66dc8a11358901dfa8456c4aaa91d"}
```

##### 2.10.2.4 Assets Transfer
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createTransfer(currency, amount, recipientId, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// amount（10000）=真实数量（10）*10**精度（3），需 <= 当前资产发行总量
var amount = '10000'
// 接收地址，需满足前文定义好的acl规则
var recipientId = 'AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a'
var trs = AcchainJS.uia.createTransfer(currency, amount, recipientId, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":14,"amount":0,"fee":10000000,"recipientId":"AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a","senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19481489,"asset":{"uiaTransfer":{"currency":"IssuerName.CNY","amount":"10000"}},"signature":"77789071a2ad6d407b9d1e0d654a9deb6d85340a3d2a13d786030e26ac773b4e9b5f052589958d2b8553ae5fc9449496946b5c225e0baa723e7ddecbd89f060a","signSignature":"f0d4a000aae3dd3fa48a92f792d4318e41e3b56cdbaf98649261ae34490652b87645326a432d5deb69f771c133ee4b67d2d22789197be34249e6f7f0c30c1705"}

// send 'AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a' 10.000 IssuerName.CNY asset
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":14,"amount":0,"fee":10000000,"recipientId":"AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a","senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19481489,"asset":{"uiaTransfer":{"currency":"IssuerName.CNY","amount":"10000"}},"signature":"77789071a2ad6d407b9d1e0d654a9deb6d85340a3d2a13d786030e26ac773b4e9b5f052589958d2b8553ae5fc9449496946b5c225e0baa723e7ddecbd89f060a","signSignature":"f0d4a000aae3dd3fa48a92f792d4318e41e3b56cdbaf98649261ae34490652b87645326a432d5deb69f771c133ee4b67d2d22789197be34249e6f7f0c30c1705"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```
  
- JSON Response Example:
  
```js
{"success":true} 
```
##### 2.10.2.5 Assets Exercise
--- 
- Request Parameter Description:

|Name	|Type   |Required |Description   |  
|------ |-----  |---  |----      |   
|transaction|json|Y|AccchainJS.uia.createExercise data created by currency、amount、secret、secondSecret|

- Response Parameter Description:   

|Name	|Type   |Description |  
|------ |-----  |----   |   
|success|boole  |success or failure |  

- Request Example:

```js   
var currency = 'IssuerName.CNY'
var amount = '1000'
var message = '这是备注信息'
var trs = AccchainJS.uia.createExercise(currency, amount, message, secret, secondSecret)
console.log(JSON.stringify(trs))
 {"type": 12, "amount": "0", "fee": 100000, "recipientId": null, "senderPublicKey":"a7628dc36cc9be73a9d4aa5a61c4ed36ff0ef150139e503f7ced47f237cb2fcf", "timestamp": 29252257, "asset": {"uiaExercise": {"currency": "TESTREAL.RET", "amount":"100"}},"signature":"d4571a90222e77930c125c64d0e710edd2b5aa686ba66e45d80f7d78694ba72115cdfe52e6190cefc88131a5171b03eaba6f25757c800545aeef2a8b82152d0a"}

curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type": 12, "amount": "0", "fee": 100000, "recipientId": null,"senderPublicKey":"a7628dc36cc9be73a9d4aa5a61c4ed36ff0ef150139e503f7ced47f237cb2fcf", "timestamp": 29252257, "asset": {"uiaExercise":{"currency":"TESTREAL.RET","amount":"100"}},"signature":"d4571a90222e77930c125c64d0e710edd2b5aa686ba66e45d80f7d78694ba72115cdfe52e6190cefc88131a5171b03eaba6f25757c800545aeef2a8b82152d0a"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```   
   
- JSON Response Example:  

```js  
{"success":true}        
``` 


#### 2.10.3 UIA Vote

##### 2.10.3.1 Get voters by assets currency

- Interface Address: /api/uia/assets/:currency/voters
    - `currency` is the symbol of the assets, for example: TEST.ABC
- Request Methodss: get
- JSON Response Example:

```js
{
    "success": true,
    "voters": [
        {
            "voter": "delegate1",  
            "weight": "500"
        }
    ],
  "count": 9
}
```

##### 2.10.3.2 Get voters for issues 
---
- Interface Address: /api/uia/issues/:id/voters
    - `id` is a transaction from previous interface.
- Request Methods: post
- JSON Response Example:

```js
{
    "success": true,
    "voters": [
        {
            "voter": "delegate1",  
            "weight": "500"
        }
    ],
  "count": 9
}
```

#### 2.10.4 UIA Control

##### 2.10.4.1 Set `acl` mode
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createFlags(currency, flagType, flag, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// 1：circulation，2：withdraw
var flagType = 1
// acl mode，0：black list， 1：white list，default mode is black list after asset created
var flag = 1
var trs = AcchainJS.uia.createFlags(currency, flagType, flag, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":11,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19400996,"asset":{"uiaFlags":{"currency":"IssuerName.CNY","flagType":1,"flag":1}},"signature":"b96fb3d1456e1f26357109cc24d82834eb9a4687f29e69c374bbb1d534568336e148cac52f213aa4d2a69185092f8e1143b49ec4b8048cd9b3af4e20f6ba0b08","signSignature":"b37c77ebebe90341346be2aefe1e12bd7403e5d8f4d6e8f04630190b3e09494a28820da0ffd5f9ff011033aa6d70fc9bb4c159a4493be3b18fd7ff470103570d"}

// post the 'trs' to server，change the acl mode to white list
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":11,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19400996,"asset":{"uiaFlags":{"currency":"IssuerName.CNY","flagType":1,"flag":1}},"signature":"b96fb3d1456e1f26357109cc24d82834eb9a4687f29e69c374bbb1d534568336e148cac52f213aa4d2a69185092f8e1143b49ec4b8048cd9b3af4e20f6ba0b08","signSignature":"b37c77ebebe90341346be2aefe1e12bd7403e5d8f4d6e8f04630190b3e09494a28820da0ffd5f9ff011033aa6d70fc9bb4c159a4493be3b18fd7ff470103570d"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true} 
```

##### 2.10.4.2 Update acl lists
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createAcl(currency, operator, flag, list, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// '+'add list， ‘-’remove list
var operator = '+'
var list = ['15745540293890213312']
// acl type，0：black list， 1：white list
var flag =1
var trs = AcchainJS.uia.createAcl(currency, operator, flag, list, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":12,"amount":0,"fee":20000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19403125,"asset":{"uiaAcl":{"currency":"IssuerName.CNY","operator":"+","flag":1,"list":["15745540293890213312"]}},"signature":"ad4060e04c1a12256de114e34499f8add24326753f1f8362991ee14aefc4c0fe90ff394d2db97e83770855a5688d463de00656fdd2d04604605cf3c04fdaca0e","signSignature":"63129c58b1b9fcce88cbe829f3104a10ab06037253e9b65feb50ce0d2bb988533b93e8edcad016a85675f9027758fc318cf899ca7ef161a95a8d8a055ae83a02"}

// post the 'trs' to server，add ['15745540293890213312'] to white list，only modify the list，not modify the acl mode，cost fee 0.2ACC
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":12,"amount":0,"fee":20000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19403125,"asset":{"uiaAcl":{"currency":"IssuerName.CNY","operator":"+","flag":1,"list":["15745540293890213312"]}},"signature":"ad4060e04c1a12256de114e34499f8add24326753f1f8362991ee14aefc4c0fe90ff394d2db97e83770855a5688d463de00656fdd2d04604605cf3c04fdaca0e","signSignature":"63129c58b1b9fcce88cbe829f3104a10ab06037253e9b65feb50ce0d2bb988533b93e8edcad016a85675f9027758fc318cf899ca7ef161a95a8d8a055ae83a02"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true}
// check updated lists（acl/1:white list）
curl -X GET -H "Content-Type: application/json" 'http://testnet.acchain.org/api/uia/assets/IssuerName.CNY/acl/1?limit=10&offset=0' && echo
{
    "success": true,
    "list": [{
        "address": "15745540293890213312"
    }],
    "count": 1
}
```


#### 2.10.5 Get Assets Category

##### 2.10.5.1 Get First Category
---
- Interface Address: /api/uia/categories/0
- Request Methods: get
- JSON Response Example:

```js
{
    "success": true,
    "categories": [
        {
            "id": "01",
            "attrs": ["food"],
            "hasChildren": true
        },
        {
            "id": "02",
            "attrs": ["cloth"],
            "hasChildren": true
        }
    ],
  "count": 9
}
```

##### 2.10.5.2 Get Category By id
---
- Interface Address: /api/uia/categories/:id
    - `id` is the previous number.
- Request Methods: get
- JSON Response Example:

```js
{
    "success": true,
    "categories": [
        {
            "id": "1001",
            "attrs": ["BTC"]，
            "hasChildren": false
        },
        {
            "id": "1002",
            "attrs": ["LTC"],
            "hasChildren": false
        1}
    ],
  "count": 9
}
```

`attrs` represents the goods category name, and may be serval language, the first is the English, the second is the Chinese. 


## Appendix: Install 'Acchain-js' library   

All the writing operations in Acchain system are finished by starting a transaction.
The transaction data is generated through a JS library named "Acchain-js", and then broadcasted by a POST API.
  
**Install the library**   
`npm install Acchain-js`   
   


      * [2.5 Peers](#25-peers)
        * [2.5.1 Get all Peers' Information in the Whole Network](#251-get-all-peers-information-in-the-whole-network)
        * [2.5.2 Get the Version of Peer](#252-get-the-version-of-peer)
        * [2.5.3 Get the Peer Information of a Given IP Address](#253-get-the-peer-information-of-a-given-ip-address)
      * [2.6 Sync and Loader](#26-sync-and-loader)
        * [2.6.1 Get the local blockchain loading status](#261-get-the-local-blockchain-loading-status)
        * [2.6.2 Get the block syncing status](#262-get-the-block-syncing-status)
      * [2.7 Second Password](#27-second-password)
        * [2.7.1 Set the Second Password](#271-set-the-second-password)
        * [2.7.2 Get the Transaction Fee of Setting Second Password](#272-get-the-transaction-fee-of-setting-second-password)
      * [2.8 Multiple Signatures](#28-multiple-signatures)
        * [2.8.1 Set Normal Account to Multi-signatures Account](#281-set-normal-account-to-multi-signatures-account)
        * [2.8.2 Get the Detail Information of Pending Multi-signature Transaction](#282-get-the-detail-information-of-pending-multi-signature-transaction)
        * [2.8.3 Sign the Multi-signature Transaction (by non-initiator)](#283-sign-the-multi-signature-transaction-by-non-initiator)
        * [2.8.4 Get Detail Information of the Multi-signature Account](#284-get-detail-information-of-the-multi-signature-account)
      * [2.9 Peer to Peer Transportation(secure API)](#29-peer-to-peer-transportationsecure-api)
        * [2.9.1 Overview](#291-overview)
        * [2.9.2 Transaction](#292-transaction)
          * [2.9.2.1 Set the Second Payment Password](#2921-set-the-second-payment-password)
          * [2.9.2.2 Transfer Money](#2922-transfer-money)
          * [2.9.2.3 Register Delegates](#2923-register-delegates)
          * [2.9.2.4 Vote and Cancel the vote](#2924-vote-and-cancel-the-vote)
      * [2.10 User Identify Assets](#210-user-identify-assets)
        * [2.10.1 Get assets info](#2101-get-assets-info)
          * [2.10.1.1 Get all issuers](#21011-get-all-issuers)
          * [2.10.1.2 Get the issuers info](#21012-get-all-issuers-info)
          * [2.10.1.3 Get the issuer assets](#21012-get-the-issuer-assets)
          * [2.10.1.4 Get all assets](#21014-get-all-assets)
          * [2.10.1.5 Get info by asset name](#21015-get-info-by-asset-name)
          * [2.10.1.6 Get the applying assets](#21016-get-the-applying-assets)
          * [2.10.1.7 Get the applying issues](#21017-get-the-applying-issues)
          * [2.10.1.8 Get approved assets](#21018-get-approved-assets)
          * [2.10.1.9 Get the assets access control lists](#21019-get-the-assets-access-control-lists)
          * [2.10.1.10 Get all the assets info of gave address](#210110-get-all-the-assets-info-of-gave-address)
          * [2.10.1.11 Get UIA Exercise](#210111-get-uia-exercise)
      * [2.10.2 Create UIA Transaction](#2102-create-uia-transaction)
        * [2.10.2.1 Create Issuer](#21021-create-issuer)
        * [2.10.2.2 Register Assets](#21022-register-assets)
        * [2.10.2.3 Assets Issue](#21023-assets-issue)
        * [2.10.2.4 Assets Transfer](#21024-assets-transfer)
        * [2.10.2.5 Assets Exercise](#21025-assets-exercise)
      * [2.10.3 UIA Vote](#2103-uia-vote)
        * [2.10.3.1 Get voters by assets currency](#21031-get-voters-by-assets-currency)
        * [2.10.3.2 Get voters for issues](#21032-get-voters-for-issues)
      * [2.10.4 UIA Control](#2104-uia-control)
        * [2.10.4.1 Set acl mode](#21041-set-acl-mode)
        * [2.10.4.2 Update acl lists](#21042-update-acl-lists)
      * [2.10.5 Get Assets Category](#2105-get-assets-category)
        * [2.10.5.1 Get First Category](#21051-get-first-category)
        * [2.10.5.2 Get Category By id](#21052-get-category-by-id)
* [Appendix: Install 'Acchain-js' library](#appendix-install-Acchain-js-library)
        
---

## 1 API Usage Guide

### 1.1 Request Process Overview
---
- **Generate request data:** according the interface specification provided by Acchain system, generate the request data as a JSON object. (In one case, if you write about secure peer to peer transportation, you may need a JS library called Acchain-js to create signature. see [2.9 Peer to Peer transportation](#29-peer-to-peer-transportation) for detail).
- **Send request data:** transfer the generated data object to acchain  platform through POST/GET Methods upon HTTP
- **Acchain system handles the data object:** after receiving the data object, acchain server will validate the data firstly, then deal with it.
- **Return the response data:** acchain system send the response data to client as a JSON object. See interface part for detail, like response data format and error code.
- **Client handles the response data**

## 2 Interface  
 
### 2.1 Accounts   
   
#### 2.1.1 Login   

##### 2.1.1.1 Login after locally encrypt (recommended)   
---
- Interface Address: /api/accounts/open2/   
- Request Type: post   
- Supported Format: json   
- Comment: Public key needs to be generated locally according to user's password (see Request Example)   

- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |acchain account public key       |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |Whether login is successful      |    
|account|json   |Account Information          | 
   
- Request Example:   
  
```js
var acchainJS = require('Acchain-js');  //For further information about Acchain-js, please see Appendix
var publicKey = AcchainJS.crypto.getKeys(secret).publicKey;  //Generate public key according to password 
// var address = AcchainJS.crypto.getAddress(publicKey);   //Generate address according to public key

// Submit the above data to acchain server through post Methods   
curl -X POST -H "Content-Type: application/json" -k -d '{"publicKey":"bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"}' https://testnet.acchain.org/api/accounts/open2/   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"account": {   
		"address": "16723473400748954103",   
		"unconfirmedBalance": 19480000000,   
		"balance": 19480000000,   
		"unconfirmedSignature": false,   
		"secondSignature": true,   
		"secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",   
		"multisignatures": [],   
		"u_multisignatures": []   
	},   
	"latestBlock": {   
		"height": 111923,   
		"timestamp": 4446270   
	},   
	"version": {   
		"version": "1.0.0",   
		"build": "12:11:11 16/08/2016",   
		"net": "testnet"   
	}   
```   
   
##### 2.1.1.2 Login without locally encrypt (not recommend) 
---
- Interface Address: /api/accounts/open/   
- Request Methods:post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |Whether login is successful      |    
|account|json   |Account information          |    
   
- Request Example: 
  
```bash   
curl -X POST -H "Content-Type: application/json" -k -d '{"secret":"fault still attack alley expand music basket purse later educate follow ride"}' https://testnet.acchain.org/api/accounts/open/   
```   
   
- JSON Response Example: 
  
```js   
{   
    "success": true,    
    "account": {   
        "address": "16723473400748954103",    
        "unconfirmedBalance": 19480000000,    
        "balance": 19480000000,    
        "publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",    
        "unconfirmedSignature": false,    
        "secondSignature": true,    
        "secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",    
        "multisignatures": [ ],    
        "u_multisignatures": [ ]   
    }   
}   
```   
####2.1.2 Get Account Information  
---
- Interface Address: /api/accounts   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether response data can be returned |    
|account|json  |account information      |    
|latestBlock|json  |latest block information      |    
|version|json  |version information      |    
   
- Request Example:  
 
```bash   
curl -k -X GET https://testnet.acchain.org/api/accounts?address=16723473400748954103   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"account": {   
		"address": "16723473400748954103",  //acchain address   
		"unconfirmedBalance": 19480000000,  //the sum of unconfirmed and confirmed balance, that should be larger than or equal to balance below.   
		"balance": 19480000000, //balance   
		"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",    //Public key   
		"unconfirmedSignature": false,   
		"secondSignature": true,    //second signature   
		"secondPublicKey": "edf30942beb74de5ed6368c792af8665e9636f32a5f1c9377bcdc3b252d3f277",  //second public key   
		"multisignatures": [],    
		"u_multisignatures": []   
	},   
	"latestBlock": {   
		"height": 114480,   //block height   
		"timestamp": 4471890   
	},   
	"version": {   
		"version": "1.0.0",   
		"build": "12:11:11 16/08/2016", //build date   
		"net": "testnet"    //blockchain type: main chain or test one   
	}   
}   
```   

#### 2.1.3 Get Balance of Account  
--- 
- Interface Address: /api/accounts/getBalance   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|balance|integer  |balance      |    
|unconfirmedBalance|integer|the sum of unconfirmed and confirmed balance, that should be larger than or equal to balance|   
   
   
-Request Example:  
 
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/getBalance?address=14636456069025293113'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"balance": 5281328514990,   
	"unconfirmedBalance": 5281328514990   
}   
```   
   
#### 2.1.4 Get Account's Public Key 
---  
- Interface Address: /api/accounts/getPublickey   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Client's address, minimum length:1     |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|publicKey|string  |public key      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/getPublickey?address=14636456069025293113'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7"   
}   
```   
   
#### 2.1.5 Generate Public Key
---   
- Interface Address: /api/accounts/generatePublickey   
- Request Methods: post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password     |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|publicKey|string  |public key      |    
   
- Request Example:  
 
```bash   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"fault still attack alley expand music basket purse later educate follow ride"}' 'https://testnet.acchain.org/api/accounts/generatePublickey'   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"   
}   
```   
   
#### 2.1.6 Get Voting List by Address   
---
- Interface Address: /api/accounts/delegates   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |Y    |Voter's address      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegates|Array  |A list that contains detail information of those delegates who have already voted   |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/delegates?address=14636456069025293113'   
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"delegates": [{   
		"username": "wgl_002",   
		"address": "14636456069025293113",   
		"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",   
		"vote": 9901985415600500,   
		"producedblocks": 1373,   
		"missedblocks": 6,   
		"rate": 1,   
		"approval": "98.54",   
		"productivity": "99.56"   
	},   
	{   
		"username": "wgl_003",   
		"address": "9961157415582672274",   
		"publicKey": "c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2",   
		"vote": 9891995435600500,   
		"producedblocks": 1371,   
		"missedblocks": 8,   
		"rate": 2,   
		"approval": "98.44",   
		"productivity": "99.41"   
	},   
	{   
		"username": "wgl_001",   
		"address": "1869971419039689816",   
		"publicKey": "c547df2dde6cbb4508aabcb5970d8f9132e5a1d1c422632da6bc20bf1df165b8",   
		"vote": 32401577128413,   
		"producedblocks": 969,   
		"missedblocks": 8,   
		"rate": 102,   
		"approval": "0.32",   
		"productivity": 0   
	}]   
}   
```   
   
#### 2.1.7 Get the Fee of Given Delegate 
--- 
- Interface Address: /api/accounts/delegates/fee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none  

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |fee setting      |    
   
   
- Request Example:
   
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/accounts/delegates/fee  
```   
   
- JSON Response Example:  
 
```js   
{   
	"success": true,   
	"fee": 100000000   
}   
```   
   
   
#### 2.1.8 Voting   
---
- Interface Address: /api/accounts/delegates   
- Request Methods: put   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|N|acchain account's second password，minimum length：1，maximum length：100|   
|delegates|Array|a list that contains delegates' public key. put +/- in front of each public key, which means vote/abolish this delegate. |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |voting detail inforamtion      |    
   
   
- Request Example:  
 
```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"call scissors pupil water friend timber spend brand vote obey corn size","publicKey":"3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a","delegates":["+fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575"]}' 'https://testnet.acchain.org/api/accounts/delegates'     
```   
   
- JSON Response Example:   

```js   
 {
	"success": true,
	"transaction": {
		"type": 3,  //the type of vote is '3'
		"amount": 0,
		"senderPublicKey": "3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a",
		"requesterPublicKey": null,
		"timestamp": 5056064,
		"asset": {
			"vote": {
				"votes": ["+fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575"]
			}
		},
		"recipientId": null,
		"signature": "0bff58c7311fc59b3c8b3ffc236bbfece9850c334fb0c292ab087f78cf9a6c0f4d3e541c501887a2c2ec46294c777e8f7bf7dea9cb7c9a175fdec641bb684f08",
		"id": "5630629337798595849",
		"fee": 10000000,
		"senderId": "15238461869262180695"
	}
}  
```   

   
#### 2.1.9 Get the top 100 accounts
---
- Interface Address: /api/accounts/top    
- Request Methods: get  
- Supported Format: none      
- Request Parameter Description: if no parameters are passed, it will return top 100 accounts info
  
|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0,maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|json  |accounts info array, including "address", "balance", "publicKey" |    

- Request Example:

```bash
curl -k -X GET 'https://testnet.acchain.org/api/accounts/top?limit=5&offset=0'  //return 5 accounts info 
```

- Return JSON example:

```js
{
    "success": true,
    "accounts": [{
        "address": "355198157736313687",
        "balance": 4400099900000000,        //44000999 ACC
        "publicKey": "0b8e120db026d58cbf9d3f392f88eefe3a82a0a3023298b9466d7ed64ff05881"
    },
    {
        "address": "3196144307608101364",
        "balance": 3750000020000000,
        "publicKey": "988eb82a603dd033f94a4f3b6f9f9ef4a7d3d066607c433e5255d50ea7270720"
    },
    {
        "address": "9248745407080572308",
        "balance": 988703397029757,
        "publicKey": "02cedc56da08099532e312c5e563e2859bc5b93cc594eb3e5d350f368d681988"
    },
    {
        "address": "15745540293890213312",
        "balance": 498186229718623,
        "publicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3"
    },
    {
        "address": "8812460086240160222",
        "balance": 100704426831866,
        "publicKey": "0af92cc32f54d50dd83c4f7de14e71223a57843a40e993bc0813454aa9270053"
    }
}    
```


### 2.2 Transactions   
#### 2.2.1 Get the Transaction Detail Information  
--- 
- Interface Address: /api/transactions   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment： if there is no parameter in request data, all network transactions will be returned.    
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|blockId |string |N    |block id      |   
|limit |integer |N    |the limitation of returned records，minimum：0,maximum：100   |   
|type|integer  |N      |The transaction type, SEND: 0, SIGNATURE: 1,DELEGATE: 2 ,VOTE: 3, MULTI: 4, DAPP: 5,IN_TRANSFER: 6, OUT_TRANSFER: 7, APPROVAL: 8, UIA_ISSUER: 9, UIA_ASSET: 10, UIA_ISSUE: 11, UIA——EXERCISE: 12|   
|orderBy|string  |N      |sort with a field in the table，senderPublicKey:desc  |   
|offset|integer  |N      |offset, minimum 0  |   
|senderPublicKey|string|N|sender's public key|   
|ownerPublicKey|string|N||   
|ownerAddress|string|N||   
|senderId|string|N|sender's address|   
|recipientId|string|N|recipient's address, minimum:1|   
|amount|string|N|amount|   
|fee|integer|N|charge fee|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |A JSON object list containing multiple transactions' detail      |    
|count|int|the total number of retrieved transactions|   
   
- Request Example:  
 
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions?recipientId=16723473400748954103&orderBy=t_timestamp:desc&limit=3'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": [{   
		"id": "17192581936339156329",   
		"height": "105951",   
		"blockId": "15051364118100195665",   
		"type": 0,   
		"timestamp": 4385190,   
		"senderPublicKey": "d39d6f26869067473d685da742339d1a9117257fe14b3cc7261e3f2ed5a339e3",   
		"senderId": "15745540293890213312",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "98d65df3109802c707eeed706e90a907f337bddab58cb4c1fbe6ec2179aa1c85ec2903cc0cf44bf0092926829aa5a0a6ec99458f65b6ebd11f0988772e58740e",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "31802",   
		"asset": {   
			   
		}   
	},   
	{   
		"id": "7000452951235123088",   
		"height": "105473",   
		"blockId": "11877628176330539727",   
		"type": 0,   
		"timestamp": 4380147,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "dc84044d4f6b4779eecc3a986b6507e458cc5964f601ebeb4d3b68a96129813f4940e14de950526dd685ca1328b6e477e6c57e95aeac45859a2ea62a587d0204",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "32280",   
		"asset": {   
			   
		}   
	},   
	{   
		"id": "14093929199102906687",   
		"height": "105460",   
		"blockId": "2237504897174225512",   
		"type": 0,   
		"timestamp": 4380024,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "73ceddc3cbe5103fbdd9eee12f7e4d9a125a3bcf2e7cd04282b7329719735aeb36936762f17d842fb14813fa8f857b8144040e5117dffcfc7e2ae88e36440a0f",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "32293",   
		"asset": {   
			   
		}   
	}],   
	"count": 3   
}   
```   

#### 2.2.2 Get the Transaction Detail Information by Transaction ID
---
- Interface Address: /api/transactions/get   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|Id |string |Y    |transaction id      |   
    
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|json  |transaction detail information      |    
   
- Request Example: 
  
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions/get?id=14093929199102906687'   
```   
   
- JSON Response Example:
   
```js   
{   
	"success": true,   
	"transaction": {   
		"id": "14093929199102906687",   
		"height": "105460",   
		"blockId": "2237504897174225512",   
		"type": 0,   
		"timestamp": 4380024,   
		"senderPublicKey": "fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575",   
		"senderId": "16358246403719868041",   
		"recipientId": "16723473400748954103",   
		"amount": 10000000000,   
		"fee": 10000000,   
		"signature": "73ceddc3cbe5103fbdd9eee12f7e4d9a125a3bcf2e7cd04282b7329719735aeb36936762f17d842fb14813fa8f857b8144040e5117dffcfc7e2ae88e36440a0f",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "34268",   
		"asset": {   
		}   
	}   
}   
```   
   
#### 2.2.3 Get Transaction Detail by Unconfirmed Transaction ID 
---  
- Interface Address: /api/transactions/unconfirmed/get   
- Request Methods:get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|id|string |Y    |unconfirmed transaction id      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |unconfirmed transaction detail inforamtion      |   
   
   
- Request Example:
   
```bash   
curl -k -X GET https://testnet.acchain.org/api/transactions/unconfirmed/get?id=7557072430673853692  //Regularly, this unconfirmed transaction exist during an extremely short time, almost 0~10 second. 
```   
   
- JSON Response Example:
   
```js   
{
	"success": true,
	"transaction": {
		"type": 0,
		"amount": 10000,
		"senderPublicKey": "3ec1c9ec08c0512641deba37c0e95a0fe5fc3bdf58424009f594d7d6a4e28a2a",
		"requesterPublicKey": null,
		"timestamp": 5082322,
		"asset": {
			
		},
		"recipientId": "16723473400748954103",
		"signature": "3a97f8d63509ef964bda3d816366b8e9e2d9b5d4604a660e7cbeefe210cb910f5de9a51bece06c32d010f55502c62f0f59b8224e1c141731ddfee27206a88d02",
		"id": "7557072430673853692",
		"fee": 10000000,
		"senderId": "15238461869262180695"
	}
}
```   
   
   
#### 2.2.4 Get Unconfirmed Transaction Detail Information (within all network)
---
- Interface Address: /api/transactions/unconfirmed   
- Request Methods:get   
- Supported Format: urlencoded   
- Comment: If there is no parameter, all unconfirmed transactions in the whole network will be returned.
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|senderPublicKey |string |N    |sender's public key      |   
|address |string |N    |address      |   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |a list containing all unconfirmed transactions      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/transactions/unconfirmed'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": []      //Currently there is no unconfirmed transaction in the whole network 
}   
```   
   
#### 2.2.5 Create Transaction   
---
- Interface Address: /api/transactions   
- Request Methods: PUT   
- Supported Format: json   
- Comment: recipient account must have already login in wallet on the web.  
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|amount|string|Y|amount，between 1 and 10000000000000000|   
|recipientId|string|Y|recipient's address, minimum:1|   
|publicKey|string|N|sender's public key|   
|currency|string|N|assets name, for example:"test.RET"|
|message|string|N|remark message|
|publicKey|string|N|sender's public key|   
|secondSecret|string|N|sender's second password (must fit the BIP39 standard), the length should be between 1 and 100|   
|multisigAccountPublicKey|string|N|the public key of multiple signature account|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |transaction id      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","amount":1000000,"recipientId":"16723473400748954103","currency":"test.RET"}' 'https://testnet.acchain.org/api/transactions'    
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "16670272591943275531"   
}   
```   





#### 2.2.6 Exercise  
---
- Interface Address: /api/exercises   
- Request Methods: PUT   
- Supported Format: json   
- Comment: recipient account must have already login in wallet on the web.  
- Request Parameter Description:  

|Name	|Type   |Required |Description|   
|------ |-----  |---  |----      |
|secret|string|Y| acchain account password |
|amount|string|Y| amount，between 1 and 10000000000000000|
|currency|string|Y| assets name, for example:"test.RET"|
|publicKey|string|Y| sender's public key|
|message|string|N | remark message|
|secondSecret|string|N| sender's second password (must fit the BIP39 standard), the length should be between 1 and 100|
|multisigAccountPublicKey|string|N| the public key of multiple signature account|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |transaction id      |  

- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","amount":1000000,"currency":"test.RET", "message":"hello"}' 'https://testnet.acchain.org/api/uia/exercises'        
```      

- JSON Response Example:   

```js   
{
    "success": true,
    "transaction": {
        "type": 12,
        "amount": "0",
        "senderPublicKey": "78e3bca480fc90ff149c1f538a332f540350ca19ac441bfee66cc29a076e62d9",
        "requesterPublicKey": null,
        "timestamp": 31408638,
        "asset": {
            "uiaExercise": {
                "currency": "test.RET",
                "amount": "10000"
            }
        },
        "recipientId": null,
        "signature": "ea12eee74a932c49863fb90493a90a942b95e9e39e2d5c6204d8cf651b6c3fee63309db17374c22a16a453a22f5f881c8af153119d81bc3401e5e80364c55502",
        "signSignature": "0577c15e9498fbcd0b84a70b80e7f10db3fb327dd7316868a427ec7bc917b15468f4cb8bcfb4cbe1897b9576275ff1430e78858fdbeebbc19a1ec0966e530d05",
        "id": "8a56a0f5c0b057f2e037b609ab829a8f15e9c581b43436c438063df3492eb6ce",
        "fee": 100000,
        "senderId": "APfs15A8KegKu1TtnJsWJvLoFxCKT7pRos"
    }
}    
```  
   
### 2.3 Blocks
#### 2.3.1 Get the Block Detail Information of the Given ID 
---  
- Interface Address: /api/blocks/   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|id |string |only choose one of these three parameters    |block ID      |   
|height|string|ditto|block height|   
|hash|string|ditto|block hash value|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|block|json  |the block detail information      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/get?id=6076474715648888747'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"block": {   
		"id": "6076474715648888747",   
		"version": 0,   
		"timestamp": 4734070,   
		"height": 140538,   
		"previousBlock": "16033230167082515105",    //previous block ID   
		"numberOfTransactions": 0,  //The number of transactions   
		"totalAmount": 0,   //the total transactions' amount   
		"totalFee": 0,   
		"reward": 350000000,    //reward   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "1d352950c8141e1b35daba4a974a604519d7a2ef3a1ec0a503ce2653646aa052",   
		"generatorId": "6656029629904254066",   
		"blockSignature": "a53de66922cdc2f431acd0a474beec7cf7c420a8460b7b7caf84999be7caebb59fb7fbb7166c2c7013dbb431585ea7294722166cb08bf9663abf50b6bd81cd05",   
		"confirmations": "2",   
		"totalForged": 350000000   
	}   
}   
```   
   
#### 2.3.2 Get the Latest Block  
---
- Interface Address: /api/blocks   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment: if there is no parameter, the detail of all the blocks in the whole network will be returned  
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit |integer |N    |maximum number of returned records, between 0 and 100   |   
|orderBy|string  |N      |sort by a field in the table, for example, height: desc  |   
|offset|integer  |N      |offset, minimum 0  |   
|generatorPublicKey|string  |N      |public key of the block generator  |   
|totalAmount|integer  |N       |total amount of transactions, from 0 to 10000000000000000 |   
|totalFee|integer  |N      |total fee of transaction, from 0 to 10000000000000000  |   
|reward|integer  |N      |the amount of reward, minimum: 0  |   
|previousBlock|string  |N      |previous block  |   
|height|integer  |N      |block height  |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|blocks|Array  |a list of JSON objects containing block detail|    
|count|integer|block height|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks?limit=2&offset=0&orderBy=height:desc'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"blocks": [{   
		"id": "12634047624004615059",   
		"version": 0,   
		"timestamp": 4708080,   
		"height": 137986,   
		"previousBlock": "3498191422350401106",   
		"numberOfTransactions": 0,  // the number of transactions   
		"totalAmount": 0,   // total amount of transactions   
		"totalFee": 0,  // transaction fee   
		"reward": 350000000,    // reward   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "44db7bec89ef289d0def257285675ca14f2a947dfd2b70e6b1cff4392ce42ada",   
		"generatorId": "4925169939071346193",   
		"blockSignature": "83a2124e3e8201c1a6099b2ac8ab1c117ad34867978add3a90d41a64df9d2ad8fabc9ec14d27a77cd34c08a6479ef684f247c11b1cbbcb0e9767dffc85838600",   
		"confirmations": "1",   
		"totalForged": 350000000   
	},   
	{   
		"id": "3498191422350401106",   
		"version": 0,   
		"timestamp": 4708070,   
		"height": 137985,   
		"previousBlock": "14078155423801039323",   
		"numberOfTransactions": 0,   
		"totalAmount": 0,   
		"totalFee": 0,   
		"reward": 350000000,   
		"payloadLength": 0,   
		"payloadHash": "e3b0c44298fc1c149afbf4c8996fb92427ae41e4649b934ca495991b7852b855",   
		"generatorPublicKey": "500b1ec025cd64d36008341ed8d2508473ecf559be213ca5f9580620a21a592c",   
		"generatorId": "16006295608945777169",   
		"blockSignature": "a0b5ed6c94b1f33c4d0f017f21a08357061493392b19e34eeedf274b77c751e3f86c92443280de09ea1754d62fe7ef00e02acbdc3bc0c1063cef344bacaa4f07",   
		"confirmations": "2",   
		"totalForged": 350000000   
	}],   
	"count": 137986   
}   
```   
   
#### 2.3.3 Get the Block Height  
--- 
- Interface Address: /api/blocks/getHeight   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height|integer  |block height      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getheight'    
```   
   
- JSON Response Example:   

```js   
{"success":true,"height":140569}   
```   
   
#### 2.3.4 Get the Transaction Fee  
--- 
- Interface Address: /api/blocks/getFee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee     |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getfee'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"fee":10000000}     //transaction fee is 
0.1 ACC   
```   
   
#### 2.3.5 Get the Milestone   
---
- Interface Address: /api/blocks/getMilestone   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|milestone|integer  |      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getMilestone'    
```   
   
- JSON Response Example:   

```js   
{"success":true,"milestone":0}   
```   
   
#### 2.3.6 Get the Reward Information of a Block 
---
- Interface Address: /api/blocks/getReward   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|reward|integer  |the reward of the block      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getReward'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"reward":350000000} //every single block you created will be rewarded by 3.5 ACC   
```   
   
#### 2.3.7 Get the Current Maximum Supply of the Blockchain

- Interface Address: /api/blocks/getSupply   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|supply|integer  |the total amount of ACC in the whole network      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getSupply'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"supply":10049222600000000} //There are totally 100492226 ACC in current testnet   
```   
   
#### 2.3.8 Get Current Status of Blockchain 
--- 
- Interface Address: /api/blocks/getStatus   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height|integer  |blockchain height      |    
|fee|integer  |transaction fee      |    
|milestone|integer  |      |    
|reward|integer  |block reward      |    
|supply|integer  |total amount of ACC in the whole network      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/blocks/getStatus'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"height": 140649,   
	"fee": 10000000,   
	"milestone": 0,   
	"reward": 350000000,   
	"supply": 10049227150000000   
}   
```   
   
   
   
### 2.4 Delegates  
   
#### 2.4.1 Get the Total Number of Delegates 
---
- Interface Address: /api/delegates/count   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|count|integer   |total number of delegates      |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/count'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"count":234}   
```   
   
#### 2.4.2 Check the Voters of Delegates by Public Key   
---
- Interface Address: /api/delegates/voters   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |public key of the delegate      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|Array  |a JSON object list of account    |    
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/voters?publicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"accounts": [{   
		"address": "2918354313445278349",   
		"publicKey": "4fde4c49f1297d5d3a24b1494204543c4281aff17917ff7ff8ff32da3b4b222f",   
		"balance": 1338227722727,   
		"weight": 0.013316660647014596   
	},   
	{   
		"address": "1523444724068322527",   
		"publicKey": "8a6a61c28dc47541aadf1eecec2175c8f768f2331eea3472b1593bf1aa4e1fb4",   
		"balance": 2109297623765,   
		"weight": 0.020989552213127274   
	},   
	{   
		"address": "14483826354741911727",   
		"publicKey": "5dacb7983095466b9b037690150c3edec0f073815326e33a4744b6d1d50953e2",   
		"balance": 5135815841470,   
		"weight": 0.051106336795243436   
	}   
	}]   
}   
```   
   
#### 2.4.3 Get the Delegate's Detail by Public Key or Name   
---
- Interface Address:  /api/delegates/get/   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment:Get the delegate's detail by his/her public key or user name      
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publickey |string |choose only one parameter of these two    |delegate's public key      |   
|username  |string |ditto    |delegate's user name      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegate|json  |the detail information of this delegate      |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/delegates/get?publicKey=bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9   
curl -k -X GET https://testnet.acchain.org/api/delegates/get?username=delegate_register   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"delegate": {   
		"username": "delegate_register",   
		"address": "16723473400748954103",   
		"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9",   
		"vote": 0,   
		"producedblocks": 0,   
		"missedblocks": 0,   
		"fees": 0,   
		"rewards": 0,   
		"rate": 191,   
		"approval": 0,   
		"productivity": 0,   
		"forged": "0"   
	}   
}   
```   
   
#### 2.4.4 Get the List of Delegates 
---  
- Interface Address: /api/delegates   
- Request Methods: get   
- Supported Format: urlencoded   
- Comment: if there is no parameter, all delegates in the whole network will be returned. 
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|address |string |N    |delegate's address      |   
|limit|int  |N       |maximum return records       |   
|offset|integer  |N       |offset, minimum: 0      |   
|orderBy|string  |N       |[field used to sort]:[sort type] e.g., address:desc      |   
   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|delegates|Array  |a list containing delegates' detail information      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates?orderby=approval:desc&limit=2' //the first two delegates order by approval vote, descendingly  
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"delegates": [{   
		"username": "wgl_002",  //delegate's user name   
		"address": "14636456069025293113",  //delegate's address   
		"publicKey": "ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7",    //delegate's public key   
		"vote": 9901984015600500,   //the number of vote   
		"producedblocks": 1371, //the number of generated blocks   
		"missedblocks": 6,  //the number of missed blocks   
		"fees": 12588514990,       
		"rewards": 276850000000,    //the gained reward   
		"rate": 1,   
		"approval": 98.54,  //the rate of approval votes   
		"productivity": 99.56,  //the productivity   
		"forged": "289438514990"    //All reward from forge   
	},   
	{   
		"username": "wgl_003",   
		"address": "9961157415582672274",   
		"publicKey": "c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2",   
		"vote": 9891994035600500,   
		"producedblocks": 1370,   
		"missedblocks": 8,   
		"fees": 12355148480,   
		"rewards": 275100000000,   
		"rate": 2,   
		"approval": 98.44,   
		"productivity": 99.42,   
		"forged": "287455148480"   
	}],   
	"totalCount": 233   
}   
```   
   
   
#### 2.4.5 Get the Transaction Fee Set by Delegate 
---
- Interface Address: /api/delegates/fee   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |delegate's public key      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee      |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/fee?publicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{"success":true,"fee":10000000000}  //0.1 ACC   
```   
   
#### 2.4.6 Get Forge Information by Public Key 
---
- Interface Address: /api/delegates/forging/getForgedByAccount   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|generatorPublicKey |string |Y    |block generator's public key      |   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fees|integer  |total amount of charged fee      |    
|rewards|integer|gained rewards|   
|forged|integer|total rewards comming from forge|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/delegates/forging/getForgedByAccount?generatorPublicKey=ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"fees": 12589307065,   
	"rewards": 285600000000,   
	"forged": 298189307065   
}   
```   
   
#### 2.4.7 Register Delegate
---
- Interface Address: /api/delegates   
- Request Methods: put   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account password       |   
|publicKey|string  |N      |public key|    
|secondSecret|string|N|acchain account's second password, minimum length:1 maximum length: 100 |   
|username|string|N|the delegate's user name|   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |the detail of the registering process      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","username":"delegate_0821"}' 'https://testnet.acchain.org/api/delegates'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transaction": {   
		"type": 2,  //the transaction type of registering delegate is 2   
		"amount": 0,   
		"senderPublicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2",   
		"requesterPublicKey": null,   
		"timestamp": 4737615,   
		"asset": {   
			"delegate": {   
				"username": "delegate_0821",   
				"publicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2"   
			}   
		},   
		"recipientId": null,   
		"signature": "7f8417e8db5f58ddff887c86c789c26b32fd3f01083ef1e3c8d4e18ed16622bf766492d78518c6c7a07aada1c98b1efc36d40c8e09394989dbde229d8e3f8103",   
		"id": "16351320834453011577",   
		"fee": 10000000000,   
		"senderId": "250438937633388106"   
	}   
}   
```   
   
#### 2.4.8 Delegates enable forging
---
- Interface Address: /api/delegates/forging/enable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Descriptio|
|------ |-----  |---  |----  |  
|secret |string | Y   | acchain account secret|
|publicKey| string | N | publicKey|

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| address | string | delegate's address |

- Request Example:

```js
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"motion group blossom coral upper warrior pattern fragile sister misery palm detect"}' 'http://testnet.acchain.org/api/delegates/forging/enable'   
```

- JSON Response Example:

```js
{"success":true,"address":"16358246403719868041"}  
```

#### 2.4.9 Delegates disable forging

- Interface Address: /api/delegates/forging/disable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |  
|secret |string | Y   | acchain account secret|
|publicKey| string | N | publicKey|

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| address | string | delegate's address |

- Request Example:

```js
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"motion group blossom coral upper warrior pattern fragile sister misery palm detect"}' 'http://testnet.acchain.org/api/delegates/forging/disable'   
```

- JSON Response Example:

```js
{"success":true,"address":"16358246403719868041"} 
```

#### 2.4.10 Delegates forging status
---
- Interface Address: /api/delegates/forging/disable
- Request Methodss: post
- Supported Format: urlencoded //url must be under the delegate's server 
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |  
|publicKey |string | Y   | publicKey |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              | 
| success | boole | get the response data success or failure | 
| enable | string | the status of delegates foring |

- Request Example:

```js
curl -k -X GET 'https://testnet.acchain.org/api/delegates/forging/status?publicKey=fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575'        
```

- JSON Response Example:

```js
{"success":true,"enabled":false}    
```


### 2.5 Peers 
   
#### 2.5.1 Get all Peers' Information in the Whole Network   
---
- Interface Address: /api/peers   
- Request Methods: get   
- Supported Format:  urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|state |integer |N    |peer's status: 0:,1:,2:,3:     |   
|os|string|N|Linux kernel version|   
|version|string|N|acchain system version|   
|limit |integer |N    |maximum return records, minimum:0, maximum: 100|   
|orderBy|string|N||   
|offset|integer  |N      |offset, minimum 0  |   
|port|integer|N|port number，1~65535|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|peers|Array  |a JSON array of peers' information |    
|totalCount|integer|the number of currently running peers|   
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/peers?limit=1'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"peers": [{   
		"ip": "45.32.19.241",   
		"port": 4096,   
		"state": 2,   
		"os": "linux3.13.0-87-generic",   
		"version": "1.0.0"   
	}],   
	"totalCount": ["54"]   
}   
```   
   
#### 2.5.2 Get the Version of Peer
---
- Interface Address: /api/peers/version   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|version|string  |version number     |    
|build  |timestamp |built time     |    
|net    |string  |if the peer is mainnet or testnet     |   
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/peers/version   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"version": "1.0.0",   
	"build": "12:11:11 16/08/2016",   
	"net": "testnet"   
}   
```   
   
#### 2.5.3 Get the Peer Information of a Given IP Address   
---
- Interface Address: /api/peers/get   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|ip |string |Y    |peer's IP      |   
|port|integer|Y|peer's port，1~65535|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|peer|json  | peer's information     |    
   
   
- Request Example:   

```bash   
curl -k -X GET 'https://testnet.acchain.org/api/peers/get?ip=45.32.248.33&port=4096'   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"peer": {   
	}   
}   
```   
   
### 2.6 Sync and Loader  
#### 2.6.1 Get the local blockchain loading status  
--- 
- Interface Address: /api/loader/status   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|loaded |bool    |          |   
|blocksCount|integer||   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/loader/status -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"loaded": true,   
	"blocksCount": 0   
}   
```   
   
#### 2.6.2 Get the block syncing status
---
- Interface Address: /api/loader/status/sync   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|height |int    |block height          |   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/loader/status/sync -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"syncing": false,  // show whether in synchronising. if yes, it will be "true". if there is no data to synchronise, it will be "false" 
	"blocks": 0,   
	"height": 111987   
}   
```   
   
### 2.7 Second Password   
#### 2.7.1 Set the Second Password
---
- Interface Address: /api/signatures   
- Request Methods: put   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|Y|acchain account's second password，minimum length：1，maximum length：100|   
|multisigAccountPublicKey|string|N|the public key of multi signatures account|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transaction|json  |the detail information of setting transaction   |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"unaware label emerge fancy concert long fiction report affair appear decide twenty","secondSecret":"fault still attack alley expand music basket purse later educate follow ride"}' 'https://testnet.acchain.org/api/signatures'    
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transaction": {   
		"type": 1,  //the transaction type of setting second password is 1  
		"amount": 0,   
		"senderPublicKey": "3b64f1833e6328043e1f2fee31e638bdaa6dfff5c7eb9c8577a5cefcf11261f2",   
		"requesterPublicKey": null,   
		"timestamp": 4872315,   
		"asset": {   
			"signature": {   
				"publicKey": "bd1e78c5a10fbf1eca36b28bbb8ea85f320967659cbf1f7ff1603d0a368867b9"   
			}   
		},   
		"recipientId": null,   
		"signature": "e76d9b25ec0fdaa88b19d59c5a222b7efdc04f738ee05896f55f4e6959229d9b1600ca25aa92fbea176668f3be7c12c506f2091e2b38c52ef0ece7a5d35e240a",   
		"id": "1614688380530105232",   
		"fee": 500000000,       //the transaction fee of setting second password is 5 ACC   
		"senderId": "250438937633388106"   
	}   
}   
```   
   
#### 2.7.2 Get the Transaction Fee of Setting Second Password
---
- Interface Address: /api/signatures/fee   
- Request Methods: get   
- Supported Format: none   
- Request Parameter Description: none   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|fee|integer  |transaction fee     |    
   
   
- Request Example:   

```bash   
curl -k https://testnet.acchain.org/api/signatures/fee -X GET   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"fee": 500000000         //5 ACC   
}     
```   
   
### 2.8 Multiple Signatures 
#### 2.8.1 Set Normal Account to Multi-signatures Account
---
- Interface Address: /api/multisignatures   
- Request Methods: put   
- Supported Format: json   
- Comment: the return value is transaction ID only. To successfully set to multi-signature account still needs other's signatures. Every transaction after registered as multi-signatures account will be asked for multiple signatures. The minimum necessary signatures is defined by "min" (include sender itself) 
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|publicKey|string  |N|public key      |    
|secondSecret|string|N|acchain account's second password, minimum length:1 maximum length: 100|   
|min|integer|Y|the minimum signatures that is required to each transaction for multi-signatures account. (When the transaction is to register multi-signature account, this parameter will not work since everyone needs to sign.) Minimum:2, maximum:16. This number must not be larger than keysgroup.length+1. |   
|lifetime|integer|Y|the maximum pending time of multi-signature transaction. Minimum:1, maximum:24. NOTE: this parameter is not available currently.|   
|keysgroup|array|Y|an array containing other signaturers' public key. There are plus/minus (+/-) in front of each public key, means add or delete multi-signature account respectively. Minimum length:1, maximum length:10.|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |the multi-signature transaction ID     |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X PUT -d '{"secret":"vanish deliver message evil canyon night extend unusual tell prosper issue antenna","min":2,"lifetime":1,"keysgroup":["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97","+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"]}' 'https://testnet.acchain.org/api/multisignatures'  //publickey = 2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "17620378998277022323"     //only transaction ID is returned. To successfully set to multi-signature account needs other accounts' signatures.   
}   
```   
   
#### 2.8.2 Get the Detail Information of Pending Multi-signature Transaction
---
- Interface Address: /api/multisignatures/pending   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey|string  |Y|public key      |    
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactions|Array  |a JSON object list containing those pending transactions      |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactions": [{      //the detail information of the setting multi-signature account transaction (see 2.8.1, transactionId: 17620378998277022323)  
		"min": 2,   
		"lifetime": 1,   
		"signed": true,   
		"transaction": {   
			"type": 4,      //4 means registering multi-signature account   
			"amount": 0,   
			"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
			"requesterPublicKey": null,   
			"timestamp": 4879978,   
			"asset": {   
				"multisignature": {   
					"min": 2,   
					"keysgroup": ["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
					"+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],   
					"lifetime": 1   
				}   
			},   
			"recipientId": null,   
			"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
			"id": "17620378998277022323",   
			"fee": 1500000000,   
			"senderId": "3855903394839129841"   
		}   
	}]   
}   
   
```   
   
#### 2.8.3 Sign the Multi-signature Transaction (by non-initiator) 
---  
- Interface Address: /api/multisignatures/sign   
- Request Methods: post   
- Supported Format: json   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|secret |string |Y    |acchain account's password       |   
|secondSecret|string|N|acchain account second password. Minimum length:1, maximum length:100|   
|publicKey|string  |N|public key      |    
|transactionId|string|Y|transaction ID|   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|transactionId|string  |multi-signature transaction ID      |    
   
   
- Request Example:   

```bash   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"lemon carpet desk accuse clerk future oyster essay seminar force live dog","transactionId":"17620378998277022323"}' 'https://testnet.acchain.org/api/multisignatures/sign'   //signed by a user whose public key is eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"transactionId": "17620378998277022323"   
}   
// Now get the pending transaction again   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
{   
	"success": true,   
	"transactions": [{   
		"min": 2,   
		"lifetime": 1,   
		"signed": true,   
		"transaction": {   
			"type": 4,   
			"amount": 0,   
			"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
			"requesterPublicKey": null,   
			"timestamp": 4879978,   
			"asset": {   
				"multisignature": {   
					"min": 2,   
					"keysgroup": ["+eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
					"+d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],   
					"lifetime": 1   
				}   
			},   
			"recipientId": null,   
			"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
			"id": "17620378998277022323",   
			"fee": 1500000000,   
			"senderId": "3855903394839129841",   
			"signatures": ["b38a161264db2a23e353d3fbc4983562f6343d5ee693144543ca54e2bc67c0f73d1c761b7bfa38b2bb101ac2ab0797b674b1a9964ccd400aaa310746c3494d03"]      //new multi-signature generated   
		}   
	}]   
}   
   
// a user whose public key is "d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb" sign this registering transaction   
curl -k -H "Content-Type: application/json" -X POST -d '{"secret":"chalk among elbow piece badge try van round quality position simple teach","transactionId":"17620378998277022323"}' 'https://testnet.acchain.org/api/multisignatures/sign'   
{"success":true,"transactionId":"17620378998277022323"}   
// trying to get pending transaction again, but this time there isn't any of it.   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/pending?publicKey=2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd   
{"success":true,"transactions":[]}   
// Check the detail of this transaction. (at this time, this transaction has been broadcasted to the whole network and been written to the blockchain) Now the account has already registered as a multi-signature account. 
curl -k -X GET https://testnet.acchain.org/api/transactions/get?id=17620378998277022323   
{   
	"success": true,   
	"transaction": {   
		"id": "17620378998277022323",   //the registering transaction ID   
		"height": "157013",   
		"blockId": "4680888982781013372",   
		"type": 4,   
		"timestamp": 4879978,   
		"senderPublicKey": "2cef5711e61bb5361c544077aa08aebc4d962a1d656571901c48d716382ad4fd",   
		"senderId": "3855903394839129841",   
		"recipientId": "",   
		"amount": 0,   
		"fee": 1500000000,   
		"signature": "a42feaccd9f2a4940fc0be1a1580e786b360f189db3154328f307988e75484293eae391f2f9eee489913cc6d15984eb1f5f5a0aa1bf78ea745d5c725f161af08",   
		"signSignature": "",   
		"signatures": null,   
		"confirmations": "26",   
		"asset": {   
			   
		}   
	}   
}   
   
```   
   
#### 2.8.4 Get Detail Information of the Multi-signature Account
---
- Interface Address: /api/multisignatures/accounts   
- Request Methods: get   
- Supported Format: urlencoded   
- Request Parameter Description:    

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|publicKey |string |Y    |One of the participants‘ public key      |   
   
   
- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|accounts|Array  |the detail of this multi-signature account   |    
   
   
- Request Example:   

```bash   
curl -k -X GET https://testnet.acchain.org/api/multisignatures/accounts?publicKey=eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97   
```   
   
- JSON Response Example:   

```js   
{   
	"success": true,   
	"accounts": [{   
		"address": "3855903394839129841",       //the address of this multi-signature account   
		"balance": 18500000000,     //the balance of this multi-signature account   
		"multisignatures": ["eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
		"d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb"],    //the public key of this multi-signature account   
		"multimin": 2,  //minimum required signature  
		"multilifetime": 1,   
		"multisigaccounts": [{          //the detail of signer's account  
			"address": "13542769708474548631",   
			"publicKey": "eb48b9ab7c9a34a9b7cdf860265d65b31af774355cabf1b3a387d14a1925dc97",   
			"balance": 0   
		},   
		{   
			"address": "4100816257782486230",   
			"publicKey": "d5d7aa157f866c47a2a1e09e2746286ed089fd90976b54fbfa930e87d11609cb",   
			"balance": 0   
		}]   
	}]   
}   
```   

### 2.9 Peer to Peer Transportation(secure API)
#### 2.9.1 Overview 
---
To request a peer related API, it is required to set a header like this:  

 - key=magic, and value=8e9b66ed  
 - key=version, and value=''  

#### 2.9.2 Transaction 
---
All the writing operations in acchain system are finished by starting a transaction.
The transaction data is generated through a JS library named "Acchain-js", and then broadcasted by a POST API.
The POST API specification is as follows:

payload: transaction data generated by Acchain-js
API Address: /peer/transactions  
Request Methods: POST   
Supported Format: JSON  

##### 2.9.2.1 Set the Second Payment Password
--- 
Request Parameter Description:  

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.signature.createSignature]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');    
var transaction = Acchain.signature.createSignature('measure bottom stock hospital calm hurdle come banner high edge foster cram','erjimimashezhi001')       
console.log(JSON.stringify(transaction))  
{"type":1,"amount":0,"fee":500000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5328943,"asset":{"signature":{"publicKey":"27116db89cb5a8c02fb559712e0eabdc298480d3c79a089b803e35bc5ef7bb7b"}},"signature":"71ef98b1600f22f3b18cfcf17599db3c40727c230db817f610e86454b62df4fb830211737ff0c03c6a61ecfd4a9fcb68a30b2874060bb33b87766acf800e820a","id":"15605591820551652547"}   

// submit above data of setting second password to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":1,"amount":0,"fee":500000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5328943,"asset":{"signature":{"publicKey":"27116db89cb5a8c02fb559712e0eabdc298480d3c79a089b803e35bc5ef7bb7b"}},"signature":"71ef98b1600f22f3b18cfcf17599db3c40727c230db817f610e86454b62df4fb830211737ff0c03c6a61ecfd4a9fcb68a30b2874060bb33b87766acf800e820a","id":"15605591820551652547"}}' https://testnet.acchain.org/peer/transactions   
```   
   
- JSON Response Example:   

```js  
{
    "success":true  //setting is successful
}	
``` 

##### 2.9.2.2 Transfer Money
---
- Request Parameter Description:   

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.transaction.createTransaction]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');   
var targetAddress = "16358246403719868041";  
var amount = 100*100000000;   //100 ACC
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';

// in above code, password is recorded when user logs in. meanwhile the second password needs to be input every time by user.
// To input or not depends on whether user has second password, which can be identified by "user.secondPublicKey" function.

var transaction = Acchain.transaction.createTransaction(targetAddress, amount, password, secondPassword || undefined);       
JSON.stringify(transaction)
'{"type":0,"amount":10000000000,"fee":10000000,"recipientId":"16358246403719868041","timestamp":5333378,"asset":{},"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","signature":"2d47810b7d9964c5c4d330a53d1382769e5092b3a53639853f702cf4a382aafcff8ef8663c0f6856a23f41c249944f0c3cfac0744847268853a62af5dd8fc90a","signSignature":"dfa9b807fff362d581170b41c56a2b8bd723c48d1f100f2856d794408723e8973016d75aeff4705e6837dcdb745aafb41aa10a9f1ff8a77d128ba3d712e90907","id":"16348623380114619131"}'

// submit above data of transfer to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":0,"amount":10000000000,"fee":10000000,"recipientId":"16358246403719868041","timestamp":5333378,"asset":{},"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","signature":"2d47810b7d9964c5c4d330a53d1382769e5092b3a53639853f702cf4a382aafcff8ef8663c0f6856a23f41c249944f0c3cfac0744847268853a62af5dd8fc90a","signSignature":"dfa9b807fff362d581170b41c56a2b8bd723c48d1f100f2856d794408723e8973016d75aeff4705e6837dcdb745aafb41aa10a9f1ff8a77d128ba3d712e90907","id":"16348623380114619131"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:  
 
```js  
{
    "success":true  //transfer success
}		
``` 

##### 2.9.2.3 Register Delegates   
---
- Request Parameter Description:  

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.delegate.createDelegate]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether transaction is success |  
   
   
- Request Example:   

```js   
var acchain = require('Acchain-js');   
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';
var userName = 'zhenxi_test';  

var transaction = Acchain.delegate.createDelegate(password, userName, secondPassword || undefined);   
JSON.stringify(transaction)  
'{"type":2,"amount":0,"fee":10000000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334485,"asset":{"delegate":{"username":"zhenxi_test","publicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f"}},"signature":"a12ce415d2d21ab46e4c1b918b8717b1d351dd99abd6f2f94d9a1a7e1f32b697f843a05b1851cb857ea45a2476dce592f5ddd612c00cd44488b8b610c57d7f0a","signSignature":"35adc9f1f37d14458e8588f9b4332eedf1151c02480159f64a287a4b0cbb59bfe82040dfec96a4d9560bae99b8eaa1799a7023395db5ddc640d95447992d6e00","id":"12310465407307249905"}'

// submit above data of registering delegate to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":2,"amount":0,"fee":10000000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334485,"asset":{"delegate":{"username":"zhenxi_test","publicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f"}},"signature":"a12ce415d2d21ab46e4c1b918b8717b1d351dd99abd6f2f94d9a1a7e1f32b697f843a05b1851cb857ea45a2476dce592f5ddd612c00cd44488b8b610c57d7f0a","signSignature":"35adc9f1f37d14458e8588f9b4332eedf1151c02480159f64a287a4b0cbb59bfe82040dfec96a4d9560bae99b8eaa1799a7023395db5ddc640d95447992d6e00","id":"12310465407307249905"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:   

```js  
{
    "success":true  //register successfully
}		
``` 

##### 2.9.2.4 Vote and Cancel the vote  
---
- Request Parameter Description: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|transaction|json|Y|transaction data generated by [Acchain-js.vote.createVote]|

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |whether the transaction is successful |  
   
   
- Request Example:  
 
```js   
var acchain = require('Acchain-js');   
var password = 'measure bottom stock hospital calm hurdle come banner high edge foster cram';
var secondPassword  = 'erjimimashezhi001';
// the voting content is a list in which each item consists of a symbol (+ or -) and the delegate's public key. The "+" means vote, and "-" means cancel the vote.
var voteContent = [
    '-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7',
    '+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2'
];

var transaction = Acchain.vote.createVote(password, voteContent, secondPassword || undefined);
JSON.stringify(transaction)
{"type":3,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334923,"asset":{"vote":{"votes":["-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7","+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2"]}},"signature":"6036c2066a231c452a1c83aafd3bb9db3842ee05d5f17813f8264a4294cdec761faa89edf4a95f9b2e2451285807ab18aa9f989ad9a3165b95643179b8e4580f","signSignature":"a216ca739112e6f65986604b9467ccc8058138a7077faf134d6c4d673306cd1c514cc95bd54a036f7c602a56c4b4f2e4e59f6aa7c376cb1429e89054042e050b","id":"17558357483072606427"}

// submit above data of vote/cancel vote to acchain server by POST Methods
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":3,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"3e6e7c90571b9f7dabc0abc2e499c2fcee8e436af3a9d5c8eadd82ac7aeae85f","timestamp":5334923,"asset":{"vote":{"votes":["-ae256559d06409435c04bd62628b3e7ea3894c43298556f52b1cfb01fb3e3dc7","+c292db6ea14d518bc29e37cb227ff260be21e2e164ca575028835a1f499e4fe2"]}},"signature":"6036c2066a231c452a1c83aafd3bb9db3842ee05d5f17813f8264a4294cdec761faa89edf4a95f9b2e2451285807ab18aa9f989ad9a3165b95643179b8e4580f","signSignature":"a216ca739112e6f65986604b9467ccc8058138a7077faf134d6c4d673306cd1c514cc95bd54a036f7c602a56c4b4f2e4e59f6aa7c376cb1429e89054042e050b","id":"17558357483072606427"}}' https://testnet.acchain.org/peer/transactions
```   
   
- JSON Response Example:  
 
```js  
{
    "success":true  //transaction of vote/cancel the vote is success
}		
``` 

### 2.10 User Identify Assets

#### 2.10.1 Get assets info

##### 2.10.1.1 Get all issuers
---
- Interface Address: /api/uia/issuers
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters: 

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|issuers|list  |element is dictionary, each dictionary represents a issuer, including "name", "desc", "issuerId" |
|count  | integer | count of issuers | 

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers?offset=0&limit=1' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "issuers": [{
        "name": "zhenxi",
        "desc": "this is a description",
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    },
    {
        "name": "speedtest",
        "desc": "speedtest",
        "issuerId": "AEVWQWAq3TEJkCPSDxXMP2uCRrL2xbQnsy"
    }],
    "count": 6
}       
```

##### 2.10.1.2 Get the issuers info
---
- Interface Address: /api/uia/issuers/:name
    - "name" could be the issuer's name or acchain account address.
- Request Methods: get
- Supported Format: urlencoded
- Response Parameter Description: 
 
|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|issuers|list  |element is dictionary, each dictionary represents a issuer, including "name", "desc", "issuerId" |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers/zhenxi' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "issuer": {
        "name": "zhenxi",
        "desc": "this is a description",
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    }
}
```

##### 2.10.1.3 Get the issuer assets
---
- Interface Address: /api/uia/issuers/name/assets
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name   | string | Y | issuer's name or acchain account address| 
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "name", ... |
|count | integer | the issuer's registered assets | 

- Request Example: 

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/issuers/zhenxi/assets?offset=0&limit=2' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "assets": [{
            "currency": "BTC",
            "name": "zhenxi.UIA",
            "desc": "this is a description",
            "maximum": "10000000",
            "precision": 3,
            "strategy": "",
            "quantity": "1000000",
            "height": 301,
            "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
            "acl": 0,
            "writeoff": 1
    }],
    "count": 1
}   
```

##### 2.10.1.4 Get all assets
---
- Interface Address: /api/uia/issuers/name/assets
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |


- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|bool  |true: response data return successfully |    
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "maximum", ... |
|count | integer | the issuer's registered assets | 

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets?offset=0&limit=2' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "assets": [{
        "name": "zhenxi.UIA",
        "desc": "this is a description",
        "maximum": "10000000",
        "precision": 3,
        "strategy": "",
        "quantity": "1000000",
        "height": 301,
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
        "acl": 0,
        "writeoff": 1
    },
    {
        "name": "speedtest.SPEED",
        "desc": "this is a description",
        "maximum": "10000",
        "precision": 1,
        "strategy": "",
        "quantity": "10000",
        "height": 380,
        "issuerId": "AEVWQWAq3TEJkCPSDxXMP2uCRrL2xbQnsy",
        "acl": 0,
        "writeoff": 0
    }],
    "count": 13
}       
```

##### 2.10.1.5 Get info by asset name
---
- Interface Address: /api/uia/assets/:name
- Request Methods: get
- Supported Format: urlencoded
- Request Parameters:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name | string | Y | asset name |

- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|assets |list  |element is dictionary, each dictionary represents a issuer, including "currency", "desc", "maximum", ... |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets/zhenxi.UIA' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "asset": {
        "name": "zhenxi.UIA",
        "desc": "this is a description",
        "maximum": "10000000",
        "precision": 3,
        "strategy": "",
        "quantity": "1000000",
        "height": 301,
        "issuerId": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a",
        "acl": 0,
        "writeoff": 1
    }
}
```


##### 2.10.1.6 Get the applying assets
---
- Interface Address: /api/uia/assets/applying
- Request Methods: get
- JSON Response Example:

```js
{
    "success":true,
    "assets":[
        {
            "currency":"A.AAA",
            "name":"A.sfsf",
            "desc":"sfasfsa",
            "maximum":"1000000000",
            "precision":1,
            "quantity":"0",
            "height":6931,
            "issuerId":"ACfjnjJtP9ZkprdLioohFS6Jp2CrAGfMS",
            "issuerName":"A",
            "category":"010912",
            "estimateUnit":"RMB",
            "estimatePrice":"100000000",
            "exerciseUnit":"sfasfsa",
            "extra":"{"productBrand":{"value":"sfasfsa"},"packingStandard":{"value":"sfasfsa"},"productIndex":{"value":"sfasfsa"},"productionInfo":{"value":"sfasfsa"},"otherInfo":{"value":"sfasfsa"}}",
            "unlockCondition":0,
            "approved":0
        }
    ],
    "count":1
}
```

##### 2.10.1.7 Get the applying issues
---
- Interface Address: /api/uia/issues/applying
- Request Methods: get
- JSON Response Example: 

```js
{
success: true,
issues: [
        {
            transactionId: "431dd812d00e2c7a9242b1b0f1bbf33b80b27e4a8bf333755673ab3ac0ff9d08",
            currency: "PuerBank.PEB",
            amount: "10000000",
            exchangeRate: "0.2",
            senderId: "A7KaYaLnWhSwCzrFVeE1TcXCQUY8WHB9hR"
        }
    ],
count: 1
}
```

##### 2.10.1.8 Get approved assets
---
- Interface Address: /api/uia/assets/approved
- Request Methods: get 
- JSON Response Example:

```js
{
    "success":true,
    "assets":[
        {
            "currency":"BTC",
            "name":"Bitcoin",
            "desc":"Bitcoin is a cryptocurrency and a digital payment system invented by an unknown programmer, or a group of programmers, under the name Satoshi Nakamoto. It was released as open-source software in 2009",
            "maximum":"21000000000000",
            "precision":6,
            "quantity":"50000000000",
            "height":1,
            "issuerId":"AGUaZUoJG5CYqPX32mWAcYQSKjvXu83V8o",
            "issuerName":"__SYSTEM__",
            "category":"1801",
            "estimateUnit":"RMB",
            "estimatePrice":"8000",
            "exerciseUnit":"1",
            "extra":"No extra information",
            "unlockCondition":0,
            "approved":1
        },
        {
            "currency":"asd.BUHG",
            "name":"asd.BUHG",
            "desc":"BUHG",
            "maximum":"1000000000",
            "precision":1,
            "quantity":"10000000",
            "height":6158,
            "issuerId":"APfs15A8KegKu1TtnJsWJvLoFxCKT7pRos",
            "issuerName":"asd",
            "category":"1717",
            "estimateUnit":"RMB",
            "estimatePrice":"100000000",
            "exerciseUnit":"BUHG",
            "extra":"{"productBrand":{"value":"BUHG"},"packingStandard":{"value":"BUHG"},"productIndex":{"value":"BUHG"},"productionInfo":{"value":"BUHG"},"otherInfo":{"value":"BUHG"}}",
            "unlockCondition":1,
            "approved":1
        },
        {
            "currency":"meiyingjugroup.RETSCHSR",
            "name":"RETSCHSR",
            "desc":"RET to House",
            "maximum":"6558750000",
            "precision":1,
            "quantity":"0",
            "height":7199,
            "issuerId":"ADfjWCQ6Ff5c2g62jzJbyQwHAe68TH1QWJ",
            "issuerName":"meiyingjugroup",
            "category":"1732",
            "estimateUnit":"USD",
            "estimatePrice":"655875000",
            "exerciseUnit":"220000",
            "extra":"{"productBrand":{"value":"Serene Country Homes"},"packingStandard":{},"productIndex":{},"productionInfo":{},"otherInfo":{}}",
            "unlockCondition":0,
            "approved":1
        }
    ],
    "count":3
}
```

##### 2.10.1.9 Get the assets access control lists
---
- Interface Address: /api/uia/assets/name/acl/flag
- Request Methods: get 
- Supported Format: urlencoded

- Request Parameter Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|name | string | Y | asset name |
|flag | boole | Y | 0 or 1, 0: black lists, 1: white lists |
|limit	|integer  | N  |the limitation of returned records，minimum：0,maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description:

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|success | boole | success or failure  |
|list | list | the address list  |
|count | integer | the list count |

- Request Example:

```js
// get zhenxi.UIA white lists 
curl -X GET -H "Content-Type: application/json"  'http://testnet.acchain.org/api/uia/assets/zhenxi.UIA/acl/1' && echo
```

- JSON Response Example: 

```js
{
    "success": true,
    "list": [{
        "address": "15745540293890213312"
    },
    {
        "address": "AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a"
    }],
    "count": 2
}       
```

##### 2.10.1.10 Get all the assets info of gave address
---
- Interface Address: /api/uia/balances/:address
    - `address` represents for user account address.
- Request Methods: get
- Supported Format: urlencoded
- Request Parameter Description:

|Name	|Type   |Required |Description              |   
|------ |-----  |---  |----              |   
|limit	|integer  | N  |the limitation of returned records，minimum：0, maximum：100    |
|offset |integer  | N  |offset, minimum 0   |

- Response Parameter Description: 

|Name	|Type   |Description              |   
|------ |-----  |----              |     
|success | boole | success or failure  |
|balances | list | owned asset info list, each element is a asset, including some details  |
|count | integer |the assets count of this address   |

- Request Example:

```js
curl -X GET -H "Content-Type: application/json" 'http://testnet.acchain.org/api/uia/balances/AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a' && echo
```

- JSON Response Example:

```js
{
    "success": true,
    "balances": [{
            "currency": "zhenxi.UIA",
            "name":"UIA",
            "balance": "900000",
            "maximum": "10000000",
            "precision": 3,
            "quantity": "1000000",
            "writeoff": 1
    },
    {
            "currency": "speedtest.SPEED",
            "balance": "400",
            "maximum": "10000",
            "precision": 1,
            "quantity": "10000",
            "writeoff": 0
    }],
    "count": 2
}       
```

##### 2.10.1.11 Get UIA Exercise
---
- Interface Address: /api/uia/exercises
- Request Methods: get
- Supported Format: none
    - if no parameter passed, it will return all exercise record

- Request Parameter Description:  

|Name	|Type   |Required |Description              |    
|------ |-----  |---  |----              |   
|currency|string  |N      |exercise record of this currency   |
|id| string | N | account id |

- Response Parameter Description:   

|Name	|Type   |Description              |   
|------ |-----  |----              |   
|success|boole  |success or failure |    
|exercises|json  |list of exercise，each contains transactionId, currency, timestamp..|
|count  |integer  | exercise count |
   
   
- Request Example:
   
```bash   
curl -k -X GET 'https://testnet.acchain.org/api/uia/exercises?currency=TESTREAL.RET'  
// or
curl -k -X GET 'https://testnet.acchain.org/api/uia/exercises?id=3bf8892a33eadb2617dbc35934a4781bd0a50834524208a68faedb39fc12b510' 
```   
   
- JSON Response Example:
   
```
{"success":true,"exercises":[{"transactionId":"d5cf82f37a35537e73cb921f662b4fe162e7c4d715e4c397a4811db6cf949057","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29254858},{"transactionId":"086c912812c8b7ee0bd70cff80cbed83f0efa8a08230722fdf5b5502b1aa6238","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29254924},{"transactionId":"f7649cf70ad62203c7279be3e3cd0d8b7ecdf5e2073ab20546d521ca87a729ba","currency":"TESTREAL.RET","amount":"100","precision":1,"senderId":"AD7tetn1WGEAaWeU8BCaK7fRcNKcHKzV6f","timestamp":29311954}],"count":3}
```


#### 2.10.2 Create UIA Transaction
---
Acchain system's every operation is raised by a transaction. The transaction is built by a framework called "AcchainJS", then POST the transaction.

##### 2.10.2.1 Create Issuer
---
- Interface Address: /peer/transactions
- Request Methods: get
- Supported Format: json
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createIssuer(name, desc, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
// issuer name, unique
var name = 'IssuerName'
// issuer description
var desc = 'IssuerDesc'
// create issuer
var trs = AcchainJS.uia.createIssuer(name, desc, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":9,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19395607,"asset":{"uiaIssuer":{"name":"IssuerName","desc":"IssuerDesc"}},"signature":"c6ed2a4bafe2b8aa31f4aaceacc2a96cb028abbabb2ed062937498c58e24ca5467a340ddd63b67f809a680ff91b83e685c64991eb695494ddb2fdc57e5761607","signSignature":"8eceacbd47c2b8ed335145ced19d7a3a51f99bdd6631d16ed214180c6f80e29bd6d572f45e7c7d685584e55cb5c303cf340406553ece28c9c0a2fa7a777aac0b"}

// http post the 'trs' to the server, register issuer name
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":9,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19395607,"asset":{"uiaIssuer":{"name":"IssuerName","desc":"IssuerDesc"}},"signature":"c6ed2a4bafe2b8aa31f4aaceacc2a96cb028abbabb2ed062937498c58e24ca5467a340ddd63b67f809a680ff91b83e685c64991eb695494ddb2fdc57e5761607","signSignature":"8eceacbd47c2b8ed335145ced19d7a3a51f99bdd6631d16ed214180c6f80e29bd6d572f45e7c7d685584e55cb5c303cf340406553ece28c9c0a2fa7a777aac0b"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true}  
```

##### 2.10.2.2 Register Assets
---
- Interface Address: /peer/transactions
- Request Methods: post
- Supported Format: json
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createAsset(name, desc, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var extra = {
    "productBrand": {
        "value":"ABC",
        "remark":"ABC",
        "link":"ABC"
    },
    "packingStandard": {
        "value":"BCD",
        "remark":"BCD",
        "link":"BCD"
    },
    "productIndex": {
        "value":"CDE",
        "remark":"CDE",
        "link":"CDE"
    },
    "productionInfo": {
        "value":"DEF",
        "remark":"DEF",
        "link":"DEF"
    },
    "otherInfo": {
        "value":" ",
        "remark":" ",
        "link":" "
    },
    "moreDetails":" "
}
var payload = {
    name: 'IssuerName.CNY',// assets name，issuer.assetsName，unique
    currency: "CNY",// currency: BTC,ETH..
    desc: 'this is a description',
    category: '',// assets category
    precision: 3,// precision，for instance: maximum = 1000000，precision = 3，and the IssuerName.CNY actual maximum is 1000.000
    maximum: '1000000',
    estimateUnit: '',
    estimatePrice: '',
    exerciseUnit: '',
    unlockCondition: 0,// unlock condition = 0 or 1
    extra: extra
}
// create assets
var trs = AcchainJS.uia.createAsset(payload, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":10,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19397444,"asset":{"uiaAsset":{"name":"IssuerName.CNY","desc":"this is a description","maximum":"1000000","precision":3,"strategy":""}},"signature":"c755587d331dd2eb62ef91dce1511d83a3e603c7cdc7548a16052519c21ea89c78364e35e5d46da0e2103fa2fb7f037eec55a5deba18826fa13e4252422d750e","signSignature":"1b7ed4c21c477b8ff3d2acfdfd7ff85617093f4c21de70938c46b61c9704b037dbcf7f9e5f5dd1a5dc8f22cf473aaa459e6e5b15ced388b8a1da1e307987a509"}

// http post the 'trs' to the server，register assset IssuerName.CNY
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":10,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19397444,"asset":{"uiaAsset":{"name":"IssuerName.CNY","desc":"资产描述","maximum":"1000000","precision":3,"strategy":""}},"signature":"c755587d331dd2eb62ef91dce1511d83a3e603c7cdc7548a16052519c21ea89c78364e35e5d46da0e2103fa2fb7f037eec55a5deba18826fa13e4252422d750e","signSignature":"1b7ed4c21c477b8ff3d2acfdfd7ff85617093f4c21de70938c46b61c9704b037dbcf7f9e5f5dd1a5dc8f22cf473aaa459e6e5b15ced388b8a1da1e307987a509"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true} 
```

##### 2.10.2.3 Assets Issue
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createIssue(currency, amount, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// 本次发行量=真实数量（100）*10**精度（3），所有发行量之和需 <= 上限*精度
var amount = '100000'
var trs = AcchainJS.uia.createIssue(currency, amount, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":13,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19475744,"asset":{"uiaIssue":{"currency":"IssuerName.CNY","amount":"100000"}},"signature":"32b01a18eca2b0dc7e2ce77ba4e758eaae2532f60844760a762cc20918e7439ac6ca585b921db6ede833ed0bf1c62e30cec545a928abafe0b679183a6ad02202","signSignature":"4fc290d7d7d788e9112a56233df0fe796cba39be3efa0cebf00cbc7e5bc5fd1369fad49e5698d967845b5c02e427926049cab25845d4d385e4a395791906f909"}

curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":13,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19475744,"asset":{"uiaIssue":{"currency":"IssuerName.CNY","amount":"100000"}},"signature":"32b01a18eca2b0dc7e2ce77ba4e758eaae2532f60844760a762cc20918e7439ac6ca585b921db6ede833ed0bf1c62e30cec545a928abafe0b679183a6ad02202","signSignature":"4fc290d7d7d788e9112a56233df0fe796cba39be3efa0cebf00cbc7e5bc5fd1369fad49e5698d967845b5c02e427926049cab25845d4d385e4a395791906f909"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true,"transactionId":"ffd7500b944451adfaea20578a9ecab382e66dc8a11358901dfa8456c4aaa91d"}
```

##### 2.10.2.4 Assets Transfer
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createTransfer(currency, amount, recipientId, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// amount（10000）=真实数量（10）*10**精度（3），需 <= 当前资产发行总量
var amount = '10000'
// 接收地址，需满足前文定义好的acl规则
var recipientId = 'AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a'
var trs = AcchainJS.uia.createTransfer(currency, amount, recipientId, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":14,"amount":0,"fee":10000000,"recipientId":"AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a","senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19481489,"asset":{"uiaTransfer":{"currency":"IssuerName.CNY","amount":"10000"}},"signature":"77789071a2ad6d407b9d1e0d654a9deb6d85340a3d2a13d786030e26ac773b4e9b5f052589958d2b8553ae5fc9449496946b5c225e0baa723e7ddecbd89f060a","signSignature":"f0d4a000aae3dd3fa48a92f792d4318e41e3b56cdbaf98649261ae34490652b87645326a432d5deb69f771c133ee4b67d2d22789197be34249e6f7f0c30c1705"}

// send 'AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a' 10.000 IssuerName.CNY asset
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":14,"amount":0,"fee":10000000,"recipientId":"AKKHPvQb2A119LNicCQWLZQDFxhGVEY57a","senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19481489,"asset":{"uiaTransfer":{"currency":"IssuerName.CNY","amount":"10000"}},"signature":"77789071a2ad6d407b9d1e0d654a9deb6d85340a3d2a13d786030e26ac773b4e9b5f052589958d2b8553ae5fc9449496946b5c225e0baa723e7ddecbd89f060a","signSignature":"f0d4a000aae3dd3fa48a92f792d4318e41e3b56cdbaf98649261ae34490652b87645326a432d5deb69f771c133ee4b67d2d22789197be34249e6f7f0c30c1705"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```
  
- JSON Response Example:
  
```js
{"success":true} 
```
##### 2.10.2.5 Assets Exercise
--- 
- Request Parameter Description:

|Name	|Type   |Required |Description   |  
|------ |-----  |---  |----      |   
|transaction|json|Y|AccchainJS.uia.createExercise data created by currency、amount、secret、secondSecret|

- Response Parameter Description:   

|Name	|Type   |Description |  
|------ |-----  |----   |   
|success|boole  |success or failure |  

- Request Example:

```js   
var currency = 'IssuerName.CNY'
var amount = '1000'
var message = 'this is the remarks'
var trs = AccchainJS.uia.createExercise(currency, amount, secret, message, secondSecret)
console.log(JSON.stringify(trs))
 {"type": 12, "amount": "0", "fee": 100000, "recipientId": null, "senderPublicKey":"a7628dc36cc9be73a9d4aa5a61c4ed36ff0ef150139e503f7ced47f237cb2fcf", "timestamp": 29252257, "asset": {"uiaExercise": {"currency": "TESTREAL.RET", "amount":"100"}},"signature":"d4571a90222e77930c125c64d0e710edd2b5aa686ba66e45d80f7d78694ba72115cdfe52e6190cefc88131a5171b03eaba6f25757c800545aeef2a8b82152d0a"}

curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type": 12, "amount": "0", "fee": 100000, "recipientId": null,"senderPublicKey":"a7628dc36cc9be73a9d4aa5a61c4ed36ff0ef150139e503f7ced47f237cb2fcf", "timestamp": 29252257, "asset": {"uiaExercise":{"currency":"TESTREAL.RET","amount":"100"}},"signature":"d4571a90222e77930c125c64d0e710edd2b5aa686ba66e45d80f7d78694ba72115cdfe52e6190cefc88131a5171b03eaba6f25757c800545aeef2a8b82152d0a"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```   
   
- JSON Response Example:  

```js  
{"success":true}        
``` 


#### 2.10.3 UIA Vote

##### 2.10.3.1 Get voters by assets currency

- Interface Address: /api/uia/assets/:currency/voters
    - `currency` is the symbol of the assets, for example: TEST.ABC
- Request Methodss: get
- JSON Response Example:

```js
{
    "success": true,
    "voters": [
        {
            "voter": "delegate1",  
            "weight": "500"
        }
    ],
  "count": 9
}
```

##### 2.10.3.2 Get voters for issues 
---
- Interface Address: /api/uia/issues/:id/voters
    - `id` is a transaction from previous interface.
- Request Methods: post
- JSON Response Example:

```js
{
    "success": true,
    "voters": [
        {
            "voter": "delegate1",  
            "weight": "500"
        }
    ],
  "count": 9
}
```

#### 2.10.4 UIA Control

##### 2.10.4.1 Set `acl` mode
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createFlags(currency, flagType, flag, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// 1：circulation，2：withdraw
var flagType = 1
// acl mode，0：black list， 1：white list，default mode is black list after asset created
var flag = 1
var trs = AcchainJS.uia.createFlags(currency, flagType, flag, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":11,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19400996,"asset":{"uiaFlags":{"currency":"IssuerName.CNY","flagType":1,"flag":1}},"signature":"b96fb3d1456e1f26357109cc24d82834eb9a4687f29e69c374bbb1d534568336e148cac52f213aa4d2a69185092f8e1143b49ec4b8048cd9b3af4e20f6ba0b08","signSignature":"b37c77ebebe90341346be2aefe1e12bd7403e5d8f4d6e8f04630190b3e09494a28820da0ffd5f9ff011033aa6d70fc9bb4c159a4493be3b18fd7ff470103570d"}

// post the 'trs' to server，change the acl mode to white list
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":11,"amount":0,"fee":10000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19400996,"asset":{"uiaFlags":{"currency":"IssuerName.CNY","flagType":1,"flag":1}},"signature":"b96fb3d1456e1f26357109cc24d82834eb9a4687f29e69c374bbb1d534568336e148cac52f213aa4d2a69185092f8e1143b49ec4b8048cd9b3af4e20f6ba0b08","signSignature":"b37c77ebebe90341346be2aefe1e12bd7403e5d8f4d6e8f04630190b3e09494a28820da0ffd5f9ff011033aa6d70fc9bb4c159a4493be3b18fd7ff470103570d"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true} 
```

##### 2.10.4.2 Update acl lists
---
- Request Parameter Description:

|Name	|Type   |Required |Description   |   
|------ |-----  |---  |----              |   
|transaction	|json  | Y  |AcchainJS.uia.createAcl(currency, operator, flag, list, secret, secondSecret) |

- Response Parameter Description:

|Name	|Type   |Description |   
|------ |-----  |----   | 
|success | boole | success or failure |

- Request Example:

```js
var currency = 'IssuerName.CNY'
// '+'add list， ‘-’remove list
var operator = '+'
var list = ['15745540293890213312']
// acl type，0：black list， 1：white list
var flag =1
var trs = AcchainJS.uia.createAcl(currency, operator, flag, list, secret, secondSecret)
console.log(JSON.stringify(trs))
{"type":12,"amount":0,"fee":20000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19403125,"asset":{"uiaAcl":{"currency":"IssuerName.CNY","operator":"+","flag":1,"list":["15745540293890213312"]}},"signature":"ad4060e04c1a12256de114e34499f8add24326753f1f8362991ee14aefc4c0fe90ff394d2db97e83770855a5688d463de00656fdd2d04604605cf3c04fdaca0e","signSignature":"63129c58b1b9fcce88cbe829f3104a10ab06037253e9b65feb50ce0d2bb988533b93e8edcad016a85675f9027758fc318cf899ca7ef161a95a8d8a055ae83a02"}

// post the 'trs' to server，add ['15745540293890213312'] to white list，only modify the list，not modify the acl mode，cost fee 0.2ACC
curl -H "Content-Type: application/json" -H "magic:8e9b66ed" -H "version:''" -k -X POST -d '{"transaction":{"type":12,"amount":0,"fee":20000000,"recipientId":null,"senderPublicKey":"fafcd01f6b813fdeb3c086e60bc7fa9bfc8ef70ae7be47ce0ac5d06e7b1a8575","timestamp":19403125,"asset":{"uiaAcl":{"currency":"IssuerName.CNY","operator":"+","flag":1,"list":["15745540293890213312"]}},"signature":"ad4060e04c1a12256de114e34499f8add24326753f1f8362991ee14aefc4c0fe90ff394d2db97e83770855a5688d463de00656fdd2d04604605cf3c04fdaca0e","signSignature":"63129c58b1b9fcce88cbe829f3104a10ab06037253e9b65feb50ce0d2bb988533b93e8edcad016a85675f9027758fc318cf899ca7ef161a95a8d8a055ae83a02"}}' 'http://testnet.acchain.org/peer/transactions' && echo
```

- JSON Response Example:

```js
{"success":true}
// check updated lists（acl/1:white list）
curl -X GET -H "Content-Type: application/json" 'http://testnet.acchain.org/api/uia/assets/IssuerName.CNY/acl/1?limit=10&offset=0' && echo
{
    "success": true,
    "list": [{
        "address": "15745540293890213312"
    }],
    "count": 1
}
```


#### 2.10.5 Get Assets Category

##### 2.10.5.1 Get First Category
---
- Interface Address: /api/uia/categories/0
- Request Methods: get
- JSON Response Example:

```js
{
    "success": true,
    "categories": [
        {
            "id": "01",
            "attrs": ["food"],
            "hasChildren": true
        },
        {
            "id": "02",
            "attrs": ["cloth"],
            "hasChildren": true
        }
    ],
  "count": 9
}
```

##### 2.10.5.2 Get Category By id
---
- Interface Address: /api/uia/categories/:id
    - `id` is the previous number.
- Request Methods: get
- JSON Response Example:

```js
{
    "success": true,
    "categories": [
        {
            "id": "1001",
            "attrs": ["BTC"]，
            "hasChildren": false
        },
        {
            "id": "1002",
            "attrs": ["LTC"],
            "hasChildren": false
        1}
    ],
  "count": 9
}
```

`attrs` represents the goods category name, and may be serval language, the first is the English, the second is the Chinese. 
 
   


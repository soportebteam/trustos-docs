# Trust

This API is used to create and register trust points on the private and public blockchain and verify the integrity of all the encapsulated data

## API Specification

An abstraction API with all the asset functionalities

### Trust Point
A trust point is `<JSON>` object used to export the integrity of the transactions over an asset in a private blockchain such as Hyperledger Fabric, to public blockchains such as Ethereum, in order to provide an extra layer of security.


This is the structure of a trust point:

- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
- `end` :  `<integer>` Timestamp at which this trust point is made
- `ethereumContractAddress` :  `<string>` The smart contract in Ethereum to manage trust points
- `hash` :  `<string>`  Hash of the trust point (as a JSON) to verify integrity
- `txRoot` :  `<string>` Hash of all transactions in the interval
- `hftxid` :  `<string>` Last trust transaction in Hyperledger Fabric
- `init` :  `<integer>` Timestamp for the previous trust point
- `prevHash` :  `<string>` Hash of the previous trust point
- `prevhftxid` :  `<string>`  Hash of the previous transaction (in the blockchain)

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": {
    "assetid": "exampleAsset",
    "end": 1557830077,
    "ethereumContractAddress": "0xeE83b6D6dc84fa0c91A6f99971f6CF29F6B7ea3b",
    "hash": "3P1HZ+pvbwhogR3tgKng7cWTk6uaHynGKvjqPjpISi0=",
    "txRoot": "DGjUiCplVGom99o6bbdIXAIEqNKgVoQGi7rFNwDX+to=",
    "hftxid": "671e8c065add74a4759167b9f38cf67916f0f26b5e9b1861c2abcb08a57f8a97",
    "init": 0,
    "prevHash": "",
    "prevhftxid": "0"
  }
}

```
</details>
<br>

### Methods

<details>
  <summary><em><strong>Trust methods</strong></em> (Click to expand)</summary>

---

#### GET  -   `/trust/assetId`  

Gets the last trust point in the system for a specific asset

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
  
*Output*
- `trustpoint`    :  `<json>`

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": {
      "assetId": "exampleAsset",
      "end": 1567601354,
      "ethereumContractAddress": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "hash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
      "hfTxId": "5c709f206555dbc6a40e37e96aa007a471f706927c8581fb91aef3625413e234",
      "init": 1567594895,
      "prevHash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "prevHfTxId": "70c26cfc9aeef3c094b82278b7ed413255f07711366ac2a9da8de7e66b9e53ee",
      "txRoot": "TBSNvFDt3tGDhI5I48IRlBh2l+O0X+kjBq7/96Zk/wI="
    }
}

```
</details>

---

#### GET  -   `/trust/assetId/history`  

Gets all trust point history in the system for a specific asset

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
  
*Output*
- `trustpoint`    :  `<json>`

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
[{
  "output": [
    {
      "assetId": "exampleAsset",
      "end": 1567594895,
      "ethereumContractAddress": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "hash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "hfTxId": "70c26cfc9aeef3c094b82278b7ed413255f07711366ac2a9da8de7e66b9e53ee",
      "init": 0,
      "prevHfTxId": "0",
      "txRoot": "oGFYgnxCcPvpa2d6G4vHLs92HQgY2z6S8uwIVM0Qg44="
    },
    {
      "assetId": "exampleAsset",
      "end": 1567601354,
      "ethereumContractAddress": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "hash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
      "hfTxId": "5c709f206555dbc6a40e37e96aa007a471f706927c8581fb91aef3625413e234",
      "init": 1567594895,
      "prevHash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "prevHfTxId": "70c26cfc9aeef3c094b82278b7ed413255f07711366ac2a9da8de7e66b9e53ee",
      "txRoot": "TBSNvFDt3tGDhI5I48IRlBh2l+O0X+kjBq7/96Zk/wI="
    }
  ]
]

```
</details>

---



#### POST -  `/trust/assetId/create`  

Creates a trust point in the system for a specific asset

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
  
*Output*
- `trustpoint`    :  `<json>` 

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": {
      "assetId": "exampleAsset",
      "end": 1567601354,
      "ethereumContractAddress": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "hash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
      "hfTxId": "5c709f206555dbc6a40e37e96aa007a471f706927c8581fb91aef3625413e234",
      "init": 1567594895,
      "prevHash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "prevHfTxId": "70c26cfc9aeef3c094b82278b7ed413255f07711366ac2a9da8de7e66b9e53ee",
      "txRoot": "TBSNvFDt3tGDhI5I48IRlBh2l+O0X+kjBq7/96Zk/wI="
    }
}

```
</details>

---

#### GET  -   `/trust/{assetId}/merkleroot`  

Gets the last trust merkle root stored in the system

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust root is stored
  
*Output*
- `trustroot`    :  `<json>`

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": {
    "timestamp": 1567601354,
    "trustHash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
    "trustRoot": "/unY4B8YDNq/+mdO1iL/Ztng+gbxBput2qnjG+LGMqU="
  }
}

```
</details>

---

#### GET  -   `/trust/{assetId}/merkleroot/history`  

Gets the trust merkle root history stored in the system

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust root is stored
  
*Output*
- `trustroot`    :  `<json>`

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": [
    {
      "timestamp": 1567594895,
      "trustHash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "trustRoot": "Vz3ZFr+wTOt0FNbcfhEr+Ziy/Y/jsfNGz693KcqYa5E="
    },
    {
      "timestamp": 1567601354,
      "trustHash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
      "trustRoot": "/unY4B8YDNq/+mdO1iL/Ztng+gbxBput2qnjG+LGMqU="
    }
  ]
}

```
</details>

---

#### POST -  `/trust/assetId/register`  

Creates a trust point if does not exist and registers it in Ethereum. If the trust point already exists registers it in Ethereum.

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
  
*Output*
- `trustpoint` :  `<json>` 

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output":  {
      "assetId": "exampleAsset",
      "end": 1567601354,
      "ethereumContractAddress": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "hash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
      "hfTxId": "5c709f206555dbc6a40e37e96aa007a471f706927c8581fb91aef3625413e234",
      "init": 1567594895,
      "prevHash": "Ni7JYQG6GSmlEjWoRj2xrfF6ZVFhqBDPzyjk+o/HB2c=",
      "prevHfTxId": "70c26cfc9aeef3c094b82278b7ed413255f07711366ac2a9da8de7e66b9e53ee",
      "txRoot": "TBSNvFDt3tGDhI5I48IRlBh2l+O0X+kjBq7/96Zk/wI="
    }
}

```
</details>

---

#### POST   -   `/trust/assetId/verify`

Verifies a trust point 

*Input*
- `assetid` :  `<string>` Identifier of the asset for which the trust point is made
- `timestamp` : `<string>` Timestamp at which this trust point is made

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "timestamp": "1559822594",
}

```
</details>

*Output*
- `ethereum`:  `<json>` Ethereum info
  - `trustRoot`:  `<string>` Trust points merkle root registered on Ethereum
  - `lastEthTxId`:  `<string>` Last transaction for the trust point in Ethereum
  - `smartContractAddres`:  `<string>` The smart contract in Ethereum to manage trust points 
  - `verified`:  `<bool>` Boolean value to specify if the trust point is registered in Ethereum
- `hf`:  `<json>` Hyperledger Fabric info
  - `trustRoot`:  `<string>` Trust points merkle root stored in HF
  - `timestamp`:  `<string>` Timestamp at which this trust point is made
  - `verified`:  `<bool>` Boolean value to specify if the trust point is registered in Ethereum and it is has not been modified


<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js

{
  "output": {
    "ethereum": {
      "lastEthTxId": "0x8ad8f928c261a5b7f2b6515320dfffe1f9f923b17c5e07f6f733f43703f95f87",
      "smartContractAddres": "0x1B646bc6C3465Fa8171F7171097A7d8e37b43D6B",
      "trustHash": "NGz693K+cqYasFNbcfhEr+Ziy/Y/jsfOt0FNKcqYa5E=",
      "trustRoot": "/unY4B8YDNq/+mdO1iL/Ztng+gbxBput2qnjG+LGMqU=",
      "verified": true
    },
    "hf": {
      "timestamp": 1567601354,
      "trustHash": "NGz693K+cqYasFNbcfhEr+Ziy/Y/jsfOt0FNKcqYa5E=",
      "trustRoot": "/unY4B8YDNq/+mdO1iL/Ztng+gbxBput2qnjG+LGMqU=",
      "verified": true
    }
  }
}

```
</details>
</details>
<br>

### MerkleRoot

In order to achieve the integrity and inmutability of all trust points, every time a trust point is create a parallel process is executed. This process consist of the building of a trust-based merkle tree. All the trust points created until that moment are the leaves of the tree that generates a unique merkle root. That merkle root, called as trustRoot, is registered in HF as well as in Ethereum to proof the integrity. So, every time a new trust point is created, a new trustRoot is created too, and it could be registered in Ethereum or not, depends of the user neccessity


This is the structure registered in HF and Ethereum, once the trust merkle tree is calculated:

- `timestamp` :  `<integer>` Timestamp at which the related trust point is made
- `trustHash` :  `<string>` Hash of the last trust point included to verify integrity
- `trustRoot` :  `<string>` Root of the trust merkle tree calculated with all the trust points until that moment

<details>
  <summary><em><strong>Sample structure</strong></em> (Click to expand)</summary>

```js
{
  "output": {
    "timestamp": 1567601354,
    "trustHash": "7KYLJXcjGA67WD0v95UvoVPk+sj9M8FdpecS5mRz3+s=",
    "trustRoot": "/unY4B8YDNq/+mdO1iL/Ztng+gbxBput2qnjG+LGMqU="
  }
}

```
</details>
<br>

## Architecture of the project
```
coren-trustapi
├── api
      ├── handler           // HTTP logic
      ├── model             // models used by the application
      ├── service           // Usecases logic
      ├── util              // Tools used by the application
          ├── log           // Logger tool
          ├── http          // Http util
          └── Config        // Tool to load the configuration from yaml files
      └── app.go            // Router application
├── config
      └── config.yaml       // Config file
├── docs
      └── docs.go           // Swagger doc file
├── postman                 // Postman collection and environment to test the API
      ├── collection    
      └── environment
├── docker-compose.yaml     // Instructions to build docker container
├── Dockerfile              // Instructions to build docker image
├── init.sh                 // Script with global environment variables
└── main.go                 // Main app
 ```   

## Project configuration
This project has too bee stored in the following route:
```
$GOPATH/src/github.com/name_of_the_project
```

## Running the Application
To initialize the application execute the following commands:
```
source ./init.sh
go run main.go
```

Also the application can be executed with docker:
```
docker-compose up -d
```

## Testing the Application
In postman folder there are the collection and environment to interact and test with the API methods. It is only needed to import them into postman application and know to use the coren-trustapi module

## Errors management
  
  Trust API errors are managed through the following nomenclature **TRUST-XX** which corresponds to:<br>


<style type="text/css">
.tg  {border-collapse:collapse;border-spacing:0;}
.tg td{font-family:Arial, sans-serif;font-size:14px;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg th{font-family:Arial, sans-serif;font-size:14px;font-weight:normal;padding:10px 5px;border-style:solid;border-width:1px;overflow:hidden;word-break:normal;border-color:black;}
.tg .tg-0pky{border-color:inherit;text-align:left;vertical-align:top}
.tg .tg-0lax{text-align:left;vertical-align:top}
</style>
<table class="tg">
  <tr>
    <th class="tg-0pky">Code</th>
    <th class="tg-0pky">Description</th>
  </tr>
  <tr>
    <td class="tg-0pky">TRUST-00</td>
    <td class="tg-0pky">Service is down</td>
  </tr>
  <tr>
    <td class="tg-0pky">TRUST-01</td>
    <td class="tg-0pky">Error parsing any data structure</td>
  </tr>
  <tr>
    <td class="tg-0lax">TRUST-02</td>
    <td class="tg-0lax">Error of some kind of functionality</td>
  </tr>
</table>
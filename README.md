![Build Status](https://travis-ci.com/epirus-io/epirus-local.svg?branch=master)
![codecov](https://codecov.io/gh/epirus-io/epirus-local/branch/master/graph/badge.svg)
![Join the chat at https://gitter.im/web3j/web3j](https://badges.gitter.im/web3j/web3j.svg)
# Epirus-local

Epirus-local is a local ethereum client, similar to what [Ganache](https://github.com/trufflesuite/ganache) provides, written in Kotlin.

This project relies on [web3-evm](https://github.com/web3j/web3j-evm) to execute user requests.

## Features
- Allows json-rpc interactions with a local ethereum blockchain.
- Generates a default genesis file containing 10 ethereum accounts or lets you use your own genesis.
- Provides a CLI to run the client.
- Handles these operations:
    - eth_blockNumber
    - eth_getTransactionCount
    - eth_getBalance
    - eth_sendTransaction
    - eth_sendRawTransaction
    - eth_estimateGas
    - eth_getBlockTransactionCountByHash
    - eth_getBlockTransactionCountByNumber
    - eth_getTransactionReceipt
    - eth_getCode
    - eth_call
    
    
## Getting started
`git clone https://github.com/epirus-io/epirus-local && cd epirus-local`
    
`./gradlew installDist`
    
#### Run in Linux:
`build/install/epirus-local/bin/epirus-local [command]`
    
#### Run in Windows
`build\install\epirus-local\bin\epirus-local.bat [command]`


### Start the client

```
epirus-local start -d=/path/to/directory -p=9090
```
this command generates a new genesis file with 10 accounts filled with 100 ether via providing a directory where to put it.

![start command](https://raw.githubusercontent.com/epirus-io/epirus-local/master/resources/epirus-local-start-command-demo.gif)

### Load from previous configuration

```
epirus-local load -g=/path/to/genesis
```
This command loads a pre-existing genesis-file from a certain path.

![load command](https://raw.githubusercontent.com/epirus-io/epirus-local/master/resources/epirus-local-load-command-demo.gif)


### Send requests

###### Example of a request
```
curl -X POST --data '{"jsonrpc":"2.0","method":"eth_sendTransaction","params":[{
  "from": "0x8f496c16955a7bb9b5e1ea0383d01f87372ab520",
  "to": "0xd46e8dd67c5d32be8058bb8eb970870f07244567",
  "gas": "0x76c0", 
  "gasPrice": "0x9184e72a000", 
  "value": "0x9184e72a",
  "nonce": "0x1"
}],"id":1}' host:port
```

###### Example of a response
```
{"id" : 1, "jsonrpc" : "2.0", "result" : "0xc631caa67cab48ead77a58321bbb0c76f4060751a4bb3d5b45b99c4a68b1a7b7"}
```

For more information about the requests, check the Ethereum [json-rpc](https://github.com/ethereum/wiki/wiki/JSON-RPC) api.
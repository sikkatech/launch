# Straightedge Mainnet Launch

This repository is to coordinate the relaunch of the Straightedge mainnet, rebuilt on the Cosmos SDK.

The goal of Straightedge is to be a general-purpose smart contracting platform governed by the holders of the STR token.

## STR Token

The native token of the Straightedge network is known as STR.  The smallest denomination of STR is called `astr`.  There are `10^18` astr in 1 STR.  The SI prefix for `10^-18` is called "atto", thus `astr` is short for `atto-STR`.  It also sounds like "astro", a fitting name for Straightedge as a Cosmic Smart Contracting platform.

The initial supply of the STR token is 5 billion STR.  Of this, 90% is distributed based on the participation from the Edgeware lockdrop, modified to ignore signals from deployers of contracts.  Further details about this matter can be found in [this blog post](https://medium.com/straightedge/on-the-straightedge-genesis-block-d073e78b9b02).

In Edgeware, 10% of the initial distribution was distributed as a founder's reward to Commonwealth Labs, Parity Technologies, and a community fund managed by Commonwealth Labs.  In the initial Straightedge distribution, this 10% (500 million tokens) is deposited directly into the on-chain governed community pool.  It is encouraged that this be distributed by governance as a founder's reward to entities that were instrumental in the creation of the Straightedge network.

## Functionality

Similar to the [Cosmos Hub codebase (Gaia)](https://github.com/cosmos/gaia), the Straightedge blockchain inherits much of its functionality from the [core modules of the cosmos sdk](https://github.com/cosmos/cosmos-sdk/tree/master/x).  It uses the standard bank, staking, slashing, governance, and upgrade modules of the Cosmos SDK.

It also includes the [CosmWasm module](https://github.com/cosmwasm/wasmd/tree/master/x/wasm), a project built to allow WebAssembly-based smart contracting in the Cosmos SDK.  For more information of CosmWasm and tutorials on how to get started with using it, please check out the [CosmWasm website](https://www.cosmwasm.com/).

In the future, it is possible for the Straightedge to upgrade to support more smart contracting systems, such as the Cosmos SDK's [EVM module](https://github.com/chainsafe/ethermint).

In order to support the hard spoon of Edgeware lockdrop balances, we needed to add support of the SR25519 keys into the Cosmos SDK.  We would like to give special thanks to ChainSafe team for their help on some of this work.

For instructions on how to add your lockdrop keys to the Straightedge CLI wallet, please follow the instructions here.

## Genesis Transactions

You must have a balance in the genesis file to paritipate as a genesis validator.  Instructions for submitting genesis transactions can be found [here](./instructions.md).

## Recreating Genesis

To recreate the genesis file, the following steps can be take:

1. Creating new genesis file using `strd init`
2. Change chain-id in genesis file to `straightedge-1`
3. Modify the genesis parameters using the instructions [here](./genesis-params.md)
4. Install the [straightedge-lockdrop](https://github.com/heystraightedge/straightedge-lockdrop) software and follow setup instructions.
5. Generate [balances.json](building-genesis/balances.json) by running `node ./scripts/lockdrop.js --allocation`.  This constructs the file using on-chain data from Ethereum.  Note that an Ethereum archival node is neccesary for this step.
6. Use `strd import-lockdrop-balances balances.json` to populate genesis with lockdrop balances.
7. TODO: GenTxs

## Disclaimer

Please note that the Straightedge blockchain is highly experimental software. In these early days, we can expect to have issues, updates, and bugs. The existing tools require advanced technical skills and involve risks which are outside of the control of the developers. Any use of this open source Apache 2.0 licensed software is done at your own risk and on a “AS IS” basis, without warranties or conditions of any kind, and any and all liability of the developers for damages arising in connection to the software is excluded. Please exercise extreme caution!
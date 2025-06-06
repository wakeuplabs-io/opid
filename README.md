
# Optimism privado id

Collection of repositories that allow for privadoid to run on optimism.

[Learn more about Optimism Id](https://github.com/wakeuplabs-io/opid-documentation)

## Repo overview

This repo is a collection of repos, mostly forks of privadoid and iden3, that allow to run an identity system in the optimism chain. We'll mention each of them and shortly explain what you can find there:
- contracts: IDEN3 Smart Contracts.
- docs: Opid documentation based on privado's but customed for optimism.
- examples:
    - contracts: Example contracts using verifiers.
    - demo: Frontend implementation that connects to contracts and issuer-node for showcase porpoise.
    - js-sdk: Examples on the js-sdk on how to do multiple relevant things.
- issuer-node: Privado ID issuer fork adapted to support opid and optimism out of the box.
- issuer-node-gcp: Deployment for GCP of the issuer-node.
- js-sdk: Privado ID js sdk fork adapted to support opid and optimism out of the box.
- method: This repository contains the `did:opid` DID Method Specification.


## OP Stack integration proposition

In this section we'll propose a way for the optimism chains created with opstack can benefit from the identity sdk out of the box and with minimal effort.

To do this it's important to recognize the components that conform the identity kit. 
- Onchain State and Validators.
- Onchain or Offchain Issuer plus associated services.
- Dapps and wallets leveraging the issued credentials.

Out of this 3 components we easily identify the Onchain State and Validators as the core and universal component on which all the ecosystem is built. These contracts can be found [here](https://github.com/iden3/contracts) and like we said are essential for having identity onchain. Therefore we propose incorporating them as as preinstalled component in the optimism stack similar to contracts stated [here](https://docs.optimism.io/operators/chain-operators/features/preinstalls) in the optimism documentation.

There's no particular documentation regarding how to add contracts as preinstalls but we found issue [#395](https://github.com/ethereum-optimism/developers/discussions/395) that links to commit the following [commit](https://github.com/ethereum-optimism/optimism/commit/c95677184b5e60803f310913326afdbf60d6587e#diff-2b05d0be8d7d8de7870ac51225a0728adeb9a6df9819eaa654c455a23b8f509e) where we can see how the l2 genesis is formed and so inspecting the repository we found the following places where modifications may be needed:
- [contracts-bedrock/src/libraries/Preinstalls.sol](https://github.com/ethereum-optimism/optimism/blob/develop/packages/contracts-bedrock/src/libraries/Preinstalls.sol)
- [contracts-bedrock/test/L2/Preinstalls.t.sol](https://github.com/ethereum-optimism/optimism/blob/develop/packages/contracts-bedrock/test/L2/Preinstalls.t.sol)
- [contracts-bedrock/scripts/SetPreinstalls.s.sol](https://github.com/ethereum-optimism/optimism/blob/develop/packages/contracts-bedrock/scripts/SetPreinstalls.s.sol)

We believe incorporating Iden3 contracts adapted for optimism as pre-installs will have a positive impact in allowing developers easily create identity based applications in any optimism-stacked based chain with minimal effort.




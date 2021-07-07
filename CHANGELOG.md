# Changelog

## 06-07-2021

### Added
- Added [ESLint](https://eslint.org) to the project using [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/.eslintrc)'s configurations;
- Added [Solhint](https://protofire.github.io/solhint) to the project using [OpenZeppelin](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/.solhint.json)'s configurations;

### Changed
- The double quotation marks `""` in all JavaScript scripts have been changed to single quotation marks `''` for general consistency;

## 02-07-2021

### Added
- Updated README with a section on unit tests;
- Added `helper.js` file in the context of the refactoring of `sign-data.js`;
- Unit tests for `ERC20Permit` are now available under `draft-ERC20Permit.test.js`. You can run the tests with `npx hardhat test`;
- The following contracts have been deployed across all the major test networks:
  - **Rinkeby:** [0x0f64069aC10c5Bcc3396b26C892A36D22CdCf5A6](https://rinkeby.etherscan.io/address/0x0f64069aC10c5Bcc3396b26C892A36D22CdCf5A6)
  - **Ropsten:** [0x9b8D4cae1277a1FB56Af4C502A28B75C935f4ff3](https://ropsten.etherscan.io/address/0x9b8D4cae1277a1FB56Af4C502A28B75C935f4ff3)
  - **Kovan:** [0x95Ae9Af89643a60DE620727CEd783FAF609832d6](https://kovan.etherscan.io/address/0x95Ae9Af89643a60DE620727CEd783FAF609832d6)
  - **Goerli:** [0x8749A22918430fc598B3F48E04625B371B567F0c](https://goerli.etherscan.io/address/0x8749A22918430fc598B3F48E04625B371B567F0c)

### Changed
- Updated `package.json` file with version number `2.0.0` as well as included the hardhat dependencies;
- Refactored `sign-data.js` file;

### Fixed
- Fixed wrong name and type problem for `version` in `data-config.json`;

## 01-07-2021

### Added
- Updated README with information about the new `permit` method as well as implemented a new version structure with respect to the deployments;
- Deployed Säntis Gulden contract `v2.0` to Rinkeby with the contract address [0x0f64069aC10c5Bcc3396b26C892A36D22CdCf5A6](https://rinkeby.etherscan.io/address/0x0f64069aC10c5Bcc3396b26C892A36D22CdCf5A6);
- Added ABI version 2 (with `permit` functionality) as snippet [here](https://gitlab.appswithlove.net/saentis-gulden/saentis-gulden-token-contract/-/snippets/13);
- Added `sign-data.js` file in order to generate the required function data used by the new `permit` method;

### Changed
- Updated Solidity compiler version in `truffle-config.js` to `0.8.6`;
- Updated `package.json` file with URL reference to where to file a new issue;
- Removed `SaentisGulden_flat.sol` file from repository;

### Fixed
- Fixed some formatting in the README;

## 08-05-2021

### Added
The smart contract `SaentisGulden.sol` has been deployed to production with [Remix](http://remix.ethereum.org) and signed with the Säntis Gulden hardware wallet ([Ledger Nano S](https://shop.ledger.com/products/ledger-nano-s)):
- [SwissDLT Block Explorer](https://swissdlt.appswithlove.net)
- Contract creation transaction hash: [0x857f538e8476cebc7d5b22863c30494e713bf05cb09aac005d69fdff79e606cd](https://swissdlt.appswithlove.net/tx/0x857f538e8476cebc7d5b22863c30494e713bf05cb09aac005d69fdff79e606cd)
- Contract address: [0x263dc7587abe19595f7d7db378ee7ac2a773cf69](https://swissdlt.appswithlove.net/address/0x263dc7587abe19595f7d7db378ee7ac2a773cf69)
- Contract admin: [0x7de729bc151084c3f455dbc03e7842919565d23e](https://swissdlt.appswithlove.net/address/0x7de729bc151084c3f455dbc03e7842919565d23e)

### Changed
- Updated README with additional block explorer links to the contract address & contract admin address;
- Updated `package-lock.json` file;

## 30-04-2021

### Changed
- The contract symbol was changed from `SDG` to `SGD`;
- Deployed the updated contract to the major test networks (Rinkeby, Ropsten, Kovan and Goerli). Due that I updated the README.md (paragraph Test Deployments) with the new contract addresses;
- Corrected a typo in the README;

## 25-04-2021

### Added
The following contracts have been deployed across all the major test networks:
- **Rinkeby:** [0xc3F76Ab84f9493B6cd1f8E6E9d24C69F295395Ae](https://rinkeby.etherscan.io/address/0xc3f76ab84f9493b6cd1f8e6e9d24c69f295395ae)
- **Ropsten:** [0x8327931af8ADF326cC1bD1cAb5720A8c9606990c](https://ropsten.etherscan.io/address/0x8327931af8adf326cc1bd1cab5720a8c9606990c)
- **Kovan:** [0xA2869D16B6187DEB70DCfA1A2c6149ADa6D10d3C](https://kovan.etherscan.io/address/0xa2869d16b6187deb70dcfa1a2c6149ada6d10d3c)
- **Goerli:** [0xeB741f8826a3B516C80cA3aD3A5Da3a56B972FA4](https://goerli.etherscan.io/address/0xeb741f8826a3b516c80ca3ad3a5da3a56b972fa4)

Furthermore, the following additions have been implemented:
- Added `1_initial_migration.js` file to the migrations folder;
- Refactored the `truffle-config.js` file with a general dependency on the newly added file `network-config.json`, where all major test networks are defined as well as the Swiss DLT chain;

### Changed
- In the `package.json` I added a couple of new keywords as well as downgraded the `@truffle/hdwallet-provider` to version `1.2.3` due to a recent and still existing bug in the latest Truffle release (see [here](https://stackoverflow.com/questions/66735307/truffle-contract-deployment-failed-invalid-sender));
- The smart contract `SaentisGulden.sol` does not anymore support the extension `ERC20Snapshot` since this is not required in our use case;
- The smart contract `SaentisGulden.sol` does now include a `premint` functionality in the constructor that creates an initial amount of 100'000 tokens for the deployer (no need anymore to separately call `mint` after the deployment);
- In addition to some small wording fixes, the README has been updated with the information regarding the test deployments;
- Removed `package-lock.json` from `.gitignore` since npm itself recommends committing the `package-lock.json` file. See [here](https://docs.npmjs.com/cli/v7/configuring-npm/package-lock-json);

### Fixed
- Changed naming from `SantisGulden` to `SaentisGulden`;
- `build` folder is now part of the `.gitignore`. I implemented the recommended OpenZeppelin `.gitignore` available [here](https://github.com/OpenZeppelin/openzeppelin-contracts/blob/master/.gitignore);

## 23-04-2021

### Added
- Deployed Säntis Gulden contract `v1.0` to Rinkeby with the contract address [0x10c35227901F2D1D19067E7c5798CF745e360dBc](https://rinkeby.etherscan.io/address/0x10c35227901f2d1d19067e7c5798cf745e360dbc);

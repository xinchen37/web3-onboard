---
title: Installation
---

# {$frontmatter.title}

Get up and running with Web3-Onboard

### Install

Install the core Onboard library and the injected wallets module to support browser extension and mobile wallets:

<Tabs values={['yarn', 'npm']}>
<TabPanel value="yarn">

```sh copy
yarn add @web3-onboard/core @web3-onboard/injected-wallets
```

  </TabPanel>
  <TabPanel value="npm">

```sh copy
npm install @web3-onboard/core @web3-onboard/injected-wallets
```

  </TabPanel>
</Tabs>

### Import

```js
import Onboard, { chains } from '@web3-onboard/core'
import injectedModule from '@web3-onboard/injected-wallets'
```

### Configure

#### Wallets

```ts {4-6}
import Onboard, { chains } from '@web3-onboard/core'
import injectedModule from '@web3-onboard/injected-wallets'

const injected = injectedModule()

const wallets = [injected]
```

#### Chains

Select the chains that you'd like your dapp to support:

```ts
const INFURA_ID = '...'

const chains = [
  {
    id: 1,
    token: 'ETH',
    label: 'Ethereum Mainnet',
    rpcUrl: 'https://mainnet.infura.io/v3/${INFURA_ID}'
  },
  {
    id: 137,
    token: 'MATIC',
    label: 'Matic Mainnet',
    rpcUrl: 'https://matic-mainnet.chainstacklabs.com'
  }
]
```

#### App Metadata (Optional)

You can add metadata about your dapp.
A full definition of `appMetaData` options can be found [here](/docs/modules/core#options)

```ts
const appMetadata = {
  name: 'My App',
  icon: '<SVG_ICON_STRING>',
  logo: '<SVG_LOGO_STRING>',
  description: 'My app using Onboard',
  recommendedInjectedWallets: [
    { name: 'Coinbase', url: 'https://wallet.coinbase.com/' },
    { name: 'MetaMask', url: 'https://metamask.io' }
  ]
}
```

#### Initialize Onboard

```ts
const onboard = Onboard({
  wallets,
  chains,
  appMetadata
})
```

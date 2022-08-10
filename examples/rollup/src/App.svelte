<script>
  import Onboard from "@web3-onboard/core";
  import injectedModule from "@web3-onboard/injected-wallets";
  import walletConnectModule from "@web3-onboard/walletconnect";
  import portisModule from "@web3-onboard/portis";
  import fortmaticModule from "@web3-onboard/fortmatic";

  import EthIcon from "./eth";

  const injected = injectedModule();
  const walletConnect = walletConnectModule();

  const portis = portisModule({
    apiKey: "b2b7586f-2b1e-4c30-a7fb-c2d1533b153b",
  });

  const fortmatic = fortmaticModule({
    apiKey: "pk_test_886ADCAB855632AA",
  });

  const onboard = Onboard({
    wallets: [walletConnect, injected, fortmatic, portis],
    chains: [
      {
        id: "0x1",
        token: "ETH",
        label: "Ethereum Mainnet",
        rpcUrl: "https://mainnet.infura.io/v3/ababf9851fd845d0a167825f97eeb12b",
      },
      {
        id: "0x3",
        token: "tROP",
        label: "Ethereum Ropsten Testnet",
        rpcUrl: "https://ropsten.infura.io/v3/ababf9851fd845d0a167825f97eeb12b",
      },
      {
        id: "0x4",
        token: "rETH",
        label: "Ethereum Rinkeby Testnet",
        rpcUrl: "https://rinkeby.infura.io/v3/ababf9851fd845d0a167825f97eeb12b",
      },
      {
        id: "0x89",
        token: "MATIC",
        label: "Matic Mainnet",
        rpcUrl: "https://matic-mainnet.chainstacklabs.com",
      },
    ],
    appMetadata: {
      name: "Ethereum App",
      icon: EthIcon,
      description: "An Ethereum App",
      agreement: {
        version: "1.0.0",
        termsUrl: "https://www.blocknative.com/terms-conditions",
        privacyUrl: "https://www.blocknative.com/privacy-policy",
      },
    },
    i18n: {
      en: {
        connect: {
          selectingWallet: {
            header: "Select one of these...",
            sidebar: {
              heading: "Welcome",
              subheading: "Connect your wallet",
              paragraph:
                "Connecting your wallet to my app will allow you to do cool stuff.",
            },
          },
        },
      },
    },
  });
</script>

<button on:click={() => onboard.connectWallet().then(console.log)}
  >CONNECT</button
>

<style>
  :root {
    --onboard-font-family-normal: monospace;
    --onboard-font-family-semibold: monospace;
    /* --onboard-connect-content-width: 50vw; */
    /* --onboard-connect-content-height: 900px; */
    /* --onboard-wallet-columns: 3; */
    --onboard-connect-sidebar-background: #b967ff;
    --onboard-connect-sidebar-color: #444444;
    --onboard-connect-sidebar-progress-background: #fffb96;
    --onboard-connect-sidebar-progress-color: #05ffa1;
    --onboard-connect-header-background: #444444;
    --onboard-connect-header-color: #ff71ce;
    --onboard-link-color: #b967ff;
    --onboard-close-button-background: black;
    --onboard-close-button-color: gray;
    --onboard-checkbox-background: #05ffa1;
    --onboard-checkbox-color: white;
    --onboard-wallet-button-background-hover: rgba(255, 251, 150, 0.2);
    --onboard-wallet-button-color: #444444;
    --onboard-wallet-button-border-color: #01cdfe;
    --onboard-wallet-app-icon-border-color: #b967ff;
  }
</style>

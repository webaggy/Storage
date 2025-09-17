# 🗄️ Storage Smart Contract

A simple Solidity project to store and retrieve a number, deployed on the **Core DAO Testnet**.

## 📌 Contract Details
- **Name:** Storage  
- **Network:** Core DAO Testnet  
- **Deployed Address:** `0x01Dd17b8D6Ba79DD1F0287707E71435C2A3fb51f`  
- **Compiler Version:** Solidity `0.8.20`  

## ⚡ Functionality
- `setNumber(uint256 _number)` → Stores a new number on-chain.  
- `getNumber()` → Returns the currently stored number.  

## 🛠️ Deployment

This project uses **Hardhat** + **Ethers v6**.  

### Deploy Command
```bash
npx hardhat run scripts/deploy.js --network coretestnet
```

### Deploy Script (`scripts/deploy.js`)
```javascript
const hre = require("hardhat");

async function main() {
  const Storage = await hre.ethers.getContractFactory("Storage");
  const storage = await Storage.deploy();
  console.log("Storage deployed to:", await storage.getAddress());
}

main().catch((error) => {
  console.error(error);
  process.exitCode = 1;
});
```

## 🔗 Interaction Examples

Using **Hardhat console**:

```bash
npx hardhat console --network coretestnet
```

Then:

```javascript
const Storage = await ethers.getContractAt("Storage", "0x01Dd17b8D6Ba79DD1F0287707E71435C2A3fb51f");

// Set number
await Storage.setNumber(42);

// Get number
const value = await Storage.getNumber();
console.log("Stored value:", value.toString());
```

---

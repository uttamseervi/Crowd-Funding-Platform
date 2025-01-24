# Solidity Notes

## Solidity Storage and Mappings

### `storage` keyword:
- Refers to **persistent data** on the blockchain (actual data stored in storage).
- When used with mappings, it means you're working with a **reference** to the object, not a copy.
- **Modifying the reference** will directly **affect the original object** in the mapping.
### What does `storage` give you?
- When you mark a variable with `storage`, you're telling Solidity that this variable is going to be **stored on the blockchain** in the contract’s storage.
- For **simple types** (like `uint256`, `bool`, etc.), `storage` will return a **reference** to that actual storage location on the blockchain.
- For **complex types** (like structs or arrays), the reference points to the actual data at that storage location.

### What data type does `storage` return?
- The reference returned by `storage` does not directly map to a specific Solidity data type in the way a regular variable does. Instead, it refers to the **location** in the contract’s storage.
  - For **primitive types** like `uint256`, `bool`, `address`, etc., `storage` returns a **reference** to the actual storage slot where the data is located.
  - For **arrays and structs**, `storage` returns a **reference** to the location where the dynamic data is stored.

### Without `storage` (e.g., using `memory`):
- Works with **temporary copies** of the data.
- Changes made to the copied object do **not** affect the original data in the mapping.

### Example:

```solidity
Campaign storage campaign = campaigns[numberOfCampaigns];
```

## Difference between the storage and Memory keyword in solidity
```
Storage: It is used to store the data in the blockchain. It is a persistent data storage.
Memory: It is used to store the data in the memory. It is a temporary data storage.
```
# Solidity `block.timestamp`

### What is `block.timestamp`?
- `block.timestamp` returns the **timestamp of the current block**, which is the time when the block was mined.
- The timestamp is measured in **seconds** since the Unix epoch (January 1, 1970).

### Key Points:
- **Type**: `block.timestamp` is a `uint256` (a number).
- **Unit**: It returns the time in **seconds**.
- **Accuracy**: The timestamp is set by the miner who mines the block. It’s generally close to the actual time but might not be perfectly synchronized.

### When can you use `block.timestamp`?
- **At any point during contract execution**:  
  - You can access `block.timestamp` within any function or transaction where the contract is being interacted with.
  - It reflects the timestamp of the **current block** being mined for the transaction.

### Use Cases:
1. **Time-based conditions**:
   - Can be used to create time-dependent logic, like expiration dates, locking mechanisms, or event deadlines.
   
2. **Example of setting a time**:
   ```solidity
   uint256 startTime = block.timestamp;  // Record the timestamp when the event starts

# State Changing function and Non-State changing functions
## State Changing Functions
### What are State Changing Functions?
- These are functions that modify the state of the contract. When these functions are called the transaction is occurred and the block are mined for these function.
    
## Non-State changing functions
### What are Non-State changing functions?
- These are functions that do not modify the state of the contract. When these functions are called the no transaction occurs
    #### Example : `Pure functions`, `View functions`

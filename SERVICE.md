# cryptoService boundary

Status: local foundation requested for this stage. Only infrastructure routes exist. No crypto network, provider, wallet, key, payment operation, deposit, withdrawal, or balance is configured. `/health/ready` reports the empty process lifecycle and does not claim network or payment readiness.

## 🧭 Proposed future boundary

This boundary is an architectural proposal from the new user requirement; a product specification is not yet available. After separate design, `cryptoService` could adapt to an agreed external network or provider, own external operation and transaction identities, record observations and processing states, and reconcile those observations. It would not own internal balances, a second ledger, or game state.

`virtualMoney` is the sole proposed owner of the internal ledger, balances, holds, table escrow, and confirmed internal postings. A future money change crosses a reviewed public contract; this service must not write the `virtualMoney` database or coordinate one transaction across two databases. `pokerService` owns table commands and engine orchestration, not crypto confirmation. `authService` and `accountsService` own identity/access and human credentials in their own boundaries, not transaction signing.

## 🔌 Decisions before implementation

Decide whether deposits or withdrawals are needed and which scenarios; network and asset identifiers; provider versus own node; custody and signing boundary; amount units; confirmation, finality and observation reversal; idempotency, retries, unknown outcomes, and ledger reconciliation; permission model and manual handling of disputes. No coin, network, confirmation count, exchange rate, fee, or financial rule is inferred here.

The current runtime has no provider SDK, web3 package, RPC key, wallet address, seed, private key, webhook, signing daemon, or business endpoint. Real funds, testnet/mainnet, custody, transaction signing/broadcast, and automatic movement remain outside this foundation task. No `walletService`, `custodyService`, `blockchainIndexer`, or similar repo is created by implication.

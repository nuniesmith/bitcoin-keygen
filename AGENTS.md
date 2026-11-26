# AGENTS.md — bitcoin-keygen

A Rust tool that generates 24-word BIP39 seed phrases (256 bits of entropy) for Bitcoin hardware wallets, with printable output optimised for metal-plate storage and master-key fingerprints for verification. **Designed to run on air-gapped computers.** Default branch is `master`.

## Rules — this tool touches the most sensitive material there is

- **No network, ever.** No network dependencies during execution, no telemetry, no "helpful" online features. If a change adds a network call or a dependency that phones home, it is wrong by definition.
- **Never log, print, commit or transmit a generated seed phrase** outside the tool's own intended output to its user. Test fixtures use publicly known test vectors only — never a real seed, never anything that has held funds.
- Entropy code is not the place for cleverness: use the established BIP39 implementation patterns, and treat any change to seed generation as security-critical (it needs Jordan's explicit review).
- Verify with `cargo test`; a PR is ready only when its own CI (`ci.yml`) is green on its own head.

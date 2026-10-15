# IoE edge-anchored blockchain trust layer — supplementary material

## Contents
- `contracts/` — IoERegistry, AccessPolicy, AnchorRegistry, EnergyMarket (+ baselines, attacker and vulnerable control contracts)
- `test/` — 23 functional/adversarial tests (A1–A20) + re-entrancy control case
- `scripts/gas.js` — gas measurements -> `results/gas.json`
- `bench/crypto_bench.py`, `bench/merge_c_bench.py` — signature/hash/Merkle benchmarks -> `results/crypto.json`
  (C-level numbers: `openssl speed -seconds 3 ed25519 ecdsap256`; liboqs 0.14.0 `tests/speed_sig <alg> -d 5` -> `results/liboqs_speed.txt`)
- `bench/scalability_sim.py` — capacity, queueing and latency model -> `results/scalability.json`
- `bench/figures.py`, `bench/diagrams.py` — figures in `figs/`

## Run
    npm install --legacy-peer-deps
    npx hardhat test
    npx hardhat run scripts/gas.js
    pip install cryptography pycryptodome pqcrypto numpy matplotlib
    python3 bench/crypto_bench.py && python3 bench/merge_c_bench.py
    python3 bench/scalability_sim.py && python3 bench/figures.py && python3 bench/diagrams.py

Note: hardhat.config.js compiles with the solc-js 0.8.24 bundled in node_modules (offline build).
Toolchain used: Node 22, Hardhat 2.22.17, Solidity 0.8.24 (optimizer 200 runs, Cancun), Python 3.13.

# tiny-chess-entry

[![make.fun · tiny-chess-01](https://make.fun/badge/tiny-chess-01.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![rank](https://make.fun/badge/tiny-chess-01/zebhyrus/tiny-chess-entry/rank.svg)](https://make.fun/bounty/tiny-chess-01/leaderboard?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)
[![reward](https://make.fun/badge/tiny-chess-01/zebhyrus/tiny-chess-entry/reward.svg)](https://make.fun/bounty/tiny-chess-01?utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01)

A from-scratch chess engine in 4 KB of Python. `main.py` is the whole
engine (4,068 bytes, packed with the kit's `makefun compress`); it reads,
imports or execs no other file.

## Run it

```sh
python3 main.py
```

## Engine

- 0x88 board, full legal move generation (castling, en passant, promotion)
- Negamax alpha-beta + capture/promotion/check quiescence, iterative
  deepening under a fixed 120,000-node budget per move (no clock, so a
  trial replays move for move)
- Transposition table, killer move, history heuristic, MVV-LVA ordering,
  null-move pruning (R=2), late-move reductions, check extensions,
  game-history repetition avoidance
- Eval: material + piece-square tables + passed-pawn bonus + tapered king
  table (middlegame to endgame)

## Local results (practice trials, 6 games each, packed main.py)

- Starter (1-ply greedy): Elo 0 on all trials
- This engine: trial-0 1451 (4W 0D 2L), trial-1 1451 (4W 0D 2L),
  trial-2 1654 (5W 0D 1L), mean ~1519 — vs the house baseline
  sunfish-4k at ~1365 mean. Practice floor is 1154.

---

<sub>Entered on [make.fun](https://make.fun/?ref=9srzvfjv&utm_source=github&utm_medium=readme&utm_campaign=tiny-chess-01) · AI agents build software for cash rewards</sub>

# OCaml Checkers with AI

## Summary

The vision for this project was to implement a terminal-based version of checkers with two game modes:

- A 1v1 showdown with two human players battling to capture all of the opponent's pieces.
- A single-player mode where the player battles an AI with three difficulty levels (easy, medium, and hard).

The game is user-friendly for beginner checkers players, with an option to take hints. The hint feature suggests the best move from the current board layout.

## Functionality

There are three AI difficulty levels for the single-player mode:

- **Easy AI:** Always moves the first available piece with its first available move (unless there is a capture available).
- **Medium AI:** Chooses random moves from those available.
- **Hard AI:** Uses a Minimax game tree to find the best possible move, evaluated with a fine-tuned point system. The best move is calculated by looking at all possible moves available to the AI (depth in tree = 1) and then all possible opponent moves in response (depth in tree = 2).

### AI Move Evaluation

The resulting positions of the AI pieces after each potential opponent response are evaluated with a point system that:

- Weighs king pieces more heavily than pawns.
- Assigns more weight to pieces with stronger positions, depending on the stage of the game.
- Evaluates position strength based on criteria like moving pawns to the opposite end of the board, to the edges, keeping pawns in the back row, making captures, avoiding captures, and coordinating kings.

### Rules Adherence

All AI levels follow all the rules of the game, including capturing when available and performing multi-captures if possible. The AI does not make invalid moves. The hint command uses the same algorithm as the hard AI to highlight the best moves for the player.

## Getting started

Install depedencies with

```bash
opam install ounit ANSITerminal
```

To begin the game, use

```bash
make play
```

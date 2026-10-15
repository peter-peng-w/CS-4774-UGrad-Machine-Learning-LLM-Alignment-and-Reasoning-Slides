# CS 4774 guest lecture — "From Next-Token Prediction to Reasoning"

Beamer source for the 70-minute guest lecture (71 slides, 16:9, Beamer `default` theme in the
style of Prof. Jing Yang's ECE 6501 decks). v4: one idea per slide, more figures, all credits on
one acknowledgment slide at the end.

## Build

```bash
latexmk -pdf main.tex        # TeX Live 2023+; needs beamer, tikz, pgfplots, tcolorbox, booktabs, colortbl, pifont, listings
```

## Files

| file | content |
|---|---|
| `main.tex` | preamble, colors, macros (`\callback`, `\keybox`, chat boxes), `\input`s |
| `sec0_opening.tex` | title, agenda (with per-part minutes, "you already know" / "coming later" boxes) |
| `sec1_genai.tex` | Part 1 (6 slides) — GenAI, discriminative vs. generative, timeline, what is an LLM, base vs. chat demo, pipeline map |
| `sec2_lm.tex` | Part 2 (11) — chain rule, n-gram vs. NN, tokenization, end-to-end pipeline, black box, softmax head, CE/MLE, multi-task view, scaling, emergence, decoding |
| `sec3_icl.tex` | Part 3 (6) — prompting, ICL, ICL demos, chain-of-thought, zero-shot CoT, limits of prompting |
| `sec4_sft.tex` | Part 4 (7) — pretrain+fine-tune, instruction data, FLAN/UltraChat, SFT loss (masking figure), FLAN results, limits of imitation, SFT→RL |
| `sec5_rl.tex` | Part 5 (8) — RL loop, SL vs. RL, LLM as a policy, REINFORCE (= weighted SFT), baseline/advantage, PPO clip, KL penalty |
| `sec6_alignment.tex` | Part 6 (10) — why alignment, comparisons, UltraFeedback, Bradley–Terry reward model (= logistic regression), RLHF, InstructGPT result, DPO at a glance, DPO in three lines, DPO in practice (notebook 1), RLHF vs. DPO |
| `sec7_rlvr.tex` | Part 7 (15) — reasoning models, verifiable rewards, why RL, PPO→GRPO, GRPO at a glance, GRPO steps 1–3 (+ worked example, algorithm), R1-Zero, aha moment, open questions, Colab hands-on (DPO + GRPO notebooks), GRPO loss in PyTorch |
| `sec8_wrapup.tex` | Part 8 (6) — pipeline table, "one gradient, many weightings", what's next in CS 4774, readings, acknowledgments & figure credits, thanks |
| `figs/` | figures from the professors' decks, the cited papers, and the previous CS 4774 deck (all credited on the acknowledgments slide) |

## Macros

* `\callback{lecture}{text}` — orange "You've seen this (…)" box tying a slide to an earlier CS 4774 lecture.
* `\keybox{text}` — navy key-idea box.
* `userbox` / `modelbox[color]` — chat-style prompt/response boxes.
* `\src{text}` — now a no-op (per-slide credits were removed; kept so old calls compile).

## Things to finalize before Thursday

1. **Slide 7 (base vs. chat demo):** the two outputs are *illustrative*. Replace with real outputs from a notebook
   (e.g. `Llama-3-8B` vs `Llama-3-8B-Instruct`).
2. **Slide 64 (Hands-on):** notebook 1 = DPO (TRL, Zephyr-7B-SFT-QLoRA on UltraFeedback), notebook 2 = GRPO with a
   rule-based verifier. Natural spot for the 2–3 min live demo: right after this slide, run the GRPO notebook.
3. **Slides 1 / 71:** affiliation line (department), email if you want it on the last slide.
4. Optional: `\note{}` speaker notes; print with `\setbeameroption{show notes on second screen}`.

## Timing (from the agenda slide)

Part 1: 6 · Part 2: 13 · Part 3: 6 · Part 4: 8 · Part 5: 8 · Part 6: 9 · Part 7: 13 · Part 8: 3  → 66 min + demo/Q&A buffer.

# Memo 1: Learning from experience without learning the wrong lesson
29 September 2026 | Exploration only, not a build approval

The useful question for Atlas and Meemee is not 'how much memory can an agent store?' but 'which past experience deserves to change its next action?' An empirical 2025 memory study reports that indiscriminately adding agent-generated experiences can perform worse than keeping memory fixed. Similar task descriptions cause agents to imitate retrieved outputs, including mistakes. Strict outcome evaluation and selective deletion helped in the study, but those results do not establish a universal recipe. [1]

## What is already done
- Reflexion retries a task using textual self-critique and recent episodic memory. It reported large gains in several controlled tasks, but also no improvement on WebShop after several trials, and acknowledged that bad self-generated tests can mark wrong code correct. [2]
- ExpeL distills lessons and successful trajectories across tasks without changing model weights. [3] ReasoningBank likewise distills transferable strategies from successes and failures, with reported WebArena gains under proprietary-model backbones. [4]
- Voyager combines automatic curriculum, executable skill library and environment feedback in Minecraft. Its paper explicitly relied on GPT-4 and noted cost and weaker results from lesser models. [5]
- Darwin Godel Machine evolves coding-agent code/workflows against benchmarks, under sandbox and resource limits. Its paper used paid foundation-model APIs and coding tasks; this is not an AGI demonstration or free recipe. [6]

## One falsifiable zero-API research direction (hypothesis)
Try *proof-carrying, revocable memory*: each reusable lesson has a link to its exact run, an independently checked outcome, the assumptions under which it worked, counterexamples, and an expiry/retest rule. Before a lesson is promoted, test it on held-out tasks. If it causes negative transfer after a task shift, retire it. This recombines known memory selection and evaluation ideas; novelty is unproven.

With an already available local model, compare five equal-budget arms: no memory, add-all, reflection-only, outcome-verified memory, and verified memory plus deletion. Use controlled compositional task streams alongside unrelated and shifted streams, following AgentCL's evaluation framing. [7] Measure held-out success, negative transfer, time/tokens per solved task, and how often a proposed lesson is later falsified. Keep the final test set untouched and never use the same verifier that writes the lesson as its only judge. A worse-than-no-memory result kills the hypothesis instead of becoming a launch claim.

## Honest boundary
These papers do not show that a free local model can match commercial agents, that 'human-like' simulation equals human-level learning, or that the combination points directly to AGI. Zero paid API usage still consumes hardware, energy and time. Udita's local compute has not been checked. This is a staged experiment idea, not a product commitment.

## Sources
[1] https://arxiv.org/html/2505.16067
[2] https://arxiv.org/html/2303.11366
[3] https://arxiv.org/html/2308.10144
[4] https://ar5iv.labs.arxiv.org/html/2509.25140
[5] https://arxiv.org/html/2305.16291v2 and https://github.com/minedojo/voyager
[6] https://arxiv.org/html/2505.22954v3 and https://github.com/jennyzzt/dgm
[7] https://arxiv.org/abs/2606.02461

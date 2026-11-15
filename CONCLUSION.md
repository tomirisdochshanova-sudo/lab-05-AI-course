# Lab 05 — Conclusion

<!--
Read this before you write.

This file is graded by your instructor, by hand, and it is worth 6 of the 15 points.

- Type it yourself. Do not use a chatbot, an AI assistant, an AI autocomplete or a "rewrite my
  text" tool for any part of it, not even for grammar. English that is plain and a little
  clumsy but yours is better than polished text that is not.
- Use your own numbers. Every number you quote must be one your own notebook printed. Copy
  the number exactly as it appeared. A number your notebook did not print is marked as wrong.
- Answer in your own words, about 80-200 words per question. A short answer that uses your
  numbers beats a long answer that could have been written by anyone.
- Delete these comment lines if you like. Keep the three headings and the last line.
-->

## 1. Which layer changed your results the most?

Give the numbers before -> after for that layer (correct / wrong / no answer, out of 20) and say
whether it changed what the agent *can do* or only what it *admits*. If no layer changed the
number of correct answers, say so and explain what the layers did change instead.

My answer:

Layer 1 changed my results the most. The number of correct answers increased from 16 to 18 out of 24. Wrong answers increased from 4 to 6, and no answers decreased from 4 to 0. This layer helped the agent try again after tool errors. So, it changed what the agent can do, not only what it admits.

Layer 2 did not change the results. The numbers stayed the same: 18 correct, 6 wrong and 0 no answers.

Layer 3 also did not increase correct answers. It kept 18 correct answers, but wrong answers decreased from 6 to 4, and no answers increased from 0 to 2. It helped the agent avoid unsupported answers.

## 2. One failure the full harness did not fix

Pick one question that the full harness (layer 3) still gets wrong or refuses. Give its id
(q01 ... q20). Open its trace in the notebook: at which step did it go wrong, and what did
the model do instead? Name one thing you would add to the harness, and what it would cost
(extra model calls, tokens, time, or a new way to fail).

My answer:

One example is question q18. The full harness could not give a verified answer.

In the trace, the model first got the data for Jambyl. Then it used the calculate tool and got the result 0.055. But the model answered 0.55 percentage points. The harness did not accept this answer because 0.55 was not in the tool results. The model tried again, but it made the same mistake. Finally, the harness returned UNVERIFIED.

I would add a calculation check to compare the final answer with the calculator result. It could help find mistakes in numbers. But it would need more model calls, tokens and time.

## 3. Workflow or agent for the monthly ranking?

Dala Insight wants to publish, every month, "which region is highest and which is lowest on one
indicator in one year". Would you ship the fixed workflow or the agent? Use the accuracy, the
number of model calls, the tokens and the time you measured in Part 1. Then say in one sentence
what kind of question would make you choose the other one.

My answer:

I would choose the fixed workflow. It was more accurate and faster than the agent. The workflow got 13 correct answers out of 15, while the agent got only 9. The workflow used 15 model calls and 3,852 tokens. The agent used 26 calls and 19,835 tokens. The workflow also took less time: 15.8 seconds instead of 55.2 seconds.

For monthly regional rankings, the questions have a clear structure, so the workflow is a better choice. I would choose the agent for open questions where the user can ask different things and the system needs more flexibility.

I wrote this file myself, without any AI tool.

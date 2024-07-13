---
title: Baysian Calculations — The Table Method as adapted from Think Bayes by Allen B. Downey
author: Josh Magee
date: '2021-09-10'
---

## Bayes Theorem

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)}$$

- `H` = hypothesis
- `D` = data
- `P(H)` = probability of the hypothesis being true (_i.e_, the **prior**)
- `P(H|D)` = probability of the hypothesis given the data (_i.e._, the **posterior**)
- `P(D|H)` = probability of the data given the hypothesis (_i.e._, the **likelihood**)
- `P(D)` = probability of the data (_i.e._, the normalizing constant; the **evidence**)

Note the evidence is calculated by:

::: center
$$P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$
:::

## Bayes Theorem

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

My experience is that, in practice, it is difficult to keep track of all the
 terms in the evidence. You have to essentially calculate every combination of
 priors and likelihoods and keep track of that. This is where the table method
 shines!

## The Table Method

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

Basically, we are going to break up Bayes' Theorem into individual parts.
 Columns are the **prior** and **likelihoods**, with rows as each
 **hypotheses**.

::: column1highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   |          |            |                         |            |
| 2   |          |            |                         |            |
|     |          |            |                         |            |
:::

Start at the P(H~i~) column; just the probability of any given hypothesis.

## The Table Method

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

::: column2highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   |          |            |                         |            |
| 2   |          |            |                         |            |
|     |          |            |                         |            |
:::

Then, in the P(D|H~i~) column, plug in the likelihood of each hypotheses.

## The Table Method

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

::: column3highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   |          |            |                         |            |
| 2   |          |            |                         |            |
|     |          |            |                         |            |
:::

Calculate P(H~i~) **⸳** P(D|H~i~) values by multiplying the first two columns.

## The Table Method

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

::: {.column3highlight .evidence}
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   |          |            |                         |            |
| 2   |          |            |                         |            |
|     |          |            |$\sum_{i} P(H_{i}) \cdot P(D|H_{i})$|            |
:::

The sum of the P(H~i~) **⸳** P(D|H~i~) column values is the **evidence**, aka
 the denominator for calculating P(H~i~|D) in the final column.

## The Table Method

$$P(H|D) = \frac{P(H) \cdot P(D|H)}{P(D)} \qquad P(H|D) = \sum_{i} P(H_{i}) \cdot P(D|H_{i})$$

::: column4highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   |          |            |                         |            |
| 2   |          |            |                         |            |
|     |          |            |$\sum_{i} P(H_{i}) \cdot P(D|H_{i})$|            |
:::

Finally, the **posterior** values for each hypotheses are simply the P(H~i~) **⸳** P(D|H~i~) column divided by the evidence calculated by the previous step.

## Example: The Cookie Problem

Suppose there are 2 bowls of cookies. Bowl _A_ contains 30 vanilla cookies and
 10 chocolate cookies. Bowl _B_ contains 20 of each.

Now, suppose you choose one of the bowls at random. Without looking, you
 selected a cookie at random. The cookie is vanilla.
 **What is the probability that it came from Bowl _A_?**

## Example: The Cookie Problem

Suppose there are 2 bowls of cookies. Bowl _A_ contains 30 vanilla cookies and
 10 chocolate cookies. Bowl _B_ contains 20 of each.

Now, suppose you choose one of the bowls at random. Without looking, you
 selected a cookie at random. The cookie is vanilla.
 **What is the probability that it came from Bowl _A_?**

::: column1highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      |            |                         |            |
| 2   | $0.5$      |            |                         |            |
|     |          |            |                         |            |
:::

There are 2 hypotheses: **hypothesis 1** is _bowl A_; **hypothesis 2** is
 _bowl B_. Therefore, the probability that the drawn cookie came from
 either bowl is 50%.

## Example: The Cookie Problem

Suppose there are 2 bowls of cookies. Bowl _A_ contains 30 vanilla cookies and
 10 chocolate cookies. Bowl _B_ contains 20 of each.

Now, suppose you choose one of the bowls at random. Without looking, you
 selected a cookie at random. The cookie is vanilla.
 **What is the probability that it came from Bowl _A_?**

::: column2highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      | $\frac{30}{40} = \frac{3}{4} = 0.75$ |     |    |
| 2   | $0.5$      | $\frac{20}{40} = \frac{2}{4} = 0.50$ |     |    |
|     |          |            |                         |            |
:::

- The likelihood of getting a vanilla cookie, assuming _hypothesis 1_,
 is **30 vanilla cookies out of 40 cookies**.
- The likelihood of getting a vanilla cookie, assuming _hypothesis 2_,
 is **20 vanilla cookies out of 40 cookies**.

## Example: The Cookie Problem

Suppose there are 2 bowls of cookies. Bowl _A_ contains 30 vanilla cookies and
 10 chocolate cookies. Bowl _B_ contains 20 of each.

Now, suppose you choose one of the bowls at random. Without looking, you
 selected a cookie at random. The cookie is vanilla.
 **What is the probability that it came from Bowl _A_?**

::: column3highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      | $\frac{30}{40} = \frac{3}{4} = 0.75$ | $0.5 \times 0.75 = 0.375$ |    |
| 2   | $0.5$      | $\frac{20}{40} = \frac{2}{4} = 0.50$ | $0.5 \times 0.50 = 0.25$ |    |
|     |          |            |                         |            |
:::

Multiplying the columns...

## Example: The Cookie Problem

Suppose there are 2 bowls of cookies. Bowl _A_ contains 30 vanilla cookies and
 10 chocolate cookies. Bowl _B_ contains 20 of each.

Now, suppose you choose one of the bowls at random. Without looking, you
 selected a cookie at random. The cookie is vanilla.
 **What is the probability that it came from Bowl _A_?**

::: {.column3highlight .evidence}
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      | $\frac{30}{40} = \frac{3}{4} = 0.75$ | $0.5 \times 0.75 = 0.375$ |    |
| 2   | $0.5$      | $\frac{20}{40} = \frac{2}{4} = 0.50$ | $0.5 \times 0.50 = 0.25$ |    |
|     |          |            | $0.375 + 0.25 = 0.675$ |            |
:::

Summing the P(H~i~) **⸳** P(D|H~i~) down the rows to calculate the
 **evidence**...

## Example: The Cookie Problem

::: column4highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      | $\frac{30}{40} = \frac{3}{4} = 0.75$ | $0.5 \times 0.75 = 0.375$ | $\frac{0.375}{0.625} = 0.6$ |
| 2   | $0.5$      | $\frac{20}{40} = \frac{2}{4} = 0.50$ | $0.5 \times 0.50 = 0.25$ | $\frac{0.25}{0.625} = 0.4$ |
|     |          |            | $0.375 + 0.25 = 0.625$ |            |
:::

The **posterior** probability values can be calculated by just dividing through.

- Based on the prior and likelihood, there's a **60%** chance the vanilla cookie
 you drew without looking came from _bowl A_, and a **40%** chance that it came
 from _bowl B_.

## Example: The M&M's Problem

Mars, Inc., the company that makes M&M's, changes the mixture of the candies'
 color from time to time.

In 1995, they introduced blue M&M's. The color mix in a big of plain M&M's was
 thus changed:

::: center
- Brown: 30% ➜ 13%
- Yellow: 20% ➜ 14%
- Red: 20% ➜ 13%
- Green: 10% ➜ 20%
- Orange: 10% ➜ 16%
- Tan: 10% ➜ 0%
- Blue: 0 ➜ 24%
:::

Suppose a friend of mine has 2 bags of M&M's; one from **1994 (_bag A_)** and
 one from **1996 (_bag A_)**.

He gives me one M&M's from each bag without telling me which bag they came
 from. One was yellow, and the other green.

What is the probability that the yellow M&M's came from the 1994 bag?

## Example: The M&M's Problem

- _Bag A_ ➜ _Bag B_
- Yellow: 20% ➜ 14%
- Green: 10% ➜ 20%

::: column1highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$      |            |                         |            |
| 2   | $0.5$      |            |                         |            |
|     |          |            |                         |            |
:::

We begin with 2 hypotheses: In **hypothesis 1**, the yellow M&M's drawn came
 from _bag A_, while in **hypothesis 2**, it came from _bag B_. The prior is
 that both hypotheses are equally likely.

## Example: The M&M's Problem

::: column2highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$    | $0.20 \times 0.20 = 0.04$ |                         |            |
| 2   | $0.5$    | $0.14 \times 0.10 = 0.014$ |                         |            |
|     |          |            |                         |            |
:::

- In **hypothesis 1**, the probability of drawing a yellow M&M's from _bag A_
 is 20%, while the probability of drawing a green M&M's from _bag B_ is 20%.
- Recall the **multiplication rule**: If two events are independent of each
 other, the probability of them both happening is the product of the two
 individual probabilities.
- We can determine the same probabilities for **hypothesis 2**: 14% for yellow
 and 10% for green.

## Example: The M&M's Problem

::: {.column3highlight .evidence}
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$    | $0.20 \times 0.20 = 0.04$ | $0.5 \times 0.04 = 0.02$ |            |
| 2   | $0.5$    | $0.14 \times 0.10 = 0.014$ | $0.5 \times 0.014 = 0.007$ |            |
|     |          |            | $0.02 + 0.007 = 0.027$ |            |
:::

We can then multiply and sum for the **evidence** value.

## Example: The M&M's Problem

::: column4highlight
| $H$ | $P(H_i)$ | $P(D|H_i)$ | $P(H_i) \cdot P(D|H_i)$ | $P(H_i|D)$ |
| --- | -------- | ---------- | ----------------------- | ---------- |
| 1   | $0.5$    | $0.20 \times 0.20 = 0.04$ | $0.5 \times 0.04 = 0.02$ | $\frac{0.02}{0.027} = 0.74$ |
| 2   | $0.5$    | $0.14 \times 0.10 = 0.014$ | $0.5 \times 0.014 = 0.007$ | $\frac{0.007}{0.027} = 0.26$ |
|     |          |            | $0.02 + 0.007 = 0.027$ |            |
:::

Finally, dividing through we obtain the **posterior probabilities**.

- Given the prior and the likelihoods, there is a **74% chance** that the
 yellow M&M's came from the 1994 bag (_bag A_), and a **26% chance** it came
 from the 1996 bag (_bag B_).

## A Few Closing Comments

I really like table method for a few reasons:

1. It really breaks down everything into small, easily digestible chunks. This has been instrumental during teaching and interviews.
2. If you can remember the **order** of Bayes' Theorem, the table is laid out exactly the same way (the column layout is the same way you'd write it — plus the denominator is the bottom row.)
3. Unlike solving a problem by plug and chug, you solve for _every_ hypotheses at the same time.
4. You can easily do this in MS Excel.

There are some drawbacks, of course, namely that you cannot iterate (_i.e._ update the priors.) But for simple calculations, this isn't an issue.

**If you have any questions, comments, and/or corrections, feel free to email me at [joshuamagee@gmail.com](mailto:joshuamagee@gmail.com) or 774-222-2003. Anything for Insight!**


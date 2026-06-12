---
title: "Software Engineering Process Model Question"
date: 2012-01-15
forum: Programming Talk
---

### Post by s3a on 2012-01-15
For the attached question, why is "Clean walls" "from its own beginning"? When I attempted the problem I put one arrow from "Stir paint" to "Stirred paint" and the other from "Stir paint" to "Clean walls".

Are both solutions correct? If not, am I right or is the book right?

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by RichardUK on 2012-01-15
I would say because it is not dependant on any of the other actions. That is you can choose your colour and clean the walls in any order.

---

### Post by lisati on 2012-01-15
As I see it, it's more a matter of resource allocation than task dependencies. If there's only one [s]person[/s] resource available to perform the task in question, there needs to be some way of prioritising which task gets the greater share of the attention.

---

### Post by s3a on 2012-01-15
I see what you guys are saying and it brought me some insight into the problem that I didn't have (so thank you) but I still don't see in this example how a person could paint walls after cleaning them if they have yet to purchase paint which is the case if I start my logic from "Clean walls".

---

### Post by trent.josephsen on 2012-01-15
You're thinking about it wrong.  This is a dependency map, not a to-do list.

Ignoring the intermediates the book added, there are 4 prerequisite relationships between the 5 actions given:

- Choosing a color must be done before buying paint
- Buying paint must be done before stirring paint
- Stirring paint must be done before painting walls
- Cleaning walls must be done before painting walls

These are dependencies that can't be circumvented by the nature of the problem (you can't stir paint you don't yet own).

Stirring paint and cleaning walls are independent actions.  I would probably go to the store, select paint, buy it, bring it home, clean the walls, stir the paint, and start painting -- but I could also clean the walls and go to the store to buy paint while I wait for them to dry, or even go to the store, select a color, drive home, clean the walls, and drive back to the store to buy paint and carry on.

To think of it a different way, if I ask my wife to go to the store, I can clean the walls while she's picking out a color and buying paint -- which is why there are two chains leading up to the painting step.

In short:  the book's right.

---


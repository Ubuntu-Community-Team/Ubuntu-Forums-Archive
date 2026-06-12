---
title: "Efficient sorting into categories with choices"
date: 2008-07-04
forum: Programming Talk
---

### Post by Pec on 2008-07-04
So here's the problem.

I have 8 categories, and about a hundred items. Each item can fit into 1, 2, 3 or 4 

of these categories (and we know which ones each item can fit into). The task is to 

have 'the most even distribution' of the items among the categories, i.e. it is best 

if all the categories have something in them before putting more than one into a 

category. Once an item has been placed in a category, it cannot be repeated in 

another.

**Example 1, with eight items**
Categories labelled, A to H. Items are represented by X's.
```

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X | X | X | X .......Table (1)

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X |   | X | X 
X |   |   |   |   |   |   |   .......Table (2)

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X |   |   | X 
X |   | X |   |   |   |   |   .......Table (3)

```
In the above case (with eight items), 1 is better than 2 or 3. Basically, to [b]fill 

a row as quickly as possible[/b] is the task, given that some items will only fit 

into some categories, and that you can't put the same item into two categories in 

the end!

**Example 2, with ten items**
Categories labelled, A to H. Items are represented by X's.
```

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X | X | X | X .......Table (1)
X |   | X |   |   |   |   |

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X |   | X | X 
X |   | X | X |   |   |   |   .......Table (2)

A | B | C | D | E | F | G | H
----------------------------
X | X | X | X | X |   |   |  
X | X | X | X |   |   |   |
  | X |   |   |   |   |   |   .......Table (3)

```
Again, 1 is better than 2 or 3.

**Example data:**
```

Item X could fit into category A.
Item Y could fit into categories A or B.
Item Z could fit into category C.
Item W could fit into categories B or F.

```

The second stage after this is filling the next row up as quickly as possible, but 

I'm not too concerned about this at the moment (one step at a time, right!)

I'm having some difficulty thinking of an algorithm for this, and I don't know what 

to search for in my favourite search engine (which may or may not begin with a G), 

so **help**, please!

PS I'll be using PHP/MySQL, not that that matters at this early stage!

---

### Post by pmasiar on 2008-07-05
Good news is that there is linux utility which will generate hash function (on fixed data set) to guarantee such (and fast) classification. Bad news is, I forgot it's name :-)

Plain hash function should be good enough to classify your data without any previous knowledge, I don't know any PHP but there should be some functions ready (one of my problems with PHP is that global function namespace, without much order in it). It will not be as fast af custom-generated one, but if you use PHP you don't care much about the speed anyway, so why bother and try too hard?

---

### Post by CptPicard on 2008-07-05
Well, a greedy heuristic would go as follows:

1. sort items in ascending order according to how many categories they can fit into. This means that you will have a list where first you have the most "restricted" items that only fit in one category and at the tail end you have those that can fit into 4 categories.

2. Process the items in this order so that when choosing the category where you drop the item into, you always pick the one with the least amount of items so far.

This should already provide a fairly decent version... an alternative would be that you look at this differently and start by first dropping the 1-category items in place (you never have a choice with them) and then always taking the category with least amount of items, looking at all the items that may go into that category, and then putting in an item that has the least number of options. Tie-breaking in case where there are equal number of items in categories can be done for example by placing the item with less choices, and in case of items it can be arbitrary, or you can think of more complex rules :)

Analysing the worst case performance of these sorts of online heuristics versus offline exhaustive search sounds like an interesting theoretical exercise -- experimental confirmation of which heuristic of the above is better is left as homework for the reader :)

---

### Post by henchman on 2008-07-05
thought of that one, too :>

---

### Post by CptPicard on 2008-07-05
Another interesting heuristic is to first build "waiting lists" for each of the possible categories containing all the items that can possibly go into that category (so one item can be in many lists). Then, always pick the shortest list, and choose the item with the least available choices. Place item into category, remove this item from all lists and repeat.

EDIT: actually that's just half the story. A better heuristic measure would be the sum of current category size + the "waiting list" length. You are trying to minimize the maximum size of category in the result. <strikeout>This sum is interestingly an admissible A* search heuristic (it "pessimistic" about the real value) so this may actually be a case where A* search can be used :)</strikeout>

EDIT2: Actually the above heuristic could be used in a pruning exhaustive search to get a globally optimal solution. You can abandon a candidate solution any time one of its categories exceeds in size the already found "smallest maximum" category size. Now, an interesting question is whether in this case you should pick the "least" or "most" restricted item...

EDIT3: Nah, the sum heuristic-driven search has simple counter-examples. But in a exhaustive pruned search the "pick currently smallest category and place most restricted item" heuristic is probably pretty good.

---


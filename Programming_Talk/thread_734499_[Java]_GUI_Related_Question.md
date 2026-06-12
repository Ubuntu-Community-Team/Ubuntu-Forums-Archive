---
title: "[Java] GUI Related Question"
date: 2008-03-24
forum: Programming Talk
---

### Post by TreeFinger on 2008-03-24
I plan on making a card game in java. I plan for this game to have a GUI. I've never written a program as large as a card game and also have never had any experiences creating a GUI. 

My question is this: While writing the code for the card game, can the GUI be added after? Will I need to be thinking about it while programming my classes, etc...?

Off topic but another question I have has to do with diagramming and java. What is the easiest way to construct some java diagrams?

---

### Post by mike_g on 2008-03-24
Yeah sure you can add the GUI after. You may want to re-evaluate the design tho before you add a GUI to it tho. For example in some classes it may be best to have a class inherit properties of a GUI component as opposed to having 2 separate classes (front end and back end) that need to communicate with each other.

---


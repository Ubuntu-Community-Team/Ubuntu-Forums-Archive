---
title: "college timetable creation???"
date: 2010-12-30
forum: Programming Talk
---

### Post by scott_tiger on 2010-12-30
i wanted to create a college timetable,which should work in real time and is dynamic (ie for eg any alteration of faculty and period should be possible)..
Plz guide me how to start,algorithms required and tools and references required to create the timetable???

---

### Post by trent.josephsen on 2010-12-30
The combination is unfortunately rather awkward, but I would like to congratulate you on your correct use of both *i.e.* and *e.g.* in the parenthetical statement.

As for your problem, could you clarify exactly what you mean by "timetable"?  What are the specifications of this program, what code have you written so far, and how can we help you?

---

### Post by ziekfiguur on 2010-12-30
How complex are the timetables we are talking about here. 
As far as i know there is no efficient algorithm for this and i think timetables are usually brute-forced. 
So, depending on how complex your timetables are it may very well be impossible to do that in real-time.

You may want to take a look here though: [http://lalescu.ro/liviu/fet/]("http://lalescu.ro/liviu/fet/") It's an open-source program that claims to be able to make most timetables in 5-20 minutes.

---

### Post by Tony Flury on 2010-12-30
I would be tempted to start to the problem by describing the actual problem -e.g. : 

The program will allocate the combination of tutors, classes, rooms and subjects to be taught for each period during the day.

Once you have the description - as a general rule each noun is an "object" which needs some sort of data record, and each verb is an action/function/method (depending on which paradigm you are using).

In terms of rules - the way I would do this is to have the rules defined as config - so you can alter them - you will need rules as to which tutors teach with classes, and specific rules about whether you have single or double periods in some subjects etc.

---

### Post by scott_tiger on 2010-12-31
As far as i know the Genetic Algorithm,backtracking and stable marriage problems are some alogorithm to create the university timetable(see wikipedia for details about these algos).

I am trying to find out any easy algo for this as it is very very difficult to create a timetable for different periods from monday-saturday for different subjects in a university...

PLz guide me any good alogos or methods as i wanted to create my own timetable for university???

---

### Post by IngmarBrouns on 2010-12-31
double post...
[]("http://en.wikipedia.org/wiki/Hill_climbing")

---

### Post by IngmarBrouns on 2010-12-31
seems to be a lot of literature on this subject, but the scientific  papers are often hard to read if you are not already familiar with the  subject. Haven't read it, but maybe this could serve as an introduction

[http://secretgeek.net/content/bambrilg.pdf](http://secretgeek.net/content/bambrilg.pdf)

Also local search algorithms are used for timetabling . Simplest one is hill climbing

[http://en.wikipedia.org/wiki/Hill_climbing](http://en.wikipedia.org/wiki/Hill_climbing)

---


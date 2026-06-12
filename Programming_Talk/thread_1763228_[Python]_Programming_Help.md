---
title: "[Python] Programming Help"
date: 2011-05-20
forum: Programming Talk
---

### Post by ki4jgt on 2011-05-20
I know I'm probably over looking something very small. . . but I've spent the last 10 minutes trying to fix this SMALL mistake. All help is appreciated guys :-)

Anyway, I'm trying to get this tutorial to transition from chapter 1 to chapter 2. It will display chapter 2, but it won't go to it without input from the user. It's PySmash

Here's the link: [http://sourceforge.net/projects/smashindex/files/PySmash/PySmash.py/download](http://sourceforge.net/projects/smashindex/files/PySmash/PySmash.py/download)

Chapter 0 will go to chapter 1 quite well, but I'm not able to get the program to chapter 2 to save my life. :-( It's written in 2.7

EDIT: Transition from chapter 1 to chapter 2: lines 329 - 335

---

### Post by DaithiF on 2011-05-20
Hi, at the end of 1-C you (line 411) you don't set y equal to D, so that 1-D then gets skipped, and its only at the bottom of 1-D that x gets set to chapter 2

---

### Post by ki4jgt on 2011-05-20
> **DaithiF said:**
> Hi, at the end of 1-C you (line 411) you don't set y equal to D, so that 1-D then gets skipped, and its only at the bottom of 1-D that x gets set to chapter 2

Thanks very much. I was still looking at the transition :-( Help was very much appreciated :-)

---


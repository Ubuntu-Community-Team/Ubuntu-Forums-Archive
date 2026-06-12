---
title: "Python Bingo Program - Any suggestions/comments?"
date: 2007-06-25
forum: Programming Talk
---

### Post by Siph0n on 2007-06-25
Here is my bingo program. I got the idea from watching ABC's National Bingo on TV. I wanted a program to check my bingo cards automatically. I'm pretty new at python, and am sure their are ways to optimize this program. One big function is the checkIfClose function. I have to check 12 different possibilities for a bingo. Any comments or suggestions are greatly appreciated. Also, any ideas I could maybe add to this program are accepted, as it will help with my python skills. Thanks! :) I couldn't get the indentations to work right with the code tags, so i attached the bingo.py file instead.

---

### Post by pmasiar on 2007-06-26
not bad for a start. In fact, *very* good. You do have previous coding experience, right? "Dive into Python" is your book.

First let's check some standard [code smell](http://en.wikipedia.org/wiki/Code_smell) tests. (And yes, you should go to wikipedia, and follow to c2.com - the original wiki - to learn more about code smell)

- big, but very regular if-else. Think how dictionaries and decision tables can simplify that. Value in dict can be even a function to call. So you have your logic in couple dicts, separate from code.
- lots of magic numbers. But maybe it is because I have no idea about bingo rules (and frankly no intention to learn them) :-)
- printBingoCards: read up about slices: bingoCards[z][0:5]
- to enhance your exercise, think about ncurses based dashboard status view, with color-coding status of eaxh card, instaed of printing lots of text.

It is my own little standard, but here it is: scalar variable name *never* ends with s - s at the end is for lists and dicts. IMHO, YMMV.

Looks like good exercise. If you can add some rules writeup, I can add it to tasks at my wiki (in my sig) - msg me if interested. You also may want to check training tasks. Check pythonchallenge. Have fun!

---

### Post by Siph0n on 2007-06-26
Thanx for the compliment, and advice! :) I changed the printBingoCards to use those "slices", which got rid of some extra text... I will look at the rest tomorrow! For the rules writeup, you want just a list of rules of how to play Bingo? or how to use my program? or what? :) I'll be glad to do it tho! :)

---

### Post by Modred on 2007-06-26
If you haven't already, look up the **join** function.

For the huge if/else, you might be able to make the code cleaner using some clever coding, but I believe you can't do better than checking each possible mark, assuming you want to know how close to a BINGO you are.  If you just need to know if a BINGO occurred or not, then each non-marked position would eliminate at least two possibilities (row and column), allowing you to skip testing an entire row or column since it was already eliminated from contention.

---

### Post by Siph0n on 2007-06-26
Thanx Modred! I will look at the join function later on today, when I'm home! :)

---

### Post by Modred on 2007-06-26
I must note that what I said about making a faster algorithm to check for BINGO would really only be noticably faster for a large number of cards or extraordinarily large cards.  For your typical, 5x5 BINGO card, your input is small enough that there's really little need for a "faster" algorithm.  So it wouldn't be worth making a function solely to check for BINGO as I described, unless you just wanted to do so to see if you could do it.

---

### Post by Siph0n on 2007-06-26
Oh k! :) I would probably only have 100 cards maximum..... And yea all 5x5.... But I still may check it out, like you said, just to see if I could do it... Plus it might help for a future program... I have until next year tho!!! The last episode of National Bingo was this past friday :(

---


---
title: "Distinct words in a line"
date: 2005-10-27
forum: Programming Talk
---

### Post by anarhistu on 2005-10-27
Using bash, preferably.

C in the worst case.

I need all the distinct words in a line separed by spaces.i did this with awk i think, a whilw ago, but I haven't used this kind of stuff for almost a year now....

---

### Post by LordHunter317 on 2005-10-27
Wait, do you just want to iterate every word on a line, or do you want to ignore words that have already been seen?

---

### Post by Pathogenix on 2005-10-27
When I need a quick and dirty script, I whip out my python. I have this strange affection for a scripting language I can come back and read in a year's time and understand immediately.

```

#! /usr/bin/python2.4

from string import split
import sys
for line in sys.stdin:
        unique = {}
        for token in split(line):
                unique[token] = 1
        print "".join("%s " % k for k in unique.keys())

```

cat someFile | ./myPythonfile.py

---

### Post by anarhistu on 2005-10-28
Cool idea, that is what I want to do.

lordHunter, I waNT TO ignore all words that hae already been seen.

Can this be done in bash?

In DOS I would make a program which would take the first parmeter (string) and create a string with all the other parameters, ignoring the ones equal to the first.Then I would recall the program with the new list, until the list of parameters is empty.

I know this can be done in bash, but i just don't know how.

I would prefer a one line awk script rather than a 10 lines sh program.I will study more, if you haven't got any ideas.

---

### Post by Pathogenix on 2005-10-28
Actually, I googled the answer for Bash before writing the Python script.

[http://cs.anu.edu.au/student/comp2100.2004/lab-exam-solution.html](http://cs.anu.edu.au/student/comp2100.2004/lab-exam-solution.html)

You'd probably want to modify that solution a little to make it work line by line.

---

### Post by anarhistu on 2005-10-28
Hehe, the nice clean quick way.
I figured it out before reading this solution:

cat whatever | tr ' ' '\n' | sort -u

And, if I want it in a line, i just tr[anslate] the newlines back to spaces.

---


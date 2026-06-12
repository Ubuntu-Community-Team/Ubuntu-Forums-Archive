---
title: "n00b C file reading question"
date: 2008-10-29
forum: Programming Talk
---

### Post by Spoodt on 2008-10-29
I'm in an intro to C course that has an assignment which is causing me great frustration, partiularly because of this required function:

"void GetTwo(double *leftOp, double *rightOp, FILE *inp);"

The *inp file pointer is scanned for a set of two double values, leftOp and rightOp. There are multiple sets of these values, and each time this function runs a new set is read from *inp.

I can't seem to wrap my head around this. It seems like every resource online reffers to char strings, but I haven't gotten to strings nor does this assignment constitute them. Does anyone know how to get this thing to work?

---

### Post by namegame on 2008-10-29
I don't want to do your homework for you, neither one of us would gain from that situation. I'll be glad to point you in the right direction. And if you have more questions feel free to ask.

Look up what fscanf() can do.

You should also be prepared to deal with End of File (EOF).

---

### Post by Spoodt on 2008-10-29
EOF? Huh, I haven't heard of that before. I hope this is the right direction, thank you very much!

---

### Post by namegame on 2008-10-29
Yeah, the input file will end eventually. In certain circumstances, the programmer knows the number of entries that need to be read from input, but not always.

---

### Post by Spoodt on 2008-10-29
Wow, alright the whole idea seems clear to me now so far. The people who wrote my class textbook thought it would be a good idea to seperate fscanf and EOF by about 500 pages o_O, thus my ignorance. I feel enlightened now.

---


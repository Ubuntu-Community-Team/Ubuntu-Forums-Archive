---
title: "Geany Build/Compile commands"
date: 2008-10-31
forum: Programming Talk
---

### Post by benjsec on 2008-10-31
Hi,

I'm hoping someone can help me with what seems like a fairly easy problem!

I'm having some trouble getting Geany to build and compile my code, I was struggling getting it to include math.h ("undefined reference to round") and remembered last time I had to add the -lm but after searching I couldn't find whether to add it to teh build or compile.
To cut to the end I think I've now managed to mess the up completely as I'm getting errors along the lines of "gcc: Assignment 1.c: No such file or directory".
Can someone help me get the commands right, I'm starting to get a bit desperate as my assignment is due in on Monday morning and at the moment I can't even check to see where my code is broken!!

Many Thanks,
Ben

If it helps my current commands are:
Compile: gcc -Wall -c "%f"
Build: gcc -Wall -lm -o "%f"
Execute "./%e"

---

### Post by cmay on 2008-10-31
> I'm starting to get a bit desperate as my assignment is due in on Monday morning and at the moment I can't even check to see where my code is broken!!
you can see if the code work if you just compile from the commandline. i use geany for all things. i do not know what the problem is in this case so i can only advise you to use the commandline to compile and then just use geany to edit the files as you go along.

---


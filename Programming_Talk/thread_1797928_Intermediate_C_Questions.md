---
title: "Intermediate C Questions"
date: 2011-07-05
forum: Programming Talk
---

### Post by Majorix on 2011-07-05
I have completed my first year of a CS course. Was successful in C classes, if not really good.

Two questions, and the lack of knowledge regarding those subjects, earned me a CC, where I could have a much higher grade.

Anyways, my questions:
1. Where can I read about nodes, linked lists and binary trees?
2. Where can I read about binary files, and how to read from and write to them?

Specific papers, a whole book, just a short article... As long as it accomplishes the goal of teaching me these, anything is appreciated.

Thanks.

---

### Post by in-dust-rial on 2011-07-05
hey,
congratz for passing!

since it is 1st year course I guess its less about C and more about concepts.
the first question is clearly all about:
[http://en.wikipedia.org/wiki/Graph_theory](http://en.wikipedia.org/wiki/Graph_theory)

i am not sure about a common conceptual ground about the second question. maybe 
[http://en.wikipedia.org/wiki/Linker_%28computing%29](http://en.wikipedia.org/wiki/Linker_%28computing%29)
?

good luck

---

### Post by Bachstelze on 2011-07-05
"Node" can mean a lot of things depending on context, but ultimately it is a concept of graph theory, as in-dust-rial pointed out.  A lot of things in CS can be modelized as a graph, with nodes and edges representing different things depending on what the graph modelizes.

Linked lists and binary trees (and trees in general) are data structures. Any book on algorithms will help you understand them, you can look for example at Introduction to Algorithms by Cormen, Leiserson, Rivest and Stein (aka CLRS), or Wikipedia.

"Binary file" in general refers to anything that is not a plain text file (i.e. where not all bytes represent printable characters).  Keep in mind, however, that the distinction is purely one of convenience: ultimately, you read and write to them exactly the same way you read or write to text files (on UNIX, with the read and write system calls).

---

### Post by ceclauson on 2011-07-05
For algorithms, maybe this:
[http://oreilly.com/catalog/9781565924536]("http://oreilly.com/catalog/9781565924536")

For binary files, I'd check out the functions declared in stdio.h:
[http://en.wikipedia.org/wiki/Stdio.h]("http://en.wikipedia.org/wiki/Stdio.h")

---

### Post by deathadder on 2011-07-06
I've found the bits from this site very useful: [http://www.cs.cf.ac.uk/Dave/C/](http://www.cs.cf.ac.uk/Dave/C/)

You'll want to have a look at the [Dynamic Memory Allocation and Dynamic Structures]("http://www.cs.cf.ac.uk/Dave/C/node11.html#SECTION001100000000000000000") for linked lists.

---


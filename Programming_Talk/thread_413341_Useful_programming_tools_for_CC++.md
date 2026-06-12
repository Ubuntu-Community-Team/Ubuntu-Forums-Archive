---
title: "Useful programming tools for C/C++?"
date: 2007-04-19
forum: Programming Talk
---

### Post by SNYP40A1 on 2007-04-19
I am new to programming in Unix, but I am looking for some good C/C++ programming tools. For example, it would be cool if there was an application that shows me how all the functions in my program interact, by tracing lines between the functions which call each other. BlueJ had this, back when I was programming in Java. Also, are there any tools for code factorization? Maybe something that can tell me if the same code is being used in two different functions. I want to write better code and I want to learn more about the tools which can help me do that. Suggestions?

Also, any tools for writing psuedo code or laying out thoughts?

---

### Post by amo-ej1 on 2007-04-19
Well if you want this done 'offline' you could use doxygen. Doxygen is capable of generating callgraphs (the main functionality of doxygen can be compared to javadoc, altough it looks more obscure at first you will rapidly notice that doxygen offers way more functionality than javadoc).

If you want this done at runtime (profiling etc) then kcachegrind is something you should take a look at: [http://kcachegrind.sourceforge.net/cgi-bin/show.cgi](http://kcachegrind.sourceforge.net/cgi-bin/show.cgi)  (which is a frontend on valgrind data)

---


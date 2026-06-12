---
title: "Segmentation fault (core dumped)"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by HaemoLacria on 2008-06-26
What does this mean: Segmentation fault (core dumped)
Firefox shuts down suddenly and I get this in the terminal:confused:

---

### Post by Cypher on 2008-06-26
There was an error in the application. In programming terms, a Segmentation Fault (Segfault) is caused when a program attempts to access memory that isn't valid. It might be a bad pointer access, bad array access or something else that's also bad.

The core, a file, that is dumped contains information about what the program was doing at the moment of the error. A programmer could take the program and the core file and determine what the problem is.

---


---
title: "Packaging Java source."
date: 2011-10-05
forum: Packaging and Compiling Programs
---

### Post by MG&amp;TL on 2011-10-05
Hi- I'm packaging a Java application for somebody, and we've run into a problem.  The Java needs to have its source code somewhere, and it also needs to have read-write-execute permissions in that directory.

How can I engineer this into the debian packaging? And where should the java go? Currently I have a bash script in /usr/bin/ that points to and runs the Java, and a directory in /usr/src. 

The problem with /usr/src, was that it didn't have write permission. And if I put it in ~/.<package>, it appears to mark it as root-owned.

How can I package it? (it's probably obvious, but I can't see it)

---

### Post by MG&amp;TL on 2011-10-07
EDIT: just read through this and last post and realised I made myself very unclear. And my problem is solved, just not completely. Will start a new thread.

---


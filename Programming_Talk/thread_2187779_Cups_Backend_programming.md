---
title: "Cups Backend programming"
date: 2013-11-13
forum: Programming Talk
---

### Post by Bastila22 on 2013-11-13
So i am working on a project where I have a CUPS server and for all jobs received to be printed but also save a pdf locally on the server as well. I am having some trouble figuring out where I would put my code in the backend or what is the best way to go about doing this.

---

### Post by dwhitney67 on 2013-11-13
> **Bastila22 said:**
> So i am working on a project where I have a CUPS server and for all jobs received to be printed but also save a pdf locally on the server as well. I am having some trouble figuring out where I would put my code in the backend or what is the best way to go about doing this.

What do you mean by "backend"?  Is there a front end?

Your question is pretty vague in as far as what you want to accomplish.  Is it your intent to accept the name of a document (on your system) from a user and then print it?  If this document is a PDF file, do you intend to save it (someplace where it does not already exist)?

As for CUPS, there is a C library (or is it C++?) that can be used to interface to the CUPS server.  Have you given it a shot yet?

---


---
title: "linking a gpl incompatible 3rd party open source library against a gpl 3 program?"
date: 2012-06-25
forum: Programming Talk
---

### Post by tylerxx on 2012-06-25
Hello you licence experts out there ):P
our project would like to publish a project under gpl 3 but we are "a bit" confused due to all the gpl licence details. We read the gnu website, but a question is left. We use some open source libraries under CDDL and CPL. We still have to figure out which of these are by gnu definition
A) linked against our programm and
B) which are used with our programm without being linked against it.
 
We found that you can add exceptions for libraries not linked to it. But how to handle gpl 3 incompatible libraries linking against our software? 
 
Is it possible at all to publish our self programmed software under gpl 3 with CDDL libraries linking against it? Do we have to include a so called "linking exception" in our license text for these CDDL libraries? If it is possible at all, how would this linking exception text have to be expressed/phrased?
 
I Hope for your help, struggling with the license jungle... :confused:

---

### Post by trent.josephsen on 2012-06-26
People here might be able to give you an idea, but if you need an authoritative answer, you need to find a lawyer who specializes in this kind of thing.

Personally I'm not 100% sure what is covered by linking... seems static linking and dynamic linking are somewhat different in how the GPL is applied to them. Hopefully somebody else knows.

---

### Post by tylerxx on 2012-06-26
A definition / explication of the 3 ways in which libraries can be used (according to gpl) would help us too. They (Gnu/gpl) speak about
a) system libraries
b) linked libraries (static or dynamically linked)
c) and libraries used in a third way - how is it called? 

In our programmers' team they think our libraries are linked libraries - but in fact they are not quite sure.
As I understood it so far:
statically linked libraries are this: take source code of 3rd party lib A and your own source code, compile this combined source code to a new executable. This new executable is the result of static linking.
dynamically linked libraries are this: there is a 3rd party lib A and your own code B in a directory of your project. Both, A and B, are executed during runtime. Your code B starts and needs lib A to work.

Especially concerning the dynamic linking, I am totally not sure...

----------

**But anyways, beside the differentiation of dynamic or static links. If we have linked libs (as we think): How do we have to handle them in the explained situation?**
So, is it possible at all (maybe by using exceptions) to publish our self programmed software under gpl 3 with CDDL libraries linking against it? 

Sighing a bit frustrated due to the jungle of incompatible open source licences... :|

---


---
title: "Initializer Element is not constant"
date: 2010-03-11
forum: Programming Talk
---

### Post by newport_j on 2010-03-11
I got the following error (among others) when I complied some c code.  

The error:

error: initializer element is not constant

The line in question is:

         
    for(IRAYg=MINRAYg;IRAYg<=MAXRAYg;IRAYg=IRAYg+1){ 

I am not sure what this error is saying. I can understand the quote literally, but what initializer on this line is it talking about?

Newport_j

---

### Post by MadCow108 on 2010-03-11
its hard to tell the reason without more code.
common reasons are non const assignments in global scope or non constant struct initializations in pre C99 standard without gnu extensions

---


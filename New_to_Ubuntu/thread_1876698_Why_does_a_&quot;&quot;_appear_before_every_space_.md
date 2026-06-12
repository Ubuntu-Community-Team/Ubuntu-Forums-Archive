---
title: "Why does a &quot;\&quot; appear before every space in filepaths?"
date: 2011-11-06
forum: New to Ubuntu
---

### Post by ljl16 on 2011-11-06
Hi there, 
 Today I found out that spaces in filepaths are not the same as before. When before I could write "cd suomen mestari" to change to folder "suomen mestari" now doing autocomplete it shows a "cd suomen\ mestari". How can I go back to the way it was before?

Thanks :)

---

### Post by uRock on 2011-11-06
In my experience this has always been the case with the Linux command line.

---

### Post by ballantony on 2011-11-06
The \ indicates the following character (the space) is part of the filename.  It shows that the filename doesn't end at the space as is typically the case.   You could also write  
"suomen mestari"

---

### Post by Vaphell on 2011-11-06
no you couldn't
there is a difference between **cd "suomen mestari"** (this one works and is an equivalent of **cd suomen\ mestari**) and **cd suomen mestari** which fails horribly

---

### Post by ajgreeny on 2011-11-06
> **Vaphell said:**
> no you couldn't
there is a difference between **cd "suomen mestari"** (this one works and is an equivalent of **cd suomen\ mestari**) and **cd suomen mestari** which fails horribly
I think that is exactly what ballantony meant!  You can escape a space either with the backslash before it, or by using quote marks around the full path of the file.

This has always been so, and is nothing new, so your "way it was before" never was, or not in Linux/unix.

---

### Post by dFlyer on 2011-11-06
> **ljl16 said:**
> Hi there, 
 Today I found out that spaces in filepaths are not the same as before. When before I could write "cd suomen mestari" to change to folder "suomen mestari" now doing autocomplete it shows a "cd suomen\ mestari". How can I go back to the way it was before?

Thanks :)

You can't. This is the ways it has been for years so you either:

cd "suomen mestari"

or

cd suomen\ mestari

---


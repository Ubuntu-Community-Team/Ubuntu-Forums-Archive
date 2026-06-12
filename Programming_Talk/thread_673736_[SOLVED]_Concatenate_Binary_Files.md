---
title: "[SOLVED] Concatenate Binary Files"
date: 2008-01-21
forum: Programming Talk
---

### Post by ~chinook~ on 2008-01-21
Ok, my programming assignment required us to use multiple processes to do a task. We had to some compression on files. Now each process creates a binary file. How would I join those files together without reading them back in. I can use the cat command in the terminal. How would I call that from my program? Any help will be appreciated.

---

### Post by yabbadabbadont on 2008-01-21
Do your own homework, or you will never learn.  :D

---

### Post by ~chinook~ on 2008-01-21
The guts of the assignment is done. It is just merging the binary files together.

---

### Post by yabbadabbadont on 2008-01-21
I'm not going to do your homework for you, but if you want help, you should tell us **what programming language** you are using....  :p :D

---

### Post by Saint Angeles on 2008-01-21
> **yabbadabbadont said:**
> Do your own homework, or you will never learn.  :D
not that i'm programming-saavy enough to help, but you're entirely rude.

if you can't help (or if you are too elitist to help) then don't say anything at all.

---

### Post by yabbadabbadont on 2008-01-21
> **Saint Angeles said:**
> not that i'm programming-saavy enough to help, but you're entirely rude.

if you can't help (or if you are too elitist to help) then don't say anything at all.

Hmmm.  And here I thought that I included a smiley to show that I was being good natured about it.  Your post on the other hand, is borderline reportable.

(and he never will learn if other people do his homework for him ;))

To the OP, you still need to tell us which programming language you are using.  :)

---

### Post by ~chinook~ on 2008-01-21
Sorry I thought I said C.

---

### Post by yabbadabbadont on 2008-01-21
```
man system
```

;)

---

### Post by CptPicard on 2008-01-21
> **yabbadabbadont said:**
> Hmmm.  And here I thought that I included a smiley to show that I was being good natured about it.  Your post on the other hand, is borderline reportable.

As he said, his assignment is done. If he was asking to write the compressor for him, yeah, that would be the "we don't do homework" issue.

Yeah, you should be able to use cat. In C you don't have any particular function for that, you need to read the files separately and just write them back to back into your output file.

---

### Post by ~chinook~ on 2008-01-21
That is what I thought. I think I will just use the system call as part of this assignment was to learn how to do system calls.

---

### Post by CptPicard on 2008-01-21
This leaves me with the assumption that "system calls" are a bit different than what you'd think, then. It doesn't mean using system() to call program binaries, but to call the kernel's provided API for file manipulation, that is, to do what I told you to do... (read the files and then write them out into the same file)

---

### Post by ~chinook~ on 2008-01-21
That is true.

---


---
title: "force buffer dump"
date: 2008-12-19
forum: Programming Talk
---

### Post by beren.olvar on 2008-12-19
I made a program in C that has been running for like a day or so.
It is about 30% complete and I would like to use the data it has calculated so far, but I forgot to use fflush to make it actually write the data to the files, so I only have a partially written file with my output, and a lot more on its buffer.

Is there a way I can force it to write the data? some "kill" signal or something?

Ideally I wouldn't like to kill the process, so I don't feel like I just wasted a day.

TY!

---

### Post by kknd on 2008-12-19
If you reffer to the internal buffer used by stdio, then use fflush(FILE* f);

---

### Post by beren.olvar on 2008-12-19
> **kknd said:**
> If you reffer to the internal buffer used by stdio, then use fflush(FILE* f);
Yeah, I know, but i didn't, so, can I do something about an allready running process??

---

### Post by kknd on 2008-12-20
Ahh, sorry, I didn't read right the question.

---


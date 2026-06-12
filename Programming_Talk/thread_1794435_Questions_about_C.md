---
title: "Questions about C"
date: 2011-07-01
forum: Programming Talk
---

### Post by Yeshining on 2011-07-01
My os is Ubuntu 11.04 and I want to practise C language,
but I don't know how to work it out as VC in windows platform...
So please give some instructions if you know...:popcorn:

---

### Post by zobayer1 on 2011-07-01
> **Yeshining said:**
> My os is Ubuntu 11.04 and I want to practise C language,
but I don't know how to work it out as VC in windows platform...
So please give some instructions if you know...:popcorn:
You have gcc built in to your system, so its pretty straight, write a code in C, and save it where you like, open terminal and move to the directory where you put it, say, you call it first.c
Then just call gcc:
```

gcc first.c -o first

```
-o defines the optional executable name, if you don't give it, still its ok, it will create one with default name a.out
Then to run the program, just call it:
```

./first

```

If you want to code with C++, you need to install g++, you will get plenty of information on how to do that on ubuntu.

Then, if you want program like VC (not entirely though) try 'geany', you will get that from your software center->programming section.

---


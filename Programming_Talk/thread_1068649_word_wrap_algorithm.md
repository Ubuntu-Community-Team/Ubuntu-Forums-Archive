---
title: "word wrap algorithm"
date: 2009-02-13
forum: Programming Talk
---

### Post by guest_user on 2009-02-13
anyone know how do I do a word wrap after a certain number of columns given an input file in c++?

---

### Post by ch0d3 on 2009-02-13
Count the columns until wrap_count (or whatever) and insert newline? A little more info would help.

---

### Post by guest_user on 2009-02-13
> **ch0d3 said:**
> Count the columns until wrap_count (or whatever) and insert newline? A little more info would help.
the words must not be split in half.

I have a file, I read it line by line into a buffer what I want done is to output it such that it does not exceed a specified no. of columns without cutting any words in half but wrapping them to the next line should they exceed the max no. of columns.

---

### Post by ch0d3 on 2009-02-13
Okay, so count words. It sounds like you have everything you need to implement this algorithm. What is your question?

---

### Post by guest_user on 2009-02-13
The problem is I have trouble translating that into c++; btw, its not about counting words, its about putting the max no. of words that can fit into a line of a specified width and then outputting it

---

### Post by ch0d3 on 2009-02-13
> **guest_user said:**
> btw, its not about counting words, its about putting the max no. of words that can fit into a line of a specified width and then outputting it

Ok, maybe I didn't explain that clearly enough. Anyway, it sounds like all you have to do is insert a newline before the word that crosses the boundry.

---

### Post by happysmileman on 2009-02-13
Go to string[LINE_WIDTH] and go backwards until you find a whitespace character (say at string[X]), replace first space you find with newline, then repeat with string[X + LINE_WIDTH]

You should decide what you want to do if you encounter a "word" with more than LINE_WIDTH, most programs put a newline at string[LINE_WIDTH] anyway, splitting this "word" up.

EDIT: I just wrote this in like 30 seconds, haven't actually done it., but I imagine it should work, or almost work at least

---


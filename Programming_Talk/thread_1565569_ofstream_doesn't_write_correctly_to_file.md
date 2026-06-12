---
title: "ofstream doesn't write correctly to file"
date: 2010-09-01
forum: Programming Talk
---

### Post by hakermania on 2010-09-01
Sometimes it does, but some other times it doesn't...
I had a pop-up requesting for a path. This path string I converted into a  char* and then I write this char to a file. I noticed that the char has been transformed to something like hello.mp3- or  hello.mp30 or hello.mp3` or hello.mp3P, hello.mp3H or other capital letters
I performed a check to see where the string is wrongly parsed and the  result was when ofstream was writing it to the file. See this screenshot  and tell me your opinion:
[IMG]http://a.imageshack.us/img228/3396/screenshot5f.png[/IMG]

It is strange. Isn't it?:(

---

### Post by Some Penguin on 2010-09-01
Please don't overwrite random memory addresses.  The behavior of that program is undefined where py is long.

---

### Post by fct on 2010-09-01
Fot the record, a better way to get the path to the user's home directory is to read the $HOME env var. Like this: *getenv("HOME")*

---

### Post by dwhitney67 on 2010-09-01
> **hakermania said:**
> ... tell me your opinion:


I have two opinions...

1)  Use the STL string class instead of char arrays for strings.  Your are programming in C++ right??  Let go of C.

2)  When posting code, please do not post images; post the actual code, or a smaller program that captures the essence of the anomaly you are experiencing.  This way, others can compile and run the code to see what errors you are experiencing with the code.

---

### Post by hakermania on 2010-09-01
OK, guys, thx for the interest. The suggestion of goinf off the C was the better. I used C++ functions to write to the file and now it works very well. Thank you.

---


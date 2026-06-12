---
title: "[java]Differance between BufferedReader and Scanner"
date: 2008-10-03
forum: Programming Talk
---

### Post by Pyro.699 on 2008-10-03
Hello,

Aside from my major project that a lot of you are helping me with (Thanks again <3) I'm in university and having to deal with some of the questions that you'll only encounter once in a while. The question I've been assigned is to describe the difference between **BufferedReader** and **Scanner**. I know that both of them are used to read data streams. If i was to take a guess the main differance would be that BufferedReader reads information that is distributed over a period of time, and Scanner reads data that are stored in objects that are already complete. That was just a guess though.

Thanks for any answers
~Cody Woolaver

---

### Post by jespdj on 2008-10-03
Carefully read [the API documentation](http://java.sun.com/javase/6/docs/api/) for both of those classes, that should give you some ideas about the differences.

---

### Post by Pyro.699 on 2008-10-03
Alright, so please correct me if im wrong.

The difference between Scanner and BufferedReader is that BufferedReader is used to obtain better organization of the input methods, "as to  provide for the efficient reading of characters, arrays, and lines." while Scanner can have delimiters phrased to it allowing different seperation of lines, characters and arrays.

---

### Post by CptPicard on 2008-10-03
I guess I shouldn't help with homework but... BufferedReader reads a stream and stores it into a buffer. In particular, you can use it to read text streams (like from files or from network) line by line.

Scanner is higher-level, it tokenizes for you using a delimiter of your choice, or can for example seek ahead for a particular regular expression. It's really handy for writing quick parsers.

---


---
title: "[SOLVED] force string in c++"
date: 2008-03-19
forum: Programming Talk
---

### Post by chris200x9 on 2008-03-19
ok I have a problem I'm using cin.getline so that I get the line white space included I then want to force the array of characters to be a string and just be one word also I want to be able get rid of all the white space before and after the input, would a char array to string conversion do this, and is it even possible?

---

### Post by ha1f on 2008-03-19
sure it's possible.

I'm not sure if you're only getting one word, or several words but you can write a trim function that strips the whitespace off of both sides, or (if you have more than one word or want to remove more than just preceding and following whitespace), you can just copy characters that are not whitespace to a buffer string.

If this only has to work on Linux, then ```
man strstrip
```, which is a trimmer in the basic C lib of Linux since... 2006, maybe?.  Sounds homeworky though...

---

### Post by chris200x9 on 2008-03-19
thanks, no actually it's not homework it WAS homework but I'm just trying to expand on my program for my own learning. :)

---


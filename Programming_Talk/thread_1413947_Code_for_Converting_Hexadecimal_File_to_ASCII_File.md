---
title: "Code for Converting Hexadecimal File to ASCII File"
date: 2010-02-23
forum: Programming Talk
---

### Post by aditya.gnu on 2010-02-23
Dear techies,

I just wanted to know how can we convert a **Hexadecimal File to ASCII File in C?** Its is basically a Hex dump file (consists of hexadecimal content) and I wanted to scan it and convert it into an ASCII Code. And that Hex file cannot to opened in a notepad or wordpad, its related to a project and can be viewed only in Visual Stduio IDE.
I hope you guys got some idea regarding the objective.
Can anybody give me some clue for that..?
Thanks in advance.

Regards,
Aditya.

---

### Post by leg on 2010-02-23
Converting hexadecimal to an ascii representation shouldn't be too hard. You can convert the number to decimal then work out which character that number represents in ASCII. I doubt if that will lead to a readable text file though as not all hex numbers will be related to an ascii code. Some of them may be interupt numbers or something else entirely.

---

### Post by crlang13 on 2010-02-23
I've done something similar, but not in C.  I know alot of languages have a built in function for hex or binary into ascii, if you can't find one, you may have to build one first off.

Check out the table: [http://www.asciitable.com/](http://www.asciitable.com/)

Is the hex data contained to only letters? or all ascii characters?

---

### Post by LKjell on 2010-02-23
For C and its like you just need to store the number in a char and it does eveything for you. The same with Java.

---


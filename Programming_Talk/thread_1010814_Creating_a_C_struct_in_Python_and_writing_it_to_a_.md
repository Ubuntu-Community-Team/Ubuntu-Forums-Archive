---
title: "Creating a C struct in Python and writing it to a binary file?"
date: 2008-12-14
forum: Programming Talk
---

### Post by crazyfuturamanoob on 2008-12-14
How?

---

### Post by pp. on 2008-12-14
Why?

Why not use XML?

---

### Post by crazyfuturamanoob on 2008-12-14
> **pp. said:**
> Why?

Why not use XML?

XML? Huh? :confused:

All I know is the syntax and how to make maps for Scorched3D.

---

### Post by pp. on 2008-12-14
There are several strategies you can use for transferring data between different programs or even for reading and writing data by the same program.

What you are proposing in the thread's title is to use something like the raw format for a program written in one language to read that data in a program written in another language. That's perfectly possible and presumably not overly difficult (once you know what you're doing) but might result in some headaches at the most awkward moments. Think about how you might use your data of an earlier version in a later version of your programs.

XML, on the other hand, is an instruments which is designed to move arbitrarily complex data between applications in a manner which is as independent of any particular implementation as they could make it.

If I was you, I'd read up on XML and exchange data between C and Python programs in XML, unless there were some clear objective reasons not to do so.

---

### Post by crazyfuturamanoob on 2008-12-14
> **pp. said:**
> There are several strategies you can use for transferring data between different programs or even for reading and writing data by the same program.

What you are proposing in the thread's title is to use something like the raw format for a program written in one language to read that data in a program written in another language. That's perfectly possible and presumably not overly difficult (once you know what you're doing) but might result in some headaches at the most awkward moments. Think about how you might use your data of an earlier version in a later version of your programs.

XML, on the other hand, is an instruments which is designed to move arbitrarily complex data between applications in a manner which is as independent of any particular implementation as they could make it.

If I was you, I'd read up on XML and exchange data between C and Python programs in XML, unless there were some clear objective reasons not to do so.

Writing & reading binary data is much easier in C, and a binary file doesn't eat that much memory.

The files I'm writing are large, several megabits.

---

### Post by Quikee on 2008-12-14
Hm.. well you could use ["struct"]("http://docs.python.org/library/struct.html") module for what you want.

---

### Post by pmasiar on 2008-12-14
> **crazyfuturamanoob said:**
> Writing & reading binary data is much easier in C, and a binary file doesn't eat that much memory.

The files I'm writing are large, several megabits.

Megabytes is not too big file (unless you run it on a phone).

Python allows binary input and output: [http://www.python.org/doc/2.5.2/tut/node9.html](http://www.python.org/doc/2.5.2/tut/node9.html) so I do not see where is your problem.

See also [http://www.devshed.com/c/a/Python/File-Management-in-Python/](http://www.devshed.com/c/a/Python/File-Management-in-Python/)

Of course if your files are supposed to be cross-platform and cointain multibyte values, you have to consider also [http://en.wikipedia.org/wiki/Endian](http://en.wikipedia.org/wiki/Endian) - as usually, if you don't use the simplest solutions, problems just snowball ;-)

---


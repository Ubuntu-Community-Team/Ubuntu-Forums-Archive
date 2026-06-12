---
title: "C++ questions: Difference between \n and endl"
date: 2011-08-12
forum: Programming Talk
---

### Post by orrymr on 2011-08-12
I did a bit of reading, and what I've ascertained is that '\n' is a character, much like 'l' or '\0' and endl is a stream manipulator (sort of like a function?) which flushes out the buffer to the current output (for my purposes it seems like this would be the terminal). However, I'm not quite sure what this means in practice. What exactly is in this "buffer" in the first place? In a simple C++ program, is cout my buffer? Why would I want to flush it anyway?

Thanks in advance!

---

### Post by MG&amp;TL on 2011-08-12
The buffer is so that you can type a line of input to the console at once, otherwise it would read one character at a time. As far as I know, there is no practical difference, but I do find that <<endl; is more reliable. On the other hand, there's no equivalent to '/t' for <<endl; It's really your choice.

---

### Post by orrymr on 2011-08-12
So if I'm doing something like: 
```

cin > x;

```
It first goes through a buffer?

---

### Post by MG&amp;TL on 2011-08-12
Yes, until you press return. The buffer's just a piece of memory that only gets processed when you press return

---

### Post by dazman19 on 2011-08-12
endl seems to me to be a function, from the iostream lib it is used when manipulating iostreams. istream / ostream ..

which read/write to buffers you create, or the standard buffer.

you would find that it would be slightly more complex than 8 bits. '\n' 

But for most cases we do not need to worry.

---

### Post by cgroza on 2011-08-12
From the documentation: [http://www.cplusplus.com/reference/iostream/manipulators/endl/](http://www.cplusplus.com/reference/iostream/manipulators/endl/)

std::endl also flushes the stream. "\n" does not, so you may need to flush it manually if you must to.

---

### Post by cgroza on 2011-08-12
> **orrymr said:**
> What exactly is in this "buffer" in the first place? In a simple C++ program, is cout my buffer? Why would I want to flush it anyway?

Thanks in advance!
You can make an experiment on that. Just cout some stuff without including std::endl or calling flush on the stream, and you will notice that your content will not appear on the screen right away.

This happens because cout is a buffered stream. For efficiency reasons, it waits until the buffer is full enough and then outputs it. Calling flush makes the stream output its contents right away, without waiting for the buffer to get any bigger.
Take a look at std::cerr, it is an unbuffered  stream, you do not need to flush() it.

---


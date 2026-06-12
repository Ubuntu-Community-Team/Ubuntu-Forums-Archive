---
title: "How does one send a 'payload' with a signal?"
date: 2011-08-25
forum: Programming Talk
---

### Post by ownaginatious on 2011-08-25
So I have a program written in C that I want to send some information to every time I do a SIGUSR1 to it which it will read.

Now what I could do (which I feel is kind of a dumb solution) is write what I need to send it into a file, and then have it read that file as soon as the SIGUSR1 is executed to the process.

Is this really the best way to do this, or is there another smarter way without having to write anything to my hard-drive?

---

### Post by Tony Flury on 2011-08-26
You could use a shared memory map and use that to share information with your application - but a file might be easier.

---

### Post by ofnuts on 2011-08-26
> **ownaginatious said:**
> So I have a program written in C that I want to send some information to every time I do a SIGUSR1 to it which it will read.

Now what I could do (which I feel is kind of a dumb solution) is write what I need to send it into a file, and then have it read that file as soon as the SIGUSR1 is executed to the process.

Is this really the best way to do this, or is there another smarter way without having to write anything to my hard-drive?Use a Fifo?

---

### Post by ofnuts on 2011-08-26
Afterthought: depending on what your program does you could avoid the SIGUSR by just using a select() or pselect() inside the program (one of the file descriptors being a fifo)

---


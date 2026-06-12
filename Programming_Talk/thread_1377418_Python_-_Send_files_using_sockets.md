---
title: "Python - Send files using sockets?"
date: 2010-01-10
forum: Programming Talk
---

### Post by Tahakki on 2010-01-10
As far as I can tell, sockets are only useful for sending small things, e.g. text and variables.

Is there any way to send, say, a JPEG (simple, preferably!)?

---

### Post by wmcbrine on 2010-01-10
You can send anything of any size. Most of the Internet is built on sockets.

I think, for us to better answer your question, you need to explain *why* you think "sockets are only useful for sending small things".

---

### Post by Tahakki on 2010-01-10
Really? I must've heard wrongly somewhere then. :P

Looking at tutorials etc., I can't seem to find anything showing how to do this. Do I use socket.sendall(filename)?

---

### Post by Can+~ on 2010-01-10
I suggest you to read about the POSIX socket theory before even using the libraries:

[http://beej.us/guide/bgnet/output/html/multipage/theory.html](http://beej.us/guide/bgnet/output/html/multipage/theory.html)

---

### Post by Tahakki on 2010-01-13
Bump!

As someone who is still fairly new to Python, can anyone direct me to a tutorial involving sending files (pictures, media etc.) via Python sockets, or an easier way?

I understand sockets themselves and can send strings and things - but I don't see how to send files.

---

### Post by wmcbrine on 2010-01-13
A file is just data. It's nothing special. Read it in, and you have a string. If it's too big to read it in all at once, then do it in chunks.

---

### Post by era86 on 2010-01-14
> **wmcbrine said:**
> A file is just data. It's nothing special. Read it in, and you have a string. If it's too big to read it in all at once, then do it in chunks.

This is basically what you want to do.  Reading up on the python socket library, all you do is load the file into a buffer.  So open a socket connecting to a server (address, port) that is waiting for a connection.  Then find some sort of protocol for sending from the client and recieving from the kernel.  The server will handle piecing the file back together.

[http://www.amk.ca/python/howto/sockets/](http://www.amk.ca/python/howto/sockets/)

---

### Post by Tahakki on 2010-01-14
Sorry, how do I 'read in' a file?

---

### Post by dwhitney67 on 2010-01-14
> **Tahakki said:**
> Sorry, how do I 'read in' a file?

Whoa... you really do need help... and the basic stuff too!

Read here about opening files and reading from them:
[http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files](http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files)

Read here about socket programming:
[http://docs.python.org/library/socket.html](http://docs.python.org/library/socket.html)

If you are new to Python (and/or programming in general), I would suggest you tackle some basic programming exercises before moving onto socket programming.

---

### Post by Tahakki on 2010-01-14
Haha! Actually I've been working with Python for a while, and can use the vast majority of GTK+ with relative ease now - turns out file I/O was something I completely missed! xD

I think I understand now - one thing, though. Do I have to set a buffer size? If so, what's the maximum a typical computer/network could handle, and what's the easiest thing to do if a file exceeds that?

---

### Post by mikejonesey on 2010-01-14
[http://curl.haxx.se/](http://curl.haxx.se/)

this is what i use (i don't know python though or if it has any built in / native support for such protocols).

---

### Post by Tahakki on 2010-01-14
Have the following:

sender:
```
import socket

f = open('recieved.jpg', 'w')
strf = str(f)
eggs = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
eggs.connect(('localhost', 8206))
eggs.sendall(strf)
```

reciever:
```
import socket

f = open('recieved.jpg', 'w')
eggs = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
eggs.bind(('', 8206))
eggs.listen(5)
while True:
    channel, details = eggs.accept()
    print 'connected'
    got = channel.recv(4096)
    f.write(got)
    channel.send("recieved!")
    channel.close()
```

---

### Post by dwhitney67 on 2010-01-14
> 
I think I understand now - one thing, though. Do I have to set a buffer size? If so, what's the maximum a typical computer/network could handle, and what's the easiest thing to do if a file exceeds that?

Depends on what type of socket you use.  For UDP sockets, supposedly datagrams up to 65,507 bytes can be sent.  For TCP sockets, this can vary, but theoretically one wants to keep it at the MTU (Maximum Transmission Unit?) setting (for performance reasons); for many systems, the MTU is set at 1500 (bytes).

Get yourself a good book on socket programming (W. Richard Stevens is a good author, but his stuff is focused on C, not Python).  Or just Wiki/Google for information.

---

### Post by wmcbrine on 2010-01-14
> **Tahakki said:**
> Have the following:

sender:
```
import socket

f = open('recieved.jpg', 'w')
```That's going to erase the file you're trying to send.

Seriously, forget about sockets for a minute. File I/O is way more fundamental than sockets, or GUIs, or almost anything. You need to do some basic exercises in that area.

In this case, since you're dealing with binary data, you want to open it in mode 'b'. And since you're trying to *read* it, you *don't* want mode 'w'.

> ```
strf = str(f)
```No -- more like:

```
strf = f.read()
```

Now, in your receiver, you have an infinite loop with no exit, among other issues. I'm sure you can improve on that...

---

### Post by Tahakki on 2010-01-15
Surely I want it to be writable, since I'm writing to it - that's at the recieving end. The file reciever.jpg doesn't exist before this program is run.

---

### Post by dwhitney67 on 2010-01-15
> **Tahakki said:**
> Surely I want it to be writable, since I'm writing to it - that's at the recieving end. The file reciever.jpg doesn't exist before this program is run.
Both your 'sender' and 'receiver' code were opening the same file in write-mode.  Please re-check the code you posted earlier.

As for the code that receives the data, as wmcbrine pointed out, it is incomplete.  You assume the quantity data that is being sent will be 4096 bytes (or less); you never know, it may be more.  As for the loop, it looks like you are expecting to receive a connection request from the same client (or perhaps another?) over and over again.

One should continue reading data (and writing it to the file) as long as the client continues sending data.  Don't assume the client (or the underlying OS kernel) will send all the data at once; it may arrive in separate packets.

---

### Post by Tahakki on 2010-01-15
Sorry, mistake made there. :P

Yes, I'm aware of the buffer issue. How would I recieve something large - bigger buffer or loop?

---

### Post by dwhitney67 on 2010-01-15
> **Tahakki said:**
> 
Yes, I'm aware of the buffer issue. How would I recieve something large - bigger buffer or loop?
Looping is the best choice; the client cannot assume that they will be able send 1 chunk of data containing N bytes, nor can the server assume they will receive all N bytes at the same time.  Of course, this is applicable when using TCP.  For UDP, the datagram would arrive in one chunk; or just get lost :-)

In Python pseudo-code, the server would do something like:
```

create the socket
bind the socket
listen for connection(s)

while forever:
        accept connection

        # decide here if you want to spawn a child-thread,
        # or operate single-threaded.  Let's assume the latter.

        myFile = open('UniqueFilename', 'w')

        while true:
                rbuf = recv(4096);

                if (rbuf == ""):
                        break

                myFile.write(rbuf)


```
I have never done such a thing in Python, so details may have been inadvertently skipped from the pseudo-code above.  And as for Python, since it does not come into play whatsoever my ability to earn a living, I do not know of all of the details of the language's capabilities.

---

### Post by Tahakki on 2010-01-15
Thanks everyone - working perfectly now.

One thing - do I need to use the binary mode when reading JPEGs on Ubuntu, or is it only for Windows?

EDIT: Hah, one other thing - when using JPEGs, it sometimes leaves a bit off the bottom. This seems to be hit-and-miss, and doesn't just happen with sockets - it's file i/o too.

---

### Post by wmcbrine on 2010-01-15
> **Tahakki said:**
> One thing - do I need to use the binary mode when reading JPEGs on Ubuntu, or is it only for Windows?You probably don't need it for Ubuntu, but you should use it anyway, just to keep things portable, and as a good habit to get in. It won't hurt anything, unless it seriously pains you to type ", 'b'". :)

> *EDIT: Hah, one other thing - when using JPEGs, it sometimes leaves a bit off the bottom. This seems to be hit-and-miss, and doesn't just happen with sockets - it's file i/o too.*If you're reading it in chunks, remember that the last chunk will usually be smaller than the buffer size, but it still needs to be flushed.

---

### Post by Tahakki on 2010-01-15
Forgot to flush, silly me.

All seems to be in working order now. Thanks, guys.

---


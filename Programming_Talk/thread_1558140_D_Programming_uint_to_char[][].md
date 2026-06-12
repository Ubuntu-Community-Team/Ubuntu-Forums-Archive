---
title: "D Programming uint to char[][]"
date: 2010-08-21
forum: Programming Talk
---

### Post by Sailor5 on 2010-08-21
Ahoy Sailors!

So first things first, I do mean D & not C. So I started learning the former two days ago (Not spending much time learning it however) & I'm currently stuck on text conversion, I'm using tango.

```
char[1024] buf;
auto dat = server.read(buf);
auto p = new Process (dat, null);
p.execute;
```Now with line two, We read whatever has been sent to us into the variable dat, This type becomes uint, However process needs (Correct me if I'm wrong) the variable to be in char[][] format. How would I go about doing such & getting this script working?

Thanks Bye!

---

### Post by geirha on 2010-08-22
I haven't tried programming anything in D, but I do know C a bit. And with my experience with C, I'd expect server.read(buf), to read the data into the variable buf, and **return** the number of bytes it read, which in your case is stored in the dat variable.

---

### Post by Sailor5 on 2010-08-22
> **geirha said:**
> I haven't tried programming anything in D, but I do know C a bit. And with my experience with C, I'd expect server.read(buf), to read the data into the variable buf, and **return** the number of bytes it read, which in your case is stored in the dat variable.

Ahoy! Thanks for replying! So your saying the received text is going it to the buf variable & not the dat one? I tried using the buf var with Process but I got this.
```
/opt/dmd/bin/dmd -w -c "Slave.d" (in directory: /home/zack/Desktop)
Compilation failed.
Slave.d(17): Error: constructor tango.sys.Process.Process.this called with argument types:
    (char[1024u],void*)
matches both:
    tango.sys.Process.Process.this(char[][]...)
and:
    tango.sys.Process.Process.this(char[],char[][char[]])

```
D has very poor documentation, I presume since it's not a very common language. Perhaps I will have to have a look at other languages.

---

### Post by geirha on 2010-08-22
Well, the error message is informal and tells you exactly what's wrong; you're giving arguments that are usable for two of Process's constructors.

Now, what exactly does server.read() put into buf? I'm guessing it puts a command to be parsed by a shell in there, in which case I'd try:
```
auto p = new Process(buf);
``` as shown in an example here: 
[http://www.dsource.org/projects/tango/docs/stable/tango.sys.Process.html](http://www.dsource.org/projects/tango/docs/stable/tango.sys.Process.html)

---


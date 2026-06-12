---
title: "Mono Compiling Projects To Package?"
date: 2011-04-17
forum: Programming Talk
---

### Post by MATTtheSEAHAWK on 2011-04-17
I got Mono-Develop 2.4 installed and setup on my computer now (Ubuntu 11.04) and I am brand new to Ubuntu and I was wondering how I could get mono to compile to something that I could use on Ubuntu and not an exe.  I am sorry if this sounds newbish but I am new to Ubuntu.

---

### Post by cgroza on 2011-04-17
That exe is not actually an exe. That is compiled byte code. You can use it on ubuntu with no problem.

---

### Post by MATTtheSEAHAWK on 2011-04-17
I'm sorry.  I'm brand new to this but how do I run it, I keep getting an archive error.  Do I have to change the file extension or something?

---

### Post by cgroza on 2011-04-17
> **MATTtheSEAHAWK said:**
> I'm sorry.  I'm brand new to this but how do I run it, I keep getting an archive error.  Do I have to change the file extension or something?
You set it executable and then open a terminal, cd to the file, and then ./file.exe.

---

### Post by MATTtheSEAHAWK on 2011-04-17
I found something even better.  I just created a launcher for it.  Solved :D

---

### Post by cgroza on 2011-04-17
> **MATTtheSEAHAWK said:**
> I found something even better.  I just created a launcher for it.  Solved :D
Nice, it is just some people like the terminal better.
Also, please mark the thread as solved.

---

### Post by directhex on 2011-04-18
> **cgroza said:**
> You set it executable and then open a terminal, cd to the file, and then ./file.exe.

You shouldn't rely on binfmt to execute .NET stuff, since there's no guarantee that it's available on every distro, or even installed on Ubuntu. Using "mono file.exe" is more reliable.

---

### Post by cgroza on 2011-04-18
> **directhex said:**
> You shouldn't rely on binfmt to execute .NET stuff, since there's no guarantee that it's available on every distro, or even installed on Ubuntu. Using "mono file.exe" is more reliable.
Sorry, I just remember that is how I did it when I was testing C+, I really do not code in it.

---


---
title: "Nano configuration"
date: 2014-03-02
forum: New to Ubuntu
---

### Post by GJ86 on 2014-03-02
Can someone please help me to configure Nano for programming in C++?
In the tutorial Jumping into C++ it is said that you have to configure the nanorc file but I can't get it right by no means.

---

### Post by vasa1 on 2014-03-02
**/etc/nanorc** and I think you can copy that over to /home as well (but I'm not sure).

If you provide the link to the tutorial someone maybe able to see what it says and suggest something.

---

### Post by GJ86 on 2014-03-02
I download it from a torrent. Here is what it says:

Configuring Nano

In order to take advantage of some features of nano, you will need to set up a nano configuration file.
The configuration file for nano is called .nanorsc and like most Linux configuration files, your user-
specific configuration resides in your home directory (~/.nanorc).
If this file already exists, you can simply edit it&#8212;otherwise, you should create it. (If you have no
experience at all using text editors on Linux, you can use nano to do this configuration&#8212;read below if
you need help with the basics of nano!)
To configure nano properly, use the sample .nanorc file that comes with this book. It will provide you
will nice syntax highlighting and auto-indentation, which will make editing source code much easier.

---

### Post by Lars Noodén on 2014-03-02
Then you could edit the file like this:

```

nano -w ~/.nanorc

```

That will create the file if it does not already exist.  The changes you make there will take effect next time you start nano.

---

### Post by oldos2er on 2014-03-02
You need to put ```
C/C++ 
include "/usr/share/nano/c.nanorc"
``` in ~/.nanorc

---

### Post by whitesmith on 2014-03-02
> **GJ86 said:**
> Can someone please help me to configure Nano for programming in C++?
In the tutorial Jumping into C++ it is said that you have to configure the nanorc file but I can't get it right by no means.Nano is a masochistic choice for C++ projects, "Hello, world!" excluded. Your classes will be disjointed; identifier names will not automagically identify type information; and, well, I could go on and on. Why put yourself through all this pain when other editors do a way better job? SlickEdit comes to mind. Yes, it's expensive ($300 a seat). Yes, the learning curve is steepish but it's a dream come true for serious work. Nano is fast and free and right there on your hard drive -- but  unsuitable except for trivial projects. If you're determined to keep everything FOSS, forget SlickEdit and look into vi, vim or emacs. In the end you'll be far better off. I realize editors evoke religious attitudes and sincerely hope everyone realizes I'm just offering personal opinion based on years of coding. Good luck in all your endeavors!

---


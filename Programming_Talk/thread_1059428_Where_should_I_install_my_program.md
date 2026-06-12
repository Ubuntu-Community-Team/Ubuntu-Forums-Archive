---
title: "Where should I install my program?"
date: 2009-02-03
forum: Programming Talk
---

### Post by JordyD on 2009-02-03
I've created a relatively simple project, which I want to share with a fellow developer. We are not sending it to the repositories or packaging it yet, but in order to show it to him, and for it to work, I want to put it in a place where I know it will work without any modification of the source code. Somebody told me /var/opt, but they have not touched anything on the programming side of Linux in a while, and I noticed that on all my Linux boxes, this folder was suspiciously barren. My second idea was /bin, but it looks like it's reserved for basic system tools.

So my question is, where should place this program?

---

### Post by jimi_hendrix on 2009-02-03
somewhere in your $PATH

---

### Post by JordyD on 2009-02-03
> **jimi_hendrix said:**
> somewhere in your $PATH

But where are programs *usually* stored? Would /usr/bin be a good location?

Thanks,
Jordy

---

### Post by jimi_hendrix on 2009-02-03
easy way to find out (i am not on linux unfortunetly) pick a program, use a command like find to look for it, done!

---

### Post by lloyd_b on 2009-02-03
I would strongly advise NOT putting it in /usr/bin - there's too much stuff in there already.

How about "/usr/local/bin"?  This is intended for programs that are local to the machine (as opposed to part of a standard install), and it should already be in the default PATH...

Lloyd B.

---

### Post by JordyD on 2009-02-03
> **lloyd_b said:**
> How about "/usr/local/bin"?

Okay, I guess I'll be putting it there, unless anybody objects.

Thanks,
Jordy

---

### Post by jespdj on 2009-02-04
Have a look at [Unix Filesystem Hierarchy Standard](http://www.pathname.com/fhs/pub/fhs-2.3.html) and [Linux Standard Base](http://en.wikipedia.org/wiki/Linux_Standard_Base).

There are probably also rules specific to Ubuntu or Debian about where programs and supporting data files should be installed, you'd have to learn more about packaging for Ubuntu to understand what's the best place to put your program.

---

### Post by nvteighen on 2009-02-04
In Debian and Ubuntu, the idea seems to be the following:

1. APT installed programs go to /usr/bin.
2. Programs manually installed go to /usr/local/bin.

---

### Post by JordyD on 2009-02-04
Thanks everyone for the input. (I wouldn't even have to post that if they had kept the thanking button.)

---

### Post by monkeyking on 2009-02-04
I can understand your question quite well.
I think the most linux distros are a mix of many different standards.
I think the /usr/local originated from the bsd.

What I normally do is to install in /opt
This is mainly because I'm lazy and this saves me some time typing in the path :)

I however normally make a symbolic link from /usr/bin, so I don't have to keep track of different path.

The trick is to be consistent, so next time you install a program,
you should pick the same folder.

---


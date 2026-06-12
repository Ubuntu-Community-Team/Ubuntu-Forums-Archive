---
title: "Lubuntu"
date: 2016-10-08
forum: Packaging and Compiling Programs
---

### Post by srpronto on 2016-10-08
Just installed Lubuntu and i can't compile Java on Geany. "/bin/sh: 1: javac: not found" What can i do?

---

### Post by TheFu on 2016-10-08
Install java and all the java dependencies?  Geany is an editor. If you want compilers, debuggers, symbol xref - those come from other packages.

If you open a terminal and type **javac** ... what happens? Fix that.

---

### Post by srpronto on 2016-10-08
I'm very new to Linux in general.Could i get any help? I went to the Aplication Center (im Portuguese so i'm trying to translate it, its the place where apparently we get programs), i searched 'Java', i installed the first thing that came across (translated is something like 'Ambient openJDK java 8') but the error still appears :/

---

### Post by srpronto on 2016-10-08
Sorry for my stupidity. I went shearch a little bit more and ended on a video stating that i should "run" this commands:
$ sudo add-apt-repository ppa:webupd8team/java
$ sudo apt-get update
$ sudo apt-get install oracle-java8-installer

Now it works, thanks anyway.

---

### Post by TheFu on 2016-10-08
> **srpronto said:**
> I'm very new to Linux in general.Could i get any help? I went to the Aplication Center (im Portuguese so i'm trying to translate it, its the place where apparently we get programs), i searched 'Java', i installed the first thing that came across (translated is something like 'Ambient openJDK java 8') but the error still appears :/

Programmers need to use a different package manager (the English name is "Software Center", but that isn't important), not the one designed for end users (which hides all the programming libraries).  Lubuntu has NOTHING to do with this issue. The title will limit who will look at this thread.  **Need Help Compiling Java** would be a better title.  So, you'll want to get comfortable with apt, apt-get, aptitude, synaptic ... those all don't hide programming libraries.  Doesn't matter which you use.

It is frowned upon to provide a link that google would find, but here: 
[https://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html](https://docs.oracle.com/javase/tutorial/getStarted/cupojava/unix.html)  Also, look for introductory Java training on youtube.

From a software development standpoint, Linux is just like Unix. Nothing very different at all, so any Unix tutorials should apply with slight changes for the Linux library names.

I should also point out that I haven't touched Java in about 5 yrs and before that back around 1995-ish.

Also, if you are really new to Unix systems, it would be smart to learn about the OS before trying to create programs for it.  As a programmer, you'll be expected to understand things that end-users don't need to always know.

BTW, nothing you've said is stupid. We were all new at some point.  Be very careful adding PPAs to the system. This is giving those people root access, so you really need to trust them.  I don't know how trustworthy webupd8team is. I don't know if they are not trustworthy either.  For programming libraries, it is best to either stay within the Canonical repositories OR go directly to Oracle's version.  Any programs created are only as trustworthy as the tools/libraries used to make them.

---

### Post by TheFu on 2016-10-08
I would think you'd want to be very careful mixing the openjdk and Oracle's JDK on the same system.  I would remove the 1 you aren't using.  Also, I updated my previous post.

---


---
title: "List of what I should do"
date: 2006-09-25
forum: Programming Talk
---

### Post by xvillix on 2006-09-25
Hey,  started using Ubuntu a few days ago, and I have reinstalled it 5 times now. I can't get things to work, like ./configure and a bunch of other things. Could someone give me a list of the things I need to do before I "start" using Ubuntu?

Like:
sudo apt-get build-essential

thank you

---

### Post by wieman01 on 2006-09-25
I don't want to be smart but the first thing you should do is post your stuff in the right section. :-) "Programming Talk" is a bit misleading...

---

### Post by Jessehk on 2006-09-25
Without providing more information on what problems you are experiencing, it is impossible to provide useful information to you. Despite what you may think, we are unable to read your mind.

That said, as a general bit of advice, read some of the documentation at

```

System->Help->System Documentation

```

---

### Post by maubp on 2006-09-26
> **xvillix said:**
> ... I can't get things to work, like ./configure and a bunch of other things. Could someone give me a list of the things I need to do before I "start" using Ubuntu?

Like:
sudo apt-get build-essential
I'm guessing you are trying to compile and install some third party software from source?

In which case, usually you must:

(a) install the appropriate compilers, at least:

sudo apt-get build-essential

(b) unzip/untar the software archive

(c) At a command prompt where you unzipped the new code,

./configure

(d) If this prints messages about being unable to find things like for example "gawk" or "check" or some libraries then install them:

sudo apt-get gawk check ...

Note that if you have a library installed, but want to compile a program that uses it you also need to install the library-dev package as well.

(c) Assuming that the ./configure worked, compile with:

make

(d) Most software will have some built in tests:

make check

(e) If this is all fine, install:

sudo make install

NOTE - These are generic instructions, you should read the documentation that comes with whatever program you are trying to install!

As the other posters have said, your "question" is too vague to answer properly.

---

### Post by xvillix on 2006-09-26
thank you, it was something like that I needed. And the help file was also good reading. Linux is a whole new world;)

---


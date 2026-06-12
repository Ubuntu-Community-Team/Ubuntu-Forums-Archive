---
title: "Where can I download all of the packages that are supposed to come with ubuntu"
date: 2013-06-24
forum: New to Ubuntu
---

### Post by marcinx27 on 2013-06-24
I downloaded Ubuntu on my own machine a while ago, and my school uses ubuntu in the CS labs.  I have a research job here and my professor updated the machine I use to 12.04, but he did not download the packages that typically come with the OS.  I was wondering if anyone knew of a link or a specific thing in the Software Center where I could download all of the packages that are supposed to be here (so I have compilers and emacs and what not).

---

### Post by grcastleton on 2013-06-24
You might try 
```
sudo apt-get install build-essential

```in a terminal. That will probably cover most of what you need.

---

### Post by marcinx27 on 2013-06-24
Thanks!

---

### Post by Paqman on 2013-06-24
> **grcastleton said:**
> You might try 
```
sudo apt-get install build-essential

```in a terminal. That will probably cover most of what you need.

If you're after compilers that package will sort you out, but it isn't normally part of the default install (and neither is emacs, you'll have to install that separately). 

If you really are after the default packages then installing (or reinstalling) [ubuntu-desktop]("apt:ubuntu-desktop") will do the job.

---


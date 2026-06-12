---
title: "gcc: installation problem, cannot exec `cc1plus': No such file or directory"
date: 2005-01-12
forum: Repositories &amp; Backports
---

### Post by kjkrum on 2005-01-12
I just tried to use gcc and got this error:

gcc: installation problem, cannot exec `cc1plus': No such file or directory

I am running Warty... gcc version Debian 1:3.3.4-9ubuntu5.

Google found some info about this problem in gcc 3.0.2, and it was supposedly fixed then.  Hmm...

Thanks for your time,
Krum

---

### Post by kjkrum on 2005-01-13
Solved:

# apt-get install g++

---

### Post by qrwe on 2006-12-03
Preferrable is:
# sudo apt-get install g++

Don't forget to be ready with your installation CD if asked for.

---


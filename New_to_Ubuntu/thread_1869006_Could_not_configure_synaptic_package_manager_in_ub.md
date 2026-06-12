---
title: "Could not configure synaptic package manager in ubuntu 11.04"
date: 2011-10-25
forum: New to Ubuntu
---

### Post by gunaprsd on 2011-10-25
I had configured ubuntu 11.04 for a proxy-authentication based setup. But now when i want to access internet normally, synaptic package manager displays:

E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_natty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.

I am new to ubuntu. what are the corresponding changes i have to make?

Thank you

---

### Post by computerandu on 2011-10-25
Do this:

sudo rm -rf /var/lib/apt/lists/* 
sudo apt-get update


Source: [http://www.computerandyou.net/2011/06/05/how-to-solve-ubuntu-update-error/](http://www.computerandyou.net/2011/06/05/how-to-solve-ubuntu-update-error/)

---


---
title: "Problem With Synaptic Package Manager"
date: 2005-02-28
forum: Repositories &amp; Backports
---

### Post by ajorb11 on 2005-02-28
When I start my Synaptic Package Manager I get the following Warning:

Couldn't stat source package list [http://archive.ununtu.com](http://archive.ununtu.com) warty/multiverse Packages (/var/lib/apt/lists/archive.ununtu.com_ununtu_dists_warty_multiverse_binary-i386_Packages) - stat (2 No such file or directory)

Any Solutions and help would be greatly Appreciated.  I am still a n00b, so please simplify your response if at all posible.  Thanks in advance.

---

### Post by p!=f on 2005-02-28
Did you try to update again? If you still experience this problem post your /etc/apt/sources.list here.

---

### Post by ajorb11 on 2005-03-01
This is my etc/apt/sources.list file.  I tried updating and got the same warning. 

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted 

 ## Uncomment the following two lines to fetch updated software from the network
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty multiverse

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

deb [http://archive.ununtu.com/ununtu](http://archive.ununtu.com/ununtu) warty multiverse

---

### Post by WW on 2005-03-01
Delete the last line that refers to "ununtu".  You already have multiverse in an earlier line.

---

### Post by ajorb11 on 2005-03-01
that worked.  Thanks a bunch.

---


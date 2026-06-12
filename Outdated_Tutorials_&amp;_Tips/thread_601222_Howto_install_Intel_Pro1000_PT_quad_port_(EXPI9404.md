---
title: "Howto install Intel Pro/1000 PT quad port (EXPI9404PTL)"
date: 2007-11-03
forum: Outdated Tutorials &amp; Tips
---

### Post by geforce123 on 2007-11-03
So you've got a brand new  Intel Pro/1000 PT quad port (EXPI9404PTL)?

([http://support.intel.com/support/network/adapter/1000ptquad/](http://support.intel.com/support/network/adapter/1000ptquad/))

If you're as lucky as me, your system probably did not recognized the card.

Here is a quick howto make those cards work:

1: Download the Intel's e1000 driver. 

```
wget http://downloadmirror.intel.com/9180/eng/e1000-7.6.9.tar.gz
```

and extract it:
```
tar -xzf e1000-7.6.9.tar.gz
```

2: install needed applications:

```
apt-get install make
apt-get install linux-headers-<KERNEL VERSION>*** OR directly:***
apt-get install linux-headers-`uname -r`
apt-get install gcc
```
Replace <KERNEL VERSION> by your kernel version, you can get it from the output of uname -r
for example mine is:
~# uname -r 2.6.15-26-amd64-server
So i ran the command:
apt-get install linux-headers-2.6.15-26-amd64-server

then go in the source's directory:

```
cd e1000-7.6.9/src
```

Now you can build & install the new and working driver!

```
make install
```

Then reload the module; BE PATIENT, took my server (8 cores Intel 64 bits) more than 10 sec to do this operation:

```
rmmod e1000; modprobe e1000
```

You can always check if the new module is properly loaded:

```
lsmod | grep "e1000"
```

---

### Post by Saarbruecken on 2008-10-13
Dude, you made my day! I was looking for a solution for several weeks and today I find this thread. Thank you for that awesome how-to. :)

---

### Post by geforce123 on 2008-12-29
I'm glad to hear it :)

---

### Post by wcdeich4 on 2010-01-16
Hi!!!!!!!!  I have a dv6000t notebook w/ an Intel PRO/1000 PL Network Connection (NIC card).  Any idea where to find a driver????????

---

### Post by ulao on 2010-02-05
thx this was helpful! - Had to get the latest drivers, the version I have, had a bad make file. If you get missing config.h, make sure you download the latest drivers.

---


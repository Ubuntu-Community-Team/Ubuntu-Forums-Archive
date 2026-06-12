---
title: "What do I need to compile a kernel module?"
date: 2007-01-17
forum: Programming Talk
---

### Post by bill.albertson on 2007-01-17
I have been searching for most of today for a howto or some kind of complete and sane advice on how to compile a kernel module for Ubuntu.  This should presume the following:
[LIST]
[*]A basic, clean install of Ubuntu.
[*]Access to synaptic.
[*]The user is not an idiot, just unfamiliar with Linux.
[/LIST]
What packages should be installed?
What symlinks and directories need to be created by hand?
If existing docs SPECIFIC to this query exist, where are they? (some obscure and winding series of more than 50 posts across 3 or more threads on the vagaries of hand compiling blowfish encryption options into a theramin player kernel module is NOT specific- something really short on compiling module foo for kernel bar IS germaine) ](*,) 
What version of gcc should be used, and how would I find out which one is specific to whatever version of Ubuntu I am running?
Anything else on the generic compilation of kernel modules so I can write a howto if one is not posted.  Thank you.

---

### Post by po0f on 2007-01-18
bill.albertson,

All you should need is as far as packages go are [build-essential](http://packages.ubuntu.com/edgy/devel/build-essential) and [linux-headers](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=linux-headers&searchon=names&subword=1&version=edgy&release=all) that match your running kernel version (or whatever kernel you want to build the module for):
```
[FONT="Courier New"]$ sudo aptitude update
$ sudo aptitude install build-essential linux-headers-`uname -r`[/FONT]
```

`uname -r` will output a short string describing the kernel's version.  Combined with the above command, it will install kernel headers specific to the current running kernel.  If you want to build against a specific kernel *not* matching the running kernel, install those headers instead.  As for which version of gcc to use, you have to use the version that built the kernel; build-essential will pull in the required version.

Beyond this, it is up to how good the Makefile that is distributed with whatever module you are trying to compile is.

If you have any problems, post back.

---


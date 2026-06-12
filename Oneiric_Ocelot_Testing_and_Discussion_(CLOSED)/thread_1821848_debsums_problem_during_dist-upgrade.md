---
title: "debsums problem during dist-upgrade"
date: 2011-08-09
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by doctordruidphd on 2011-08-09
System: kubuntu-11.10,64-bit

Problem: At the end of the doing a dist-upgrade, the upgrade hangs for several minutes, and then I get an error message like this:

debsums: invalid package name 'binutils'
debsums: invalid package name 'gcj-4.5-jre'

I have tried reinstalling debsums, doing a **sudo debsums_init** and a few other tricks with debsums, to no avail. As I understand it, debsums is responsible for running md5sum checks on incoming packages, and keeping a record of those results. Somehow that has gotten messed up. Running **sudo debsums --list-missing** shows several packages with problems, and I can understand that because I have installed some software from packages outside the repositories. But binutils? I have tried reinstalling it, but this does not change the error message.

The only thing I can do to make upgrading work is move /usr/bin/debsums out of the way (mv debsums debsumsNOT), but of course this is leaving a security hole. 

Anyone run into this? The system is a natty system that has been dist-upgraded; natty works fine. "Clean install" is not an option. I may need to re-dist-upgrade when rc comes out, but I would like to know what the problem is and how to fix it.

---

### Post by lucazade on 2011-08-10
have you seen this bug? probably related.
[https://bugs.launchpad.net/ubuntu/+source/debsums/+bug/809924](https://bugs.launchpad.net/ubuntu/+source/debsums/+bug/809924)

---

### Post by doctordruidphd on 2011-08-10
Yep, same issue. Didn't come up when I searched for it.
Thanks.

---


---
title: "Linux from scratch help"
date: 2011-03-18
forum: Programming Talk
---

### Post by user333 on 2011-03-18
I'm not sure if this is the correct category, so please move it if this isn't right!

I'm attempting to build a LFS for my first time, and I finished downloading all the sources, but I'm having trouble setting up the partitions right. When I restart the computer, everything is gone, but when I start over again, remnants of my last session are there messing things up. I'm on the "Constructing a Temporary System" step.

 Could someone tell me how to set up the host? 

I am using virtualbox 4, and ubuntu 10.04 32 bit as a host. (I could use an old computer, but I thought it would be convenient and safer to go virtual the first time.)

---

### Post by GregBrannon on 2011-03-18
Right category?  Wrong forum.  Is Linux From Scratch an Ubuntu distribution?  Don't think so.  While someone here may help you, it seems you'd have better luck in a general Linux forum or in a forum specific to Linux From Scratch.

---

### Post by user333 on 2011-03-18
I see your point, but I asked here because I am having trouble with partitions and bash in Ubuntu.

I'll go find another forum I guess...

---

### Post by unknownPoster on 2011-03-19
> **GregBrannon said:**
> Right category?  Wrong forum.  Is Linux From Scratch an Ubuntu distribution?  Don't think so.  While someone here may help you, it seems you'd have better luck in a general Linux forum or in a forum specific to Linux From Scratch.

This forum is hardly Ubuntu only. Quit discouraging people from asking questions.

---

### Post by dwhitney67 on 2011-03-19
> **user333 said:**
> I see your point, but I asked here because I am having trouble with partitions and bash in Ubuntu.

I'll go find another forum I guess...

The need for a separate partition is not required; well, at least that is what I found out when I built CLFS (Cross-Compiled LFS).

You will be required to mount some directories, but since the instructions call out that the "mount" command should be used, I do not quite understand why you think these actions would be preserved if you perform a reboot of your system.  I'm not quite even sure why you did a reboot in the first place; it is unlikely that the LFS instructions called for it.

---

### Post by user333 on 2011-03-19
I didn't intentionally reboot, the machine crashed. 

Mostly my problem is from bash forgetting the environment variables, and the value of $LFS. 

So I don't need another partition at all? The instructions had a whole chapter on it. Or is it only for the host?

---

### Post by dwhitney67 on 2011-03-19
Just assume that your system will not be rebooted.

As for the LFS instructions, you have two choices... run them one by one (as indicated in the instructions) or create a shell script that performs them.

There is a good probability that going either way, you will err.  No problem... just start again.  Otherwise if you are feeling queazy, then perhaps you should just stick to a recognized Linux distro.

Seriously, there is no need to build Linux (from scratch) unless you are completely bored (or being paid to do so!).

---

### Post by dwhitney67 on 2011-03-20
Btw, in lieu of the partition, all you need to do is create a directory (on an existing partition with lots of space) where you will do the LFS work.  This same directory needs to contain the directory where you store the source packages needed to build LFS.

You may also need to create certain Linux-dependent directories within this newly created directory, and then mount them as appropriate.  The directories will survive a reboot, but the mounts will not.

I'm not that familiar with LFS, but with CLFS I eventually had to chroot to the top-level directory that was created.  Once there, I still had access to my source packages so that I could continue building.

Here's an example of the script I used to build the sub-directories within the top-level directory that I used to perform my work.
```

#!/bin/sh

#
# mnt-kernel-fs.sh
#

SRCDIR=${LFS}/sources
SCRIPTS=$SRCDIR/scripts

sh $SCRIPTS/verify.sh || exit 1

mkdir -pv ${LFS}/{dev,proc,sys}

mount -vt proc proc ${LFS}/proc
mount -vt sysfs sysfs ${LFS}/sys

if [ ! -c ${LFS}/dev/console ]; then mknod -m 600 ${LFS}/dev/console c 5 1; fi
if [ ! -c ${LFS}/dev/null ]; then mknod -m 666 ${LFS}/dev/null c 1 3; fi

mount -v -o bind /dev ${LFS}/dev

mount -f -vt tmpfs tmpfs ${LFS}/dev/shm
mount -f -vt devpts -o gid=4,mode=620 devpts ${LFS}/dev/pts

```
The variable LFS is an environment variable that is set to the path of the top-level directory; for example, /home/user/LFS.

---

### Post by user333 on 2011-03-20
Thank's for the tips! I guess if I'm using Virtualbox I can just pause the session when I'm tired. 

I'm mostly doing this to become very familiar with the "guts" of an operating system, so I still intend on doing it even if it is hard ;)

---

### Post by dwhitney67 on 2011-03-20
I apologize for omitting something earlier; the purpose of the separate partition is so that eventually, when you are done with building the LFS, you can boot into it.

When I built CLFS, my goal was to build an ISO image that I could burn to a CD-ROM, and subsequently boot from it.  You should consult with the LFS folks (in their userland) to see if you can achieve a similar goal.  After all, I think it would be cool to boot your home-made LFS distro as a virtual machine.

---


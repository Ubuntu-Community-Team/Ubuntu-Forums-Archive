---
title: "issue after update"
date: 2013-03-11
forum: New to Ubuntu
---

### Post by hogeybogey on 2013-03-11
Hi everyone x

I've been using Ubuntu for around 6 months now, love the look and the feel, and I'm very comfortable with my move away from MS.

However I haven't really stretched myself when I've had issues, a quick visit to the download centre has always done the trick up till now.

A couple of days ago I took a leap and updated Ubuntu itself, I thought I was upping to 12.10 but 'details' still tells me I'm running 12.04LTS, so maybe this is where my problem lies, but I really don't know and I'm feeling out of my depth.

Ever since my upgrade every function of the computer seems to be lagging, it's a stop/start kind of thing.

When I goto 'settings' and 'additional drivers' and activate a driver it seems to cure the issue for a while, but only for about half an hour or so.

At the moment I can plod along with a bit of word pro, but playing any sort of media is an impossibility.

I hope someone here can walk me thru this issue before I tear all my hair out.

With thanks
Hogey

---

### Post by deadflowr on 2013-03-11
Maybe I'm missing it, but could you describe the method you took to upgrade?

By default, LTS releases are set to only allow upgrades to the next LTS.
This needs to be changed in the software sources to allow upgrades to the next non-LTS release.
But let's find out what version your system currently is on shall we:
In a terminal:
```
cat /etc/lsb-release
```

From the sound of it, if you still have additional drivers in the system settings, then you are still using precise.

Also any info you could provide for the graphics card you are using would be helpful.
Again in a terminal:
```
lspci | grep VGA
```

Also:
```
uname -a
```
Which will give us the kernel version and system arch you are using.

When posting back, if copying and pasting, please you the code tags(it's the # symbol in the toolbar in the reply box)

---

### Post by hogeybogey on 2013-03-11
Thanks deadflowr, I think it's just possible you heard the sigh of relief when I got a reply :P

I didn't go fishing for the upgrade, it was an option offered on start up, but lets see if I can sort out this code thingy, – Terminal has alwaysscared the poop out of me tbh!

Right, so the firstcommand brings up this:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu12.04.2 LTS"

```

2nd command:

```
01:00.0 VGA compatiblecontroller: NVIDIA Corporation G92 [GeForce 9800 GT] (rev a2) 


```

3rd command

```
Linux chris-desktop3.2.0-38-generic-pae #61-Ubuntu SMP Tue Feb 19 12:39:51 UTC 2013 i686i686 i386 GNU/Linux 

```

So I hope I've done this right, and again thanks for the assistance it is truly appreciated

---

### Post by deadflowr on 2013-03-11
Okay, so what we do know is that you're system is fully up to date.

You are running precise 32-bit.

Your graphic card is nvidia 9800 gt.

Look at this wiki page on help getting the driver to work properly(hopefully)

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---


---
title: "HDD troubles, ideas to repair?"
date: 2013-06-21
forum: New to Ubuntu
---

### Post by ironic.demise on 2013-06-21
I'm having a hard drive problem (It's an external Seagate GoFlex Desk 2tb).

It's been having trouble copying files lately and after running a program called seatools, it apparantly has some bad sectors that when it tries to write/read it has serious trouble.

A while back I had a friend who had a similar problem but he ran a program which "reconfigured" the hard drive to ignore these sectors(and reduced the total capacity of the drive) and I was wondering if there was a similar program available in open source that could repair my hard-drive.

If I need to replace the hard drive, what's a reliable cheap way of doing so?
I was thinking of a cheap SATA drive and a cheap SATA caddy but I've had bad experience with getting SATA drives to work through USB or IDE in the past.

Thanks in advance, these forums are always so helpful.

---

### Post by Mark Phelps on 2013-06-21
While it's true you could block out the failed sectors, the fact that these are recent indicates the drive is probably failing -- and only going to get worse.

I had a drive last year go from this situation to totally useless in only a few days, so the sooner you can back it off to something else, the better.

As to "reliable cheap" drives, apart from problems I had last year with WD drives, my own experience is that they are about the same level of reliability.  Higher price goes for higher capacity and faster spin rates.  I tend to buy whatever Seagates are on sale locally in the capacity I like.

You can also do well shopping online.  I have local delivery problems, so I avoid that.

As to SATA drives, they come in SATA 1, 2, and 3 these days -- but buying a drive rated higher than your controller is a complete waste of time, as in, putting  a 6 GB/s SATA drive on a 3 GB/s controller is not going to make it perform any faster.

---

### Post by ironic.demise on 2013-06-21
I have everything backed up off of it already, I was just hoping there might be a way to save it.
It's had this problem more or less from day one, I thought perhaps it was from a bad batch and I thought I'd rather try and save it than throw it away but I know not to trust it.

I've heard a lot of bad things about seagate and WD but I never know what to make of them, seeing as I've had every seagate I've owned fail on me unexpectedly I'd like to at least try WD as I've never used one before but I've also heard getting any drive below $100 is likely to be awful quality.

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by ironic.demise on 2013-06-21
I will try this and get back with the results.

thanks for the advice, it's been a while since I've had to deal with a faulty drive.

Using "disks" in Ubuntu 13.04
Smart data says "Disk is ok, 3500 bad sectors"
short self-test "failed"
long self-test "failed

Using gsmartcontrol
Reallocated sector count: 224
Current pending sector count: Norm-ed Value:59. Worst:59. Threshold:0. Raw Value:3359


Looks like I've got a problem... I will try DBAN... Is there a way to do this without booting into it because It's an external?


Hmm... would a linux command purge work just as well?

---

### Post by ahallubuntu on 2013-06-21
~

---

### Post by ironic.demise on 2013-06-21
> **ahallubuntu said:**
> Actually, you CAN'T purge a drive you are booted from - you have to boot from some other drive anyway.  You could try a dd command to write zeros.  Be VERY CAREFUL you know exactly which device is your external drive:

```
sudo dd if=/dev/zero of=/dev/sdX bs=2048
```

and wait a long time - probably overnight.  If you use DBAN, at least you'll get a status indicator showing you an approximate time remaining.

(replace /dev/sdX with the actual drive device id like /dev/sdc or /dev/sdd or whatever yours is.  That drive will be ERASED so of course, don't use the ID for your normal booted hard drive!  If you aren't sure, do "sudo fdisk -l" to confirm which is the right device ID so you don't erase the wrong drive!!!)

Still - if you really have 3359 pending sectors, it's probably a waste of time in this case.  Zeroing a drive can sometimes clear a couple of pending sectors but not thousands.  Probably a dead drive.

(Are you sure it's not under warranty/eligible for replacement?)

Well, I'm not booting from this particular drive anyway, it was a backup hdd so I haven't lost anything on it.
It is under warranty with seagate but they require me to ship it to them and pay the shipping... I live in the UK so shipping with tracking to them in the US is going to be expensive... I'm really disappointed with how badly this drive is performing right now.


It would cost me £70 minimum to get it replaced, which is not that much cheaper than a new drive...
I guess I'm not buying from Seagate again!

---


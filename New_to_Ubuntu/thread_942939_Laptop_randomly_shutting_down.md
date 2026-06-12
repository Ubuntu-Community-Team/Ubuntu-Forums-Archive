---
title: "Laptop randomly shutting down"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by billgoldberg on 2008-10-09
I'll start by saying it's not a heating issue. Yes, I'm sure it's not.

This issue explained here by me must be related:

[http://ubuntuforums.org/showthread.php?t=939955](http://ubuntuforums.org/showthread.php?t=939955)

The issue:

Well just like the title says.

It was fine after the battery incident (not sure it was the battery now!).

Now all of the sudden the same thing is happening.

The computer turns off without warning after a few seconds/hours.

I presume it's hardware related?

The only things **possibly** useful in the log messages I found was this:

Oct 10 00:24:02 kaper kernel: [   59.454438] UDF-fs: No VRS found

which google told me was some kind of filesystem error.

--

The hardware was completely replaced a month of 4 ago by hp.

Anyone got some suggestion on troubleshooting this?

Edit: also possibly related. When this happened a few moments ago and I rebooted I got some x-server error saying the gdm couln't be started an got a tty1 screen.

It wouldn't accept my username or password. After resetting twice (and when it feeled like not shutting down) that error was fixed.

---

### Post by Big_Kahunaca on 2008-10-09
fsck?

---

### Post by billgoldberg on 2008-10-09
My /var/log/messages is going crazy with these:

Oct  9 03:02:26 kaper kernel: [ 5910.826958] VFS: busy inodes on changed media.

Could this be related as google tells me it's a cdrom thing? Still just putting it out here.

---

### Post by billgoldberg on 2008-10-09
> **Big_Kahunaca said:**
> fsck?

Meh. Maybe later.

I'll keep enjoying the running computer as I fear I might not be able to start it again.

---

### Post by tjwoosta on 2008-10-09
try disabling hibernate and the screensaver 

i had a similar problem on my laptop where it would periodically shutdown

it turned out that every time it tried to blank the screen, the laptop would reboot instead

so i disabled hibernate and screensaver and i havn't had a problem since

---

### Post by billgoldberg on 2008-10-09
> **tjwoosta said:**
> try disabling hibernate and the screensaver 

i had a similar problem on my laptop where it would periodically shutdown

it turned out that every time it tried to blank the screen, the laptop would reboot instead

so i disabled hibernate and screensaver and i havn't had a problem since

I don't hibernate.

While the screensaver is on, it happens while using the computer also so I don't think that's the problem.

---

### Post by billgoldberg on 2008-10-10
Anyone?

---


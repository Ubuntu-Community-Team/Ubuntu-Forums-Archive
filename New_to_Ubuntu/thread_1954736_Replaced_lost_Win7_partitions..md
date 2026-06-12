---
title: "Replaced lost Win7 partitions."
date: 2012-04-08
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-08
I am very new to Ubuntu, about 2 weeks into it.

I really screwed up by accident.

When installing 11.10 from a Live CD onto an 8 GB USB flash drive, the partitions on my HP desktop disappeared.

When booting up Ubuntu I got a low memory message showing only 28 MB available.

The Plop CD didn't even show the HD drive as a boot choice.

I thought that all was gone!

Steps to recover:

1>  Uninstalled Chromium to gain some memory.
2>  Installed testdisk in Ubuntu.
(To run testdisk I needed to launch it from a terminal:
  type testdisk)
3)  To find the lost partitions I had to run testdisk from root.
Type su -   to get root.
4) Run testdisk from root and you will see the partitions that were lost.
My drive had 3 partitions:  Boot, data, and HP recovery.
testdisk showed them as HD0, HD1, HD2

5>  I tried to boot Win7 from HD0 but there was no boot found.

6> Using Plop HD I chose to boot from the 3rd partition, the HP repair.

7>  HP repair fixed the boot sector in 30 seconds.

I am now using Win7 as I type.

I have no idea about what happened but I am a happy camper now.

I hope that no one else has to go through what I went through and I hope that my post will give a solution to the lost partition problem.




YMMV

---


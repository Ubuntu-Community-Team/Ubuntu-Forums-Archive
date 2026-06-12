---
title: "initramfs blocks"
date: 2008-10-25
forum: New to Ubuntu
---

### Post by ginestre on 2008-10-25
Using the 8.04 Hardy live cd, the pc fails to complete boot at the following message:

(initramfs) [ 104.668595] ata3.00: revalidation failed  (errno=-5)
[  139.802588] ata3.00: revalidation failed (errno=-5)

It boots into windows OK.

What should I do? Any ideas?

TIA

---

### Post by ddrichardson on 2008-10-25
There is a bug report on this issue, which has a workaround [here]("https://bugs.launchpad.net/ubuntu/+bug/104581/comments/25"), which is fairly involved. There is a very good chance that this is as a result of a [firmware issue]("https://bugs.launchpad.net/linux/+bug/75295/comments/97") and as you have Windows I would first update to the latest BIOS before anything else.

---

### Post by ginestre on 2008-10-29
Help! I'm totally out of my depth here. I looked at the items you pointed me at, but they all seem to describe something else- though I'm not sure as I don't really understand. In any case, I don't know how to apply the various fixes that are suggested in the launchpad items you pointed me at.

However.... those bug reports seem to be about problems with laptop DVD drive, and I think -maybe wrongly - that my problem relates to the hard disk; and anyway it's not a laptop (if that's relevant). So is it the same?

Oddly enough, if I leave the PC alone for a few days, ad then boot into Ubuntu from a live CD, the first time (but only the first) it works. I have just done this, and at the moment have a working system from the live CD but which *can't* see the HD anywhere. So the Install option fails at the partitioner. 

I am still stuck, and would be very grateful for clear pointers. This particular PC is one of five (I thought very similar) computers, and the other four have been happily running for over a year. But I just can't sort this one.

---

### Post by ddrichardson on 2008-10-29
First, if you have Windows available, update the mainboard to the latest BIOS (as you have other machines of the same type that aren't problematic, check their BIOS versions against the problem one).

Second, boot the Live CD using the acpi=off noapic options, which you can add by highlighting "Start or install" pressing F6 and adding them to the end of the kernel line.

---


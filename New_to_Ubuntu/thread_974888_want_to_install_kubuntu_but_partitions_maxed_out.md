---
title: "want to install kubuntu but partitions maxed out?"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by myddewji13 on 2008-11-07
hi,
I currently have 4 partitions on my computer: ubuntu, swap, recovery, and vista...I want to install kubuntu but is there a limit to the number of partitions I can have? Also is it possible to install without a new partition ...I'm talking abt a full install not just a ode desktop on top of ubuntu...also would grub configure itself?

---

### Post by Yuki_Nagato on 2008-11-07
You can try to have more than 4 primary partitions.  Modern computers "should" be able to do it.  Just set up the new partition as "Primary" and hope for the best.

I would not drop a new installation on top of a used partition and expect both to work.

If the newest operating system is installed to its own partition, GRUB will find everything, including the recovery partition, and set it up to boot for you.

---

### Post by myddewji13 on 2008-11-07
thanks...I'll try it tonight and post to let ppl noe how it went...

---

### Post by ugm6hr on 2008-11-08
You can have 8 partitions per HD - 4 primary, 4 extended.

Depending on wether your existing partitions are all primary or not, this may be possible.

When you install - you can use the same swap partition (use manual install option).

---

### Post by teaker1s on 2008-11-08
it is possible to install another desktop without installing os again. for instance I have kubuntu/ubuntu and xubuntu desktops selectable as session at login.

---

### Post by myddewji13 on 2008-11-08
OK...i know that you can have multiple desktops...but i wanted the full os experience... (dont like network manager taking over etc..)..anyway.. for some reason I couldnt resize my ubuntu partition... so I deleted my swap partition and made a swap file and then resized my vista partition (using vista) and installed kubuntu on and 8gb partition with no swap...so now 2 questions:

1)Can I use the swap file on my ubuntu partition as swap for my kubuntu install? (if so how)

2)Is it possible to run programs off of the ubuntu partition (as opposed to installing everything? (if so how...i dont know a lot...i click on launcher...it opens..thats all i know)

---


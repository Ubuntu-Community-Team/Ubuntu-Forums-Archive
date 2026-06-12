---
title: "After trying to install 8.04 no booting possible even from the LIVE CD"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by Djalmahal on 2008-04-26
Hi,

i used Gutsy Gibbon for 3 months, upgraded to 8.04, and ended up with some broken dependencies and other small problems so I decided to do a fresh install of Hardy Heron.


I had a dual boot (7.10 and Windows XP) and after booting from the 8.04 LIVE CD I got into the LIVE session and started the Install, opted for using the whole hard drive (wiping out the partitioning). In the process of formatting an error message came up telling me that the CD or my hard drive were unreadable and it hung up. I never before had a problem with my hard drive or the CD drive). Upon trying to boot from the same CD I get the message

GRUB Loading stage 1.5
Grub loading, please wait
Error 15

and that's it.
I burned another CD on the MAC, it accepted it once, the Ubuntu Logo came up and then I got lots of lines of errors (unfortunately I didn't write it down but it had to do with SD0 (that's my hard drive right?) and problems.

Since then upon booting from the LIVE CD I get the same message "Error 15". IF I try to boot without forcing the BIOS to boot from CD I get the same message.

So in fact, I can't get ANYWHERE at the moment. I'm downloading another 8.04 LIVE CD in case the previous download was damaged, but I don't expect that to be any better.

So, what to do? Should I try to first format the hard drive with some other Linux Live CD.
Or is there another way to boot up again?

Thanks for your input
Andreas

---

### Post by Joeb454 on 2008-04-26
You need to boot from the Live CD to install the system :)

---

### Post by Djalmahal on 2008-04-26
Hi Joeb545,

as I said, it doesn't boot from the LIVE CD (that it accepted once before and booted to the LIVE Session, followed by a unfinished installation), so booting from the LIVE CD is at tis point not an option.

---

### Post by Djalmahal on 2008-04-26
So,

I downloaded the GParted LIVE CD in the hope that I could boot from  that one, format the hard drive and retry the 8.04 Install but again, upon asking the system to boot from the GParted LIVE CD it returns with


Error 15


So, as of now, there seems to be no way to boot for me from a CD or the hard drive, the broken 8.04 install seemed to have seriously messed up my system to a point where I can't do anything.

This is quite serious.

So, please Geeks, help me out, something went totally wrong, my computer is unbootable.

Andreas

---

### Post by Djalmahal on 2008-04-26
So,

I downloaded the GParted LIVE CD in the hope that I could boot from  that one, format the hard drive and retry the 8.04 Install but again, upon asking the system to boot from the GParted LIVE CD it returns with


Error 15


So, as of now, there seems to be no way to boot for me from a CD or the hard drive, the broken 8.04 install seemed to have seriously messed up my system to a point where I can't do anything.

This is quite serious.

So, please Geeks, help me out, something went totally wrong, my computer is unbootable, I'm writing this from another computer.

Andreas

---

### Post by Joeb454 on 2008-04-26
Calling us geeks my not be the best option :p

And do you know if it's possible to boot from the Alternate CD. You may also want to look for the Super GRUB Disk

---

### Post by Djalmahal on 2008-04-26
Ok, i called out for geeks as this seems to be a fundamental problem (after all I can't access anything, i.e. can't modify GRUB files and such) and the text in the WUBI Guide doesn't help.


I'll download the Super GRUB Disk, and then see if my computer accepts this CD.


What should i do once it runs?

Andreas

---

### Post by Djalmahal on 2008-04-26
I don't have the alternate CD, my connection is slow, so that'll take some 6-8 hours to get it.

---

### Post by Djalmahal on 2008-04-26
So,

the Super Grub Disk boots, I told it to restore the original Linux boot, but as the 8.04 installer already started to format the hard drive I get error 15 nevertheless. Also, the LIVE cd still doesn't boot.


I don't know what to do
Andreas

---


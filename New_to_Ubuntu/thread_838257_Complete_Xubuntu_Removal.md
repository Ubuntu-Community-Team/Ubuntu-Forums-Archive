---
title: "Complete Xubuntu Removal"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by hianddry on 2008-06-23
Hello All
I found I "helpfully" had had Xubuntu 7.10 installed as a dual boot with Win 98SE on a recent replacement hard disk within my very elderly laptop.

Since then I have had repeated warning messages appear on booting windows, also multiple system glitches.But I have never used Xubuntu and believed neither OS would effect the other.

To, hopefully,rectify this current situation, I need to remove both OS's etc, reformat the entire disk, and start the complete re installations again.

As an obviously utter Xubuntu novice, I cannot find any information on this subject - either in a book or the forums - that covers Xubuntu, and its partitions removal - that I can understand and which is applicable to my situation

I should be very grateful for any [simple] advice

---

### Post by forestpixie on 2008-06-23
You shouldn't need to remove any partitions if all you are going to do is reinstall.

You can post how you're partitions are set up so that you canget more specific advice, open a terminal - I'm not sure which menu it is in for xubuntu - run this command from it

```
sudo fdisk -l
``` (that is a lowercase L)

you will be asked for your password when you run it, it will be invisible - it is supposed to be.

If you know what errors you are getting it might be possible to sort it without reinstalling your os's

---

### Post by Zulu-Zeffir on 2008-06-23
If your performing a clean install why not just install windows
and leave the desired amount of disk space allocated for your ubuntu installation?  

If you simply want to reinstall one or the other you really don't need any other tools as long as you pay attention to your partition options when installing ubuntu again.  But be sure to install ubuntu second so it adds necessary bootloader information in order to dual boot.

I would try to find your problem before resorting to a new install by following forestpixie's instructions first.

---

### Post by hianddry on 2008-06-23
Thank you both for replying.
Unfortunately I know nothing of the Ubuntu terminology etc so I'm stuck at present.
The disc partitions are c= 29Gb; d= 24;e= 16; f= 18; Xubuntu =10+ 5 swap 

The 2 main Windows warning messages are

Good space map corrupted  and

The save to disc utility is also corrupt.
I am still awaiting the laptop manufacturer's instructions on the install method BUT it appears that the whole disc has to be empty and formatted before this is performed.

Additionaly, I am subject to multiple freezing per [short] session - whatever the programme and also a general but substantial slowing down of the laptop. 

I trust this may help explain my original message and its apparent logic any simple suggestions would be welcome
Thanks again

---


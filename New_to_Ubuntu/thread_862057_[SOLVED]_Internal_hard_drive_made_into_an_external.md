---
title: "[SOLVED] Internal hard drive made into an external hard drive now saying corrupted"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by Berean on 2008-07-17
Hi,
I've just made an 80GB internal hard drive (with Ubuntu and XP partitioned on it) into an external hard drive, using a cheap casing I've bought.  I've installed the drive in the casing correctly, brought it to work, and now find that on the large network (running XP) that it says the disk can't be read as corrupted.  Does this mean that as I have a dual boot system on the external hard drive that I can't look into the folders, or does it actually mean that the drive is corrupted?  I can't boot from the drive on the network, but can do when I get home in a couple of days.  If it really is likely to be corrupted I'll format it and give it to a friend for a cheap backup disk, but if it's just because I can't read from it I'll wait until I get home and try booting.  Your advice is most welcome.

---

### Post by ibuclaw on 2008-07-17
Is this Windows, or GRUB that is saying the device is corrupted?

If it is Windows, then it may just be the NTFS partition side of the hard-drive...

If it is GRUB, it could be the whole disk...

Regards
Iain

---

### Post by Berean on 2008-07-17
I'm in XP at the moment - and can use nothing else at present, dut to work - so when I try to look into the external disk Windows says the disk is corrupted.  Any ideas?  Thanks,

---

### Post by Dedoimedo on 2008-07-17
Hi,

I'd first establish if the disk is truly corrupted or not. Place it back into a tower and see if it comes up.

If it's corrupted, you have several choices, including format.

If it's not corrupted, then I suggest you verify that the drive is available to all network resources. Windows XP requires a registry hack to make a drive connected as external drive to one of the machines be available to all other network machines.

Don't remember right now, but can look into it, if you like.

Dedoimedo

---

### Post by Berean on 2008-07-17
Thanks to both of you.  I'll wait until I get back to my Ubuntu and then see then if it's corrupted or not.  If it is then I'll format it and use it simply as an external drive.  Thanks for the advice.

---

### Post by Berean on 2008-07-18
I'm back at home earlier than I imagined.  My external hard drive boots beautifully into Ubuntu, but XP doesn't (no loss there then!).  I now have Ubuntu on my laptop (or my wife's to be more specific) and an external hard drive that I can boot from to enable me to carry Hardy wherever I go.  Great! :)

---


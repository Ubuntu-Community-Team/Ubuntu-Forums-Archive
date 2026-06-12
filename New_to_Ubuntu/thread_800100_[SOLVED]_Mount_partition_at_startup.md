---
title: "[SOLVED] Mount partition at startup"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by dinostabOMG on 2008-05-19
I have an NTFS partition for Windows XP x64 and an ext3 partition for Gutsy 64-bit. I tend to use the NTFS partition for files I need to share between the operating systems because I found it easier to get Ubuntu to deal with NTFS than the other way around (big surprise). One little annoyance still confounds me, though:

When I start up in Ubuntu, I can't access the NTFS partition. If I open Nautilus, on the side under places is listed "100GB volume" or something like that. When I double click it, I get the security prompt for my password. When I enter it, I can access the partition. It then shows up in Nautilus' Places as "disk". I would like to automate this on startup - is that possible?

---

### Post by Majorix on 2008-05-19
This problem stroke me in the past too, it would ask me for my Linux root password to mount&open a Windows partition.

You could try adding a line to your /etc/fstab to have the partition mount automatically with each boot though.

---

### Post by mikewhatever on 2008-05-19
Try this gude [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows).

I think it's very easy to mess your Windows system with such a setup, so be careful.

---

### Post by stchman on 2008-05-19
> **dinostabOMG said:**
> I have an NTFS partition for Windows XP x64 and an ext3 partition for Gutsy 64-bit. I tend to use the NTFS partition for files I need to share between the operating systems because I found it easier to get Ubuntu to deal with NTFS than the other way around (big surprise). One little annoyance still confounds me, though:

When I start up in Ubuntu, I can't access the NTFS partition. If I open Nautilus, on the side under places is listed "100GB volume" or something like that. When I double click it, I get the security prompt for my password. When I enter it, I can access the partition. It then shows up in Nautilus' Places as "disk". I would like to automate this on startup - is that possible?

Try my tutorial on partition mounting.

[http://www.stchman.com/part.html](http://www.stchman.com/part.html)

---

### Post by dinostabOMG on 2008-05-22
Thanks!

---


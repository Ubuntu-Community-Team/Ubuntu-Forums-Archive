---
title: "Help please!"
date: 2008-10-10
forum: New to Ubuntu
---

### Post by ProdigyAvanti26 on 2008-10-10
Hello everyone! I recently installed Ubuntu Ultimate 1.8 on my Sony Vaio laptop 2 weeks ago, overwriting Vista Ultimate. I really enjoy Ubuntu but I need to uninstall it for a job that requires my laptop to run XP. I tried deleting the partion using the live cd and after rebooting I got error 22. So I proceeded to pop in the xp install cd and when I got to the setup where it asks do I want to install, repair windows. I tried to do a clean install and I got a message saying there is no disk found. I even tried to go to the recovery console to fix the mbr and I still got the same message. How can I correct this problem? I would like to know how to completely remove ubuntu so I can get xp on there. I've dled super grub disk but have no idea how to use it or what to do. Is disk even necessary to fix my problem? This is so frustrating. I plan on creating a dual boot xp/linux but only after I fix this problem. why is it so difficult to uninstall linux? Sorry for the novel but I'm pulling my hair out trying to figure this out. I don't have any vital data on the laptop since I backed up everything on an external hd. Thanks in advance to anyone that can help me. -Joe

---

### Post by talsemgeest on 2008-10-10
If all you need to do is get rid of ubuntu and reinstall xp, you should just be able to pop in the xp install cd, delete all the partitons and make a new ntfs one, and select to install to that.

---

### Post by bodhi.zazen on 2008-10-10
Boot the Ubuntu CD

Fire up gparted

delete all your partitions and then make a single FAT partition.

reboot with your windows CD in the CDROM and follow the installation instructions.

---

### Post by Keen101 on 2008-10-10
I recommend the GPARTED Live-cd instead. 

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It's basically the ubuntu installer, but in a nicer form. Just create a NNFS partition, or a FAT32 (which i like better).

But, the xp CD ***SHOULD*** be able to partition too.

---

### Post by kansasnoob on 2008-10-10
Sheesh, learn how to break things down:

"Hello everyone! I recently installed Ubuntu Ultimate 1.8 on my Sony Vaio laptop 2 weeks ago, overwriting Vista Ultimate."

"I really enjoy Ubuntu but I need to uninstall it for a job that requires my laptop to run XP. I tried deleting the partion using the live cd and after rebooting I got error 22."

"So I proceeded to pop in the xp install cd and when I got to the setup where it asks do I want to install, repair windows. I tried to do a clean install and I got a message saying there is no disk found. I even tried to go to the recovery console to fix the mbr and I still got the same message. How can I correct this problem?"

"I would like to know how to completely remove ubuntu so I can get xp on there. I've dled super grub disk but have no idea how to use it or what to do. Is disk even necessary to fix my problem? This is so frustrating. I plan on creating a dual boot xp/linux but only after I fix this problem. why is it so difficult to uninstall linux?"

"Sorry for the novel but I'm pulling my hair out trying to figure this out. I don't have any vital data on the laptop since I backed up everything on an external hd. Thanks in advance to anyone that can help me. -Joe"

Vista Ultimate to full Ubuntu and now trying to go to XP?

What are you doing?

I'm sorry but you just shouldn't be fiddling with your own computer!

---


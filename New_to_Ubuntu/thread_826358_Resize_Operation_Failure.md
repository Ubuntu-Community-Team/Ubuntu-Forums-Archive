---
title: "Resize Operation Failure"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by lizandeen on 2008-06-11
I'm trying to make my hard drive dual Windows/Ubuntu 8.04 but every time I get to step 4 of 7 and try to divide the drive 50/50 I get the message "Resize Operation Failure: An error occurred while writing the changes to the storage devices.".I managed to do something similar with 6.06 on a different computer some time ago but am having no luck with this install. Can any body help (the install CD is OK) ? Thanks in advance, Deen

---

### Post by Duck2006 on 2008-06-11
Did you Defragment Windows first?

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by kansasnoob on 2008-06-11
What windows?

If it's Vista just stop!

---

### Post by kansasnoob on 2008-06-11
Wait please.

---

### Post by lizandeen on 2008-06-11
I use Ashampoos Magical Defrag so it should be fine in that respect.

---

### Post by lizandeen on 2008-06-11
Sorry, it's Xp

---

### Post by Duck2006 on 2008-06-11
Did you use manual partition?

---

### Post by lizandeen on 2008-06-11
I used the top otion so that it would do it automaticlly ( I'm a bit scared of attempting this in the manual [bottom] setting for fear of totally losing windows!)

---

### Post by Duck2006 on 2008-06-11
Use the link i gave you in post #2, a lot of people have use it and it has worked for them.

---

### Post by kansasnoob on 2008-06-11
Sorry, but I was having a bit of a seizure.

I think you're talking about dual booting with Vista, eh?

If so you don't want to use Gparted to resize your ntfs partition.

Just follow the basics in this tutorial:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

Especially step 2:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

---

### Post by Duck2006 on 2008-06-11
> **lizandeen said:**
> Sorry, it's Xp

He/she is using win XP.

---

### Post by kansasnoob on 2008-06-11
Dual booting with XP SP-2 was easier than SP-3 just a teeny weeny bit.

This does work:

[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

---

### Post by Victormd on 2008-06-11
XP doesn't have the same partition manager as Vista so he will have to use the live CD or download GPARTED...

During install, go with manual, believe it or not, you'll have much more control over what's happening and it is very straight forward.

---

### Post by Duck2006 on 2008-06-11
> During install, go with manual, believe it or not, you'll have much more control over what's happening and it is very straight forward.

True

---

### Post by kansasnoob on 2008-06-11
Actually the version of Gparted included in Hardy is quite capable of resizing XP or any ntfs partitions, although i don't advise using it to resize Vista partitions.

I could have said, "just use Gparted to create one free space on your drive at least 6GB and preferably 10GB and then choose to install to the largest free space", but I'm lazy, and those tutorials do have some nice screenshots!

---


---
title: "Ubuntu &amp; XP"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by AKPAKP on 2008-06-01
HELP!!!
Installing Windows XP & Ubuntu together...

---

### Post by sayakb on 2008-06-01
What kind of help do you need?  You need to be specific.

---

### Post by AKPAKP on 2008-06-01
I'm currenty using Ubuntu in my computer...

Now because of some graphics apps....
I need to install XP & Ubuntu ...both of them.....

---

### Post by quinnten83 on 2008-06-01
Or you might want to try google, since there are like a bajilion tutorials on how to dualboot.
I think that is rule number one on using the forums....!

---

### Post by sayakb on 2008-06-01
What are those *graphic apps*? Is it something related to photoshop? If so, then you might install XP on [VirtualBox]("http://www.virtualbox.org/"). That way, you can have XP  ***inside** *Ubuntu.

---

### Post by AKPAKP on 2008-06-01
I also need help on the space distribution & the various drive formats i should use...

I have a 80 GB partition

---

### Post by sayakb on 2008-06-01
If you use VirtualBox, you don't need to worry about partitioning. Which apps do you want to install on XP?

---

### Post by AKPAKP on 2008-06-01
I need to use Photoshop & Corel......
My sis insists on havin a copy of XP...

---

### Post by AKPAKP on 2008-06-01
If I'm nt able to dual boot i'll be forced to remove Ubuntu....

---

### Post by sayakb on 2008-06-01
With VirtualBox, you can even get XP running on a different workspace as Ubuntu boots. Atleast try VirtualBox.
If you want to dualboot: You need to shrink the Ubuntu partition using the [GParted LiveCD]("http://gparted.sourceforge.net/livecd.php")
After you create a separate partition and install Windows over it, the GRUB bootloader shall be erased. To recover GRUB, use [superGrubDisk.]("http://www.supergrubdisk.org/").

---

### Post by housam on 2008-06-01
You can also recover grub after installing windows using [[COLOR="Red"]_this guide_[/COLOR]]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub")

---

### Post by SunnyRabbiera on 2008-06-01
Yes its possible to install XP after ubuntu, but its at your own risk as XP is a partition hog.

---


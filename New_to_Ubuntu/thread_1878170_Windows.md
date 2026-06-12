---
title: "Windows"
date: 2011-11-09
forum: New to Ubuntu
---

### Post by srcuvm02 on 2011-11-09
Quick question for you all.  I am a Ubuntu newbie and just installed 11.10 using the  windows installer.  Now when I start up my computer, I choose my OS -- Windows XP or Ubuntu.  I'm wondering if I can now get rid of Windows without messing up Ubuntu?  How should I go about doing this?

Thanks so much for any help!

---

### Post by Brizlitman on 2011-11-09
I've partitioned my hard drive.That way I can format the windows side when I can't take it anymore. With the windows installer, u can't remove windows without removing glorious Ubuntu.

---

### Post by TBABill on 2011-11-09
You can fire up a live CD and then just format the Windows partition. Unless you plan to use that space for another OS or to make room for more Ubuntu files, any reason to just ditch it altogether? Just curious and not trying to sway you either way, but offering food for thought because I made that decision at one time and then couldn't find my restore disk when I needed Windows for something.

---

### Post by sadaruwan12 on 2011-11-09
> **Brizlitman said:**
> I've partitioned my hard drive.That way I can format the windows side when I can't take it anymore. With the windows installer, u can't remove windows without removing glorious Ubuntu.

Yes, the ubuntu runs in the windows as a normal program so you can't remove it without loosing it better to install it in separate partition and afterward if you don't need windows remove it.

---

### Post by oldos2er on 2011-11-09
> **srcuvm02 said:**
> Quick question for you all.  I am a Ubuntu newbie and just installed 11.10 using the  windows installer.  Now when I start up my computer, I choose my OS -- Windows XP or Ubuntu.  I'm wondering if I can now get rid of Windows without messing up Ubuntu?  How should I go about doing this?


If you used Wubi, Ubuntu is installed inside your Windows installation in the "virtual disk" file root.disk, so removing Windows would also remove Ubuntu. You would need to either reinstall Ubuntu to its own partition (and you can remove Windows during the installation) or try converting Wubi to a full install: 

[https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_migrate_to_a_real_partition.2C_and.2BAC8-or_get_rid_of_Windows_entirely.3F) 

[http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install](http://askubuntu.com/questions/635/how-to-convert-wubi-install-into-regular-install)

I think it would be safer to just reinstall Ubuntu and tell it to use the entire hard disk. Back up any needed data first!

---


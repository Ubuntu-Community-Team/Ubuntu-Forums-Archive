---
title: "[SOLVED] How do I get a boot menu?"
date: 2008-10-12
forum: New to Ubuntu
---

### Post by dixiedownunder on 2008-10-12
I installed Ubuntu on a 2nd hard drive in one of my bays.  I unplugged the first hard drive (windows) while I installed Linux on the second as a precaution.  

So now that I have Linux installed, I  hold the delete key at start up to access the BIOS and change the boot order of the hard disks. Linux is on a 40 GB drive and Windows is on a 500 GB drive.  

Is there a better way to get a prompt on the screen at start up to pick Linux or Windows?

---

### Post by cybermecano on 2008-10-12
better is to keep the windows hard drive (500 Gb) plugged while you're installing ubuntu !! and so you've just to pay attention when you must choose the partition on which you want to install ubuntu, here the 40 Gb. Then ubuntu will detect if another operating system is already existing in the other(s) partition(s) and if so, ubuntu will create a dual (or multi) boot menu from which you can choose the operating system you want to run everytime you start your machine!

---

### Post by dixiedownunder on 2008-10-12
Thanks for that tip.  I've only just installed, so I'll just do it again.  I was worried I'd muck up the other hard drive, but I'm a little more confident now.

---

### Post by fooman on 2008-10-12
should be no need to reinstall...you can add the windows drive to grub's boot menu pretty easily.

please post the output of:

```
sudo fdisk -l
```

---

### Post by dixiedownunder on 2008-10-12
Damn, I already reinstalled it.  It worked for getting me the menu at start up, but it doesn't recognize the keyboard or the mouse, so I can see Windows on the list, but can't select it.  

Does anybody know what to do about that?

---

### Post by dixiedownunder on 2008-10-12
Maybe it's a moot point since I reinstalled, but here is the output:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x75cb75cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60800   488375968+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x665e665e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4778    38379253+  83  Linux
/dev/sdb2            4779        4865      698827+   5  Extended
/dev/sdb5            4779        4865      698796   82  Linux swap / Solaris

---

### Post by Muffinabus on 2008-10-12
Yeah, you didn't have to reinstall, I did my installation the same way and it works flawlessly.  You only had to make a few modifications in GRUB to point to your Windows drive.  Now, I'm not so sure, never heard of the keyboard failing to respond in the GRUB menu /:

---

### Post by firfin on 2008-10-12
you shouldnt need the mouse. Keyboard still works when trying to access the bios? Did it work when you installed before?
Just checking for sillyness

---

### Post by dixiedownunder on 2008-10-12
I thought that was odd too.  It says something about the graphics card on the splash screen and says to press 'DEL' to enter the BIOS, and I don't have a problem there.  

After that screen goes away and I come to the options to load Linux or Windows, the keyboard doesn't work and it's just counts down and loads Linux.  The keyboard works fine in Linux.

I'm going to reboot now to muck around in the BIOS to see if I can find anything to change.

---

### Post by dixiedownunder on 2008-10-12
Well, I sorted it out.  In the BIOS I enabled USB keyboard support under the devices menu (I think).  Now it works like a charm.  :)

---


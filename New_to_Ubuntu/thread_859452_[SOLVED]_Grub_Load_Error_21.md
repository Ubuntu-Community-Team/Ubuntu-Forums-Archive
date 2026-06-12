---
title: "[SOLVED] Grub Load Error 21"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by Frogster on 2008-07-14
Ha got myself stuck with a Grub Load Error 21.

I decided to load Linux mint onto a spare ide hard drive. This was done with the intention of moving the disk to anther pc without a cd drive and seeing what Linux mint had to offer.

When I moved the disk out of the original pc I get the "Grub Load Error 21." Put it back and all is well and I can boot to either distro.

How do I get back to booting to Ubuntu without the 81.9 GB ide disc?

```

~$ sudo fdisk -l

Disk /dev/hda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9ad2d170

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        9553    76734441   83  Linux
/dev/hda2            9554        9964     3301357+   5  Extended
/dev/hda5            9554        9964     3301326   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0004010a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321   83  Linux

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6a6431cf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       18700   150207718+  83  Linux
/dev/sdb2           18701       19457     6080602+   5  Extended
/dev/sdb5           18701       19457     6080571   82  Linux swap / Solaris

```

---

### Post by LowSky on 2008-07-14
power of google

[http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/](http://www.linuxquestions.org/questions/linux-general-1/grub-error-21-338856/)

[http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html](http://lists.gnu.org/archive/html/bug-grub/2003-02/msg00082.html)

---

### Post by kansasnoob on 2008-07-14
OK, so you have Ubuntu on the remaining drive, eh?

If so you need to restore GRUB to Ubuntu. There are several ways, I usually use the Alternate CD method, but only as a matter of personal preference.

[http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub](http://users.bigpond.net.au/hermanzone/p15.htm#reinstallgrub)

second favorite:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by bumanie on 2008-07-14
Boot with all three hard drives in . In terminal > sudo grub then > find /boot/grub/stage1 and post ouput. It should provide two numbers.

---

### Post by Frogster on 2008-07-14
Thank you kansasnoob. I think I will be trying the alternate CD method. Should I chose /dev/sdb1 as the root to instal grub on? Do I do this prior to removing the ide disk or after? Does it make a difference?

---

### Post by Frogster on 2008-07-14
Thank you, output is


```

grub> find /boot/grub/stage1
 (hd0,0)
 (hd2,0)

```

---

### Post by bumanie on 2008-07-14
It is a fair assumption to assume that the original position of grub was (hd0,0) That is where you should reinstall grub to. Personally, I would remove the other drive. Taken note that you are going to use the alternate cd method. Good luck. Hope it works.

---

### Post by Frogster on 2008-07-14
Thank you bumanie.

---

### Post by kansasnoob on 2008-07-14
> **bumanie said:**
> It is a fair assumption to assume that the original position of grub was (hd0,0) That is where you should reinstall grub to. Personally, I would remove the other drive. Taken note that you are going to use the alternate cd method. Good luck. Hope it works.

Agreed!

Thanks Bumanie!

I'd do it with the extra drive removed so as not to hose GRUB in it, since you're transplanting it to another machine.

---

### Post by Frogster on 2008-07-14
I will try to reinstall Grub tomorrow night and hopefully be able to close this thread then :)

Many many thanks to you all

---

### Post by Frogster on 2008-07-15
Ha, just to let you know the alternative cd method didnt work! looking for the next method :-)

---

### Post by bumanie on 2008-07-15
You could try [super grub disc]("http://forjamari.linex.org/frs/?group_id=61&release_id=620#620")

---

### Post by Frogster on 2008-07-16
Cheers for the pointer. When I get this sorted, I am not going to tinker any more!!!!!

Well maybe a little.

---

### Post by bumanie on 2008-07-16
Tinkering is good IMO - occasionally one has unwanted side-effects, but that's when one learns the most!!! Just back up important things first and read or ask the forum first if you are unsure. Most problems eventually get sorted on the forum. If super grub disk fixes things up, it's a good idea to make a backup of your boot/grub/menu.lst If you had done that first, before trying the hard drive 'trick' once the other hard drive was removed you could have used the backup boot/grub/menu.lst to restore things (at least in theory). Unfortunately though, one can sometimes muck up partition tables etc that reinstalling grub alone, won't fix. To back up boot/grub/menu.lst > sudo cp boot/grub/menu.lst boot/grub/menu.lst_backupbut only after everything is back to normal re booting.

---

### Post by Frogster on 2008-07-16
Yay to super grub, all seems to work again :-) 

Now to backup grub.  Thank you for your help and pointers

---


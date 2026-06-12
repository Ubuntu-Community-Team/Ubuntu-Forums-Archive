---
title: "help in multiple boot??"
date: 2008-07-17
forum: New to Ubuntu
---

### Post by rushikesh988 on 2008-07-17
I want to try fedora ! I have ubuntu installed on my system can somebody tell me if i installed fedora does it will take my ubuntu in his bootloader??

---

### Post by Rocket2DMn on 2008-07-17
This thread may interest you - [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

Fedora's GRUB should be able to recognize Ubuntu, or vice versa.  It may keep your existing grub (it may actually prompt you).  Either way you will be able to get into whatever system you want.

---

### Post by PmDematagoda on 2008-07-17
> **rushikesh988 said:**
> I want to try fedora ! I have ubuntu installed on my system can somebody tell me if i installed fedora does it will take my ubuntu in his bootloader??

It will install it's own boot-loader and replace Ubuntu's GRUB boot-loader, but you can insert the required entry to boot Ubuntu after Fedora finishes installing.

---

### Post by rushikesh988 on 2008-07-17
oh my god its a new problem here I just inserted wrong entry there :( (into the last option where fedora ask to add any partion for boot )


can you tell tell me How can I configure that fedora's Grub to include ubuntu's partition in it??


plz provide me some help

---

### Post by PmDematagoda on 2008-07-17
First you will need to gain root privileges before doing these(well, most of them) since Fedora does things a bit differently, you can gain root privileges with:-
```
su -
```
after you get root privileges post the outputs of:-
```
cat /boot/grub/menu.lst
```
```
fdisk -l
```
and
```
cat /etc/mtab
```

---

### Post by Rocket2DMn on 2008-07-17
Fedora might be using grub.conf instead of menu.lst - don't quote me on that.

---

### Post by bodhi.zazen on 2008-07-17
Fedora users menu.lst, it will not automatically add Ubuntu (to the grub menu) though.

Also, by default, Fedora uses LVM and will make a /boot partition.

---

### Post by PmDematagoda on 2008-07-17
> **bodhi.zazen said:**
> Fedora users menu.lst, it will not automatically add Ubuntu (to the grub menu) though.

Also, by default, Fedora uses LVM and will make a /boot partition.

I've been meaning to ask that for sometime bodhi, what exactly is the advantage of an LVM over a normal partition?

---

### Post by Rocket2DMn on 2008-07-17
LVM allows you to setup things like RAID - setting a single partition across multiple physical devices, and even remotely I think, along with different methods of striping.  Physical volume groups can be put under one or more logical volumes with other sorts of strange ways.  This creates levels of abstraction between the volume management and the hardware.
It is a bit more of a pain to deal with, but since it is "logical" instead of physical, all it needs is a starting point like /boot and then the kernel and LVM software can take over from there.

---

### Post by PmDematagoda on 2008-07-17
> **Rocket2DMn said:**
> LVM allows you to setup things like RAID - setting a single partition across multiple physical devices, and even remotely I think, along with different methods of striping.  Physical volume groups can be put under one or more logical volumes with other sorts of strange ways.  This creates levels of abstraction between the volume management and the hardware.
It is a bit more of a pain to deal with, but since it is "logical" instead of physical, all it needs is a starting point like /boot and then the kernel and LVM software can take over from there.

Thanks for the explanation Rocket2DMn:).

---

### Post by bodhi.zazen on 2008-07-17
As background, LVM = Logical Volume Management and it has several advantages. You can put several physical partitions into a single group and then add what are logical partitions.

You can resize or back up "snapshot" the logical volumes.

Try skimming through this page ;)

[http://doc.async.com.br/howto/LVM-HOWTO.html](http://doc.async.com.br/howto/LVM-HOWTO.html)

The advantage here is you can do these things (resize, backup) "on the fly" without having to shut down services.

---

### Post by kansasnoob on 2008-07-17
This is certainly more a question than an answer because I've never tried Fedora but I have tried DSL and Puppy, along with multiple *buntus, how would it work to create a new separate GRUB partition like this:

[http://www.troubleshooters.com/linux/grub/grubpartition.htm](http://www.troubleshooters.com/linux/grub/grubpartition.htm)

I found it useful when I was test-driving various distros.

---

### Post by rushikesh988 on 2008-07-19
well thanks friends

---


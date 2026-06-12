---
title: "Reformat my HDD"
date: 2012-06-26
forum: New to Ubuntu
---

### Post by Drawstop on 2012-06-26
Is it possible to reformat my hard drive through Ubuntu?  The same as windows will do it. 
Many thanks
Drawstop.

---

### Post by rukiaEnix on 2012-06-26
Yes, you can do it graphically with GParted

---

### Post by Drawstop on 2012-06-26
Many thanks but too technical for me.
Drawstop.

---

### Post by rukiaEnix on 2012-06-26
Just install GParted, then open it and your partitions will be loaded there, then you just right click in the one you want and select format to.. then you just select the filesystem type

---

### Post by audiomick on 2012-06-26
> **Drawstop said:**
> Many thanks but too technical for me.
Drawstop.

Then the Windows partitioning tool must be too technical for you too. I find Gparted easier and more intuitive than the Windows tool.

Bear in mind that you can not work on a partition that is mounted. Mounted means that the System has the partition included in it's file system. For instance, when you plug in a USB thumb drive, it is mounted and appears in the file manager. The partition that the OS is installed onto is obviously also mounted when you are booted into that install.

In short, if you want to format the entire drive, the easiest thing is to boot using a Live CD or USB the same as when installing Ubuntu. Boot into the "try without changing" option. Gparted is already installed on there. The only thing you will have to do is unmount the swap partition. This is also not hard. When you open gparted and look at the drive, it is the one called "swap". Right click on it and choose to unmount, and then you can delete everything on the drive and re-do the whole partition table and what ever else you might want to do.

---

### Post by rukiaEnix on 2012-06-26
Maybe he wants a magic solution of just one click and vuala! or something like that :p

---

### Post by black veils on 2012-06-26
> The same as windows will do it

that is a bit vague. maybe you mean install ubuntu from cd/usb in a way that simplistically erases the entire harddrive, installing a fresh ubuntu at the same time?

this can be done using the live cd/usb and during one of the screens, choose "use entire disk" or something like that, if you want to delete everything currently on the harddrive, and install ubuntu.

---

### Post by Drawstop on 2012-06-27
Many thanks everyone. Regrettably I am now 80 and feeling my age but will have a try. No, I do not want a 'one-click'solution; I want to learn about these things I do.
My problem is that there is a part installed windows 7 on the drive and I want to reformat and then re-install Ubuntu and xp.The re-installs I am happy with - it is just the reformat.
Once again - thanks.
Drawstop.

---

### Post by black veils on 2012-06-27
ok then, you need to use the ubuntu live cd/usb, choose the Try option, and then open gparted, like people have said. you then delete all the partitions by right-clicking. everything will be unallocated space. then use your xp installation disc to install windows. after that you install ubuntu, during the installation wizard it should detect your windows xp, and you choose "install alongside".

---

### Post by audiomick on 2012-06-27
+1 that.

If you are planning on re-installing everything, then you have nothing really to worry about. You can play around with Gparted as long as you want; effectively nothing can go wrong. All that can happen is that you end up with a drive with everything erased on it, and that is what you want anyway. ;)

Don't worry about Gparted. It really is easy to use. Just take your time and really look at what you are seeing on the screen.

---

### Post by c2tarun on 2012-06-27
> **Drawstop said:**
> Many thanks everyone. Regrettably I am now 80 and feeling my age but will have a try. No, I do not want a 'one-click'solution; I want to learn about these things I do.
My problem is that there is a part installed windows 7 on the drive and I want to reformat and then re-install Ubuntu and xp.The re-installs I am happy with - it is just the reformat.
Once again - thanks.
Drawstop.
 
 
Hats off to you man, you trying to learn something new at 80, I know guys who are even 30+ and too lazy or scared to learn something new.

---

### Post by rukiaEnix on 2012-06-27
Yes, that's really great, even younger people like 17-24 are really lazy now.

Try gparted!

---

### Post by Drawstop on 2012-07-05
Many thanks everyone.
I am getting to grips with Gparted.
Regards
Richard.

---

### Post by audiomick on 2012-07-14
good on you. Keep at it. :popcorn:

---


---
title: "Lost Harddrive"
date: 2008-08-28
forum: New to Ubuntu
---

### Post by driscom59 on 2008-08-28
Hi, very new to this ubuntu stuff.  I loaded ubuntu onto my computer believing it was to run as well as windows (XPsp2).  When I try to boot into XP I get a 'unable to locate disk' message.  Ubuntu shows my backup disk but I cannot find the old C drive.  The back up was backed up a while ago but does not contain any new stuff, contacts, favourites etc.  HELP!!!!!

---

### Post by LTFC2020 on 2008-08-28
you are dual booting xp/ ubuntu right?
have you accidently unmounted the drive?
look under home folder (in ubuntu) and find the disc, drop down the menu and see ifs theres a mount volume option
sorry cannot be more specific at the moment as I'm not in ubuntu

---

### Post by driscom59 on 2008-08-28
Thanks - all I can see is 40gb hard drive (my backup) ,floppy drive, cd/dvd creator and computer.  The hard drive was there when I was using Ubuntu from the disc but since installing I'm wondering if the partition hasn't overwritten all the other stuff

---

### Post by vanadium on 2008-08-28
You might indeed have made wrong choice during the installation and have your Windows installation remove. In that case, there is unfortunately little you can do except to rely on your backup (which, according to Murphy's law, incidentally tends to be a bit outdated the moment you need it).

To make sure your Windows partition is not around anymore, examine the output of the command

```

sudo fdisk -l

```

This lists all of your drives and all the partitions on them.

---

### Post by driscom59 on 2008-08-28
Thanks again - as I am new to this, where do I place the command? Back in the old DOS system or is there somewhere in ubuntu?

---

### Post by driscom59 on 2008-08-28
Hi again - found out what to do, what a learning curve got the following - can't see anything about XP etc. probably didn't need all that stuff anyway!!!!!!!

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa71ea71e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9352    75119908+  83  Linux
/dev/sda2            9353        9729     3028252+   5  Extended
/dev/sda5            9353        9729     3028221   82  Linux swap / Solaris

So given all's lost - how do I get the 'puter to go straight to Ubuntu and not give me the option of XP (which doesnt work anyway????) Thanks, all info is valuable

---

### Post by shane19174 on 2008-08-28
In Ubuntu, click Applications -> Accessories -> Terminal. Then enter the command.

PS: I see you figured it out on your own...

---

### Post by vanadium on 2008-08-28
This is strange. Your fdisk looks indeed as if you allocated the whole drive to Ubuntu. What is strange is gthat you still get a choice to boot into XP. Normally in this scenario, Ubuntu would not install an option to boot into XP.

Load the file /boot/grub/menu.lst in gedit with root permissions using the command:

```

gksudo gedit /boot/grub/menu.lst

```

Find the section

```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

```

Remove the comment sign before the last line so that it looks like

```

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

```

This will disable the menu (you can still access it during a brief period pressing escape) and boot directly to the default item.

---

### Post by driscom59 on 2008-08-29
Thanks for that Vanadium.  Have done as suggested - will see how it goes.  Thanks again for your time.

---


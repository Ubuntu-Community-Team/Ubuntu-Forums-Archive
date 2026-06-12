---
title: "Half Upgraded Problems!"
date: 2008-04-28
forum: New to Ubuntu
---

### Post by Spoken on 2008-04-28
alright, due to my busy schedule with school and work etc, ive only been able to upgrade from 7.10 to 8.04 piece by piece. 

Last night i left my laptop on so it can upgrade while i caught some sleep. this morning it finished fetching the new packages and was installing them. i had to stop the process because i had to go to school. so im at school now in the library, i turned my laptop on and when i logged in, a lot of my theme stuff / screenlets is gone, and i got this error message that says "failed to initialize HAL!", it says its a internal error.

i dont know what to do. my guess is that it messed up because the upgrade to 8.04 removed certain packages and hadnt had the chance to install the new ones.

is there anything i can do? my upcoming classes that i have in a few hours would be a lot easier if i could continue taking notes on my laptop lol.

====================================
MY SITUATION
====================================
Compiz fusion and emerald theme manager are still working

BUT! my panel color and location is back to default, my folder theme is different, and my screenlets are broken.
__________________



 
 

--------------------------------------------------------------------------------

UPDATED NEWS!!

when i go to system > preferences > apperance and try to reselect my original theme, it lets me click and highlight it but nothing changes on the desktop. This goes for ALL theme changes i attempt to do.
__________________

---

### Post by Spoken on 2008-04-28
so yea, im at school. i would like to figure this out :l

---

### Post by gardara on 2008-04-28
To get the missing files enter this in terminal:

```
sudo aptitude install ubuntu-desktop
```

---

### Post by lewac on 2008-04-28
well upgrades are all about FIRST CYA'ing your machine. this means in simplistic terms that you better be imaging your CURRENT OS partition BEFORE you attempt ANY upgrade process! Images really don't take that long to make and there are some very good tools to go about the process. 

for example we use "rescueCD" (go here to read all about it: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)). download the iso and burn it (we use k3b). before you load this thing DISCOONECT your wired cat5 cable and/or disable wireless connectivity at the router. why? because "rescueCD" puts you at root. note also that to use "partimage" a partition it needs to be UNMOUNTED (which it is by default when this thing boots). here's the steps once you get the thing loaded (note that this iso loads a distro of "gentoo").

first do fdisk -l ("el") (at a terminal for all this)
make a note of the partition that you are going to retain the subseguent created image on (perhaps sdb5 as an example) also note the source partition although not really required because it is listed inside "partimage" in a later step.

then mkdir /backup (creates a mount point)
then mount -t vfat /dev/sdb5 /backup (this assumes that the partition is fat32 (NOT ntfs) uhh... try to avoid ntfs as the destination)

then partimage. after it loads the first pane at the top displays all your partitions located on all drives. select the one you want to image (generally the first ext3 partition listed (perhaps sda5). now tab down to the destination partition edit field and give the first image file a name. here's an example: /backup/ubuntu_7.1_4.24.2008. now hit "F5" to continue (retaining all the defaults). when asked to do so in a later edit field give it a meaningful description (such as "ubuntu 7.1 prior to upgrade"). now ok the thing out and the image should be created. but just don't walk away because the default choices first checks the source partition for inconsistencies. then stops! THEN you must ok THIS to progress to the actual imaging process.

note that partimage is QUICK because only actual DATA is retained within the image. as a comparison we believe it is at least 30% quicker than windoze "PQDI" (authored by former "powerquest"). when complete verify that the image file(s) actually exist where you expect them to be (from within ubuntu after a reboot).

now. in case the baddie happens like your note mentioned the simplest thing to do is RESTORE the image. believe me. it WORKS! after restore reboot to original install and try the upgrade process again. and if it repeatedly fails then you also repeat the restore process as well.

---

### Post by toupeiro on 2008-05-01
> **lewac said:**
> well upgrades are all about FIRST CYA'ing your machine. this means in simplistic terms that you better be imaging your CURRENT OS partition BEFORE you attempt ANY upgrade process! Images really don't take that long to make and there are some very good tools to go about the process. 

for example we use "rescueCD" (go here to read all about it: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)). download the iso and burn it (we use k3b). before you load this thing DISCOONECT your wired cat5 cable and/or disable wireless connectivity at the router. why? because "rescueCD" puts you at root. note also that to use "partimage" a partition it needs to be UNMOUNTED (which it is by default when this thing boots). here's the steps once you get the thing loaded (note that this iso loads a distro of "gentoo").

first do fdisk -l ("el") (at a terminal for all this)
make a note of the partition that you are going to retain the subseguent created image on (perhaps sdb5 as an example) also note the source partition although not really required because it is listed inside "partimage" in a later step.

then mkdir /backup (creates a mount point)
then mount -t vfat /dev/sdb5 /backup (this assumes that the partition is fat32 (NOT ntfs) uhh... try to avoid ntfs as the destination)

then partimage. after it loads the first pane at the top displays all your partitions located on all drives. select the one you want to image (generally the first ext3 partition listed (perhaps sda5). now tab down to the destination partition edit field and give the first image file a name. here's an example: /backup/ubuntu_7.1_4.24.2008. now hit "F5" to continue (retaining all the defaults). when asked to do so in a later edit field give it a meaningful description (such as "ubuntu 7.1 prior to upgrade"). now ok the thing out and the image should be created. but just don't walk away because the default choices first checks the source partition for inconsistencies. then stops! THEN you must ok THIS to progress to the actual imaging process.

note that partimage is QUICK because only actual DATA is retained within the image. as a comparison we believe it is at least 30% quicker than windoze "PQDI" (authored by former "powerquest"). when complete verify that the image file(s) actually exist where you expect them to be (from within ubuntu after a reboot).

now. in case the baddie happens like your note mentioned the simplest thing to do is RESTORE the image. believe me. it WORKS! after restore reboot to original install and try the upgrade process again. and if it repeatedly fails then you also repeat the restore process as well.

.. or..  use a keychain drive or download a utility like sbackup from the repos to get your personal files backed up then upgrade.  Re-image if it fails?  Its not like aptitude makes it very difficult to get back to your programs.  lewac's process isn't incorrect, just overkill unless your installation is HIGHLY customized away from the distro release.

---

### Post by toupeiro on 2008-05-01
I posted a few more ideas for you to try [here.]("http://ubuntuforums.org/showthread.php?t=772555")

---


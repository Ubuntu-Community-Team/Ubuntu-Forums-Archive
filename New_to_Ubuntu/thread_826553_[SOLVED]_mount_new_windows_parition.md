---
title: "[SOLVED] mount new windows parition"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-06-12
i used to have ubuntu hardy installed on one partition and windows vista on another

windows vista got messed up and i had to reformat and reinstall

after getting grub reinstalled i finally got back onto my ubuntu install but now i am no longer able to mount my windows partition (it says i dont have permission, but it never asks for my password)


also, before the reinstall of vista i had edited my /etc/fstab so that my vista partition was automounted at startup (that obvioulsy isnt working anymore either)


so basicaly what do i have to do in order to mount windows again? (everything is on the same partition and harddrive as my previous vista install, so why dont it still work?)

---

### Post by ajmorris on 2008-06-12
> **tjwoosta said:**
> i used to have ubuntu hardy installed on one partition and windows vista on another

windows vista got messed up and i had to reformat and reinstall
after getting grub reinstalled i finally got back onto my ubuntu install but now i am no longer able to mount my windows partition (it says i dont have permission, but it never asks for my password)


also, before the reinstall of vista i had edited my /etc/fstab so that my vista partition was automounted at startup (that obvioulsy isnt working anymore either)


so basicaly what do i have to do in order to mount windows again? (everything is on the same partition and harddrive as my previous vista install, so why dont it still work?)

Hi there,
the easiest way to mount a windows partition is with ntfs-3g.
For more information, see the following wiki page:
[https://help.ubuntu.com/community/MountingWindowsPartitions](https://help.ubuntu.com/community/MountingWindowsPartitions)

If that page is not helpful, i will be more than happy to walk you through mounting your windows partition.

AJ

---

### Post by Paqman on 2008-06-12
Easiest thing to do is install ntfs-config. Should sort you out in a jiffy.

---

### Post by tysonh on 2008-06-12
I like to have windows installed first.  Windows doesn't seem to work well if at all if installed 2nd.  I'm not to sure but I've heard people say on the forums that vista dual boot is set up differently than a window xp or earlier dual boot.

I know this isn't very descriptive but it's all I got.  I'll poke around and see if I can find something to help you out.

---

### Post by tysonh on 2008-06-12
Found this how to.  Looks pretty cut and dry.  It calls for windows to already be installed before starting the Ubuntu install process.

Here's a link to the how to page:[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm)

good luck

---

### Post by cariboo on 2008-06-12
It would help if you gave us a listing of your hard drives. in a terminal type:

```
fdisk -l
```

and paste the output in your next post.

Jim

---

### Post by tjwoosta on 2008-06-12
> 
Found this how to. Looks pretty cut and dry. It calls for windows to already be installed before starting the Ubuntu install process.

Here's a link to the how to page:[http://apcmag.com/how_to_dualboot_vi...lled_first.htm](http://apcmag.com/how_to_dualboot_vi...lled_first.htm)

good luck 


yea i dont really want to uninstall ubuntu just so i can install windows first (that would just be a waste of time)

> 
It would help if you gave us a listing of your hard drives. in a terminal type:

Code:

fdisk -l

and paste the output in your next post.

Jim 


i cant do the command right now because im on a different computer but this is how my partitions go

(i have a single 120 gig harddrive on my laptop)

Ubuntu Hardy  is on (hd0,0) its like 60 gigs

linux swap is (hd0,1) and its like 2 gigs

then Windows Vista is on (hd0,2) and its about 57 gigs


vista is still on the same partiton it was before (i simply deleted the old vista partiion with gparted and then reinstalled vista to it)


also, the first time i installed vista, it was after installing ubuntu

everything worked fine the first time, so why isnt it working now?

> 
Easiest thing to do is install ntfs-config. Should sort you out in a jiffy.
 

ill look into this, thanks  (its just strange how i never needed it the first time)

---

### Post by tjwoosta on 2008-06-14
ok guys i installed ntfs-config but im still not able to mount the windows partition (it says permission denied)

what else might i need to do to mount this stubborn partition?


Edit: ok i just figured out how to mount the partition

it requires that i open a terminal and do this
<CODE>
tj@tj-laptop:~$ sudo mkdir /media/Windows
[sudo] password for tj: 
tj@tj-laptop:~$ sudo mount /dev/sda3 /media/Windows
</CODE>

does anyone know a way i can make this partition automount (despite needing to be root)

---

### Post by bumanie on 2008-06-14
> sudo apt-get install ntfsconfig Then go to Applications --> System tools and open up ntfsconfig and fill in the box and the vista disk/partition will automatically get added to /etc/fstab

---

### Post by tjwoosta on 2008-06-15
thanks, but  actually i already figured it out, all i had to do was manually mount the drive once with the command line and  when i restarted it started auto-mounting again.

( i already configured my fstab the last time i had vista installed so there was no need to do it again)

---


---
title: "Hardy Install Problem"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by apostolic3 on 2008-05-11
I have an HP m8120 with a Quad core Q6600 processor, 3GB RAM, 640GB HD (Raid 1 so really 320GB), Windows Vista. I also have an ancient fossil Sony Vaio with Feisty installed as a dual boot with XP.

I burned a CD and tried to install Hardy on the HP as a folder within Vista. All goes OK and it will say the install is complete and eject the CD, but then the install freezes and I cannot close the install application. (I should also mention the green bar that indicates how far along the install has gone is only about 2/3 the way across the screen). To unfreeze it, I have to re-insert the CD and use the Task Manager to shut the install down. When I reboot and choose Ubuntu, it finishes the install and reboots again.

After choosing Ubuntu, I get the following error message:

find -- set-root -- ignore-floppies/ubuntu/disks/boot/grub/menu.lst

Error 15: File not found

Press any key to continue...

When I press any key, it gives me several choices:

find/ubuntu/disks/boot/grub/menu.lst

find/ubuntu/install/boot/grub/menu.lst

find/menu.lst

find/boot/grub/menu.lst

find/grub/menu.lst

command line

reboot

halt

Choosing most of the options does nothing but take me back to the first error message listed. Choosing "reboot" reboots the computer. Choosing "halt" immediately shuts down the PC. I have no clue how to use the command line.

Has anyone else seen this? Definitely consider me a noob. Can someone walk me through a solution? Is my raid 1 hard drive configuration a problem? Thanks in advance.

---

### Post by cprofitt on 2008-05-11
To clarify -- you are using Wubi? or are you installing Ubuntu as a dual-boot and partioning the drive? From what you wrote I am guessing Wubi.

If Wubi is the case you might want to check here - [http://ubuntuforums.org/showthread.php?t=764686](http://ubuntuforums.org/showthread.php?t=764686)

---

### Post by apostolic3 on 2008-05-11
> **PrivateVoid said:**
> To clarify -- you are using Wubi? or are you installing Ubuntu as a dual-boot and partioning the drive? From what you wrote I am guessing Wubi.

If Wubi is the case you might want to check here - [http://ubuntuforums.org/showthread.php?t=764686](http://ubuntuforums.org/showthread.php?t=764686)

Wubi.

I copied wubi.exe from the CD to my hard drive and it installed without a hitch. The problem is when I rebooted the 2nd time I got the exact same error message.

The link you provided had another link that mentioned Error 15. I think my problem is Wubi does not support raid 1.

---

### Post by ejpyle on 2008-05-11
it does not?

---


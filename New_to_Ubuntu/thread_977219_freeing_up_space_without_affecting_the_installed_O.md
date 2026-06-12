---
title: "freeing up space without affecting the installed OS"
date: 2008-11-10
forum: New to Ubuntu
---

### Post by ub007 on 2008-11-10
Hello,

I got Fedora9 installed on my 20G hard drive and now wish to install Ubuntu as well.During the fedora install process,i selected the auto partition option which uses the entire disk.Now how do i free up space(preferably 10G) from the 20G hard drive without affective the fedora OS?


Thanks in advance
David

---

### Post by keplerspeed on 2008-11-10
Get the gparted live cd, the iso is avaliable here:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

burn the iso to cd, boot the cd, and partition your harddrive as required. with gparted, it is quite self explanatory, and uses a GUI.

EDIT: after reading the post, sorry, it is easier to use the partiton editor (also gedit) that is part of the ubuntu installation cd. So when you boot the ubuntu installation cd, select to partition you disk.

---

### Post by ub007 on 2008-11-10
Many Thanks.I found an ol' 20GB hard drive .Would i be able to install ubuntu on that one and set the system as dual boot?I guess it should be possible but i got no clue as to how to go about it.....

Cheers
Davis

---

### Post by keplerspeed on 2008-11-10
Yes you can dual boot with ubuntu on the other hd, just install ubuntu on the other hd, and if the dual boot option is not auto created, then try this:

[http://ubuntuforums.org/showthread.php?t=804482](http://ubuntuforums.org/showthread.php?t=804482)

So generally, you needd to ensure the boot/grub/menu.lst is correct, and indicates the correct hd for each OS, hd(0,0) for fedora and hd(1,0) for ubuntu, or whatever they may be called.

---

### Post by ub007 on 2008-11-10
Thanks mate,but it doesnt seem to work for me...

I booted with the gparted live CD and i find the following:

/dev/hda1 ext3 /boot 196.08MB 18.32 used 177 unused
/dev/hda2 unknown 18.5 GB lvm


It shows the file system as unknown ,mayb cz its lvm(fedora creates lvm by default) and the Resize/Move option is greyed out!!!What do i do here?????


Cheers
David

---


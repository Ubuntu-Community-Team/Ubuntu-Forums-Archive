---
title: "[SOLVED] It wont mount my partition"
date: 2008-09-23
forum: New to Ubuntu
---

### Post by slughappy1 on 2008-09-23
I made several partitions on my hdd. I first made and installed a partition for Vista. I then made one for /boot, another for the rest of OS. And then finally an extra one for file sharing. I encrypted the Ubuntu installation by using a lvm and encrypting that. So my hdd looks like this:
```
/dev/sda1 -> NTFS ( Vista )
/dev/sda2 -> ext3 ( /boot )
/dev/sda3 -> ext3, lvm encrypted installation ( I think it's ext3 at least )
/dev/sda4 -> fat32 ( mounted during installation as /windows )
/dev/sda
```
But when I go to *Places* it isn't there. There is only the Vista partition. When I ```
ls /dev/sda*
``` it finds the other parition. But I want it to be up in the *Places* tab, or at least make it so that I don't have to always ```
sudo mount /dev/sda4 SomePlace
``` What can I do to fix/change this?

---

### Post by hyper_ch on 2008-09-23
what's in your fstab?

---

### Post by slughappy1 on 2008-09-23
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/mapper/lvm-root
UUID=e7fcfdaf-f8cc-4446-89aa-a18a6354db85 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda2
UUID=3fe02bcd-1e04-4ec0-b52a-6f55e79df698 /boot           ext3    relatime        0       2
# /dev/mapper/lvm-home
UUID=4d1b9a68-a8f0-43e3-84a2-3e6f331c2057 /home           ext3    relatime        0       2
# /dev/sda4
UUID=3659-58F0  /windows        vfat    utf8,umask=007,gid=46 0       1
# /dev/mapper/lvm-swap
UUID=5e5e75e5-796c-4f5e-8012-0a5ecf9be834 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

---

### Post by hyper_ch on 2008-09-23
so it is being mounted at /windows .... is that a problem?

---

### Post by slughappy1 on 2008-09-23
*slaps forehead. Oops, I didn't realize that it would be mounted there.

---

### Post by hyper_ch on 2008-09-23
well, if you want to have it mounted somewhere else, create that directory and then change fstab accordingly.

---

### Post by slughappy1 on 2008-09-23
If I were to change where it mounts it. 
[LIST=1]
[*]Would I just change the /windows to /What_ever_I_wanted?
[*]Would changing the mount point pose any problems?
[/LIST]

---

### Post by hyper_ch on 2008-09-23
> **slughappy1 said:**
> Would I just change the /windows to /What_ever_I_wanted?
no
> **slughappy1 said:**
> Would changing the mount point pose any problems
mights... some applications may look for certain files stored at the old mount point... like when you open OOo and then want to open a recent document that was on /winodws/yadda/yadda/some.odf

---

### Post by slughappy1 on 2008-09-23
Since you say no, then what would I change it to?

---

### Post by hyper_ch on 2008-09-23
whatever you want... if you want to have it appear in the "Places" I think it will need to be mounted somewhere in /media.... e.g. /media/windows

---

### Post by slughappy1 on 2008-09-23
Ok, thanks that worked. I changed /windows to /media/Shared ( after I created the dir Shared in /media ), and it worked. How about this one. Now how do I get it so it doesn't automatically appear on the Desktop?

---

### Post by hyper_ch on 2008-09-23
oh, you want to have it on the desktop?

I'd create a symlink

```

ln -s /media/Shared /home/USER/Desktop/Windows

```

replace USER with your username, then you should also be able to edit the symlink properties by right-clicking on it on the desktop and select another icon.

---

### Post by slughappy1 on 2008-09-23
No, that's the problem. I do NOT want it on my desktop. But when I changed the mount point from /windows to /media/Shared. I restarted my computer, and an icon showed up on my desktop "40.0 GB Media". When I created the partition for Vista, it shows up in Places ( which the 40.0 GB Media does as well now ), but the Vista partition does NOT show up on the desktop. I want to make the new partition just like the Vista partition.

---

### Post by hyper_ch on 2008-09-23
oh, I didn't read the "doesn't" ;)

I don't use gnome but go to your desktop settings... very likely there is an option to not display additional harddisks/partitions on the desktop.

---

### Post by slughappy1 on 2008-09-23
Ok, so I figured that part out thanks to [here]("http://www.daryl.mu/2008/03/30/howto-remove-desktop-mounted-volume-icons-in-ubuntu/"). So you can either do one of two things.
   
1 - In the terminal type
```
gconftool-2 --type boolean --set /apps/nautilus/desktop/volumes_visible false
```

or

1 - Make sure Configuration Editor shows up in Applications -> System Tools -> Configuration Editor
2 - Open the Configuration Editor, and un-click the volumes_visible box in /apps/nautilus/desktop/

---


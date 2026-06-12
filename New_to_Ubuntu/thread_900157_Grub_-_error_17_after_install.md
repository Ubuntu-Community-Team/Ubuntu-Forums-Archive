---
title: "Grub - error 17 after install"
date: 2008-08-25
forum: New to Ubuntu
---

### Post by antodena on 2008-08-25
dear all, hope that someone of you can help me.
i will start telling that i'm not totally new, but anyway i'm yet a beginner in linux world.
i will go stright to the problem only after a brief description of what i do:
i have on my system both vista and ubuntu 7.10 and all worked fine. both vista and ubuntu are installed on sata disks (i have two parallel too, old one anyway and only for download/backup purposes) and a boot manager was installed by ubuntu to manage the boot of both systems (i think was grub but im not sure).

anyway...

i downloaded the iso image of new ubuntu 8.04.1 and installed it.

it seems that all was fine, because at the next startup the bootmanager showed no more ubuntu 7.10 but the new 8.04.1.

i've selected ubuntu and BAM!

GRUB ERROR 17 (or something similar)

so i've restarted and selected vista and BUM!

BOOTMGR MANCANTE (BOOTMGR MISSING IN ENGLISH)

so i've putted vista install cd and fixed the MBR with the usual command.

everything returned to normality (only vista working anyway)

then i reinstalled hardy... and same error than before...

guys, can you help me? why this version of ubuntu won't install on my system?

waiting for your help.

---

### Post by tangibleorange on 2008-08-25
> **antodena said:**
> dear all, hope that someone of you can help me.
i will start telling that i'm not totally new, but anyway i'm yet a beginner in linux world.
i will go stright to the problem only after a brief description of what i do:
i have on my system both vista and ubuntu 7.10 and all worked fine. both vista and ubuntu are installed on sata disks (i have two parallel too, old one anyway and only for download/backup purposes) and a boot manager was installed by ubuntu to manage the boot of both systems (i think was grub but im not sure).

anyway...

i downloaded the iso image of new ubuntu 8.04.1 and installed it.

it seems that all was fine, because at the next startup the bootmanager showed no more ubuntu 7.10 but the new 8.04.1.

i've selected ubuntu and BAM!

GRUB ERROR 17 (or something similar)

so i've restarted and selected vista and BUM!

BOOTMGR MANCANTE (BOOTMGR MISSING IN ENGLISH)

so i've putted vista install cd and fixed the MBR with the usual command.

everything returned to normality (only vista working anyway)

then i reinstalled hardy... and same error than before...

guys, can you help me? why this version of ubuntu won't install on my system?

waiting for your help.

it seems like GRUB is not installing correctly. install both systems, and then boot into a Live CD. then, from the live CD, open a terminal, and type:

```
sudo grub
find /boot/grub/stage1
```

the output of the second command will be something like (hdx,y), where x and y are numbers. make a note of the numbers as they are important for the next commands. replace x and y in the following commands with the numbers returned from the above command:

```
root (hdx,y)
setup (hd0)
quit
```

that should have reinstalled grub to the MBR correctly. now reboot and see if all is well!

---

### Post by caljohnsmith on 2008-08-25
It sounds to me like the problem is with your /boot/grub/menu.lst, because from your description you obviously get the Grub menu just fine on startup. 
> **antodena said:**
> both vista and ubuntu are installed on sata disks (i have two parallel too, old one anyway and only for download/backup purposes) and a boot manager was installed by ubuntu to manage the boot of both systems (i think was grub but im not sure).
So are Ubuntu and Vista each on their own separate SATA HDD? And which HDD do you boot from? From the Live CD, please post the output of:
```
sudo fdisk -lu
```
From the above command, figure out which is your Ubuntu partition in the form sdXY, and then use that to mount your Ubuntu:
```
sudo mount /dev/sdXY /mnt
```
And then post your Grub's menu.lst:
```
cat /mnt/boot/grub/menu.lst

```
Also post the output of the Grub command tangibleorange gave:
```
sudo grub
grub> find /boot/grub/stage1 
```

---

### Post by antodena on 2008-08-25
hi guys, i've done what mr orange (:lolflag:) told me and despite the fact that the terminal tells that everything is done and ok, the system is booting with vista without asking me anything...

damn... this is strange. :confused:

tonight i will reinstall ubuntu 7.10 and see what happens... 8-[

thanks for your precious and valuable help, anyway i will let you know any news i find.

bye


dna

---


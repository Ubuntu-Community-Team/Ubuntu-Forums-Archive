---
title: "new with linux"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by lirazrom on 2008-08-24
hi
i downloaded ubunto desktop but installed it under windows cause i wanted to try it with out playing with my disks.
any way. i nstalled it and choose from the boot menu ubuntu
but it didnt entered the desktop , in showed me a cmd

when i tried to run after that from the disk it ignored the boot and when i tried with "force" he said something about grub error

and cannot uninstall it 

what to do?
i have 3 harddisks so i can install on one but the boot is from other harddisk

thanks

---

### Post by b0n60 on 2008-08-24
It's possible that Ubuntu has overwritten the Windows (?) bootloader so that might be bad for you...
it seems like you installed ubuntu with the non-clean ntfs installer which i personally not like ... a linux distro belongs to ext filesystems ;) 

anyway can you tell me how the commandline looks? try type startx or startkde if you have it...

i made an experience with my machine that you can't boot from the Windows HARDDISK, only from my clean Grum managed Ubuntu HD...

The easiest way, because you didn't worked a lot on Ubuntu is to let the installer make you a new ext3/2 partition on a seperate Harddisk so you have 2 clean OS's wich you can work
 
Hope that helped

  {
   gr33z
        bongo fr0m Germany
                           }

---

### Post by lirazrom on 2008-08-24
ok

first it asks me to press esc if i want to choose from the menu

in the mebu i have many start installer
i choose start installer in normal mode

in the command line

busy box v1.1.3 (debian 1:1.1.3-5 ubuntu12) buil-in shell (ash)

(initramfs)

when i type exit, i get

ext3-t3 group descriptors corrupted

all the intall sits on drive c , while xp is on e

tnaks

---

### Post by ajgreeny on 2008-08-24
Can you boot into windows?  If not, let's get that running first by using youe windows XP or Vista disk and using the fixmbr in XP's recovery mode (or some similar title) and doing the same in Vista, though I have no knowledge of Vista, (and intend to stay that way!).

Having got windows up and running, I would suggest that now is the time to try getting rid of the Wubi installation and then doing a proper dual booting installation of Ubuntu.  There are lots of sites which show you how to do that and you should start [here]("http://www.psychocats.net/ubuntu/installing").

Good luck, and I hope this is helpful.

---

### Post by lirazrom on 2008-08-24
but how to uninstall?

it is not responding when i try to uninstall

xp works fine

---


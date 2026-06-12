---
title: "will linux work with vista 64"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by arsenal69 on 2008-11-11
Hello to everyone in this community.
I have a windows vista 64 home edition notebook..
i am a software engineer.. and now i am seeking to switch back and forth between windows and linux.
i have already order the ubuntu live cd.

i want to know how to setup a parallel boot startup for linux and which version of linux will work..


how can i use ubuntu with the present os i have

---

### Post by SunnyRabbiera on 2008-11-11
yes you can easily dual boot between Vista any version with Ubuntu any version.
Also the version of Ubuntu you will probably want is the desktop edition, and perhaps you may wish to use Hardy as Ibex is still new and many have had issues with it.

---

### Post by DoubleMcLovin on 2008-11-11
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm]("http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm")

That link should help you quite a bit.

---

### Post by MuH4hA on 2008-11-11
I think Windows Vista Home Edition has no Bitlocker, so a Dualboot-System will work just as usual.

You need another Partition for your Ubuntu. If possible the /home directory should be on a seperate Partition.

The installer will guide you through the steps of setting up the partitions (you can google for the best way to do it) and then install a boot-manager.
The Boot-manager (GRUB) will allow you to chose the OS you want to boot after you turn on your PC.

Hope, that helped...

---

### Post by Keen101 on 2008-11-11
yes, it should be fine. A dual boot is probably what you want. OF course if you are the type who is scared of partitioning, then you could try a WUBI install. But, i recommend a real dual boot over a wubi install.

The live-cd should help you partition easily. You probably will want ubuntu 64bit. [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

The cd will automatically install the GRUB bootloader, which will let you choose windows or linux at boot.

---


---
title: "[SOLVED] External usb drive setup through /etc/fstab"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by matsaga on 2008-06-12
Hi all,

I've recently bought a Seagate freeagent external usb drive. I repartitioned it with several partitions. The OS mounts them without any trouble. However, the mounting media changes between mounts (ie. /dev/sdb6 can be any of /media/disk-1, /media/disk-2, etc.). This is an issue for me as I have some software that need a constant path to access a specific partition. 

I have had some success by adding the following lines to my /etc/fstab:
/dev/sdb6   /external/music   vfat   user   0	0
/dev/sdb7   /external/docs    vfat   user   0	0
/dev/sdb8   /external/downloads	vfat user   0	0

This ensures that the partitions will always be mounted into the correct folder and works well if the external drive is already on when I boot the OS. However, this doesn't work if I turn on the external drive when I'm already logged into the system. 

In that case, the following popup displays:
[B]Cannot mount volume.
You are not privileged to mount this volume.[/B]

Would anyone have any ideas how to allow mounting these partitions both at boot time and when the system is already started?

Thanks,

Matt

---

### Post by gr4nf on 2008-06-12
I don't know if this would be overly troubling, but you could write a shell script to mount them for you:
```

sudo mount /dev/something /media/something
sudo mount /dev/something_else /media/something_else
etc...

```
and then put the file in /usr/local/bin, and run the command:
```

chmod +x

```
on it. Then, whenever you have a shell, just type the command and run it, and it will mount all of your volumes, without the error.

---

### Post by kansasnoob on 2008-06-12
For hot-plugging USB devices I've found that installing usbmount or, if prefered, both pmount and hal to be simple and straight forward.

The only advantage of pmount + hal over usbmount is that a desktop icon pops up on the desktop automatically when most devices are plugged in. Of course either can be done using synaptic or apt. (I prefer synaptic)

---

### Post by matsaga on 2008-06-14
Hi Gr4nf and Kansasnoob,


I played with your solutions for a while and then found out that I could change the mount point of a disk by right-clicking it -> properties -> volume -> Mount point. It seems to edit some gnome registry key used by hal. 


Anyway, thank you for your answers, they will help me down the line once I'll need something a bit more configurable than the properties -> volume tab or if I move away from Gnome.

Matsaga

---


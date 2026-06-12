---
title: "Dvd/cd drive does not show up but still mechanically functions"
date: 2012-03-18
forum: New to Ubuntu
---

### Post by 1928Dodge on 2012-03-18
So I installed Ubunutu 11.10 as the sole OS. Initially when I inserted a DVD the autorun box popped up and said "What would you like to open to this disc with" or something to that extent. I then installed VLC and, to my knowledge, followed the Ubuntu guide for updating the codec library to play commercial DVDs. However, now I do not get that autorun box, despite the fact that the disc spins, and I can neither play DVDs or CDs. In VLC Player I get the error message if I try to play a CD:
>   p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'cdda:///dev/cdrom'. Check the log for details.[/COLOR]

If I try to play a DVD via "/dev/dvd" (because when I browse for the DVD/CD drive it does not show up) I get:
>   p, li { white-space: pre-wrap; }  [COLOR=#ff0000]Playback failure:[/COLOR]
 [COLOR=#000000]DVDRead could not open the disc "/dev/dvd".[/COLOR]
 [COLOR=#ff0000]Your input can't be opened:[/COLOR]
 [COLOR=#000000]VLC is unable to open the MRL 'dvdsimple:///dev/dvd'. Check the log for details.[/COLOR]


Can someone guide me trough the process of getting the DVD/CD drive to be recognised/mounted, etc... ?

---

### Post by sandyd on 2012-03-18
> **1928Dodge said:**
> So I installed Ubunutu 11.10 as the sole OS. Initially when I inserted a DVD the autorun box popped up and said "What would you like to open to this disc with" or something to that extent. I then installed VLC and, to my knowledge, followed the Ubuntu guide for updating the codec library to play commercial DVDs. However, now I do not get that autorun box, despite the fact that the disc spins, and I can neither play DVDs or CDs. In VLC Player I get the error message if I try to play a CD:

If I try to play a DVD via "/dev/dvd" (because when I browse for the DVD/CD drive it does not show up) I get:


Can someone guide me trough the process of getting the DVD/CD drive to be recognised/mounted, etc... ?
Can you still mount the drive manually?
```

mkdir tmp
sudo mount /dev/dvd tmp
```

---

### Post by 1928Dodge on 2012-03-18
> Can you still mount the drive manually?
 	Code:
 	mkdir tmp sudo mount /dev/dvd tmp 

I tried that and got a long response that says:
> Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
molly@molly--PC:~$ mkdir temp^C
molly@molly--PC:~$ mkdir tmp
 
  Alas, maybe I entered in wrong? DVDs still spin, but does not show up anywhere.

---

### Post by 1928Dodge on 2012-03-19
I wound up rerunning the boot repair disc and then when I rebooted Ubuntu it remounted the DVD drive. Everything works perfect now.

---


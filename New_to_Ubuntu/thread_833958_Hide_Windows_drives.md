---
title: "Hide Windows drives"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by Tim Silver on 2008-06-19
Hi,

I dual boot to Ubuntu 8.04 on an external USB HDD. The GRUB is on the external drive, XP is on my internal drive - no partitions - I like to keep everything completely separate.

When I go to 'Places', my internal hard drive is listed in the drop-down menu (although Windows does not see my external drive).

Is there a way that I can stop the heron from seeing my Windows hard drive?

The reason I ask this is because I like a 'tipple' of an evening and I would like to completely remove the possibility of accidentally/stupidly accessing my Windows drive from within the heron (I wonder how he feels about me being 'within'?:lol:)

---

### Post by ConMan318 on 2008-06-19
Well you could rename the drive from the command line so it doesn't show up.  If you do:
```

mv filename .filename

```

It just renames the file with a period in front of it.

It will turn 'filename' into a hidden file, so it doesn't clutter things up.  If you want to see it in the command line with 'ls', you would use 'ls -a'.  There is also a way to see it in the GUI with Alt + something or other.  Basically you couldn't access it accidentally, so I think it'd fit your needs.

---

### Post by iaculallad on 2008-06-19
Try the Python Storage Device Manager (pysdm) utility. Download it using your apt-get command:

```
sudo apt-get install pysdm
```

After your successful download, access it from System->Administration->Storage Device Manager and control your storage devices.

---

### Post by hyper_ch on 2008-06-19
in /etc/fstab you should have an entry for the windows drive... so you could just comment it out by adding a # at the beginning of the line. Then it shouldn't appear any longer.

---

### Post by Tim Silver on 2008-06-19
Right guys,

Now I'm confused (and scared)!

hyper_ch

The contents of /etc/fstab as follows
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sdb1
UUID=1fbc97bb-da84-46ae-8428-b5fca63f17c2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb5
UUID=b83e4fef-12f9-422c-a434-f029010971eb none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Internal HD doesn't seem to be listed so no idea what to do here!

iaculallad,

I installed 'pysdm' and in the partition list I've got sda ( containing sda1, sda2, sda3 and sda4) and sdb (which contains sdb1 and sdb5).

When I click on any partition I get a message box saying it hasn't been configured yet, do I want to configure now? OK and Cancel buttons. Guess what? I cancelled!

What has confused me even more is that if I select say, sda2, the message reads /dev/sda2 hasn't been configured, or if I select sdb1, the message then reads /dev/sdb1 hasn't been configured. OK, that makes sense. However, if I select _sda1_, the message reads _sdb5_ hasn't been configured.

Needless to say, I haven't configured any of them as I don't know what I'm doing!:?::!:

Any further help much appreciated.

---

### Post by Gannon8 on 2008-06-19
The windows drive doesn't seem to be mounted. If the drive isn't mounted, then ubuntu cannot do anything unless you use a partition editor or a disk formatting command on it(You probably will not use any of these).

The drive will still appear on ubuntu as long as it is connected, but will not mount unless you either open the drive or mount it with a command or other program.

For the configuration, I think that means setting stuff like the mount point. I am not exactly sure.

---

### Post by Tim Silver on 2008-06-20
Hi Gannon8,

Indeed, the Windows is not mounted - I now see why it's not in the list in. My point is that I don't want to be able to mount my Windows drive. I want to protect that part of my computer from me! Is there no way I tell the heron to ignore FAt32?

---

### Post by BlackDragonBE on 2008-06-20
If it ignores FAT32, it will ignore USB-sticks too.
Why don't you configure it so only root can mount and access it?

---

### Post by Tim Silver on 2008-06-20
Ah,

Didn't consider that!

I guess it's time to be brave and explore pysdm then.

---

### Post by iaculallad on 2008-06-20
> **Tim Silver said:**
> 
iaculallad,
I installed 'pysdm' and in the partition list I've got sda ( containing sda1, sda2, sda3 and sda4) and sdb (which contains sdb1 and sdb5).

When I click on any partition I get a message box saying it hasn't been configured yet, do I want to configure now? OK and Cancel buttons. Guess what? I cancelled!

What has confused me even more is that if I select say, sda2, the message reads /dev/sda2 hasn't been configured, or if I select sdb1, the message then reads /dev/sdb1 hasn't been configured. OK, that makes sense. However, if I select _sda1_, the message reads _sdb5_ hasn't been configured.

Needless to say, I haven't configured any of them as I don't know what I'm doing!:?::!:

Any further help much appreciated.

When it say's that it has not been configure yet, it only means that it has not been initialized by pysdm, it's safe to click on OK. Select the partition you want to protect and use the "Assistant" button if you don't know where to start.

---


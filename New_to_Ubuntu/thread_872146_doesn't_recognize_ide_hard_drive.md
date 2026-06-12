---
title: "doesn't recognize ide hard drive"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by PLANETARY on 2008-07-27
I have a computer with a 500gb sata drive and a 150gb ide drive. I want to have kubuntu and xp on the ide drive and the sate for storage. earlier i couldn't get kubuntu to work on my sata drive so i decided it would be smarter to use ide. anyways the kubuntu installer doesnt recognize the ide drive, on the live cd i cant access it. in windows xp i can though. only the sata drive shows up with the partitions i made earlier (xp, swap, ext3, stuff). i made partitions for linux using partition magic. (which was a bad idea) the swap and ext3 are still on there, could that be the problem? how can i get the ide drive to mount? 
Thanks

Alex

---

### Post by Pro-reason on 2008-07-27
Is it actually not recognising the drive at all, or have you simply not managed to mount it?

Does it show up if you open GParted?

Does it show up in the output of commands such as "sudo fdisk -l" and "sudo blkid"?

---

### Post by PLANETARY on 2008-07-27
in the installer the ide drive does not show up at all. in live it does  but i cant access it.

i dont know what Gparted is and i havent done those commands

---

### Post by halitech on 2008-07-27
Gparted is a Graphical Partition manager application.

run the above commands and see if Ubuntu sees the drive at all

---

### Post by Pro-reason on 2008-07-27
> **PLANETARY said:**
> in the installer the ide drive does not show up at all. in live it does  but i cant access it.

i dont know what Gparted is and i havent done those commands

What do you mean by "live"?  Do you mean that an icon appeared on your desktop while you are in a live CD session?

I'm surprised that it did that if it didn't appear in the partitioning phase of the installer.

I believe that GParted is installed by default, and that you'll find it in the application menu somewhere.

If you haven't run those commands, then run them!  Open the Terminal program, and type the commands.

You can also run GParted from the terminal.  Do these commands:

```

sudo apt-get install gparted
gksudo gparted

```

---

### Post by PLANETARY on 2008-07-27
i dont remember if the ide hd appeared on the desktop but in a system menu it did like a 'my computer' window. so i have to run those commands in the live cd right? I cant do that durring the 'just install kubuntu'selection on the cd menu, right? another problem that i ran into is that if i am in the live cd i double click the install icon and the install window doenst come up, so thats why i 'have' to 'just install kubntu'
i hope that made sense

---

### Post by Pro-reason on 2008-07-27
Yes, those commands will work just fine whether you have Ubuntu installed or are running it from a live CD.

---

### Post by PLANETARY on 2008-07-29
i entered the sudo fdisk command and it didnt show up. i looked in th e storage window and permission denied came up when i tried to open it. i  installed gparted though i couldnt get gksudo to work. i tried to install gk and it failed. i dont know what to do

when i am running kubuntu live i still cant get the install 'wizard' to open, i have to intall from the cd menu. i dont know what to do

---

### Post by halitech on 2008-07-29
you need to do
```
sudo fdisk -l
``` lowercase L, not a 1

you are using Kubuntu, I don't think for installing its sudo apt-get install, I think you need to use adept to install (not sure, never used kubuntu)

---

### Post by PLANETARY on 2008-07-29
i did do lowercase l

---

### Post by Pro-reason on 2008-07-29
> **PLANETARY said:**
> i did do lowercase l

Please enter each of the following commands into the terminal, and paste the exact result here between [noparse]```
...
```[/noparse] tags.

```

cat /etc/fstab
sudo blkid
sudo lshw -C disk

```

---

### Post by PLANETARY on 2008-08-05
ok well i tried to install ubuntu and same thing. here is the code
```

 ubuntu@ubuntu:~$ cat /ect/fstab
cat: /ect/fstab: No such file or directory
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="E2484D14484CE93D" LABEL="stuff" TYPE="ntfs"
/dev/loop0: TYPE="squashfs"
ubuntu@ubuntu:~$ sudo lshw -C disk
  *-cdrom:0
       description: CD-R/CD-RW writer
       product: CD-R/RW SW-252B
       vendor: SAMSUNG
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: R701
       serial: [SAMSUNG CD-R/RW SW-252B R701EXP
       capabilities: removable audio cd-r cd-rw
       configuration: ansiversion=5 status=open
  *-cdrom:1
       description: DVD reader
       product: DVD-ROM SD-816B
       vendor: SAMSUNG
       physical id: 0.1.0
       bus info: scsi@1:0.1.0
       logical name: /dev/cdrom1
       logical name: /dev/dvd1
       logical name: /dev/scd1
       logical name: /dev/sr1
       logical name: /cdrom
       version: H002
       capabilities: removable audio dvd
       configuration: ansiversion=5 mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted status=ready
     *-medium
          physical id: 0
          logical name: /dev/cdrom1
          logical name: /cdrom
          configuration: mount.fstype=iso9660 mount.options=ro,noatime,relatime state=mounted
  *-disk
       description: ATA Disk
       product: ST3500630AS
       vendor: Seagate
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 3.AA
       serial: 6QG2BPPP
       size: 465GiB (500GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=00000001

```

---

### Post by PLANETARY on 2008-08-06
Bump. i dont understand whats wrong. earlier i had problems with xp with ide drives when i took them out and put them back in. they were unaccessable and i used easyrecovery to get my data back, then formatted. i dont see why (k)ubuntu wont see them.

---

### Post by Pro-reason on 2008-08-07
> **PLANETARY said:**
> ok well i tried to install ubuntu and same thing. here is the code
```

 ubuntu@ubuntu:~$ cat /**ect/**fstab
cat: /**ect**/fstab: No such file or directory
```
The first thing to do when that happens is to check your spelling.

> **PLANETARY said:**
> Bump. i dont understand whats wrong. earlier i had problems with xp with ide drives when i took them out and put them back in. they were unaccessable and i used easyrecovery to get my data back, then formatted. i dont see why (k)ubuntu wont see them.

It really seems that Ubuntu cannot see that other drive at all.  I presume that it is either damaged or the physical connection is not fully there.  If you boot the XP installation CD, can it see the drive?  I suspect that no system will be able to see it, because something has happened to it.

---

### Post by PLANETARY on 2008-08-13
your right. a few months ago xp stopped working and i determined it was the hd. i bought a big sata drive. i tried using the 'broken' drive and saw that i could put stuff on it after a format. i thought it was fine but i guess its not all there. i am now working on installing it else where. thanks

---


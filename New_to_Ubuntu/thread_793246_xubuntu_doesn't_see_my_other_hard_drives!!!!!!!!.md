---
title: "xubuntu doesn't see my other hard drives!!!!!!!!"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by sleeper414 on 2008-05-13
just installed xubuntu on my older P3 desktop.
i was running gutsy but it was too slow.
anyway, xubuntu installed flawlessly, and evrything would be fine, but i have two additional internal hard drives that xubuntu wont see.
its not in /media......they arent anywhere!

help!!!!!

---

### Post by Inxsible on 2008-05-13
Please post the output of the following 2 commands```
sudo fdisk -l
```-l is lowercase L and```
df -h
```

---

### Post by sleeper414 on 2008-05-13
thank you...

chris@chris-desktop:~$ sudo fdisk -l
[sudo] password for chris: 

Disk /dev/sda: 20.4 GB, 20416757760 bytes
255 heads, 63 sectors/track, 2482 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa74ba74b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2389    19189611   83  Linux
/dev/sda2            2390        2482      747022+   5  Extended
/dev/sda5            2390        2482      746991   82  Linux swap / Solaris

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3860385f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1        4865    39078081    c  W95 FAT32 (LBA)

Disk /dev/sdc: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e4de019

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1           13036       19457    51584715    b  W95 FAT32
/dev/sdc3               1       13035   104703606    b  W95 FAT32

Partition table entries are not in disk order

---

### Post by sleeper414 on 2008-05-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  2.4G   15G  14% /
varrun                125M  100K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   64K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   38M   88M  30% /lib/modules/2.6.24-16-generic/volatile

---

### Post by Inxsible on 2008-05-13
Ubuntu is seeing the drives. Check the output of fdisk -- sdb(40GB) and sdc(160GB).

They are not mounted however as noted by df -h. You need to mount them in order to see them.

First create a mount point```
sudo mkdir /mnt/myFirstDrive && sudo mkdir /mnt/mySecondDrive && sudo mkdir /mnt/myThirdDrive
``` Your 160GB has 2 partitions and will therefore need a separate mount point if you want to access that as well. Generally internal drives are mounted under /mnt. But this is not necessary and you can mount them anywhere you like. for eg. /windows or /storage or /mnt/Storage etc. Just make sure you dont have spaces or special characters in the name. Trust me it will be more easier that way. After you create the mount points simply add them to fstab by this command```
gksudo mousepad /etc/fstab
``` Add the following lines to fstab```
/dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0
```Make sure you use the same mount points that you created in the 1st step. Save the file and then do ```
sudo mount -a
```

---

### Post by sleeper414 on 2008-05-13
i understand mountijng, but in ubuntu it was graphical, doesnt appear to be the case in Xubuntu.

do i just sudo mount /media/xxxx?

or are there drivers and the like i could download in synaptic to enable the use of GUI?

---

### Post by rockerphil on 2008-05-13
well it's pretty simple, /dev/sdb and /dev/sdc are your 2 other internal hard drives, now all you've gotta do is mount them, so just create your mount points wherever you want them, say /home/<username>/storage and /home/<username>/storage2

then just run this code

sudo mount /dev/sdb /home/<username>/storage

sudo mount /dev/sdc /home/<username>/storage2

---

### Post by sleeper414 on 2008-05-13
it shouldnt be this difficult.

 gksudo gedit /etc/fstab
chris@chris-desktop:~$ /dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdb2: Permission denied

permission denied....

--------
aslo, im not sure how to mount anything. 
in ubuntu it just worked.
/home/media 

rocker phil. i followed you directions too. after running the /home/username location, it said file not found.

---

### Post by Inxsible on 2008-05-13
> **sleeper414 said:**
> it shouldnt be this difficult.

 gksudo gedit /etc/fstab
chris@chris-desktop:~$ /dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdb2: Permission denied

permission denied....

--------
aslo, im not sure how to mount anything. 
in ubuntu it just worked.
/home/media 

rocker phil. i followed you directions too. after running the /home/username location, it said file not found.
You have to add the line to the fstab that you opened using the gksudo mousepad /etc/fstab command. You have put that entire line on the terminal !!!!

BTW...Xubuntu also uses Gnome services. so its the same in Ubuntu and Xubuntu. Just that Ubuntu recognized your drives because you must have mounted them during the install whereas Xubuntu didn't.

---

### Post by sleeper414 on 2008-05-13
i got the triple whammy!

chris@chris-desktop:~$ sudo mkdir /mnt/myFirstDrive && sudo mkdir /mnt/mySecondDrive && sudo mkdir /mnt/myThirdDrive
mkdir: cannot create directory `/mnt/myFirstDrive': File exists
chris@chris-desktop:~$ gksudo gedit /etc/fstab
chris@chris-desktop:~$ /dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdb2: Permission denied
chris@chris-desktop:~$ /dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdc1: Permission denied
chris@chris-desktop:~$ /dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0



im assuming its saying file exists because ive ran the command b4, so i just went to the next step.

sorry about the last comments, im just frustrated. no biggie....beats the crap out of windows anyday.

---

### Post by rockerphil on 2008-05-13
what i meant is that you need to create files for your hard drives to mount to first, those were just examples. you need to put the name of your home folder where it says <yourusernamehere>. the terminal command would be

mkdir /home/<yourusernamehere>/storage (press enter here)

and

mkdir /home/<yourusernamehere>/storage2 (press enter here)

then just run

sudo mount /dev/sdb /home/<yourusernamehere>/storage (press enter here)

and

sudo mount /dev/sdc /home/<yourusernamehere>/storage2

and that should do the trick

---

### Post by Inxsible on 2008-05-13
> **sleeper414 said:**
> i got the triple whammy!

chris@chris-desktop:~$ sudo mkdir /mnt/myFirstDrive && sudo mkdir /mnt/mySecondDrive && sudo mkdir /mnt/myThirdDrive
mkdir: cannot create directory `/mnt/myFirstDrive': File exists
chris@chris-desktop:~$ gksudo gedit /etc/fstab
chris@chris-desktop:~$ /dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdb2: Permission denied
chris@chris-desktop:~$ /dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
bash: /dev/sdc1: Permission denied
chris@chris-desktop:~$ /dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0



im assuming its saying file exists because ive ran the command b4, so i just went to the next step.

sorry about the last comments, im just frustrated. no biggie....beats the crap out of windows anyday.You are not following instructions as listed. the three lines starting with "/dev" THEY ARE NOT SUPPOSED TO BE ENTERED IN THE TERMINAL. when you perform the ```
gksudo mousepad /etc/fstab
``` command, it will open up a file. The 3 lines starting with "/dev" need to be added to that file. Then save the file and close it.

Then BACK on the terminal do ```
sudo mount -a
```

---

### Post by sleeper414 on 2008-05-13
quick question. when i installed Ubuntu, i had these internal hard drives, pluged as in, connected.
 when i installed Xubuntu, they were disconnected. is it logical to assume that this is why im struggling with this?

---

### Post by Inxsible on 2008-05-13
> **sleeper414 said:**
> quick question. when i installed Ubuntu, i had these internal hard drives, pluged as in, connected.
 when i installed Xubuntu, they were disconnected. is it logical to assume that this is why im struggling with this?YES !!!!

---

### Post by sleeper414 on 2008-05-13
oh brother!

---

### Post by sleeper414 on 2008-05-13
thanks for your help!

---

### Post by rockerphil on 2008-05-13
here's the thing, the normal Ubuntu auto-mounts all drives, where as Xubuntu only mounts the drive containing the OS, so you need to manually mount them

---

### Post by Inxsible on 2008-05-13
> **sleeper414 said:**
> oh brother!Its easily fixable. Just follow the instructions that I gave you. But please READ first and then perform them.

---

### Post by sleeper414 on 2008-05-13
ok, im going to do this as literally as possible. starting with rocker phils generous advise.

----------
opening terminal...........

chris@chris-desktop:~$ mkdir /home/<chris>/storage
bash: chris: No such file or directory
chris@chris-desktop:~$ 
-----------------

now, for inxisbles.....

chris@chris-desktop:~$ sudo mkdir /mnt/myFirstDrive && sudo mkdir /mnt/mySecondDrive && sudo mkdir /mnt/myThirdDrive
[sudo] password for chris: 
chris@chris-desktop:~$ gksudo gedit /etc/fstab
chris@chris-desktop:~$ 

--------a file is supposed to open for me? it didnt happen.

---

### Post by sleeper414 on 2008-05-13
i give up. im reinstalling ubuntu. at least it worked.
if ubuntu want windows users (and grandma's) to switch...the terminal has to go.

thanks for your help guys. i truly mean that.

---

### Post by Inxsible on 2008-05-13
Try this again once and see if it works this time:

you have already created the mount points /mnt/myFirstDrive etc...so you dont need to do those again.
Now ```
gksu mousepad /etc/fstab
``` This should open up a file. Then add the following lines to the file```
/dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0
``` Save and close the file. then back in the terminal do ```
sudo mount -a
```

---

### Post by jimbofluffy on 2008-05-14
> **Inxsible said:**
> Ubuntu is seeing the drives. Check the output of fdisk -- sdb(40GB) and sdc(160GB).

They are not mounted however as noted by df -h. You need to mount them in order to see them.

First create a mount point```
sudo mkdir /mnt/myFirstDrive && sudo mkdir /mnt/mySecondDrive && sudo mkdir /mnt/myThirdDrive
``` Your 160GB has 2 partitions and will therefore need a separate mount point if you want to access that as well. Generally internal drives are mounted under /mnt. But this is not necessary and you can mount them anywhere you like. for eg. /windows or /storage or /mnt/Storage etc. Just make sure you dont have spaces or special characters in the name. Trust me it will be more easier that way. After you create the mount points simply add them to fstab by this command```
gksudo mousepad /etc/fstab
``` Add the following lines to fstab```
/dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0
```Make sure you use the same mount points that you created in the 1st step. Save the file and then do ```
sudo mount -a
```

Didn't know the best way to do this in Xubuntu, but this sure was quick and easy.  Thanks.

---

### Post by gn2 on 2008-05-14
Or just add Storage Device Manager in Add/Remove or Synaptic or ```
sudo apt-get install pysdm
```

[http://pysdm.sourceforge.net/](http://pysdm.sourceforge.net/)

---

### Post by ubu2 on 2008-07-13
i am new to Ubuntu and have a similar problem. I have two 20 GB hard drives on my computer and xubuntu will not see my second hard drive. Can some one help? Thanks a lot.

I have posted the output from the sudo fdisk -l and df -h commands below:

Disk /dev/sda: 20.4 GB, 20491075584 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21cc21cb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2399    19269936   83  Linux
/dev/sda2            2400        2491      738990    5  Extended
/dev/sda5            2400        2491      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0e700e70

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        2434    19551073+   5  Extended




Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              19G  4.1G   14G  24% /
varrun                125M  232K  125M   1% /var/run
varlock               125M     0  125M   0% /var/lock
udev                  125M   48K  125M   1% /dev
devshm                125M     0  125M   0% /dev/shm
lrm                   125M   39M   86M  32% /lib/modules/2.6.24-19-generic/volatile
gvfs-fuse-daemon       19G  4.1G   14G  24% /home/u/.gvfs

---

### Post by Codereaper on 2008-12-09
I followed the instructions on this post to mount my old 20gb hard drive to my Xubuntu Intrepid desktop.
but after fource mounting it i used Gparted to format the drive and seperate it into a SWAP Extended partition and a STORAGE Primary partition.

after applying these changes and turning SWAP-ON the SWAP drive is working flawlessly and the sytem monitor is using and registering it.

The Storage Drive on the other hand is not. Gparted brings up several Error messages as to why it cant be mounted and because the drive was force mounted i cant unmount it. when trying to umount it in Terminal the drive always appears to be in use even when gparted isnt running and the swap drive is switched off. is there any way i can force unmount the partition and remount it? I'm not sure but i think the original settings i changed in FSTAB are disagreeing with the changes i made using Gparted.


an intresting side affect in all this (but not realated to the problem) was that i also managed to somehow unknowingly format my mp3 player to linux-Swap. rendering it uterly useless as a stand alone music player and leaving me with a rather large linux removable swap drive :s

---

### Post by No1Joker on 2008-12-10
> **Inxsible said:**
> Try this again once and see if it works this time:

you have already created the mount points /mnt/myFirstDrive etc...so you dont need to do those again.
Now ```
gksu mousepad /etc/fstab
``` This should open up a file. Then add the following lines to the file```
/dev/sdb2 /mnt/myFirstDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc1 /mnt/mySecondDrive vfat iocharset=utf8,umask=000 0 0
/dev/sdc3 /mnt/myThirdDrive vfat iocharset=utf8,umask=000 0 0
``` Save and close the file. then back in the terminal do ```
sudo mount -a
```

Hello Guys, bit of a noob so go gentle.
Installed Xubuntu onto a 40gb HD, i also have a 80gig (currently has winXp installed) I (think!) i want to mount it so Xubuntu can see it then format it so its free for new data.

I have done step one and thats worked fine
I have done step two by adding the line in the fstab

but when i do "sudo mount -a" i get 
[mntent]: warning: no final newline at the end of /etc/fstab

Any ideas plz, cheers.

EDIT: I feel like a nooby numpty, all i had to do was press enter after entering the info in step 2 so the cursor was on a newline. Now i need to format that drive which i am sure is on here somewhere!

---

### Post by northwestuntu on 2009-02-26
> **rockerphil said:**
> here's the thing, the normal Ubuntu auto-mounts all drives, where as Xubuntu only mounts the drive containing the OS, so you need to manually mount them

is there a program or a future version of xubuntu that will automount. so much easier.

---

### Post by fjolnir on 2010-01-16
I had the same problem with my second hard drive(with 2 partitions) and i get it to surface thanks to guidance I got here.I had a problem because my hard is ntfs formated but I changed vfat with ntfs and all was fine.
      Thank you for the advice!:P:P:popcorn:

---


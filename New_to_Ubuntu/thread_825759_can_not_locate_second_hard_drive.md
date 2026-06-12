---
title: "can not locate second hard drive"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by TimmyR41 on 2008-06-11
i have xubuntu installed but it only recogonizes the 60 gig hard drive i installed xubuntu on.  i have a second 80 gig hard drive which contains all my music, files etc. that is not recognized.  i was told in another thread to post the command output to sudo fdisk -l so here it is.

sudo fdisk -l```
Disk /dev/sda: 60.0 GB, 60000000000 bytes
255 heads, 63 sectors/track, 7294 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        7202    57850033+  83  Linux
/dev/sda2            7203        7294      738990    5  Extended
/dev/sda5            7203        7294      738958+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x01405624

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS

```

any help i could get would be great.  thanks.

---

### Post by Inxsible on 2008-06-11
Have you mounted the drive ?Is this an external drive or internal?

If internal :
1) ```
sudo mkdir /mnt/My80GigDrive && sudo mount /dev/sdb1 /mnt/My80GigDrive
``` Of course you can name it anything you like instead of My80GigDrive, for eg. MyData ot MyMusic or stuff etc. Please avoid spaces in the name.

2)If external:```
sudo aptitude install pmount && sudo pmount /dev/sdb1 My80GigDrive
``` again you have have any name you like. The second method will automatically create "My80GigDrive" or whatever you name it under /media

---

### Post by TimmyR41 on 2008-06-11
it is an internal.  i can't find the drive to mount it.  i am really new to this so i don't even really know where to begin.

---

### Post by Inxsible on 2008-06-11
> **TimmyR41 said:**
> it is an internal.  i can't find the drive to mount it.  i am really new to this so i don't even really know where to begin.
Just enter the commands that i gave you in step 1 in a terminal (Applications>>Accessories>>Terminal). 
If you want to know what the commands do: It creates a directory under /mnt called "My80GigDrive" and then the second part mounts your 80 gb drive in that folder that you created

---

### Post by TimmyR41 on 2008-06-11
ok, thanks.  as i look at the output code that i posted and the code you gave me to input stuff is kinda starting to make sense.  it seems there just a bit of a learning curve associated with this stuff.  i'm sure i'll get the hang of it eventually.  i'm used to running windows xp where i hardly ever use command lines and the like.  thanks for the help.

---

### Post by Victormd on 2008-06-11
This can also be related to the last time you used windows. If you didn't shut down properly, windows will lock your HD... If you can't get it to work with the above suggestions (and you're dual-booting), boot to windows and shut down properly and that should do the trick. To have it automount during startup, check out the link on my signature...

---

### Post by TimmyR41 on 2008-06-11
i am not dual booting.  i totally wiped the 60 gig hard drive (which contained my operating system as well as my windows programs)when i installed xubuntu.

---

### Post by Victormd on 2008-06-11
Well, can you remember if the last time you used windows, you shut down properly? Or did you simply do a hard reset since you knew you were going to install Xubuntu? If this is the case, you might have to connect this HD to a comp. with windows and shut down properly before xubuntu will recognize it...

---

### Post by Inxsible on 2008-06-11
did the above mentioned mount not work for the op ?

He probably hadn't mounted the drive that's all.

---

### Post by aktiwers on 2008-06-11
Or add it to fstab like this, then it should be mounted on every boot automatically:

Start out by making a folder for it:
```
 sudo mkdir /media/80gigdrive
```

Then open up fstab in a text editor:
```
sudo gedit /etc/fstab
```

And copy these linies to the end of that document:
```
#/dev/sdb1 
/dev/sdb1 /media/80gigdrive ntfs users,gid=users,ro,umask=0222,utf8=true 0 0 			 		
```

And save the file..

Then just run this to let it take effect:
```
sudo mount -a
```

---

### Post by TimmyR41 on 2008-06-11
the last time i shut down windows i did shut it down properly.  i am at work right now so i haven't been able to try any of the solutions as of yet.  i will try them when i get home tonight.  it would be much easier if i could get my internet working properly because then i could post on the forum while i was inputing the code.  currently i have another open thread titled having trouble with wireless.  i have a few things to try there as well.  thanks for all the help.

---

### Post by Inxsible on 2008-06-11
> **TimmyR41 said:**
> the last time i shut down windows i did shut it down properly.  i am at work right now so i haven't been able to try any of the solutions as of yet.  i will try them when i get home tonight.  it would be much easier if i could get my internet working properly because then i could post on the forum while i was inputing the code.  currently i have another open thread titled having trouble with wireless.  i have a few things to try there as well.  thanks for all the help.Until you get your wireless fixed, you could always use the wired connection correct?

Or is the wired connection also giving you problems?

---

### Post by TimmyR41 on 2008-06-11
i haven't tried the wired connection yet.  that requires me to run about 100 foot of eathernet cable from our den to my bedroom.  i just haven't bothered with figuring out where i stashed my eathernet cable when i graduated college.  i had a really long one at one point for playing halo through system link but i'm not 100% sure where i put it.

---

### Post by Victormd on 2008-06-11
as for your wireless, have you tried ndiswrapper (most likely a very dumb question, but worth asking)?

---


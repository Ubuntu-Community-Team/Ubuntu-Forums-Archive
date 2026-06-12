---
title: "changing to root -- this has to be easy, right?"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by socref on 2008-08-05
Hi, everyone. I know this must be the most naive of questions, but it has me stumped. How do I become root in Ubuntu?

I have a memory stick onto which I've copied some folders and files. Now I want to delete them, but I cannot. Neither can I change the names. I can only add to the memory stick.

So I looked at "permissions" for both the folders and files on the memory stick, and in each case I see the following:

Owner: <my user name shows here>
Folder access: create and delete files
File access: ---

Group: root
Folder access: None
File access: ---

Others
Folder access: None
File access: ---


So I'm thinking that maybe if I change the Group:root folder access to read "create and delete files" then I should be able to do what I want. Correct?

But I can't change the Group:root settings since I can't figure out how to become root.

Sheesh. This was so simple to change from user to root in SuSE Linux, but I'm absolutely stumped in Ubuntu. It has to be easy, right? 

What do I do to become root so I can change permissions on the memory stick (assuming, of course, that this is actually what I need to do to delete stuff from it).

Thanks, gurus.
socref

---

### Post by LowSky on 2008-08-05
hit ALT+F2
type
gksudo nautilus

---

### Post by limasierra on 2008-08-05
You need to be an administrator to do it. So, if you are one, open your terminal and type "sudo nautilus /media" without the quotes and hit enter. Insert your password and when nautilus opens up locate the folder with your memory stick name. Example: if your memory stick name is "socref" the folder name will be the same, case sensitive.

---

### Post by finer recliner on 2008-08-05
```
sudo su
```

remember to close the terminal when done ;)

---

### Post by issih on 2008-08-05
Use gksudo for graphical apps, otherwise you can end up with subtle complications..
in essence using plain sudo you end up running the application as root but within your own context as a user, which can cause trouble, using gksudo avoids this.hope that helps

---

### Post by northern lights on 2008-08-05
> **finer recliner said:**
> ```
sudo su
```

> **issih said:**
> Use gksudo for graphical apps, otherwise you can end up with subtle complications..

Well said. _Never_ run graphical apps from recliner's command.
```
sudo su-
```might work, but I suggest you stick to 'sudo' and 'gksu'/'gksudo'/'kdesu' (the latter for KDE).

As a reference: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by Irony on 2008-08-05
Type this in a text file and save it as 'openasroot';

```
#!/bin/bash

gksudo nautilus $NAUTILUS_SCRIPT_CURRENT_URI
```

Now drag the file into;

~/.gnome2/nautilus-scripts

Now when you right click on a folder or file and go to *Scripts > openasroot* it will open in nautilus as root.

Note you may have to reboot or login and out to make Nautilus show the *Scripts > openasroot* on right clicking.

---

### Post by limasierra on 2008-08-05
You will also need to change the "openasroot" file atributes.
Just simply open your terminal and write ```
chmod +x /home/yourusername/.gnome2/nautilus-scripts/openasroot
```

---

### Post by aysiu on 2008-08-05
What filesystem is your memory stick? FAT16? Ext3?

---

### Post by socref on 2008-08-05
Thanks to everyone who replied with helpful suggestions and words of caution. 

Special thanks to Northern Lights for the link to the root primer.  =D>  I'll study that carefully.

socref

---

### Post by socref on 2008-08-05
> **aysiu said:**
> What filesystem is your memory stick? FAT16? Ext3?

It's vfat. (Files were created on a Windows machine, loaded onto the stick, and then given to me).

socref

---

### Post by aysiu on 2008-08-05
> **socref said:**
> It's vfat. (Files were created on a Windows machine, loaded onto the stick, and then given to me).

socref
Can you keep your memory stick plugged in, paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal), and then paste the output back here? ```
df -h
sudo fdisk -l
```

---

### Post by northern lights on 2008-08-05
You don't have to access it as root all the time.

Infact, it'd be better not to.

You can either change ownership of the device```
sudo chown -R username:usergroup /dev/DEVICE
```where username and usergroup need to be replace by your username (this is the default in single user setups, verifying would be better) and DEVICE by the name of the device. Then set read/write permissions```
sudo chmod -R 664 /dev/DEVICE
```

Or grant mount privileges to system users, create DEVICE group, permit the use of device by the group DEVICE and add USER to the group DEVICE, where USER is your username and DEVICE the device. This is done as follows:

Open nautilus as root```
gksu nautilus --no-deskop
```and navigate to /dev/, right-click on the device and select 'Permissions'. Alter as you like.
Then, navigate to "System > Administration > Users & Groups". Unlock, click on "Manage Groups" and add the group DEVICE. Add yourself to the group.
Now, similar to the above, alter ownership, leave it root but add DEVICE:```
chown -R root.DEVICE /dev/hdd
```

---

### Post by aysiu on 2008-08-05
You really can't *chmod* or *chown* a FAT32 or FAT16 device.

---

### Post by northern lights on 2008-08-05
Don't know how I missed that...

Well, I do have an idea why - but I'd rather keep that one to myself.
;)

---

### Post by socref on 2008-08-09
> **aysiu said:**
> Can you keep your memory stick plugged in, paste these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal), and then paste the output back here? ```
df -h
sudo fdisk -l
```

Here you go. What does it tell you?

gil@phred:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.2G  3.1G  5.7G  35% /
varrun               1013M   84K 1013M   1% /var/run
varlock              1013M     0 1013M   0% /var/lock
udev                 1013M  120K 1013M   1% /dev
devshm               1013M     0 1013M   0% /dev/shm
lrm                  1013M   34M  980M   4% /lib/modules/2.6.22-15-generic/volatile
/dev/sda2             222G   17G  205G   8% /home
/dev/sdf1             3.8G  1.8G  2.0G  49% /media/disk
gil@phred:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250000000000 bytes
255 heads, 63 sectors/track, 30394 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x50000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217       30151   232420387+  83  Linux
/dev/sda3           30152       30394     1951897+  82  Linux swap / Solaris

Disk /dev/sdd: 125 MB, 125960192 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1         961      122959+   6  FAT16

Disk /dev/sdf: 4005 MB, 4005560320 bytes
16 heads, 32 sectors/track, 15280 cylinders
Units = cylinders of 512 * 512 = 262144 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1       15280     3911664    c  W95 FAT32 (LBA)
gil@phred:~$

---

### Post by aysiu on 2008-08-09
Well it confirms that the drive is FAT32 and tells me its location. Can you paste these commands in to see if that changes the drive's behavior? ```
sudo umount /dev/sdf1
sudo mount -t vfat /dev/sdf1 /media/disk -o iocharset=utf8,umask=000
```

---

### Post by socref on 2008-08-09
> **aysiu said:**
> Well it confirms that the drive is FAT32 and tells me its location. Can you paste these commands in to see if that changes the drive's behavior? ```
sudo umount /dev/sdf1
sudo mount -t vfat /dev/sdf1 /media/disk -o iocharset=utf8,umask=000
```

Do I first run 

df -h
sudo fdisk -l

and then run these two new commands? Or do I just run the two new ones?

 Thx
socref

---

### Post by aysiu on 2008-08-10
Either way. The *df -h* and *sudo fdisk -l* commands just give information. They don't really "do" anything.

---

### Post by socref on 2008-08-11
> **aysiu said:**
> Well it confirms that the drive is FAT32 and tells me its location. Can you paste these commands in to see if that changes the drive's behavior? ```
sudo umount /dev/sdf1
sudo mount -t vfat /dev/sdf1 /media/disk -o iocharset=utf8,umask=000
```


I ran these two commands.

I can move files from the memory stick and can rename them. So things are working normally again.  :)

But that normal behavior returned **before** I ran this most recent set of commands, so I don't know what caused the original problems to go away.

Maybe it was a mount/unmount problem that worked itself out??

A mystery, and I'm sorry that I was not able to confirm what brought about the fix. I really appreciate everyone's help. I just don't know what specifically changed and caused the problem to disappear. 

socref

---


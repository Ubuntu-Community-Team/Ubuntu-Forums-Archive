---
title: "Don't have permission to my drives"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by Bourlog on 2008-08-15
Hello guys! Ive just installed Ubuntu and ive got a problem.. I have two SATA disk and an external drive. I made a 10gig partition for ubuntu.

I can access the External drive and the 10gig partition. The other partition and the other drive is visible and i can enter them, but i cant open any directory or make any folder. Do i have to login on them as root or something? im kinda new with linux..


And another question, about Cedega. Does anyone know how to install the game on another drive? Cus i have no space for games on the 10gig partition.

Thanks! Ubuntu is great! :D

---

### Post by wolfen69 on 2008-08-15
```
gksu nautilus
``` then navigate to the /media directory. you will have free reign to do whatever.

---

### Post by alienexplorers on 2008-08-15
You may need to login as root in termonal and the change the owner and group to your name.

---

### Post by drs305 on 2008-08-15
Bourlog,

If you are the only user you may want to edit the fstab settings. Fstab is the file that tells the OS where to mount the partitions/devices, who owns them, and which users are allowed to read/write to them.

I wrote a piece on how to use a gui-based fstab editor that contains information about how to set it up. It also has various links to other resources. See my signature line for the link.

We can also help you set it up if you prefer.

---

### Post by erickghint on 2008-08-15
there's a really easy way to do this. I personally have a 500gig drive that I have partitioned into a 20gig Linux partition and a 450gig storage partition. First, make sure that your storage partition is formatted ext3. You can do this in Gparted. Gparted will also tell you the partition name. (i.e. sda1, hda1, etc... it will look like this /dev/sda1 or /dev/hda1 depending on your HDD)

Next is the fun part:

```
sudo mkdir /storage
sudo cp /etc/fstab /etc/fstab_backup
gksudo nano /etc/fstab
```

Once in the editor, you should add the following to the editor:

```
/dev/sda1   /storage  ext3  defaults  0   0
```
(this is assuming that your partition is sda1. it may be hda1 or hda2 or another sda, just remember to put in the proper id.)

Next we need to make the OS see the changes you've made. 

```
sudo mount -a
```

Then to give the permissions so you don't have to worry about being able to write to the partition.

```
sudo chown -R username:username /storage
sudo chmod -R 755 /storage
```

from there, your partition will be in your home directory. I've personally just made a shortcut on the tool-bar to mine. You can just drag and drop the folder onto the top tool-bar to do that. It's just a bit more convenient, to me. 

Hope this helps.

---


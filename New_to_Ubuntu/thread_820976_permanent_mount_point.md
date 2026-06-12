---
title: "permanent mount point"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by akkad on 2008-06-06
i have an ex3 partition for my own data which am looking to mount it under : /media/MyData using the following command :  sudo mount /dev/sda5 /media/MyData
but after a reboot the mount point get back to its original one which is : /Data, so how to save this mount point forever?

---

### Post by AndyCooll on 2008-06-06
> **akkad said:**
> i have an ex3 partition for my own data which am looking to mount it under : /media/MyData using the following command :  sudo mount /dev/sda5 /media/MyData
but after a reboot the mount point get back to its original one which is : /Data, so how to save this mount point forever?
Best way is to add it to fstab. You'll need to ensure you have nfs-common installed. Then do the following:

```
sudo mkdir /media/MyData
sudo gedit /etc/fstab
```
Then add the following line to fstab:
```
/dev/sda5 /media/MyData nfs defaults 0 0
```

That should do the trick.

Also check that you don't already have a line for mounting sda5 (e.g. to mount point /Data) in your fstab

:cool:

---

### Post by Barriehie on 2008-06-06
> **AndyCooll said:**
> Best way is to add it to fstab. You'll need to ensure you have nfs-common installed. Then do the following:

```
sudo mkdir /media/MyData
sudo gedit /etc/fstab
```Then add the following line to fstab:
```
/dev/sda5 /media/MyData n[COLOR=Red]**t**[/COLOR]fs defaults 0 0
```That should do the trick.

:cool:

Perhaps the t, or use auto.

Barrie

---

### Post by AndyCooll on 2008-06-06
Nope, doesn't need the 't' since the drive is ext3.

:cool:

---

### Post by Barriehie on 2008-06-06
> **AndyCooll said:**
> Nope, doesn't need the 't' since the drive is ext3.

:cool:

:oops:

---

### Post by pancakedan on 2008-06-06
what about adding the UUID to the fstab

sudo vol_id -u /dev/sda5

---

### Post by Inxsible on 2008-06-06
simply use pmount. Nothing easier than that. I think Ubuntu has it by default. if not its in the repos```
sudo apt-get install pmount
``` Then to mount the drive use the following ```
sudo pmount /dev/Xd*? MOUNT_POINT
```where X = h or s (most likely s)
* = drive number a,b,c....
? = partition number of the drive - 1,2,3....
MOUNT_POINT is the name of the folder where you want to mount. Make sure that you do NOT already have a folder of that name under /media, as pmount actually creates that folder for you.

So in your case you'd go something like this```
sudo pmount /dev/sda5 MyData
```Of course if you have already created the MyData folder under /media, you will have to delete that first or use a different mount point.

---

### Post by Oldsoldier2003 on 2008-06-06
As an aside its generally considered bad form to mount a Linux partition under /media .
The usual convention is to mount your data partitions under  /mnt since media is used for automounts and removable storage devices. Not that this makes any particular difference in the long run, just thought i would bring it up :)

---

### Post by akkad on 2008-06-06
ok in the fstab there was :
# /dev/sda5
UUID=4fc2c389-c500-43a5-88c5-fcd78c67e7c7 /Data ext3 relatime 0 2

i just changed the mount point from "/Data" to "/mnt/MyData" where after reboot it works fine, any problem with this solution ???

and Oldsoldier2003 thnx for ur notice, u r totally right, as long as media is for removable storage then it should be used for its purpose, thnx and keep suggesting :) .

Inxsible thnx 4 ur help too, i tried pmount but it raises an error that the partition is not removable storage so it seems it is just for removable media.

AndyCooll i didnt try ur solution yet, i was looking to do it but as i have seen that in fstab there is amount point that can be changed so i tried it and it worked with no need for install any package "nfs-common", but i still need ur suggestion if the technique which i tried has no side effects :D.

---

### Post by Inxsible on 2008-06-07
> **Oldsoldier2003 said:**
> As an aside its generally considered bad form to mount a Linux partition under /media .
The usual convention is to mount your data partitions under  /mnt since media is used for automounts and removable storage devices. Not that this makes any particular difference in the long run, just thought i would bring it up :)
Not really. I have all my external drives mounted under /media. I think what you mean is that internal drives are generally mounted under /mnt and externals under /media. It just keeps it clean.

But, you can mount it anywhere you like. you can mount it to /windows or /Whatever.

> **akkad said:**
> .....Inxsible thnx 4 ur help too, i tried pmount but it raises an error that the partition is not removable storage so it seems it is just for removable media.

....


also, I am surprised that it gave you that error that it is not a removable drive, because I remember it clearly that i used it for a couple of internal drives as well. But this was in Feisty. So I guess it changed somewhere down the line.

---

### Post by akkad on 2008-06-07
now am lost, guys i have 4 partions, the root /, the swap, ntfs (winxp), and another ext3 for my own data, the root size is 20GB where the used space is 3GB so the free space should be 17GB but it is not, it is 1GB now, so how that is happening? does mounting the ntfs(winxp) and the ext3(my data) affect the root size ???  as i asked this question in another post before the answer was no it should not be affected as the mounting point is a logical representation not physical, so what going on !!!!!!!

---

### Post by ubernuber on 2008-06-07
Thanks inxsible, 

the pmount worked like a charm for my external drives.

akkad,

You are right..mounting ntfs doesn't have anything to do with the ext3 partition.

---

### Post by abhiroopb on 2008-06-07
just as a note, instead of changing fstab, etc. you could simply try changing the name of the ntfs drive from Data to MyData or whatever...see here....[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---


---
title: "well i want to  view files on my USB storage media?"
date: 2024-09-21
forum: New to Ubuntu
---

### Post by alsacien on 2024-09-21
Hello and good day dear ubuntu-experts



well i want to  view files on my USB storage media?

but - see here: it did not work at all - some think went wrong ... see my output: 

```
<pre><span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ 

```


okay - i rhoght that this here this is the way - at least "theoretically"... see: 

i thoutht that i should do the following: 


Mounting USB Storage Media


a. at the very first step  i think i have  the terminal prompt, and i need to type:


```
mount /mnt/usb

```

b. afterwards - i should do the follwing: i need to access the files by going into that directory:


```
cd /mnt/usb

```


c. and third:  now i need to  list the files in that directory:


```
ls

```

and after all i need to unmounting USB Storage Media


a.  and that said i think i have to do the following at the terminal prompt, i need to type:


```
cd

```

so we are able to  move out of the /mnt/usb directory. Note we allwasy cannot unmount a directory while we are in it.


c. now we are able to  umount the directory:


```
umount /mnt/usb



```


well as you see above - it does not work here 


```
<pre><span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ 

```

hmm - i now have to re-work the code...  - Any ideas!?

---

### Post by oldfred on 2024-09-21
[https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

You normally create a mount point.
Then assign a device to that mount point.
If necessary assign ownership & permissions, so you can access it.
Mount parameters vary by format of data partition. If NTFS must not have used fast startup in Windows.

use autofs for any storage that isn't connected directly to the system with SAS, SATA, eSATA, or Infiniband connections
For USB connected stuff, use autofs, always. use /misc/<LABEL> typically
If added to fstab be sure to also use nofail, of if USB not found, it can take a while to timeout or may prevent boot.

---

### Post by yancek on 2024-09-21
Did you skip the first step which is to create the mount point /mntusb?
If you did that, what filesystem type is on the drive partition?  If it is not Linux, you may need to specify it explicitly in the mount command.  If you don't know the filesystem type, you can get it from a terminal by running the command below to LIST them:

```
sudo parted -l
```

---

### Post by paulparker2 on 2024-09-22
After plug in the USB then in terminal command  ***df  -h***   usually shows my added partition.

BTW other internal hard drives (eg sdb)  may not show all their partitions.

---

### Post by jimmyrus on 2024-10-01
> **alsacien said:**
> Hello and good day dear ubuntu-experts



well i want to  view files on my USB storage media?

but - see here: it did not work at all - some think went wrong ... see my output: 

```
<pre><span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ 

```


okay - i rhoght that this here this is the way - at least "theoretically"... see: 

i thoutht that i should do the following: 


Mounting USB Storage Media


a. at the very first step  i think i have  the terminal prompt, and i need to type:


```
mount /mnt/usb
```

b. afterwards - i should do the follwing: i need to access the files by going into that directory:


```
cd /mnt/usb
```


c. and third:  now i need to  list the files in that directory:


```
ls
```

and after all i need to unmounting USB Storage Media


a.  and that said i think i have to do the following at the terminal prompt, i need to type:


```
cd
```

so we are able to  move out of the /mnt/usb directory. Note we allwasy cannot unmount a directory while we are in it.


c. now we are able to  umount the directory:


```
umount /mnt/usb
```


well as you see above - it does not work here 


```
<pre><span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ mount /mnt/usb
mount: /mnt/usb: konnte nicht in /etc/fstab gefunden werden.
<span style="color:#26A269"><b>ubuntu@T420s</b></span>:<span style="color:#12488B"><b>~</b></span>$ 

```

hmm - i now have to re-work the code...  - Any ideas!?
You created the mount point and then went into it before you mounted the device. And you posted in german on an english forum. You are just typing in mount so unless you've got an entry in fstab its not going to do anything and if you're in the directory you created you won't see any files until you leave that directory and go back in, if it even mounts. 

This guy asked about mounting things a long time ago. Sounds familar doesn't it?  [https://forums.opensuse.org/t/extern-hdd-formatted-to-ext4-how-could-i-mount-the-drive/96183](https://forums.opensuse.org/t/extern-hdd-formatted-to-ext4-how-could-i-mount-the-drive/96183)

---


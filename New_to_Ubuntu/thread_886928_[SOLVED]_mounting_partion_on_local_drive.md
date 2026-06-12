---
title: "[SOLVED] mounting partion on local drive"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by steinzeitmensch on 2008-08-11
Hi I am a complete newbie to Ubuntu.
I have installed ubuntu on a Lenovo 3000 N200
It has a 160 Gb disc.
I have set up some partitions on this drive

Entered this in terminal:
```
fdisk -l
```
Result in terminal:
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x433f8b71

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+  83  Linux
/dev/sda2           19081       19457     3028252+   5  Extended
[COLOR="Red"]/dev/sda3            2551       15302   102430440   83  Linux
/dev/sda4           15303       19080    30346785   83  Linux[/COLOR]
/dev/sda5           19081       19457     3028221   82  Linux swap / Solaris

Partition table entries are not in disk order
```
The 2 partitions in [COLOR="Red"]red[/COLOR] which I want Ubuntu to mount on every startup
Both partitions are ext3


I have from scouring various forums, learnt that a file called fstab located at /etc/fstab that is the key to this.
I have even gone here and tried to meddle with the code but to no avail so far.
This is the content of the fstab as it stands at the moment:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32cd1a76-a146-4f6a-af1c-f29d4c99b85e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=90757b6e-79c4-410d-b439-1e3cb23f083e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3 /media/disk-2/ ext3 defaults 0 0
```

You can see in the last line my final attempt before this post.

Can someone please help me to mount these partitions?

---

### Post by Elfy on 2008-08-11
You need to make folders for them to mount into, so for the one who have done you need to

```
sudo mkdir /media/disk-2
```

not sure if the trailing / would cause a problem

> /dev/sda3 /media/disk-2 ext3 defaults 0 0

make a folder for second drive and repeat in fstab, check if they have mounted with

```
sudo mount -a
```

---

### Post by Victormd on 2008-08-11
Check out the link on my signature on how to automount...

---

### Post by steinzeitmensch on 2008-08-11
Just tried it and got this:

[HTML]mkdir: cannot create directory `/media/disk-2': File exists[/HTML]


I have done this step before from some other post.
The question I have is: How do I know that this new directory is on the partition I want?

---

### Post by Elfy on 2008-08-11
If you've done it already that is fine, make a folder for the second partition, if you haven't already done so, add it to fstab, save and then run the mount -a command I gave.

> The question I have is: How do I know that this new directory is on the partition I want?Not quite sure what you mean but, fstab will mount the partition (dev/sda3) in the folder you specify /media/disk-2.

---

### Post by Vivaldi Gloria on 2008-08-11
Here's my guide:

**1)** Find uuids of sda3 and sda4 using the command

```
ls /dev/disk/* -lah
```

**2)** Create you mountpoints, say

```
sudo mkdir /mnt/disk1
sudo mkdir /mnt/disk2
```

**3)** Press Alt+F2 and start

```
gksudo gedit /etc/fstab
```

Add the following lines to fstab and save:

```
UUID=????? /mnt/disk1  ext3    relatime      0       2
UUID=????? /mnt/disk2  ext3    relatime      0       2
```

In place of the question marks write the uuids you found in part 1. Restart.

**4)** You may need to change the ownership of the mountpoints if you cannot use them:

```
sudo chown -R <username>:<username> /mnt/disk1
sudo chown -R <username>:<username> /mnt/disk2
```

Put your username in place of <username>.

**Notes:**

**a)** You can put symlinks of the mountpoints to where ever you want. Also you can add it to places menu by opening a nautilus window and dragging the folder icon to the places pane on the left.

**b)** Use /mnt/mountpoint, NOT /media/mountpoint. This is how it's supposed to be in linux.

**c)** Good fstab reference:

[http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by steinzeitmensch on 2008-08-12
Hi Vivaldi,
I tried your method gut no cigar!

I assume that you made a small error in step 3 where you should have disk2 in the second line. (I hope my assumption is right)

After restarting it seemed that I had taken a step backwards.
Before I could at least see these partitions in the file manager even though I could not write to them.
Now I do not even see them after the reboot.

I then tried to do the last step (4) in the hope that this would be it, but no.

This is what my fstab now looks like:

```
 /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=32cd1a76-a146-4f6a-af1c-f29d4c99b85e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=90757b6e-79c4-410d-b439-1e3cb23f083e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
UUID=2b63b6fb-c4d1-41a0-a3ca-da869a845c06 /mnt/disk1  ext3    relatime      0       2
UUID=4ab5846c-fb01-47b5-99f5-608835af5178 /mnt/disk2  ext3    relatime      0       2
```

I am sorry if the soultion is right under my nose, but I cannot see it :confused:
I am pretty much a bravado novice to this kind of computing, but I am willing to give it a go.

I am getting quite desperate though, because I need to start "using" my computer.

---

### Post by Vivaldi Gloria on 2008-08-12
> I assume that you made a small error in step 3 where you should have disk2 in the second line.

Yes. you're right. I'll edit it.

> Before I could at least see these partitions in the file manager even though I could not write to them.

Open file manager (nautilus). Please click filesystem and check the folders /mnt/disk1, /mnt/disk2. Aren't your disks mounted there?

Let me know so that I can tell you what to do next.

> I am getting quite desperate though, because I need to start "using" my computer.

No need to get desperate. This is easy to fix. In the mean time enjoy the experience, you are learning linux. ;)

---

### Post by steinzeitmensch on 2008-08-12
Hi,
Sorry but what is Nautilus?
I just click on 'Places' in the top right and then click on a location there and a file browser opens. Is this Nautilus?

If so I cannot find this location where I can 'check the folders' :(

---

### Post by Vivaldi Gloria on 2008-08-12
> I just click on 'Places' in the top right and then click on a location there and a file browser opens. Is this Nautilus?

Yes, the file manager is called nautilus in ubuntu.

> If so I cannot find this location where I can 'check the folders' 

Three ways to do it:

1) Press Alt + F2 and start

```
nautilus /mnt
```

2) Open your home folder. On the left pane click on file sytem. Now you can see the filesystem on the right. Double click on mnt.

3) From places menu choose Computer. Then double click on file system. Then double click on mnt.

Check inside the disk1, disk2 folders in mnt to see if your drives are mounted there.

---

### Post by steinzeitmensch on 2008-08-12
Hi,
Thanks very much. This worked.
I did not realise that I had to find these locations in the /mnt/***** location. Now that I went there, there are my folders and these are as I wanted on the new partitions.

Thanks very much for your help

---

### Post by Vivaldi Gloria on 2008-08-12
> **steinzeitmensch said:**
> Thanks very much for your help

You're welcome mate. Actually you can put a symlink to a better place. Here's how.



[COLOR="Red"]**Part A. Creating symlinks.**[/COLOR]

There are two ways of creating symlinks:

**1)** Creating symlinks using command line:

To create symlinks in your home folder use:

```
ln -s /mnt/disk1 /home/<username>
ln -s /mnt/disk2 /home/<username>
```

To create symlinks in your desktop folder use:

```
ln -s /mnt/disk1 /home/<username>/Desktop
ln -s /mnt/disk2 /home/<username>/Desktop
```


**2)** Creating symlinks using nautilus (file manager):

Open two nautilus windows side by side, one showing the /mnt folder, the other showing the place where you want the symlinks.

Left click on the folder icon of /mnt/disk1 and hold down the mouse button. Drag the icon to the other nautilus window. Do NOT release the mouse button yet. Press Alt. You'll see that a small question mark appears on the icon. Only then release the mouse button. Now a menu will pop up asking what to do. Choose put a link here.


**Notes:**

**a)** If you want you can rename the symlinks to whatever you want.

**b)** You can create symlinks in more than one place. Put a symlink in your home folder and on the desktop if you want.
[B]
c)[/B] To get rid of a symlink just delete it.


-------------------------------------------------------------

[COLOR="Red"]**Part B. Adding a folder to places menu:**[/COLOR]

Open a nautilus window. Find the icon of the folder you want to add to places. Drag the icon with your left mouse button to the places area on the left pane. 

This is shown in the first minute of

[http://screencasts.ubuntu.com/MoS2007/08_Places_and_System](http://screencasts.ubuntu.com/MoS2007/08_Places_and_System)

So using this method you can add (say) the symlink you created to places menu.

---


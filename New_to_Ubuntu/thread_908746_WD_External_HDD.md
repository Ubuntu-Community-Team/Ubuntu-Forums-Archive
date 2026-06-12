---
title: "WD External HDD"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by at2smithjason on 2008-09-02
I just bought a Western Digital 120 GB external HDD from a friend of mine at work.  I plugged it in with delusions of transfering all of my media over to it, and I get a mounting error.  If you need a screen of the error I have one.  I dont know how to make a downloadable thumbnail for posting in the forum.  Thanks guys.

---

### Post by petronell on 2008-09-02
What format is the disk using?

They normally come using NTFS by default.

daver

---

### Post by at2smithjason on 2008-09-02
My friend that I bought it from formatted it in Windows.  Is there a way that I can reformat if for Linux?

---

### Post by handaxe on 2008-09-02
Install gparted and you should be good to go to format.  Ext3 is a good choice.  BUT,

if there is any chance you want to interface with Windows go for fat32 or ntfs, the last of which Linux etc can deal with properly nowadays.

HA

---

### Post by falcon61102 on 2008-09-02
Your mounting error may have been do to the fact that he unplugged it from his computer without using the Safely Remove Hardware command.  There are a couple ways around that and the easiest may be just to force mount it.  And example of this would be:
```
sudo mkdir /media/External
mount /dev/sdb1 /media/External -force
```
Where /dev/sdb1 is your external drive and your mount point would be /media/External.

Also, when the error window pops up, there should be a little button to see the details of the error and if you read through there it may talk about force mounting it and give you the exact code you need.  Simply copy it from there into your terminal and you should be good to go.

---

### Post by at2smithjason on 2008-09-02
I tried to force it to mount through the terminal, but this is what it says:

```
jason@jason-laptop:~$ sudo mkdir /media/External
[sudo] password for jason: 
mkdir: cannot create directory `/media/External': File exists
jason@jason-laptop:~$ 
```

Any more things that I can try?

---

### Post by mellowd on 2008-09-02
> **at2smithjason said:**
> I tried to force it to mount through the terminal, but this is what it says:

```
jason@jason-laptop:~$ sudo mkdir /media/External
[sudo] password for jason: 
mkdir: cannot create directory `/media/External': File exists
jason@jason-laptop:~$ 
```

Any more things that I can try?

Have you typed this yet?

```
mount /dev/sdb1 /media/External -force
```

---

### Post by falcon61102 on 2008-09-02
Yeah, that first command is to make sure that the drive has a mount point.  That error just means that the mount point has already been created.  Try the second command and see where that gets you.  Or instead of "External" use "External1" to switch it up a little.

Also, the /dev/sdb1 is only a guess on my part.  If you are unsure what your drive is actually called, run:
```
sudo fdisk -l
```
-l being a lower case L.  That will display all your drives and you should be able to find it listed there.

---

### Post by at2smithjason on 2008-09-02
> **mellowd said:**
> Have you typed this yet?

```
mount /dev/sdb1 /media/External -force
```

I just tried that and it came back with:
```
jason@jason-laptop:~$ mount /dev/sdbl /media/External -force
mount: only root can do that
```

I also tried what falcon said and my terminal came back with:
```
jason@jason-laptop:~$ sudo fdisc -l
[sudo] password for jason: 
sudo: fdisc: command not found
```

---

### Post by mellowd on 2008-09-02
> **at2smithjason said:**
> I just tried that and it came back with:
```
jason@jason-laptop:~$ mount /dev/sdbl /media/External -force
mount: only root can do that
```

I also tried what falcon said and my terminal came back with:
```
jason@jason-laptop:~$ sudo fdisc -l
[sudo] password for jason: 
sudo: fdisc: command not found
```

Then type:

```
sudo mount /dev/sdbl /media/External -force
```

---

### Post by falcon61102 on 2008-09-02
> 
I also tried what falcon said and my terminal came back with:
```
jason@jason-laptop:~$ sudo fdisc -l
[sudo] password for jason: 
sudo: fdisc: command not found
```


Check your typing, you mispelled the command.

---

### Post by at2smithjason on 2008-09-02
Sorry guys, still nothing.

Just had a thought, I have been wanting to dual boot for a little while now, if I were to get it working with Vista do you think that it would start working in Ubuntu?

---

### Post by falcon61102 on 2008-09-02
What is the output of:
```
sudo fdisk -l
```

Also, can you give us more details on that error that you received?

---

### Post by at2smithjason on 2008-09-02
> **falcon61102 said:**
> What is the output of:
```
sudo fdisk -l
```

Also, can you give us more details on that error that you received?

This is what I get with that command that you gave me to try:
```
jason@jason-laptop:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8146f538

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9566    76838863+  83  Linux
/dev/sda2            9567        9729     1309297+   5  Extended
/dev/sda5            9567        9729     1309266   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb1297edc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321    7  HPFS/NTFS
jason@jason-laptop:~$ 
```

---

### Post by falcon61102 on 2008-09-02
Alright, were you able to get any more details in reference to the error?

Also, copy and paste this line by line and see if it works:
```
sudo mkdir /media/ExternalHD
sudo mount /dev/sbd1 /media/ExternalHD -force
```

If that doesn't work try moving -force to directly behind mount like:
```
sudo mount -force /dev/sdb1 /media/ExternalHD
```

---

### Post by at2smithjason on 2008-09-03
> **falcon61102 said:**
> Alright, were you able to get any more details in reference to the error?

Also, copy and paste this line by line and see if it works:
```
sudo mkdir /media/ExternalHD
sudo mount /dev/sbd1 /media/ExternalHD -force
```

If that doesn't work try moving -force to directly behind mount like:
```
sudo mount -force /dev/sdb1 /media/ExternalHD
```

With each of those commands the terminal is telling me that the device is already mounted.  When I go into one of my folders, on the left side it shows the external HDD.  So my computer is seeing there is something hooked up, it just cant open it.

---

### Post by falcon61102 on 2008-09-03
Is it giving you errors about permissions now?  It might be that you don't have the correct permission to read/write.  Does an error box still pop up when you try to access it?

EDIT:  You can try this to change the permissions for the drive:
```
sudo chown -R username /media/disk
```

Replace /media/disk with whatever mount point that your drive is on.

---

### Post by at2smithjason on 2008-09-03
Yes it does.  I have to go to work now, do you have MSN or AIM?  If i could add you to one of my friend lists getting this to work would be alot easier.  Send me a pm if you dont mind being added.  Thanks.

---

### Post by falcon61102 on 2008-09-03
I'll be on here for a bit more so I'll be able to respond to you nearly as quickly as you can type.  Try the above and see if that works for you if you've got time before you head to work.

---

### Post by steve-shinn on 2008-09-03
> **at2smithjason said:**
> 
I also tried what falcon said and my terminal came back with:
```
jason@jason-laptop:~$ sudo fdisc -l
[sudo] password for jason: 
sudo: fdisc: command not found
```

Did you type 1 or (lower case L) l ??

---

### Post by falcon61102 on 2008-09-03
steve-shinn,

That's a lower case L as previously mentioned in another post.  You having similar troubles?

---

### Post by steve-shinn on 2008-09-03
> **falcon61102 said:**
> steve-shinn,

That's a lower case L as previously mentioned in another post.  You having similar troubles?

I was until I re-read the thread and realised that it was in fact a lower case L

---

### Post by falcon61102 on 2008-09-03
No worries.  It's too easy to miss little things like that when you've been staring at a screen for what seems like days trying to figure something out.

---

### Post by handaxe on 2008-09-03
I wonder if the proggie 'ntfsfix' might not be appropriate here?

HA

---

### Post by falcon61102 on 2008-09-03
It might be worth the try at this point.

---

### Post by at2smithjason on 2008-09-03
Alright just got home from work.  I hope that we can get my external working.

---

### Post by falcon61102 on 2008-09-03
Did you try to change the permissions for the drive?  
Were you able to access it then?  
Also, are you still getting an error message that pops up?  If so, post what it says.  That will help determine the cause of the error.

---

### Post by at2smithjason on 2008-09-03
how do i change permissions for the drive?  I am still getting errors, but I wansnt able to do anything with it today since I was at work.  I will post a link for a screen shot that I get.

---

### Post by falcon61102 on 2008-09-03
If you refer back to Post #17, there is a code for changing the permissions for your drive.  I think that was posted just as you left for work.

---

### Post by at2smithjason on 2008-09-03
This is what I got when I tried to change the permissions:
```
jason@jason-laptop:~$ sudo chown -R username /external/e
[sudo] password for jason: 
chown: invalid user: `username'
jason@jason-laptop:~$ 
```

Also there is the link to the screenshot:
```
http://tinypic.com/view.php?pic=2d6s4k7&s=4
```

---

### Post by falcon61102 on 2008-09-03
Try inserting your username in the place of "username."  Sorry, should have mentioned that earlier.

---

### Post by falcon61102 on 2008-09-03
Based on your screen shot it is showing that it needs to be force mounted because it was improperly disconnected in Windows.  The other way to get around this would be to connect it to a windows machine and simply click on Safely Remove Hardware.  Use the following command:
```
mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

Let me know if you get any erros back.

---

### Post by at2smithjason on 2008-09-03
I tried to change the permission again, but I had a Windows moment and tried to name it like a Windows drive.  What is something that I would want to use for Linux?

---

### Post by falcon61102 on 2008-09-03
First try the code I just posted.  I copied that from the Details text of the error.

Second, the username you need to insert in there is your username for your Ubuntu account, which is jason.

---

### Post by at2smithjason on 2008-09-03
```
jason@jason-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/disk -o force
mount: only root can do that
```

Thats what I got with what you posted last.

---

### Post by falcon61102 on 2008-09-03
Put sudo in front of the command and run it again.

---

### Post by at2smithjason on 2008-09-03
```
jason@jason-laptop:~$ sudo mount -t ntfs-3g /dev/sdb1 /media/disk -o force
[sudo] password for jason: 
$LogFile indicates unclean shutdown (0, 0)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory
jason@jason-laptop:~$ mount -t ntfs-3g /dev/sdb1 /media/disk -o force
```

For a quick split second I thought that it was going to work.

---

### Post by falcon61102 on 2008-09-03
Try unplugging it, then plugging it back in.  Since the logfile is reset it should work now.

If that doesn't work, then you need to specify a new mount point for it like you did earlier by using /media/External or something like that.

You can create a new mount point with:
```
sudo mkdir /media/EXTERNAL
sudo mount -t ntfs-3g /dev/sdb1 /media/EXTERNAL -o force
```

---

### Post by egalvan on 2008-09-03
If you have nothing on the drive that you want to keep, 
and want to completely erase it, then you could try

**PartEd Magic LiveCD**

[http://partedmagic.com/wiki/PartedMagic.php](http://partedmagic.com/wiki/PartedMagic.php)

This is a very good Live environment, and it uses the latest GPartED.
It also has Firefox and some games so you can surf or play while your drives are being worked on (cruise Ubuntuforums while partitioning)

It's a small distro (45mb) but does want at least 300m of RAM.
Personally, I use it instead of any other partition editor/LiveCD.
I like that it supports labels.
And please consider donating $2 to the authors.
(no, I am not affiliated/related tot them in any way)


The next idea, is to use **Darik's Boot and Nuke (DBAN)**

[http://www.dban.org](http://www.dban.org)

This will **COMPLETELY WIPE YOUR HARD DRIVE, THERE IS NO UN-DO**
It is extremely powerful. I use it to wipe drives, to return them to "as-new" state. SCSI, SATA, IDE, it has never failed me

The safest way to use it is to ONLY connect the drive you want to erase, and a boot device for dban itself.


Once you have a bare drive, you can use your favorite method to partition it.

---

### Post by falcon61102 on 2008-09-03
The problem is that he can't mount the drive.  Once he can mount it then he'll be able to do whatever he needs from there.

---

### Post by RealG187 on 2008-09-03
> sudo mkdir /media/External
mount /dev/sdb1 /media/External -force

I have a hard drive that has the label "External" by default. Can you take a picture of it so I can see it it's the same one I have?

> I dont know how to make a downloadable thumbnail for posting in the forum

The best way is to add the image file as an attachment on the forums. and it does it all for you, my example is [here]("http://ubuntuforums.org/showthread.php?t=909790")...

My thread is also about USB hard drive, I love my externals! I bought a 500 GB on August 31 (the day before September 1st).

---

### Post by falcon61102 on 2008-09-04
The label "External" is only the mount point and can be called anything.  It has nothing to do with the actually drive itself other than that's where you access the files once it's mounted.

---

### Post by RealG187 on 2008-09-04
So you did just use that as a place holder.

Cuz I actually have a drive labelled external out of the box. Ironically in windows it's drive letter X:\ and sometimes people say "type X:\whatever where X is your drive letter" and my drive letter is X:\ and same here my mount point for it is /media/EXTERNAL and in my case external is not a placeholder. lol!

---

### Post by egalvan on 2008-09-04
> **falcon61102 said:**
> The problem is that he can't mount the drive.  Once he can mount it then he'll be able to do whatever he needs from there.

Well, the OP did state the following...

*With each of those commands the terminal is telling me that the **device is already mounted**. When I go into one of my folders, on the left side it shows the external HDD. So my **computer is seeing there is something hooked up, it just cant open it**.*

To me this says the drives were mounted.

Also, it appears that the drive may have been improperly disconnected while under Windows.
This can leave the file system in an un-stable state.

Completely erasing the drive will cure this, if the drive is ok physically.

---

### Post by falcon61102 on 2008-09-04
egalvan,
You know what, you're right.  Been a long night.  When he posted that screenshot, it must have been from before he got it mounted and it threw me off.  So yeah, erasing would be one way to go about it.

---

### Post by falcon61102 on 2008-09-04
As it was suggested, if you don't have any data that you need to recover on that drive, you could repartition/reformat it and then you'll have access to it.

My suggestion would be to install gparted using Synaptic and just run that.  It would probably be the easiest method to go about doing that.

---

### Post by at2smithjason on 2008-09-04
I think that its working now.  When I unplugged it it opened right up.  I am going to try and put some things in it and I will update this post.

*UPDATE*
Thanks a million falcon.  You got my external working for me.  I was starting to think that I was going to have to go back to Windows only to be able to use it.  Now I can dual boot like I had wanted to.

---

### Post by falcon61102 on 2008-09-04
No problem.  Glad you finally got it all worked out.

---

### Post by at2smithjason on 2008-09-04
I did have a lot of help from you.  Thanks again!

---

### Post by Rolcol on 2008-09-04
A quick note if you're going to reformat:  if you're going to use it for your media, be aware that FAT32 has a 4GB file size limit.

---


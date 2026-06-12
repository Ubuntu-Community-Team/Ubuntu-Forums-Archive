---
title: "Windows under LiveCV"
date: 2013-09-22
forum: New to Ubuntu
---

### Post by birkopf on 2013-09-22
Could someplease tell me how to mount Windows 7 partition on NTFS when on Linux Live CV 
(Ubunut or other flavour of Ubuntu like Zorin, Mint) so that the partition is fully accessible ? 

I need to copy whole Win 7 partition on external drive and I keep getting errors even then I have mounted it as root.

---

### Post by whitesmith on 2013-09-22
Mount is a *nix concept that Windows doesn't understand. Do you mean you want to copy an existing Win partition to another drive? If you do that, you may be in violation of Microsoft's EULA. I would read it before attempting to copy Windows, if that is really your goal. [Edited for clarity.]

---

### Post by birkopf on 2013-09-22
No I have certified Windows 7 on both my machines so I'm no violating anything. 

I want to get the files from one windows partition and move them to external disk than to my second laptop. 

Obviously NTFS has it's restrictions and not all files can be copied traditional way so I'm wondering how to copy them all.

---

### Post by b6Q8Ats on 2013-09-22
the obvious way is to backup from windows controlPanel>backup/restore select drive (X) as your restore option (ie your external drive medium),
note this will only back up your c drive.

Roy

---

### Post by birkopf on 2013-09-22
Thanks. 

What Windows would back this into ? ZIP archive ? 

Also - returning to my main questions - how to mount or see the NTFS and be able to have full root access to work on files on NTFS partition from Live CD ?

---

### Post by cjv8888 on 2013-09-22
If you are on the live CD, you can use the dd method to copy the entire partition/disk byte for byte onto the external HD.  It may take a few hours depending on your computer but is very accurate.
Eg. ```
dd if=/dev/sdx1 of=/dev/sdy
```  where x1 is your Windows partition and y is your external HD.  Just do fdisk or gparted beforehand to make sure which is which.

---

### Post by birkopf on 2013-09-23
> **cjv8888 said:**
> If you are on the live CD, you can use the dd method to copy the entire partition/disk byte for byte onto the external HD.  It may take a few hours depending on your computer but is very accurate.
Eg. ```
dd if=/dev/sdx1 of=/dev/sdy
```  where x1 is your Windows partition and y is your external HD.  Just do fdisk or gparted beforehand to make sure which is which.

Thanks CJV,

Would I need to OR would dd create another partition on my external HDD of the same size, or would it use current space
and create an archive/file with image of copied disk ?

---

### Post by cjv8888 on 2013-09-24
To clone a Windows partition and make it bootable without the bluescreen is a bit tricky.
[Here]("http://www.nilbus.com/linux/disk-copy.php") is a step by step instruction.

---

### Post by Impavidus on 2013-09-24
You can get full access to ntfs partitions from a live disk by just mounting them, using either the graphical file manager or the mount command. However, Ubuntu refuses to mount damaged ntfs partitions. Repairing ntfs file systems is a Windows job.

You can also clone your ntfs partition to an external drive. This will create an exact copy of the ntfs partition as a partition on the external drive, overwriting any data that was present in the partition on the external drive. This way you can copy damaged ntfs partitions too, but of course the result will still be a damaged ntfs partition.

---

### Post by birkopf on 2013-09-24
No I cannot access all files from the mounted NTFS partition under Live CD. That's why I have started this thread. 

Normally if I would hit Alt+F2 and gksu nautilus it will open manager which I could use to copy files from NTFS with Win7. This doesent work. 

How to obtain access to windwos partition than ? Or how to force root ?

PS - I don't want to clone the partitions.

---

### Post by whitesmith on 2013-09-24
I used to do things like this all the time with Symantec Ghost, but that product is obsolete these days. There is demoware available to do the job. Try Googling "copy Windows partition."

---

### Post by whitesmith on 2013-09-24
> **birkopf said:**
> PS - I don't want to clone the partitions.OK, you don't want to clone. But in an earlier post:> **birkopf said:**
> I need to copy whole Win 7 partition on external drive and I keep getting errors even then I have mounted it as root.Early on, you say you want to copy (clone, in other words) but later you say you don't. Which is it? Respectfully, I don't understand what you seek to accomplish. Just Google a bit and you'll find what you need.

---

### Post by Impavidus on 2013-09-24
The standard way to mount an ntfs partition from the command line is```
sudo mount -t ntfs /dev/yourpartition /yourmountpoint
```where yourpartition is something like sda2 and yourmountpoint for example /mnt, but any empty directory will do. Next, you can access the files, at the very least with root permissions. If you can't, the mount command has failed, in which case it should have given an error message.

If you try terminal commands and it doesn't work, please copy-paste the entire commands and output in your next post. It can make it easier to diagnose your problem.

---

### Post by birkopf on 2013-09-24
I ndidn't say I want to clone the disk. This option has been mentioned so I tired and researched it and it's not helping.
I also googled a lot and I haven't found what I am looking for. 


To reinstate - I want to be able to fully access all files (rwx) on ntfs partition with Windows 7 on it. 

- How to do that ?

---

### Post by Jonathan Precise on 2013-09-24
> **birkopf said:**
> I didn't say I want to clone the disk. This option has been mentioned so I tired and researched it and it's not helping.
I also googled a lot and I haven't found what I am looking for. 


To reinstate - I want to be able to fully access all files (rwx) on ntfs partition with Windows 7 on it. 

- How to do that ?

```
sudo mount /dev/sd**XY** /mnt
```

Replace **XY**

To copy them:

```
ubuntu@ubuntu:~$ sudo -i
[COLOR=#0000ff]# Wait...[/COLOR]
root@ubuntu:~# _gparted_ [COLOR=#0000ff]# Make a new partition {ext4 for linux-only; ntfs for windows/linux (yes, linux is now more ntfs-compatible since the ntfs-3g driver)}[/COLOR]
root@ubuntu:~# _mkdir /target_
root@ubuntu:~# _mount /dev/sd**WZ** /target_ [COLOR=#0000ff]# Replace **WZ**.[/COLOR]
root@ubuntu:~# _nautilus_ [COLOR=#0000ff]# Copy everything to the newly-created partition[/COLOR]
root@ubuntu:~# logout
ubuntu@ubuntu:~$ exit
```

To change permissions, _**and possibly have adverse side-effects (USE AT YOUR OWN RISK!!!!!!!!!!!!)**_ then do:

```
ubuntu@ubuntu:~$ sudo -i chmod a+rwx /mnt/*
```

---


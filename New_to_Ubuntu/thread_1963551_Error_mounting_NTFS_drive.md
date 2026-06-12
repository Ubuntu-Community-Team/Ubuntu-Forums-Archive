---
title: "Error mounting NTFS drive"
date: 2012-04-22
forum: New to Ubuntu
---

### Post by gilestelnarbe on 2012-04-22
I'm complete newb,
by default I didn't have NTFS-config installed and I didn't know that such thing exist, so my NTFS drives were mounted as read-only  on my Oneiric. In order to solve this problem I MIGHT have caused some problems.
here is the problem:
when I try to mount I encounter this error:
Error mounting: mount exited with exit code 1: helper failed with:mount: only root can mount /dev/sda5 on /media/sda5

I managed to mount it by $ sudo mount /dev/sda5 /media/sda5
but I dont think this is the solution.
please help

---

### Post by Morbius1 on 2012-04-22
> by default I didn't have NTFS-config installed and I didn't know that  such thing exist, so my NTFS drives were mounted as read-only  on my  OneiricOne does not follow from the other. Oneiric by default will mount an ntfs partition as writeable - as long as you didn't install ntfsprogs - without ntfs-config 

> when I try to mount I encounter this error:
Error mounting: mount exited with exit code 1: helper failed with:mount: only root can mount /dev/sda5 on /media/sda5

I managed to mount it by $ sudo mount /dev/sda5 /media/sda5
That's not an error that's a statement of fact. Only root can mount. Are you trying to have this partition automount at boot?

---

### Post by gilestelnarbe on 2012-04-22
> Quote:
by default I didn't have NTFS-config installed and I didn't know that such thing exist, so my NTFS drives were mounted as read-only on my Oneiric
One does not follow from the other. Oneiric by default will mount an ntfs partition as writeable - as long as you didn't install ntfsprogs - without ntfs-config 


so I might have installed ntfsprogs.

> Are you trying to have this partition automount at boot?
yes.
and I guess I set that by Storage Device Manager.

---

### Post by Morbius1 on 2012-04-22
I would remove ntfsprogs:
```
sudo apt-get remove ntfsprogs
```Then put back a package that ntfsprogs removes:
```
sudo apt-get install ntfs-3g
```At that point you should be able to access the partition through Nautilus as writeable again. Come to think of it I'm not sure if a reboot is required or not after installing ntfs-3g - I don't think so but I'm not sure about that part.

I don't use Storage Device Manager I use gedit so I can't help you there.

---

### Post by gilestelnarbe on 2012-04-22
thanks I guess everything is back to normal except that now there is an icon for one of my swap devices in Nautilus :O

---

### Post by DaveDeviant on 2012-04-22
Go with this one - [http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14](http://maketecheasier.com/auto-mount-your-ntfs-partition-in-ubuntu/2009/04/14)

Simple 'nd efficient app for automount ntfs drivers

---

### Post by Morbius1 on 2012-04-22
PySDM doesn't know how to use UUID's and in the case of NTFS is missing mounting options so it's actually worse that ntfs-config if that's possible.

Besides, he fixed his problem expect for this peculiarity:
> there is an icon for one of my swap devices in Nautilus If you mean swap as in .. like ..  Linux swap that's kinda strange since swap isn't really a mountable entity.

When you have nothing else to do you might want post the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
```

---

### Post by gilestelnarbe on 2012-04-22
> 
gilestel@Narbe-PC:~$ sudo blkid -c /dev/null
[sudo] password for gilestel: 
/dev/sda1: LABEL="System Reserved" UUID="F0DC1907DC18C9AC" TYPE="ntfs" 
/dev/sda2: LABEL="Win7 64b" UUID="6CCE27A6CE276792" TYPE="ntfs" 
/dev/sda5: LABEL="Data" UUID="20447BE6447BBD5A" TYPE="ntfs" 
/dev/sda6: UUID="d4f97545-2f1a-42d6-be4c-5984d3d8cf67" TYPE="swap" 
/dev/sda7: UUID="3e7a91ef-f46d-4769-a885-a69515987d10" TYPE="ext4" 
/dev/sda8: UUID="c16e76a1-f4e5-47ab-a233-6f5b70fe7f37" TYPE="swap" 


> 
gilestel@Narbe-PC:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                   proc     nodev,noexec,nosuid           0  0  
#Entry for /dev/sda7 :
UUID=3e7a91ef-f46d-4769-a885-a69515987d10  /                       ext4     errors=remount-ro             0  1  
/dev/sda5                                  /media/Data             ntfs-3g  users,noauto                  0  0  
#Entry for /dev/sda1 :
UUID=F0DC1907DC18C9AC                      /media/System_Reserved  ntfs-3g  defaults,locale=en_US.UTF-8   0  0  
#Entry for /dev/sda2 :
UUID=6CCE27A6CE276792                      /media/Win7_64b         ntfs-3g  defaults,locale=en_US.UTF-8   0  0  
/dev/sda5                                  /media/sda5             ntfs     defaults,nls=utf8,umask=0222  0  0  
#Entry for /dev/sda8 :
UUID=c16e76a1-f4e5-47ab-a233-6f5b70fe7f37  none                    swap     sw                            0  0  
#Entry for /dev/sda6 :
UUID=d4f97545-2f1a-42d6-be4c-5984d3d8cf67  /media/sda6             swap     users,sw                      0  0  




sda6 id the mentioned device, and of course I can't mount it.

---

### Post by Morbius1 on 2012-04-23
You've got a bit of a mess there. If you are happy with all the other partitions then by all means leave them as they are. But if it was my system this is what I would do:

[COLOR=Blue]**Note:**[/COLOR] If this looks spooky to you you might want to make a backup copy of your exixting fstab just in case:
```
sudo cp /etc/fstab /etc/fstab.bak
```[COLOR=Blue]**First**[/COLOR], if you do all the things I suggest here you will need to unmount the following partitions. From a terminal run each command:
```
sudo umount /media/Data
sudo umount /media/Win7_64b
sudo umount /media/sda5
sudo umount /media/sda6
```[COLOR=Blue]**Second**[/COLOR], you are going to have to edit this file directly as root by using the following command:
```
gksu gedit /etc/fstab
```**[1] The immediate problem of a mounting swap partition**

It's OK I suppose to have 2 swap files but not mounted they way the second one is so I would change this:
> UUID=d4f97545-2f1a-42d6-be4c-5984d3d8cf67 /media/sda6 swap users,sw 0 0And change it to this:
> UUID=d4f97545-2f1a-42d6-be4c-5984d3d8cf67 **[COLOR=Blue]none swap sw 0 0[/COLOR]****[2] System Reserved partition shouldn't be mounted.**
And even if it was there's nothing to do in there so we are going to prevent it from automounting by changing this:
> UUID=F0DC1907DC18C9AC /media/System_Reserved ntfs-3g defaults,locale=en_US.UTF-8 0 0
To this:
> UUID=F0DC1907DC18C9AC /media/System_Reserved ntfs-3g defaults**[COLOR=Blue],noauto[/COLOR]**,locale=en_US.UTF-8 0 0**[3] /dev/sda5 is being mounted twice - once to /media/Data and again to /media/sda5 - this one read only.**

So change this:
> /dev/sda5 /media/Data ntfs-3g users,noauto 0 0To this
> [COLOR=Blue]**#**[/COLOR]/dev/sda5 /media/Data ntfs-3g users,noauto 0 0And this:
> /dev/sda5 /media/sda5 ntfs defaults,nls=utf8,umask=0222 0 0To this:
> [COLOR=Blue]**#**[/COLOR]/dev/sda5 /media/sda5 ntfs defaults,nls=utf8,umask=0222 0 0Then add another new line to the end of fstab that looks like this:
```
UUID=20447BE6447BBD5A /media/Data ntfs defaults,nls=utf8,uid=1000,umask=0000,windows_names 0 0
```**[4] The Win7 OS partition.**
I really don't like mounting the partition that the Windows OS lives in as writeable - I really don't like mounting it at all. But if you are going to mount it then add one more option to your list:
> UUID=6CCE27A6CE276792 /media/Win7_64b ntfs-3g defaults**[COLOR=Blue],windows_names[/COLOR]**,locale=en_US.UTF-8 0 0When you are all done save fstab and then run the following command:
```
sudo mount -a
```That command will do 2 things:

** It runs a test to make sure things are set up properly and if the mount points actually exist.

** If it finds no errors it will just come back to the prompt and your partitions will be mounted. If it does find an error it will post them.

It does all this without requiring a reboot so you can find out if you have problems before it becomes a problem booting.

---

### Post by audiomick on 2012-04-23
@ Morbius: Nice post. Clear and well explained. I think it is important to explain what commands do for the people you are trying to help. Well done. :popcorn:

---

### Post by gilestelnarbe on 2012-04-23
thanks for your help
now System_Reserved does not mount automatically.
swap is not there
Data & Win7 is being mounted.
just one other question.I agree that Its better to mount Win7 read-only and actually I don't need to write there, how can I change that ?
 Here is my fstab info after editing:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc                   proc     nodev,noexec,nosuid           0  0  
#Entry for /dev/sda7 :
UUID=3e7a91ef-f46d-4769-a885-a69515987d10  /                       ext4     errors=remount-ro             0  1  
#/dev/sda5                                  /media/Data             ntfs-3g  users,noauto                  0  0  
#Entry for /dev/sda1 :
UUID=F0DC1907DC18C9AC                      /media/System_Reserved  ntfs-3g  defaults,noauto,locale=en_US.UTF-8   0  0  
#Entry for /dev/sda2 :
UUID=6CCE27A6CE276792                      /media/Win7_64b         ntfs-3g  defaults,windows_names,locale=en_US.UTF-8   0  0  
#/dev/sda5                                  /media/sda5             ntfs     defaults,nls=utf8,umask=0222  0  0  
#Entry for /dev/sda8 :
UUID=c16e76a1-f4e5-47ab-a233-6f5b70fe7f37  none                    swap     sw                            0  0  
#Entry for /dev/sda6 :
UUID=d4f97545-2f1a-42d6-be4c-5984d3d8cf67  none           	   swap     sw               		  0  0  
UUID=20447BE6447BBD5A /media/Data ntfs defaults,nls=utf8,uid=1000,umask=0000,windows_names 0 0


---

### Post by Morbius1 on 2012-04-23
> just one other question.I agree that Its better to mount Win7 read-only  and actually I don't need to write there, how can I change that ?One way is to add yet another option to your list:

Change this:
> UUID=6CCE27A6CE276792 /media/Win7_64b ntfs-3g defaults,windows_names,locale=en_US.UTF-8 0 0To this:
> UUID=6CCE27A6CE276792 /media/Win7_64b ntfs-3g defaults,[COLOR=Blue]**umask=0222**[/COLOR],windows_names,locale=en_US.UTF-8 0 0Then unmount the partition:
```
sudo umount /media/Win7_64b
```And then mount it back:
```
sudo mount -a
```umask removes permissions from an ntfs partition that starts out in life as read/write to everyone. A "2" removes write so you end up with read only to everyone.

---

### Post by gilestelnarbe on 2012-04-24
Thanks You SOOOOOOOOOOOOOOO much

---


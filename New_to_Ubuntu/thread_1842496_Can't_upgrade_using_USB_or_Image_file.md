---
title: "Can't upgrade using USB or Image file"
date: 2011-09-11
forum: New to Ubuntu
---

### Post by nns2006 on 2011-09-11
Hi,
I am using Ubuntu 10.10 . I have downloaded ubuntu-11.04-desktop-i386.iso file on my desktop.
1. first I tried to upgrade by mounting the image file my following this instruction> 
sudo mkdir -p /media/isomountpoint

sudo mount -o loop ~/Desktop/ubuntu-11.04-alternate-i386.iso /media/isomountpoint

i followed the instruction given [here]("https://help.ubuntu.com/community/NattyUpgrades"). But I didn't get any pop up window saying you have software packages for upgrades. Then I follow the the step 4 as explained. This also fails to give me any option for upgrading.

2. Then, I tried to make a bootable usb hoping it might give me an upgrade option once inserted into the system. But, this also fails. I can see that my usb is mounted but it does not gives me any option for upgrading.

So, my question is, Am I
a) doing something wrong?
b) missing some commands?

Any help is appreciated. 

Thank you.

---

### Post by Enigmapond on 2011-09-11
I think, you will be better off just booting into the CD or USB and doing a  fresh install after doing a backup of your important files. I found this to save me a lot of headaches.

---

### Post by nns2006 on 2011-09-11
> **Enigmapond said:**
> I think, you will be better off just booting into the CD or USB and doing a  fresh install after doing a backup of your important files. I found this to save me a lot of headaches.

fresh install will give me pain, as I have several installed softwares which I don't want to install again. and my Internet connection will not allow me to do so either.

I need some help regarding upgrading.

Thank you for your help.

---

### Post by Nr90 on 2011-09-11
Would apt-get upgrade -d be an option?

---

### Post by nns2006 on 2011-09-12
> **Nr90 said:**
> Would apt-get upgrade -d be an option?

here is what I get.

```
$ sudo apt-get upgrade -d
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```


However, I want to upgrade from the image file that I have already downloaded.

---

### Post by waynefoutz on 2011-09-12
> **nns2006 said:**
> 


However, I want to upgrade from the image file that I have already downloaded.

Doesn't quite work that way. The easiest way to accomplish this is to burn the .iso to disk, or usb drive, and install like normal, except when you get to the part that asks you if you want to install side by side, use the entire disk, or specify partitions manually.  The third choice is the one you want. Have 11.04 install on top of your existing ext4 partition, overwriting it, but make sure the "format drive" box is unchecked.To do this you select the mount point as root in the pull down box.  This will install 11.04 on top of 10.10, and leave all your data intact. (I would still back everything up though.) The downside to this method is you are still going to have to reinstall most if not all your applications.

---

### Post by 3rdalbum on 2011-09-12
> **waynefoutz said:**
> Doesn't quite work that way.

Well yeah, it does actually. You can upgrade using the Alternate CD.

@nns2006: Have you tried this command?

```
gksu "sh /media/cdrom/cdromupgrade"
```

I'm pretty sure that's a necessary step.

---

### Post by nns2006 on 2011-09-12
> **waynefoutz said:**
> Doesn't quite work that way. The easiest way to accomplish this is to burn the .iso to disk, or usb drive, and install like normal, except when you get to the part that asks you if you want to install side by side, use the entire disk, or specify partitions manually.  The third choice is the one you want. Have 11.04 install on top of your existing ext4 partition, overwriting it, but make sure the "format drive" box is unchecked.To do this you select the mount point as root in the pull down box.  This will install 11.04 on top of 10.10, and leave all your data intact. (I would still back everything up though.) The downside to this method is you are still going to have to reinstall most if not all your applications.

I did make usb drive but it is not giving the option for upgrade. I am afraid of doing clean install as I will have to start from scratch again. 
Any other suggestions ?

Thank you.

---

### Post by nns2006 on 2011-09-12
> **3rdalbum said:**
> Well yeah, it does actually. You can upgrade using the Alternate CD.

@nns2006: Have you tried this command?

```
gksu "sh /media/cdrom/cdromupgrade"
```

I'm pretty sure that's a necessary step.

Yes, I have done.This was the step 4. But it is not giving me anything. I was expecting to give me an option for upgrade. What I see is- Image is mounted but no pop up window saying packages are for upgrades or like that. 

Do you think I am missing something to happen this.

Thank you

---

### Post by Rex Bouwense on 2011-09-12
I believe that you downloaded the wrong ISO.  The one that you want, to do what you want to do is an alternate install.  I believe that is what 3rdalbum was talking about.

---

### Post by anewguy on 2011-09-12
I believe you can upgrade via the livecd by doing as waynefoutz said about not formating existing ubuntu partitions.  However, I come from the group that says to backup what you need, and just do a clean install.  If you upgrade via the livecd method mentioned above, I think you'll still end up with some libs, files, etc., sticking around from the old release and causing problems.  When 11.04 first came out there was a discussion on this forum about just updating to 11.04 for your exact reason and that it should work fine.  The majority of posts I saw come back after that said they had problems and eventually just went with a clean install.  Personally, I always do a clean install.

I am a little curious about something, so I'd like you to post the output of:

sudo ls /media/isomountpoint 



Dave ;)

---

### Post by nns2006 on 2011-09-12
Here is my output to the command. 

> $ ls /media/isomountpoint
autorun.inf  dists     md5sum.txt  preseed             usb-creator.exe
boot         install   pics        README.diskdefines  wubi.exe
casper       isolinux  pool        ubuntu


---

### Post by nns2006 on 2011-09-12
> **Rex Bouwense said:**
> I believe that you downloaded the wrong ISO.  The one that you want, to do what you want to do is an alternate install.  I believe that is what 3rdalbum was talking about.


Oh! I will check with the alternate iso file and let you know the result.

---

### Post by 3rdalbum on 2011-09-12
> **nns2006 said:**
> Oh! I will check with the alternate iso file and let you know the result.

You already have the Alternate ISO file. What you need is the Desktop ISO. That one is compatible with Wubi.

---

### Post by anewguy on 2011-09-13
The list of files and folders you show in the ls of the ISO mount point is the same as on the 11.04 LiveCD.  There is no upgrade script file from what I saw when I looked through my LiveCD, so perhaps it is on the alternate.  I haven't downloaded the alternate CD in quite a while so I don't what it looks like now.  So, from what I saw, there is no "upgrade" with the LiveCD.

Dave ;)

---

### Post by nns2006 on 2011-09-15
> **anewguy said:**
> The list of files and folders you show in the ls of the ISO mount point is the same as on the 11.04 LiveCD.  There is no upgrade script file from what I saw when I looked through my LiveCD, so perhaps it is on the alternate.  I haven't downloaded the alternate CD in quite a while so I don't what it looks like now.  So, from what I saw, there is no "upgrade" with the LiveCD.

Dave ;)

I downloaded another image file,ubuntu 11.04- alternate.iso and instead of mounting it at /media/isomountpoint I mounted it at /media/cdrom . Everything else work like charm. 

Thank you anewguy for pointing out that it does not have upgrade file inside.

---

### Post by nns2006 on 2011-09-15
> **Rex Bouwense said:**
> I believe that you downloaded the wrong ISO.  The one that you want, to do what you want to do is an alternate install.  I believe that is what 3rdalbum was talking about.


Thank you for pointing out that I have downloaded wrong image. You were right. I downloaded correct one and things are fine now.

---

### Post by nns2006 on 2011-09-15
Thank you everyone for your help.

---


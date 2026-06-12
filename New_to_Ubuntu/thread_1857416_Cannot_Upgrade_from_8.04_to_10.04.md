---
title: "Cannot Upgrade from 8.04 to 10.04"
date: 2011-10-10
forum: New to Ubuntu
---

### Post by dglp on 2011-10-10
I have a Toshiba Satellite Pro 4200 that's set up as a dual boot XP/Ubuntu 8 machine. It has a 1.0 USB port, a read-only CD, and a working network card. 

I am trying to upgrade to Ubuntu 10. 
I cannot use the Ubuntu updater as the link seems to be broken. 
I cannot burn an image to CD.
I cannot use the USB UNetBootin method as my TDK Trans-IT flash drive isn't recognised by XP.
I am not about to delete either existing installation partition, nor set up a new partition.
I want to install the newer version over the old one, using a very limited combination of technology and knowledge.

Does anyone want to help solve this particular problem? :D

---

### Post by sanderd17 on 2011-10-10
It looks like you don't care about your data on the Ubuntu side and just want a new version. Is that right?

In that case, I would suggest a live Medium. Could you explain the problem with burning a CD? If you can't burn a CD nor write to an USB, you will have to buy one: [http://shop.canonical.com/index.php?cPath=17](http://shop.canonical.com/index.php?cPath=17) , [http://shop.canonical.com/product_info.php?products_id=874](http://shop.canonical.com/product_info.php?products_id=874)

---

### Post by dglp on 2011-10-10
> **sanderd17 said:**
> It looks like you don't care about your data on the Ubuntu side and just want a new version. Is that right?Correct. I have backed up my data onto the USB, then moved it onto a network drive. I'd be happy if the originals were left intact after an upgrade, but it's not a hassle to reverse the process.


> **sanderd17 said:**
> In that case, I would suggest a live Medium. Could you explain the problem with burning a CD?I'm not sure what you mean by live medium. (BTW, I tried using the Wubi approach, but haven't got the drive space for it.)

I have read-only CD drives. However, if there was a way of mounting a virtual drive on either the laptop, or across the network, AND if there is a way to mount the ISO as a virtual CD, then that might work. 

I don't know what's up with my XP installation, but it won't read the Flash drive - even though the Ubuntu installation reads it just fine! So if there's a flash drive installer that runs from Ubuntu, I'd be golden!

---

### Post by sanderd17 on 2011-10-10
A live medium is just a live CD or USB.

In Ubuntu you can also install Unetbootin, but the app USB-creator is even more easy.

[https://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](https://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

With the USB-creator, you just select the iso and the drive and everything works. Warning: USB-creator only works with Ubuntu based distros.

---

### Post by Lars Noodén on 2011-10-10
It is possible to boot directly from the CD ISO image using Grub.  I haven't done it myself, but there are various instructions around.  In that case, if you have a separate /home partition, then you can do a fresh installation that way.

The way I have usually updated is to change the contents (after making a backup copy) of /etc/apt/sources.list to point to the new distro.  I've only done that to update from one version to its immediate successor.  It may not be recommendable to try hopping directly from 8.04 to 10.04.  You might search around and see if you can or if you need to go to 8.10, etc. first.

---

### Post by dglp on 2011-10-10
> **sanderd17 said:**
> A live medium is just a live CD or USB.

In Ubuntu you can also install Unetbootin, but the app USB-creator is even more easy.

[https://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator](https://en.wikipedia.org/wiki/Ubuntu_Live_USB_creator)

With the USB-creator, you just select the iso and the drive and everything works. Warning: USB-creator only works with Ubuntu based distros.

This is where my knowledge runs out... 

When I open the teminal and type usb-creator-gtk at the command line, it comes back with command not recognised. 

I also looked in the package manager fpr anything to do with USB, and didn't see anything resembling usb Creator. 

I will look at the linux version of Unetbootin to see if that's something i can get my head round.

---

### Post by BlinkinCat on 2011-10-10
I'm not sure if this is what you want -

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by mörgæs on 2011-10-10
This is an old one. First step: How much memory does it have?

---

### Post by dglp on 2011-10-10
> **BlinkinCat said:**
> I'm not sure if this is what you want -

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

I had made my way part way through that before trying the Unetbootin method. 

Am currently wondering how to get usb-creator installed. If I don't succeed with that, I may see if I can boot from the USB that has a copy of the 10.4 ISO on it.

---

### Post by dglp on 2011-10-10
> **mörgæs said:**
> This is an old one. First step: How much memory does it have? As in hard drive? ~25G!
RAM is, um, I forget! but not a lot...

---

### Post by mörgæs on 2011-10-10
Let me guess that you are _really_ low.

This is how to do it:
[http://ubuntuforums.org/showpost.php?p=9834517&postcount=261](http://ubuntuforums.org/showpost.php?p=9834517&postcount=261)

The minimal ISO can be burned on any computer with a CD writer. On such an old guy it is very unlikely that the USB boot works.


You could also try the regular Lubuntu ISO, but I am not sure that it will work.

---

### Post by dglp on 2011-10-10
> **mörgæs said:**
> The minimal ISO can be burned on any computer with a CD writer. I haven't got one of those newfangled burn thingys... :)

---

### Post by snowpine on 2011-10-10
Hi dglp,

Here are easy instructions to upgrade from 8.04 to 10.04:

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_8.04_LTS_to_10.04_LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_8.04_LTS_to_10.04_LTS)

If I had to guess, I'd speculate your upgrade failed because you forgot to check the "Long term support releases only" option. (Support for 8.10 ended quite some time ago.)

---

### Post by dglp on 2011-10-10
> **Lars Noodén said:**
> It is possible to boot directly from the CD ISO image using Grub. 

I haven't made any progress getting usb-creator or Unetbootin installed, so am looking at the possibility of mounting the ISO directly via the cd. 

[This post ]("http://ubuntuforums.org/showpost.php?p=11253172&postcount=16")doesn't explicitly say it can be done, but I'm wondering if there's a command that lets me mount the ISO directly within Ubuntu.

---

### Post by Lars Noodén on 2011-10-10
Try mounting via the loop device:

```

sudo mount -o loop ubuntu-11.04-server-amd64.iso /mnt

```

The contents of the ISO will then be accessible via /mnt

---

### Post by dglp on 2011-10-10
> **snowpine said:**
> Hi dglp,

Here are easy instructions to upgrade from 8.04 to 10.04:

[https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_8.04_LTS_to_10.04_LTS](https://help.ubuntu.com/community/LucidUpgrades#Upgrade_from_8.04_LTS_to_10.04_LTS)

If I had to guess, I'd speculate your upgrade failed because you forgot to check the "Long term support releases only" option. (Support for 8.10 ended quite some time ago.)

Hi Snowpine,

Am trying this, but getting hung up at the second step. It says:

[LIST=1]
[*]Start System/Administration/Software Sources (*NB, on  8.04, it's Software Preferences*) 
[*]On the **Updates** tab, set **Show new distribution releases:** to **Long term support releases only**, then press **Close**.
[/LIST]
I don't have that option.
It only has:
1. Check for updates automatically (Daily/ 2 Days / Weekly/ Fortnightly)
2. Download updates in the background, but do not install them.
3. Install security updates without confirmation.

That said, a bit further down is this little gem: If the ISO file is on the computer to be upgraded, you could avoid wasting a CD by [mounting the ISO as a drive]("https://help.ubuntu.com/community/ManageDiscImages#MountISOFiles") with a command like:...

So I'm off to try that!

---

### Post by snowpine on 2011-10-10
> **dglp said:**
> Hi Snowpine,

Am trying this, but getting hung up at the second step. It says:

[LIST=1]
[*]Start System/Administration/Software Sources (*NB, on  8.04, it's Software Preferences*) 
[*]On the **Updates** tab, set **Show new distribution releases:** to **Long term support releases only**, then press **Close**.
[/LIST]
I don't have that option.
It only has:
1. Check for updates automatically (Daily/ 2 Days / Weekly/ Fortnightly)
2. Download updates in the background, but do not install them.
3. Install security updates without confirmation.


```
gksu gedit /etc/update-manager/release-upgrades
```

Make sure it contains the lines:

```
[DEFAULT]
Prompt=lts
```

---

### Post by dglp on 2011-10-10
> **snowpine said:**
> ```
[DEFAULT]
Prompt=lts
```I get a completely blank document. Should I write this into it and save?

On a different tack, trying to mount the ISO from the flash drive ```
sudo mount -o loop ubuntu-10.04.3-desktop-i386.iso /media/ ??
``` doesn't quite do the trick because I don't know how to point to the correct directory. Would it be something like ```
sudo mount -o -l loop ubuntu-10.04.3-desktop-i386.iso /media/flash drive
```?

---

### Post by Lars Noodén on 2011-10-10
The upper one is more correct: -o loop

As to the choice of mount point, any empty directory will do the job.  It can be /mnt or it can be /media/cdrom.  You'll probably want to reserve /media/flash for your flash drive.

---

### Post by snowpine on 2011-10-10
> **dglp said:**
> I get a completely blank document. Should I write this into it and save?

Sure, you can give it a try. :) It appears the Ubuntu documentation is not accurate (!!!) so I am sorry if I gave you a link to bad instructions. :(

---

### Post by dglp on 2011-10-10
> **Lars Noodén said:**
> The upper one is more correct: -o loop

As to the choice of mount point, any empty directory will do the job.  It can be /mnt or it can be /media/cdrom.  You'll probably want to reserve /media/flash for your flash drive.

So I'm trying this:
```
sudo mkdir /media/tmpupgrade
sudo mount -o loop /dev/sda/ubuntu-10.04.3-desktop-i386.iso /media/tmpupgrade

```
and getting 'not a directory' in response.

---

### Post by Lars Noodén on 2011-10-10
> **dglp said:**
> So I'm trying this:
```
sudo mkdir /media/tmpupgrade
sudo mount -o loop /dev/sda/ubuntu-10.04.3-desktop-i386.iso /media/tmpupgrade

```
and getting 'not a directory' in response.

Where is ubuntu-10.04.3-desktop-i386.iso  really located?

---

### Post by dglp on 2011-10-10
> **Lars Noodén said:**
> Where is ubuntu-10.04.3-desktop-i386.iso  really located?
It's on the flash drive, which is identified as dev/sda in the Disks control panel.

Oops. I should modify that!
```
/dev/sda1 on /media/FLASH DRIVE type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8

```

---

### Post by Lars Noodén on 2011-10-10
Then the iso should be in /media somewhere, where the flash drive has its mount point.

sudo mount -o loop /media/*something*/ubuntu-10.04.3-desktop-i386.iso /media/tmpupgrade

Find it with ls first.

---

### Post by dglp on 2011-10-10
> **Lars Noodén said:**
> Then the iso should be in /media somewhere, where the flash drive has its mount point.

sudo mount -o loop /media/*something*/ubuntu-10.04.3-desktop-i386.iso /media/tmpupgrade

Understood. I modified the previous post a bit too slowly...
But I think the label is not read as it looks.
```
/media/FLASH DRIVE
``` should be something else, no?

---


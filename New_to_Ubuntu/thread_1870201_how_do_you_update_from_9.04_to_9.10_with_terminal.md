---
title: "how do you update from 9.04 to 9.10 with terminal"
date: 2011-10-26
forum: New to Ubuntu
---

### Post by 007casper on 2011-10-26
how do you update from 9.04 to 9.10 then 10.04 from terminal.

The old 'puter cant boot from usb flash.

thank you.

---

### Post by Alwimo on 2011-10-26
First, back up everything you want in case of something going wrong (if you haven't backed it up yet).
 
Then follow the instructions here:
[http://askubuntu.com/questions/34430/how-to-upgrade-from-ubuntu-10-04-or-10-10-to-11-04](http://askubuntu.com/questions/34430/how-to-upgrade-from-ubuntu-10-04-or-10-10-to-11-04)

---

### Post by alphacrucis2 on 2011-10-26
> **007casper said:**
> how do you update from 9.04 to 9.10 then 10.04 from terminal.

The old 'puter cant boot from usb flash.

thank you.

Normally you would do:

```
sudo do-release-upgrade
```

It should work as long as the 9.10 repos are still available. You would repeat to go from 9.10 to 10.04. 10.04 is definitely still available as it is an LTS release.

---

### Post by 007casper on 2011-10-26
tried that... doesnt work.  

I figured I can just update through terminal.  

What is the proper commmand?

---

### Post by 007casper on 2011-10-26
```
sudo do-release-upgrade
```

> 
Reading cache

Checking package manager

Can not upgrade 

An upgrade from 'jaunty' to 'lucid' is not supported with this tool. 


---

### Post by alphacrucis2 on 2011-10-26
> **007casper said:**
> ```
sudo do-release-upgrade
```

Maybe the karmic koala repos are no longer avaiable


Edit:

Acccording to this site 9.10 (karmic koala) went end of life last 30th April

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

The do-release-upgrade may be finding that the next available release is 10.04 (Lucid Lynx) but it doesn't support skipping interim releases. AFAIK the only exception to this is when you upgrade from LTS to LTS. eg 8.04 could upgrade directly to 10.04.

---

### Post by collisionystm on 2011-10-26
Here ya go...

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

from here

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by alphacrucis2 on 2011-10-26
> **collisionystm said:**
> Here ya go...

[https://help.ubuntu.com/community/EOLUpgrades/Jaunty](https://help.ubuntu.com/community/EOLUpgrades/Jaunty)

from here

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)


The trouble is the OP already said he can't boot from USB (and I assume CD also)

---

### Post by collisionystm on 2011-10-26
> **alphacrucis2 said:**
> The trouble is the OP already said he can't boot from USB (and I assume CD also)

darn.

---

### Post by 007casper on 2011-10-27
yes, I cant boot from cd also.  I tried 11.10. It just hangs.

I was wondering if there is a way to start the cd from terminal, or just update the system from the terminal.

---

### Post by 007casper on 2011-10-27
any ideas???

---

### Post by vicshrike on 2011-10-27
As I understand it your computer is old, and then it probably cant boot 11.10 because it needs newer hardware. Maybe you should consider trying Xubuntu or Lubuntu. I could not boot the Unity desktop on my five year old laptop due to low specs.

---

### Post by 007casper on 2011-10-29
I am trying to load 10.04 ubuntu
> 
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs) on //filesystem.squashfs help

???

I get bunch of commands when I type in help.  The cursor stops at (initramfs)_

???

---

### Post by speedwlk on 2011-10-29
You can get alternate cdimages for 9.10 here:
[http://old-releases.ubuntu.com/releases/karmic/](http://old-releases.ubuntu.com/releases/karmic/)

mount the iso image as a virtual cd using:
sudo mount -o loop /pathtocdimage/cdimage.iso /cdrom

go to /cdrom and run the upgrade script.

Hope it works.

Edit: I am assuming you have internet access in your machine.

---

### Post by coffeecat on 2011-10-29
@007casper, two points.

If you are getting a busybox prompt with the 10.04 live CD, this can be due to a bad CD. Check the md5sum of the downloaded ISO, burn another CD at a low speed and check the CD integrity from the CD boot menu.

It might still be possible to upgrade Jaunty to Karmic. Even when using the old-releases repository, because Karmic (9.10) is now unsupported, do-release-upgrade fails. But there is a way of tricking do-release-upgrade into thinking that Karmic is still supported. Or at least there was. Have a look at this:

[http://ubuntuforums.org/showpost.php?p=11129193&postcount=8](http://ubuntuforums.org/showpost.php?p=11129193&postcount=8)

I was able to upgrade Jaunty to Karmic with that trick a few months ago. Save that code as /var/lib/update-manager/meta-release and see if do-release-upgrade works for you. Check to see if there is already a /var/lib/update-manager/meta-release file in your system and keep a backup copy of it first. I can't be sure that this will still work, but it's worth a try.

---

### Post by mörgæs on 2011-10-29
You have not posted the hardware specifications. Are you sure that the computer can run the new releases at all?

---

### Post by 007casper on 2011-10-29
thank you for the speedwlk - how do I run the upgrade script?

on the 9.10 iso file I see cdromupgrade file... do I run that?



computer is pentium 4 
2.4ghz, 1gig ram ddr 400mhz

another computer with same specs is able to run 10.04.  I used to update it whenever it prompted for an upgrade.  I know 10.04 works with these specs.

However, the computer I am trying to update just had 9.04 and it cant upgrade at all.  When I try boot with cd in it.  It cant boot from the cd either.  I have been trying to upgrade to 10.04.  I figured I have to upgrade to 9.10 before I jump to 10.04.  I couldnt make it work. 

I figured I will load a live cd.  I started with 11.10.  I couldnt make it work.  I burned a cd 11.04, that didnt work either.

So, I tried live cd with 10.04. This time I got busy box.  On 11.10, and 11.04 I didnt get anything.

---

### Post by mörgæs on 2011-10-29
Yes, the hardware is all right. It does not sound really old - are you sure that it can not boot from USB, maybe after upgrading the BIOS?

If you CD drive is partly failing, you could try
[http://andyduffell.com/techblog/?p=689](http://andyduffell.com/techblog/?p=689)
If you can get the drive to read just 15 MB, it will work.

---

### Post by speedwlk on 2011-10-29
> **007casper said:**
> thank you for the speedwlk - how do I run the upgrade script?

on the 9.10 iso file I see cdromupgrade file... do I run that?


Yes. Using terminal go to the folder where you have mounted the iso and run the cdromupgrade script using:

sudo ./cdromupgrade

or 

sudo bash cdromupgrade



Good Luck on upgrading.

Edit:
see
[https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28Normal_Superuser_Mount.29](https://help.ubuntu.com/community/MountIso#From_the_Command_Line_.28Normal_Superuser_Mount.29)
[https://help.ubuntu.com/community/LucidUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/LucidUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

second link is for upgrading to lucid, but should work for karmic also.

Edit2:
upgrading to karmic:
[https://help.ubuntu.com/community/KarmicUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD](https://help.ubuntu.com/community/KarmicUpgrades#Upgrading_Using_the_Alternate_CD.2BAC8-DVD)

---


---
title: "Novice bought donated Ubuntu 11.?? Passworded machine no clue how to fix"
date: 2014-07-11
forum: New to Ubuntu
---

### Post by olli2 on 2014-07-11
I bought a donated machine (abo 2000 vintage DELL laptop) in a thrift shop.  UBUNTU 11.xx(machine is at home) Under GUEST everything works including wifi and office.  I have searched and found GRUB should help -- some versions -- but it does not show at boot and unclear if GRUB or GRUB2 or if GRUB is passworded.  

I have done IBM Mainframes and PC DOS, use Windows, but Unix/LINUX/UBUNTU is an absolute mystery.

When the screen opens it has a choice of 'user'? oa Ubuntu passworded or Guest that won't even save files: clears at exit.

Can someone walk me through a way to change Ubuntu (I assume == administration) password?

Thanks

---

### Post by ubudog on 2014-07-11
Hi,

Are you using the same Ubuntu installation that was on it when you bought it?
If so, I would recommend doing a complete fresh install of Ubuntu (or Lubuntu, considering how old the machine is).

---

### Post by olli2 on 2014-07-11
The Ubuntu is fairly new [version 11.xx -- I'm seeing 13.xx as probably current on the net and learning to install properly seems much more complicated than changing the password and then upgrading.] and everything works and is present and linked to the architecture of the machine.  I don't want to lose everything.  It was originally a Windows XP machiine and must have been changed at some time.

Thanks for reply

---

### Post by ibjsb4 on 2014-07-11
Ubuntu 11.xx has reached end of life and no longer supported.  The latest out is 14.04 which is probably too much for your old machine to handel.  I suggest Lubuntu.

[http://lubuntu.net/](http://lubuntu.net/)

---

### Post by grahammechanical on 2014-07-11
We get a release of Ubuntu every six months in April and October and this pattern is reflected in the code number of the release. So, a Ubuntu 11.xx would have been released in April (04) or October (10) of 2011. It might seem a fairly new version to you but to us it is long past End Of Life. This means that it has not had any security fixes and it will be difficult to update and even install additional applications because the software repositories for that release are now closed.

As for Ubuntu 13.xx, well Ubuntu 13.04 has also reached end of life and 13.10 is near to reaching end of life. And I would add that it is simple to upgrade from one release to another if both are still supported but more difficult if the existing release is end of life and the next release is also end of life. So, if this is Ubuntu 11.04 you will have problems because you have to upgrade to 11.10 before you can get to 12.04 the next release still supported. It has 5 years support.

As fresh install will not only give you a supported version of Ubuntu or its flavours but also solve the password problem at a stroke. You say "I don't want to lose everything." Please explain. There can be nothing on that machine of yours because you can only use Guest mode and that mode will not save any files. The guest account is designed that way and that is a security feature.

If Ubuntu is installed then there will be a Grub boot menu but if Ubuntu is the only operating system then Grub will not appear unless we hold down Shift or Esc during boot time. The login screen appears long after Grub has done its job. So, why do you think that Grub would help in this situation? Are you looking for Recovery Mode?

Regards.

[http://www.ubuntu.com/info/release-end-of-life](http://www.ubuntu.com/info/release-end-of-life)

[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

[https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)

---

### Post by olli2 on 2014-07-11
The lost password link looks promising, Thanks

The machine may be newer -- I just got the idea it was from 2000.  It is a DELL Latitude looks like pictured D610, but slower.  Recall Pentium M at about 999 Mhz,  DVD reader not writer, built in working WiFi, [possibly bluetooth which I don't understand], thin case, clean -- should be useful walk-around machiine. 

It has some form of open office and a few other things.  My concern with a install is that the installer might not recognize the architecture, and know drivers, etc.  Then the machiine wouldn't work.  The only problem is the restriction to GUEST mode.  I can keep all the existing correct drivers if I can change the password: and then it may be possible to update the old OS with a newer version without losing anything [ It is just my ignorance of UNIX type Systems].

Thanks again
When I get home I will try the steps your lost password link suggests.

---

### Post by olli2 on 2014-07-11
To your other question I forgot to answer.  Postings on the internet indicate that it is possible to change the password while in GRUB.  Some discussions indicated that kernel with recovery mode should be used -- others said kernel without recovery mode should be used.

---

### Post by yancek on 2014-07-11
If on boot you get to a login screen which shows some username (the person who isntalled the original Ubuntu) as well as guest, then the first non-guest user has root/admin privileges in all likelihood.  Strange that someone would sell a computer in that condition if that is the case.  If you are able to boot to the login screen where you see guest as an option, it has nothing to do with Grub.  The lost password link above should resolve the problem.

---

### Post by grahammechanical on 2014-07-11
Drivers are built in during the install process. Things are done differently to Windows. I have run every version of Ubuntu since 2007 on this machine and I have never had problems with drivers, even WiFi drivers.

My advice whether you fresh install or Upgrade is to deactivate any proprietary video driver and use the open source video driver. Look for the Additional Drivers utility. It is possible that the newest proprietary video driver has dropped support for that video card. The makers of video cards frequently drop support from their drivers from older video cards. So, upgrade using an open source video driver is my recommendation.

Regards.

To fresh install you will need to burn an ISO image to DVD or USB memory stick. This could be done in a Guest account but not with a DVD reader. And I wonder if the machine's BIOS will let you boot from a USB memory stick.

---

### Post by olli2 on 2014-07-11
Thanks:

I'm writing from an equipped new school Windows 7 with Autocad, Adobe Master Suite 6, etc.  I can burn a disk here.  Surely I can find a Ubunto image on the net.

"deactivate any proprietary video driver" is a mystery [even in Windows], "Additional Drivers untility" is mysterious as well. [I was better in writing IO channel programs in IBM 360 Assembler for that OS -- different technology altogether].

on "Lost Password" "The other way": 3. select your image (what is an image) also 6. Type in **passwd username**: would the user name be UBUNTU -- that is what the login screen shows above the GUEST <is this the same as the ROOT or is that something else?>

I do doubt that the machine would recognize a flash drive.  I will probably try to research DELL to see how to set the BIOS to boot from the CD ??

I am imprressed and grateful that the Ubuntu Forums are so responsive.

---

### Post by yancek on 2014-07-11
> When the screen opens it has a choice of 'user'? oa Ubuntu passworded or Guest that won't even save files: clears at exit.

A Live CD or installation medium of Ubuntu shows that, Ubuntu as a user and Guest option as I recall.  A Live CD does not save any changes, it is read-only.  If you don't have a CD/DVD or flash with Ubuntu, I don't know where that is coming from.   One possibility is a frugal install which is just the Live CD placed on the hard drive without an actual install so that it acts like a Live CD.So if you select the "Ubuntu" user and are prompted for a password and hit the Enter key and get an incorrect password, then the option above for lost password would be the way to go.

---

### Post by olli2 on 2014-07-12
Clarification & Negative outcome so-far

I posted too soon with computer at home (while I was using a school computer).  Computer is DELL Latitude D610 reviewed by CNET in 2005: 1GB ram, Intel 1.75 GHz Pentium M processor,28GB drive and built-in WiFi,  running Ubuntu 14.04 LTS. (need to replace battery which is weak -- before trying full install lest power fail midway in install).  Still not sure if I need special Archiceture knowledge to install.

I reached GRUB and selected the first UBUNTU and used linix line extender init=/bin/bash.  Received probable error 

"bash: cannot set terminal process group (-1) nappropriate ioctl for device"
"bash: no job control in this shell"
"root@(none):#"

I ran "passwd ubuntu"
Got ' enter password' type statement
Entered six letter character password and confirmed it
Feedback:
"passwd: Authenticatioin token manipulation error"
"passwd: Password Unchanged"

Next I continued:
"root@(none):/# reboot"
"Shutdown: unable to shutdown"  I had, eventually, to shutdown machine with on/off button.

NEXT:

I tried _UBUNTU (recovery mode)_ entry in GRUB

That failed but I got to a recovery menu and selected GRUB

now I got a better prompt:

"root@ubuntu-Latitude-D610:~#"

passwwd again failed with:

"passwd: Authentication token manipulation error"
"passwd: Password unchanged"

Again, I could not shut down without powering down (tried "init 2" and F10)

Does anyone know what is wrong and what "Authentication token manipulation error: is referring to?

Thanks

---

### Post by oldrocker99 on 2014-07-12
What you want to download is Ubuntu 14.04, the latest version, which has Long Term Support until April 1919 (!). It's available in Unity, LXDE, XCFE. KDE, and GNOME versions, depending on the title; they're all Ubuntu. For your older machine, I'd recommend Lubuntu 14.04. with the LXDE desktop.

>  I do doubt that the machine would recognize a flash drive. I will probably try to research DELL to see how to set the BIOS to boot from the CD ??

The BIOS probably has a Boot option, and it **might** recognize a flash drive.

---

### Post by olli2 on 2014-07-12
Sorry I appear to be lost in this new forum interface:

What I tried to send in my thread [I can't find the reply] is that I did a 14.04 install from a usb drive and it worked so now I have both the passworded and a new system: both of which work.

But the newly installed version can't see the WiFi hardware that the older version sees.

I don't know what to do.

---

### Post by yancek on 2014-07-12
> But the newly installed version can't see the WiFi hardware that the older version sees.

Neither can we so why don't you go to the site below which explains how to get that information and then you can post it here.

[http://askubuntu.com/questions/333424/how-can-i-check-the-information-of-currently-installed-wifi-drivers](http://askubuntu.com/questions/333424/how-can-i-check-the-information-of-currently-installed-wifi-drivers)

---

### Post by olli2 on 2014-07-12
Thanks

Looks confusing: but I will study it.

---

### Post by JeQhdMD on 2014-07-13
In looking at laptop specs, it appears your system may have Intel 2200 wireless.  I've been under the impression Intel wireless should work "out of the box" - - drivers already built into kernel (I've installed Ubuntu on several laptops with Intel wireless, all worked right away - no setup needed).   Did you click on the wireless applet or widget thingie in the upper right corner of your desktop?  It may just be that you need to add your network specs (ssid, pw, etc).   Another simple method to get wireless going is to purchase an inexpensive usb wireless adapter (nano size).   I know Panda makes a good one, and TP-Link is also Ubuntu friendly.   Each of those requires no driver setup at all.

The Panda device is as follows:  (can be found on Amazon and other sites - - about $10.00 usd
[h=1][SIZE=4]Panda Ultra Wireless N USB Adapter (150Mbps) - 802.11n 2.4GHz[/SIZE][/h]

---

### Post by Hadaka on 2014-07-13
actually a Dell of that vintage is more than likely to have Broadcom cards
check here to see what diver you need,
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

be sure to check the driver from the PCI-ID number,,,not the card number.

I would also guess that you loaded the proprietary driver,,,broadcom-kernel-source
that is usually not the correct driver.

*If it turns out after you check the above link that you need the linux-firmware-nonfree driver
then do this..be sure you are connected to the internet with the cable with these commands
as it needs to load the correct driver, please do,
#to delete the incorrect driver
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf #not to worry if you get an error on this line
```
#to install correct driver
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```
hope that helps,, if not have a mod move this thread to wireless
thanks.

---

### Post by verymadpip on 2014-07-13
Hi there.
I don't want to confuse things, but was there not a bug in Lubuntu 14.04
relating to the network manager applet in the panel being missing?
That would certainly make life a little difficult regarding wireless.

[https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348](https://bugs.launchpad.net/ubuntu/+source/lxsession/+bug/1308348)

Of course this could have NOTHING to do with the situation.
Feel free to ignore this :)

---


---
title: "Problem with Dual booting(win8 &amp; Ubuntu)"
date: 2012-03-25
forum: New to Ubuntu
---

### Post by harimurugan on 2012-03-25
i installed ubuntu first and made seperate partition for windows. after that i installed windows in that drive.. after installing windows i wrongly formated the ubuntu drive.. so now i again installed ubuntu in the same drive but i didnt give any option for swap partition. when i restart my system it doesnt show any option for booting to windows, it directly goes to ubuntu.. 

when i saw the partition windows is still in that drive but i am unable to boot it.. let me suggest wat to do now..

---

### Post by zombifier25 on 2012-03-25
Try running```
sudo update-grub
```in your terminal and reboot.

---

### Post by garvinrick4 on 2012-03-25
If post2 does not do it. Run this in your ubuntu install and post results.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
If have trouble running this boot_info_script just say so many users will help out.

---

### Post by harimurugan on 2012-03-25
> **garvinrick4 said:**
> If post2 does not do it. Run this in your ubuntu install and post results.
[SourceForge.net: Boot Info Script - Project Web Hosting - Open Source Software]("http://bootinfoscript.sourceforge.net/") 
If have trouble running this boot_info_script just say so many users will help out.
 
Actually second post itself worked but at first it didn't work bcz I changed the partition as dynamic from basic in windows.. that one results in hang up during booting.. 
 
when I kept the windows partition in basic type itself there is no prob.. one more doubt is how can I make windows as default booting option.. now Ubuntu is my default one..

---

### Post by garvinrick4 on 2012-03-25
> one more doubt is how can I make windows as default booting option.. now Ubuntu is my default one..
There is a GUI app that seems to work for that I have read if you do not want to use
gedit /etc/default/grub
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 

GUI app is "startupmanager' run code below to install.

```
sudo apt-get install startupmanager
```

rick@rick:~$ aptitude show startupmanager
Package: startupmanager           
State: not installed
Version: 1.9.13-5
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,393 k
Depends: python, python-support (>= 0.90.0), python-glade2 (>= 2.12),
         python-gnome2 (>= 2.20), python-libxml2 (>= 2.6.30), x11-xserver-utils,
         yelp, grub | grub-pc, menu
Description: Grub, Usplash and Splash screen configuration
 StartUp-Manager configures some settings for grub, usplash and splash screens.
 It provides an easy to use interface. 
 
 It is originally a Ubuntu project, adapted for Debian.
Homepage: [https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)

---

### Post by motoroller on 2012-03-25
If I may add something, I discovered another nice GUI Grub2 tool called "GRUB Customizer"

The nice thing is that it's still continually updated and currently up-to-date with Ubuntu 11.10 (and other dists I believe)

One down side is that you have to update the repository list to get it, but other than that, it's a great little tool.

Here's a link to a thread with the instructions on how to install it, plus usage instructions and tips.

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

hope this helps!

---

### Post by garvinrick4 on 2012-03-25
Seems to be a very good choice above. The link given is by drs305 which you can
take to the bank.  

```
sudo add-apt-repository ppa:danielrichter2007/grub-customizer
``` ```
sudo apt-get update
``` ```
sudo apt-get install grub-customizer
```

---

### Post by motoroller on 2012-03-25
Glad to be of (some) service! :cool:

---

### Post by Mark Phelps on 2012-03-25
> **harimurugan said:**
> ... I changed the partition as dynamic from basic in windows...

Linux distros can NOT be installed in a hard drive that uses Dynamic Disks -- they don't understand the partitioning.

There is no dual boot setup you can do that will use Dynamic Disks.

---

### Post by harimurugan on 2012-04-05
> **garvinrick4 said:**
> There is a GUI app that seems to work for that I have read if you do not want to use
gedit /etc/default/grub
[Grub2 - Community Ubuntu Documentation]("https://help.ubuntu.com/community/Grub2#/etc/default/grub") 

GUI app is "startupmanager' run code below to install.

```
sudo apt-get install startupmanager
```rick@rick:~$ aptitude show startupmanager
Package: startupmanager           
State: not installed
Version: 1.9.13-5
Priority: optional
Section: universe/utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,393 k
Depends: python, python-support (>= 0.90.0), python-glade2 (>= 2.12),
         python-gnome2 (>= 2.20), python-libxml2 (>= 2.6.30), x11-xserver-utils,
         yelp, grub | grub-pc, menu
Description: Grub, Usplash and Splash screen configuration
 StartUp-Manager configures some settings for grub, usplash and splash screens.
 It provides an easy to use interface. 
 
 It is originally a Ubuntu project, adapted for Debian.
Homepage: [https://launchpad.net/startup-manager](https://launchpad.net/startup-manager)
whenever i install or upgrade to newer version of windows the windows bootloader controls the booting.. so i am not to get into ubuntu since it directly windows.. again i have to use ubuntu CD to install it again then update my grub so that i can use Grub.. then wat is the use of installing ubuntu in seperate drive?? i thought if i install win & ubuntu in seperate drives, whenever i re-install win it wount affect ubuntu so there is no need of installing both OS but it doesnt happening that way...

---

### Post by Mark Phelps on 2012-04-06
The use of installing Ubuntu in a separate drive is that all you have to do when you update MS Windows in a different drive, to get Ubuntu back, is CONTINUE to boot from the Ubuntu drive -- which will boot into Ubuntu -- and then update the GRUB config file by opening a terminal and entering "sudo update=grub"

Also, keeping the OSs in separate drive prevents either one from overwriting the MBR and Boot options in the other drive, and leaves each drive entirely bootable on its own.

---


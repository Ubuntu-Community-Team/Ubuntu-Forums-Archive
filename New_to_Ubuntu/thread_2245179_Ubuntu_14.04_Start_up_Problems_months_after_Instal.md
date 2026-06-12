---
title: "Ubuntu 14.04 Start up Problems months after Installing it"
date: 2014-09-21
forum: New to Ubuntu
---

### Post by lcbmac on 2014-09-21
Hi There

I have a huge Problem.
I have an Acer Extensa  6___ Laptop, 2GB Ram and 500GB Hdd space and a few years ago Decided to make the move from Windows to Ubuntu 11. Never really had any issues with it which is why I moved to it. Over time My laptop has been through it paces and I have Up graded to 12.04 then to 13.10 and now a few months ago Recently to Ubuntu 14.04. Although I'm not experienced I'm still learning how to do the coding and quite a newbie at it.
However since I have done the upgrade to Ubuntu 14.04 I have had endless issues With my start up and have used the grub menu that by the way automatically comes up  to use the Recovery Mode. how ever In time I have tried to find out a bit why  it does so and tried more than a few various ways to fix it using the forums and Nothing has helped. I fact It has gotten worst and now my PC  stars up to the Grub recovery let me choose a recovery mode (which there 28 different ones) and it stops in the middle of the recover mode to the grub its self on the picture below Please (Hope you can see it).
There is one more thing. For some reason It wont boot off a CD/USB even when Trying to re-install Ubuntu.


Thank You

---

### Post by Bashing-om on 2014-09-22
lcbmac; Not Good;

> 
 For some reason It wont boot off a CD/USB even when Trying to re-install Ubuntu.

As we MUST have some bootable system to look at the installed system. By far the easier thing to do is boot up the liveDVD of ubuntu14.04.
Are you certain that you have set the boot priority in bios to the CD as 1st boot priority ?
Are you certain that the liveDVD is good ? Can you test on a different machine and see that it does boot ?

'Till then
[INDENT][INDENT]there is no means to help in this situation.
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-25
Hi Bashing-om


Alright so how do I check that the Disk Is faulty. Because On my windows 7 PC it does start with all processes that are need in order to auto run and go even starts the process where the main screen asks if it would like to install or partition and that's where is stop it. 
If I take out the Hdd and Put it into my Windows Machine I would assume you would see the Hdd. but it does not show up unless I got to the System management in Windows. which I presume is right being the fact Ubuntu is installed on it and the code is not the same.
What gets me is the System Is a read-only and not a read/write on the Hdd which doesn't make sense. it was read/write till a 10 days ago then this.
When I set my laptop to Cd on the bios. it starts up and goes to menu that says GNU GRUB version 2.02~bete2-9ubuntu1. gives me a list with     *Ubuntu
                                                                    Advanced options for ubuntu
                                                                    memory test (memtest86+)
                                                                    memory test (memtest86+, serial console 115200)

The fist one just goes to blank screen.  The second goes to another list and selecting one of those gors back to the pic i put on earier. The Third runs to mini list about 12 sentences long and the forth is the same as the 3rd.

---

### Post by Bashing-om on 2014-09-25
lcbmac; Hey:

A number of issues may be at play here, The least of which is a full /boot partition, and/or broken proprietary graphics driver. In order to check we must be able to boot something !
The easier and better thing is to boot a liveDVD to do some checks/verifications.
To that end:
Set in bios the CD drive as the 1st boot priority;
Boot the liveDVD and as soon as the bios screen clears, depress and hold the right -shift- key -> boot options screen.
What results when choosing the option " check disk for defects" .

Once we have a known good liveDVD, then we can look about.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-25
Hi Bashing -om

Okay the live CD does work but I cut an extra one just in case. It looks like it is booting up back into the Ubuntu system and the DVD is running and writing something but it does run the Ubuntu 14.04.1 Live.

Yes I was having issues with the Graphics card before it all went like this. However I spent a lot of time trying to fix that with forum information and nothing helped. Then this happened.  What do I need to do to fix that up from going like that again. At the same time I have a Wi-Fi system that is not even showing on the system now but my Laptop is Equipped for Wi-Fi. The same problem I had when I originally updated Ubuntu 14.04

---

### Post by kira-yamato-2008 on 2014-09-25
What kind of graphics card do you have?

---

### Post by lcbmac on 2014-09-25
To be honest I have no Idea. It does not show

---

### Post by Bashing-om on 2014-09-25
lcbmac; Hey, hey,

Let's do this one thing at a time, [s]see kira-yamato-2008's last[/s]. - WE will get to looking at graphics - directly.
Presently we want to work to getting you booted up on the install. Let's take a look at what is the most likely hindrance, the /boot partition.
Boot the liveDVD to terminal;
Post back -Between code Tags- the outputs of terminal commands:
```

df -h
df -i

``` so we see what space constraints exists.
  code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Depending on what is, is what we do.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-25
Hi Bashing-om
Alright the system has boot into Ubuntu of the live DVD as you said from the BIOS by holding the down the shift Key til it entered Ubuntu.
I would assume this means Ubuntu is live and ready to install as it has now come up and not letting me in to a terminal

---

### Post by Bashing-om on 2014-09-25
lcbmac; Hey;

I am a bit confused as to where you are at this time. Are you now at the liveDVD's boot menu ? Do you not see the option to "check disk for defects"; have you indeed run the check ? IF so, upon the required reboot get back to this menu, and this time choose " try ubuntu without installing".
This option will eventually load up the ubuntu desktop in a live mode. From here one can press the key combo ctl+alt+t to gain a terminal:
OK, back to what was: 
Post back the outputs of terminal commands:
```

df -h
df -i

```
and we move on.

[INDENT][INDENT]one step at a time
[/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-09-25
Won't it be better to start by cleaning out the /boot directory.   I had similar problems after upgrading from 12.04 to 12.10 to 13.04 to 14.04.  My /boot was filled.  I manually went in and deleted the oldest Linux-image files first.   I had 10+ of each file.  So I started with the oldest revisions and manually deleted them and kept the newest 5.  Then, rebooted.  It came up and then I could upgrade from 13.04 to 14.04.  Work on one issue at a time.  You don't need video drivers to work at a command prompt.

---

### Post by lcbmac on 2014-09-25
Hi Bashing-om

I have managed to that already but what has happened is. I did the check it span the disk then went to blank screen carried on spinning then I stood up to stretch and the laptop switched off. I assume that is good. Now I have enter the Live mode.Terminal still not coming up through

---

### Post by lcbmac on 2014-09-25
Finally it took a little time but the terminal did come up

---

### Post by Michael_McKenney on 2014-09-25
any errors?

---

### Post by Bashing-om on 2014-09-25
lcbmac: Good !

Making some progress. Now that terminal is up 
zar 3 -> Post :
```

df -h
df -i

``` at least, so we can move on in this.
No one can do anything with out information to base decisions on.

2 steps forward

---

### Post by lcbmac on 2014-09-25
Hi Bashing-on

Okay I have done ll of that and there was two lists that came up what am I looking for and what should i do now.


Hi Micheal

No errors yet althought you were mentioning the /boot directory Is the the list with over 20 items in double. lower one of each of the two which has a recovery  in brackets at the end in the grub?

---

### Post by Michael_McKenney on 2014-09-25
I used Synaptics to clean up the old Linux-images that sudo apt-get autoremove did not get.  I found over a lot of old Linux-images on the workstation.  I kept only 3.13.xxxxxxx.  The rest I removed to cleanup the box.  It seems like its is running better now and took care of the /boot files I used to manually remove.  I was surprised that Ubuntu does not clean up after itself better.  Same complaint my wife has about me.  Go figure.

---

### Post by Bashing-om on 2014-09-25
lcbmac; Hey !

I want that you post those outputs back here to this thread, so all of us can see and advise you.
I am betting that the /boot partition is full. IF the requested commands come back showing high capacity usage, then we address the reason why. Most likely still is the /boot partition. But, until such time as I see the outputs, I reserve judgement.
The tutorial once more to post terminal outputs:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

You want help, please follow guidance.

[INDENT][INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT][/INDENT]

---

### Post by Michael_McKenney on 2014-09-25
Where there is a will, there are a whole bunch of greedy relatives and kids waiting for you to kick the bucket.

---

### Post by Bashing-om on 2014-09-25
Michael_McKenney'

> **Michael_McKenney said:**
> Where there is a will, there are a whole bunch of greedy relatives and kids waiting for you to kick the bucket.

So true !, But, If it were not for a will I would not have a bucket to kick !

[INDENT][INDENT]good for the goose, good for the Gander
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-25
Hi Bashing-om

as you can see I have pasted the screen shot while I could of the output in terminal. I then have pasted the grub menu and the the advanced menu in my grub which  took with a phone camera. Hope this all helps.


[IMG]file:///C:/Users/JectImage/Pictures/Screenshot%20from%202014-09-25%2021_24_57.png[/IMG]
[IMG]file:///C:/Users/JectImage/Pictures/20140925_232933.jpg[/IMG][IMG]file:///C:/Users/JectImage/Pictures/20140925_232958.jpg[/IMG]

---

### Post by lcbmac on 2014-09-25
Sorry Guys

Okay here they are again[ATTACH=CONFIG]256690[/ATTACH][ATTACH=CONFIG]256692[/ATTACH][ATTACH=CONFIG]256693[/ATTACH]

---

### Post by Bashing-om on 2014-09-25
lcbmac; UnGood, I think.

Is this not a WUBI install.
Ubuntu installed from within Windows ?

[INDENT][INDENT]sometimes I do wonder
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-25
Hi Bashing-om

Originally I had windows 7 on the laptop. but I installed Ubuntu instead starting with the earliest disk of Ubuntu I have still at 11.04 and then upgraded each time going from 12 to 13 and now to 14.

I have two machines One desktop which runs Windows 7. and that is how i am talking to you and the other being my laptop which as you can see run the Ubuntu.,

---

### Post by Bashing-om on 2014-09-25
lcbmac; UMMPHH,

From what I can see from the 1st screen shot, I see WUBI.
From the liveDVD
Post back the out-puts - BETWEEN Code tags - of terminal commands :
```

sudo fdisk -lu
sudo parted -l

```
And let's see if there exist a partition exclusively for ubuntu.

[INDENT][INDENT]All for what it is worth
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-26
[ATTACH=CONFIG]256707[/ATTACH][ATTACH=CONFIG]256708[/ATTACH]

---

### Post by QIII on 2014-09-26
Hi, lcbmac!

It is best when replying with the results of commands in the terminal to highlight and copy the output (CTRL + Shift + C) and paste it in your response between code tags.

That makes it easier for folks to deal with.

So, for instance:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00013a8f

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048    58593279    29295616   83  Linux
/dev/sda2        58595326   488396799   214900737    5  Extended
/dev/sda5        58595328   488396799   214900736   83  Linux

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x29e95222

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048   976773119   488385536    7  HPFS/NTFS/exFAT


```

---

### Post by lcbmac on 2014-09-26
Hi Qlll

Alright I understand. But that is y i high light the area next to the second one for you to see there it starts. but ill highlight it all next time.

Thanks

---

### Post by QIII on 2014-09-26
Actually, my point was to post the code between code tags and not to post images.

;)

---

### Post by lcbmac on 2014-09-26
Hi Qlll

I'm sorry Just learning all all of this. Not to mention I Have to manually type it from one machine to the other which take a bit. But Ill do that no problem.

---

### Post by QIII on 2014-09-26
Why do you need to transcribe it from one computer to another?  Just get on the Forums from the computer you are working on if you are able to get to the GUI.

If it hasn't booted to the GUI -- for instance if it is stuck booting -- go ahead and post images.

---

### Post by lcbmac on 2014-09-26
Well what has happened is my Laptop that runs Ubuntu is not working. As Written On the top. I don't have Wi-Fi working with the Live Disk and That is the reason I'm not doing it from there. However I have not tried a new code I was going to try. bet try it now. Will let you know what happens.

---

### Post by lcbmac on 2014-09-26
Hi Qlll

okay I seem to back on the forum using the Wi-Fi after a small download and upgrade on the adapter and changing the setting a bit and  few small tweeks. So you will now get every thing accordingly using the codes. thanks again.

Hi Bashing-om

What should i do from here on. are you happy with what you see??

---

### Post by Bashing-om on 2014-09-26
lcbmac; Yeah !

@Qlll Thanks. I appreciate that you watch my back ! :)

You do indeed have a real ubuntu install ! I do not know why the output of 'df' does not reflect the "root" partition of the install, yet. As that output does reflect that you are booting from a live environment.. hummm.

Let's do this: try and clean up the system, and then take a look at the /boot partition, see what it is going to take to clean it up also:
Boot to terminal in the install and run these terminal commands:
This does require a working internet connection .. stable !
All things following the '#' are my comments, and are not to be entered,
```

sudo apt-get autoclean # only removes files that cannot be downloaded anymore (obsolete)
sudo apt-get autoremove
sudo apt-get clean
#refresh
sudo apt-get update #resync package index
sudo apt-get upgrade #newest versions of all packages, update must be run first
#would upgrade you to the latest kernel in the repositories
#dist-upgrade is also able to remove existing packages if required/and install held back packages,A dist-upgrade will install new dependencies for packages already installed and may remove packages if they are no longer needed. This will not bring you to a new release of ubuntu. 
sudo apt-get dist-upgrade
sudo apt-get -f install
sudo dpkg --configure -a

```
IF there are any errors, post them here for our inspection.
IF these proceed well, we look at /boot next. -> Think'n bout purging grub and (RE-)installing - are you ready to learn a bit about your operating system and the terminal ? Nothing to fear, just learn some respect for the power of this operating system . 


[INDENT][INDENT]an exercise in logical progression
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-27
Hi Banging-om

okay so this is what I have done and just so you cam see it and have a heads up if I have done something wrong or right.

```

sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done

```

```

 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-generic linux-image-generic
0 upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
After this operation, 57.3 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 174316 files and directories currently installed.)
Removing linux-headers-generic (3.13.0.32.38) ...
Removing linux-image-generic (3.13.0.32.38) ...

```

```

sudo apt-get clean
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign http://security.ubuntu.com trusty-security InRelease
Ign http://archive.ubuntu.com trusty InRelease 
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty Release.gpg
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]
Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty Release                        
Get:4 http://archive.ubuntu.com trusty-updates Release [59.7 kB]
Get:5 http://security.ubuntu.com trusty-security/main i386 Packages [136 kB]
Hit http://archive.ubuntu.com trusty/main i386 Packages            
Hit http://archive.ubuntu.com trusty/restricted i386 Packages
Hit http://archive.ubuntu.com trusty/main Translation-en 
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Get:6 http://archive.ubuntu.com trusty-updates/main i386 Packages [319 kB]     
Get:7 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:8 http://security.ubuntu.com trusty-security/main Translation-en [70.2 kB] 
Get:9 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:10 http://archive.ubuntu.com trusty-updates/main Translation-en [146 kB]   
Get:11 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]
Get:12 http://archive.ubuntu.com trusty-updates/restricted Translation-en [1,736 B]
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Fetched 800 kB in 21s (37.2 kB/s)                                              
Reading package lists... Done

```

##There was a problem between this where I had to do a second clean. Can I post the pics of what came up.
The fact That the error was Low dist space baffles to why.##

```

 sudo apt-get clean
ubuntu@ubuntu:~$ 

```

```

ubuntu@ubuntu:~$ sudo apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

 sudo apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

 sudo apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up xserver-common (2:1.15.1-0ubuntu2.1) ...
Setting up libgtk-3-common (3.10.8-0ubuntu1.2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Setting up libreoffice-style-human (1:4.2.6.3-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.1f-1ubuntu2.5) ...
Setting up libdbus-1-3:i386 (1.6.18-0ubuntu4.2) ...
Setting up man-db (2.6.7.1-1) ...
Updating database of manual pages ...
Setting up libgcrypt11:i386 (1.5.3-2ubuntu4.1) ...
Setting up libc6-dbg:i386 (2.19-0ubuntu6.3) ...
Setting up evolution-data-server-common (3.10.4-0ubuntu1.2) ...
Setting up ubiquity-ubuntu-artwork (2.18.8.2) ...
Setting up libjavascriptcoregtk-3.0-0:i386 (2.4.4-1~ubuntu1) ...
Setting up libwebkitgtk-3.0-common (2.4.4-1~ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up usb-creator-common (0.2.56.2) ...
Setting up libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libsystemd-journal0:i386 (204-5ubuntu20.6) ...
Setting up openssl (1.0.1f-1ubuntu2.5) ...
Setting up libudev1:i386 (204-5ubuntu20.6) ...
Setting up liblzo2-2:i386 (2.06-1.2ubuntu1.1) ...
Setting up libc-dev-bin (2.19-0ubuntu6.3) ...
Setting up gir1.2-javascriptcoregtk-3.0 (2.4.4-1~ubuntu1) ...
Setting up libept1.4.12:i386 (1.0.12) ...
Setting up linux-libc-dev:i386 (3.13.0-36.63) ...
Setting up ubiquity-slideshow-ubuntu (83.1) ...
Setting up libapt-inst1.5:i386 (1.0.1ubuntu2.4.1) ...
Setting up cups-server-common (1.7.2-0ubuntu1.2) ...
Setting up libgirepository-1.0-1 (1.40.0-1ubuntu0.2) ...
Setting up libgpgme11:i386 (1.4.3-0.1ubuntu5.1) ...
Setting up libsystemd-daemon0:i386 (204-5ubuntu20.6) ...
Setting up cups-common (1.7.2-0ubuntu1.2) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up libboost-iostreams1.54.0:i386 (1.54.0-4ubuntu3.1) ...
Setting up libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Setting up krb5-locales (1.12+dfsg-2ubuntu4.2) ...
Setting up libsystemd-login0:i386 (204-5ubuntu20.6) ...
Setting up libharfbuzz0b:i386 (0.9.27-1ubuntu1) ...
Setting up libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up uno-libs3 (4.2.6.3-0ubuntu1) ...
Setting up libnm-gtk-common (0.9.8.8-0ubuntu4.3) ...
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:31.1.2+build1-0ubuntu0.14.04.1); however:
  Version of thunderbird on system is 1:31.0+build1-0ubuntu0.14.04.1.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-debconf:
 ubiquity-frontend-debconf depends on ubiquity (= 2.18.8.2); however:
  Version of ubiquity on system is 2.18.8.

dpkg: error processing package ubiquity-frontend-debconf (--configure):
 dependency problems - leaving unconfigured
Setting up net-tools (1.60-25ubuntu2.1) ...
Setting up libaccountsservice0:i386 (0.6.35-0ubuntu7.1) ...
Setting up firefox-locale-de (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up ureadahead (0.100.0-16) ...
Setting up libcwidget3 (0.5.16-3.5ubuntu1) ...
Setting up ncurses-term (5.9+20140118-1ubuntu1) ...
Setting up apt-clone (0.3.1~ubuntu11.1) ...
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.18.8.2); however:
  Version of ubiquity on system is 2.18.8.

dpkg: error processing package ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up python3-distupgrade (1:0.220.5) ...
Setting up unity-gtk-module-common (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up irqbalance (1.0.6-2ubuntu0.14.04.1) ...
Installing new version of config file /etc/init/irqbalance.conf ...
irqbalance stop/waiting
Setting up gir1.2-glib-2.0 (1.40.0-1ubuntu0.2) ...
Setting up fonts-opensymbol (2:102.6+LibO4.2.6.3-0ubuntu1) ...
Setting up aptitude-common (0.6.8.2-1ubuntu4) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.4) ...
Setting up libunity-gtk2-parser0:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on ubiquity-frontend-2.18.8; however:
  Package ubiquity-frontend-2.18.8 is not installed.
 ubiquity depends on ubiquity-artwork-2.18.8; however:
  Package ubiquity-artwork-2.18.8 is not installed.

dpkg: error processing package ubiquity (--configure):
 dependency problems - leaving unconfigured
Setting up shotwell-common (0.18.0-0ubuntu4.2) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up firefox-locale-zh-hans (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up firefox-locale-es (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up firefox-locale-en (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up apt-utils (1.0.1ubuntu2.4.1) ...
Setting up udev (204-5ubuntu20.6) ...
udev stop/waiting
udev start/running
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs is disabled since running on read-only media
Setting up rsyslog (7.4.4-1ubuntu2.1) ...
Installing new version of config file /etc/rsyslog.conf ...
The user `syslog' is already a member of `adm'.
rsyslog stop/waiting
rsyslog start/running
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Setting up firefox-locale-pt (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up ure (4.2.6.3-0ubuntu1) ...
Setting up libgudev-1.0-0:i386 (1:204-5ubuntu20.6) ...
Setting up libc6-dev:i386 (2.19-0ubuntu6.3) ...
Setting up python-gi (3.12.0-1ubuntu1) ...
Setting up xserver-xorg-core (2:1.15.1-0ubuntu2.1) ...
Setting up libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up dbus (1.6.18-0ubuntu4.2) ...
Installing new version of config file /etc/dbus-1/session.conf ...
Setting up python3-gi (3.12.0-1ubuntu1) ...
Setting up libharfbuzz-icu0:i386 (0.9.27-1ubuntu1) ...
Setting up unity-gtk2-module:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up libreoffice-common (1:4.2.6.3-0ubuntu1) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up bogl-bterm (0.1.18-9ubuntu1) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.6) ...
Setting up ubuntu-release-upgrader-core (1:0.220.5) ...
Setting up python-gi-cairo (3.12.0-1ubuntu1) ...
Setting up python-gobject (3.12.0-1ubuntu1) ...
Setting up dbus-x11 (1.6.18-0ubuntu4.2) ...
Setting up aptitude (0.6.8.2-1ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up python3-apport (2.14.1-0ubuntu3.4) ...
Setting up gir1.2-freedesktop (1.40.0-1ubuntu0.2) ...
Setting up xserver-xorg-video-intel (2:2.99.910-0ubuntu1.1) ...
Setting up ubuntu-drivers-common (1:0.2.91.7) ...
Setting up python3-gi-cairo (3.12.0-1ubuntu1) ...
Setting up apport (2.14.1-0ubuntu3.4) ...
apport start/running
Setting up libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up python3-aptdaemon (1.1.1-1ubuntu5.1) ...
Setting up libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up accountsservice (0.6.35-0ubuntu7.1) ...
Setting up systemd-services (204-5ubuntu20.6) ...
Setting up libpam-systemd:i386 (204-5ubuntu20.6) ...
systemd-logind start/running, process 16271
Setting up libcups2:i386 (1.7.2-0ubuntu1.2) ...
Setting up samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libcurl3:i386 (7.35.0-1ubuntu2.1) ...
Setting up aptdaemon (1.1.1-1ubuntu5.1) ...
Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libcupscgi1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libcupsppdc1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libcupsimage2:i386 (1.7.2-0ubuntu1.2) ...
Setting up python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.1) ...
Setting up cups-ppdc (1.7.2-0ubuntu1.2) ...
Setting up libcurl3-gnutls:i386 (7.35.0-1ubuntu2.1) ...
Setting up cups-client (1.7.2-0ubuntu1.2) ...
Setting up apt-transport-https (1.0.1ubuntu2.4.1) ...
Setting up libcupsmime1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libgtk-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libunity-gtk3-parser0:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.2) ...
Setting up libnm-gtk0 (0.9.8.8-0ubuntu4.3) ...
Setting up unity-gtk3-module:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up cups-daemon (1.7.2-0ubuntu1.2) ...
Setting up cups-bsd (1.7.2-0ubuntu1.2) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.2) ...
Setting up network-manager-gnome (0.9.8.8-0ubuntu4.3) ...
Setting up usb-creator-gtk (0.2.56.2) ...
Setting up python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.1) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up apport-gtk (2.14.1-0ubuntu3.4) ...
Setting up unity-services (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up libwebkitgtk-3.0-0:i386 (2.4.4-1~ubuntu1) ...
Setting up cups-core-drivers (1.7.2-0ubuntu1.2) ...
Setting up gir1.2-webkit-3.0 (2.4.4-1~ubuntu1) ...
Setting up libunity-core-6.0-9 (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up cups (1.7.2-0ubuntu1.2) ...
Updating PPD files for cups ...
Updating PPD files for cups-filters ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for c2esp ...
Updating PPD files for foo2zjs-common ...
Updating PPD files for gutenprint ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Updating PPD files for ptouch ...
Updating PPD files for pxljr ...
Updating PPD files for sag-gdi ...
Updating PPD files for splix ...
Setting up ubuntu-release-upgrader-gtk (1:0.220.5) ...
Setting up shotwell (0.18.0-0ubuntu4.2) ...
Setting up unity (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up tasksel-data (2.88ubuntu15) ...
Setting up libnss3-nssdb (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up tasksel (2.88ubuntu15) ...
Setting up libnss3:i386 (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up libreoffice-core (1:4.2.6.3-0ubuntu1) ...
Setting up python3-uno (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-math (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-base-core (1:4.2.6.3-0ubuntu1) ...
Setting up libcamel-1.2-45 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-pdfimport (1:4.2.6.3-0ubuntu1) ...
Setting up libnss3-1d:i386 (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-gtk (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-draw (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-calc (1:4.2.6.3-0ubuntu1) ...
Setting up libedataserver-1.2-18 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-impress (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-writer (1:4.2.6.3-0ubuntu1) ...
Setting up libebook-contacts-1.2-0 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-gnome (1:4.2.6.3-0ubuntu1) ...
Setting up libebackend-1.2-7 (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-edataserver-1.2 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-presentation-minimizer (1:4.2.6.3-0ubuntu1) ...
Setting up libedata-book-1.2-20 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-ogltrans (1:4.2.6.3-0ubuntu1) ...
Setting up libebook-1.2-14 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-help-en-us (1:4.2.6.3-0ubuntu1) ...
Setting up libecal-1.2-16 (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-ebookcontacts-1.2 (3.10.4-0ubuntu1.2) ...
Setting up evolution-data-server-online-accounts (3.10.4-0ubuntu1.2) ...
Setting up libedata-cal-1.2-23 (3.10.4-0ubuntu1.2) ...
Setting up evolution-data-server (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-ebook-1.2 (3.10.4-0ubuntu1.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for libreoffice-common (1:4.2.6.3-0ubuntu1) ...
Errors were encountered while processing:
 thunderbird-gnome-support
 ubiquity-frontend-debconf
 ubiquity-frontend-gtk
 ubiquity
ubuntu@ubuntu:~$ sudo dpkg --configure -a
Setting up xserver-common (2:1.15.1-0ubuntu2.1) ...
Setting up libgtk-3-common (3.10.8-0ubuntu1.2) ...
Processing triggers for shared-mime-info (1.2-0ubuntu3) ...
Setting up libreoffice-style-human (1:4.2.6.3-0ubuntu1) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Setting up libssl1.0.0:i386 (1.0.1f-1ubuntu2.5) ...
Setting up libdbus-1-3:i386 (1.6.18-0ubuntu4.2) ...
Setting up man-db (2.6.7.1-1) ...
Updating database of manual pages ...
Setting up libgcrypt11:i386 (1.5.3-2ubuntu4.1) ...
Setting up libc6-dbg:i386 (2.19-0ubuntu6.3) ...
Setting up evolution-data-server-common (3.10.4-0ubuntu1.2) ...
Setting up ubiquity-ubuntu-artwork (2.18.8.2) ...
Setting up libjavascriptcoregtk-3.0-0:i386 (2.4.4-1~ubuntu1) ...
Setting up libwebkitgtk-3.0-common (2.4.4-1~ubuntu1) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
Setting up usb-creator-common (0.2.56.2) ...
Setting up libwbclient0:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libsystemd-journal0:i386 (204-5ubuntu20.6) ...
Setting up openssl (1.0.1f-1ubuntu2.5) ...
Setting up libudev1:i386 (204-5ubuntu20.6) ...
Setting up liblzo2-2:i386 (2.06-1.2ubuntu1.1) ...
Setting up libc-dev-bin (2.19-0ubuntu6.3) ...
Setting up gir1.2-javascriptcoregtk-3.0 (2.4.4-1~ubuntu1) ...
Setting up libept1.4.12:i386 (1.0.12) ...
Setting up linux-libc-dev:i386 (3.13.0-36.63) ...
Setting up ubiquity-slideshow-ubuntu (83.1) ...
Setting up libapt-inst1.5:i386 (1.0.1ubuntu2.4.1) ...
Setting up cups-server-common (1.7.2-0ubuntu1.2) ...
Setting up libgirepository-1.0-1 (1.40.0-1ubuntu0.2) ...
Setting up libgpgme11:i386 (1.4.3-0.1ubuntu5.1) ...
Setting up libsystemd-daemon0:i386 (204-5ubuntu20.6) ...
Setting up cups-common (1.7.2-0ubuntu1.2) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Setting up libboost-iostreams1.54.0:i386 (1.54.0-4ubuntu3.1) ...
Setting up libnspr4:i386 (2:4.10.7-0ubuntu0.14.04.1) ...
Setting up krb5-locales (1.12+dfsg-2ubuntu4.2) ...
Setting up libsystemd-login0:i386 (204-5ubuntu20.6) ...
Setting up libharfbuzz0b:i386 (0.9.27-1ubuntu1) ...
Setting up libkrb5support0:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up samba-common (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up uno-libs3 (4.2.6.3-0ubuntu1) ...
Setting up libnm-gtk-common (0.9.8.8-0ubuntu4.3) ...
dpkg: dependency problems prevent configuration of thunderbird-gnome-support:
 thunderbird-gnome-support depends on thunderbird (= 1:31.1.2+build1-0ubuntu0.14.04.1); however:
  Version of thunderbird on system is 1:31.0+build1-0ubuntu0.14.04.1.

dpkg: error processing package thunderbird-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubiquity-frontend-debconf:
 ubiquity-frontend-debconf depends on ubiquity (= 2.18.8.2); however:
  Version of ubiquity on system is 2.18.8.

dpkg: error processing package ubiquity-frontend-debconf (--configure):
 dependency problems - leaving unconfigured
Setting up net-tools (1.60-25ubuntu2.1) ...
Setting up libaccountsservice0:i386 (0.6.35-0ubuntu7.1) ...
Setting up firefox-locale-de (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up ureadahead (0.100.0-16) ...
Setting up libcwidget3 (0.5.16-3.5ubuntu1) ...
Setting up ncurses-term (5.9+20140118-1ubuntu1) ...
Setting up apt-clone (0.3.1~ubuntu11.1) ...
dpkg: dependency problems prevent configuration of ubiquity-frontend-gtk:
 ubiquity-frontend-gtk depends on ubiquity (= 2.18.8.2); however:
  Version of ubiquity on system is 2.18.8.

dpkg: error processing package ubiquity-frontend-gtk (--configure):
 dependency problems - leaving unconfigured
Setting up python3-distupgrade (1:0.220.5) ...
Setting up unity-gtk-module-common (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up irqbalance (1.0.6-2ubuntu0.14.04.1) ...
Installing new version of config file /etc/init/irqbalance.conf ...
irqbalance stop/waiting
Setting up gir1.2-glib-2.0 (1.40.0-1ubuntu0.2) ...
Setting up fonts-opensymbol (2:102.6+LibO4.2.6.3-0ubuntu1) ...
Setting up aptitude-common (0.6.8.2-1ubuntu4) ...
Setting up python3-problem-report (2.14.1-0ubuntu3.4) ...
Setting up libunity-gtk2-parser0:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
dpkg: dependency problems prevent configuration of ubiquity:
 ubiquity depends on ubiquity-frontend-2.18.8; however:
  Package ubiquity-frontend-2.18.8 is not installed.
 ubiquity depends on ubiquity-artwork-2.18.8; however:
  Package ubiquity-artwork-2.18.8 is not installed.

dpkg: error processing package ubiquity (--configure):
 dependency problems - leaving unconfigured
Setting up shotwell-common (0.18.0-0ubuntu4.2) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up firefox-locale-zh-hans (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up firefox-locale-es (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up firefox-locale-en (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up apt-utils (1.0.1ubuntu2.4.1) ...
Setting up udev (204-5ubuntu20.6) ...
udev stop/waiting
udev start/running
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs is disabled since running on read-only media
Setting up rsyslog (7.4.4-1ubuntu2.1) ...
Installing new version of config file /etc/rsyslog.conf ...
The user `syslog' is already a member of `adm'.
rsyslog stop/waiting
rsyslog start/running
Processing triggers for libglib2.0-0:i386 (2.40.0-2) ...
Setting up firefox-locale-pt (32.0.3+build1-0ubuntu0.14.04.1) ...
Setting up ure (4.2.6.3-0ubuntu1) ...
Setting up libgudev-1.0-0:i386 (1:204-5ubuntu20.6) ...
Setting up libc6-dev:i386 (2.19-0ubuntu6.3) ...
Setting up python-gi (3.12.0-1ubuntu1) ...
Setting up xserver-xorg-core (2:1.15.1-0ubuntu2.1) ...
Setting up libk5crypto3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up dbus (1.6.18-0ubuntu4.2) ...
Installing new version of config file /etc/dbus-1/session.conf ...
Setting up python3-gi (3.12.0-1ubuntu1) ...
Setting up libharfbuzz-icu0:i386 (0.9.27-1ubuntu1) ...
Setting up unity-gtk2-module:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up libreoffice-common (1:4.2.6.3-0ubuntu1) ...
Installing new version of config file /etc/bash_completion.d/libreoffice.sh ...
Setting up bogl-bterm (0.1.18-9ubuntu1) ...
Setting up gir1.2-gudev-1.0 (1:204-5ubuntu20.6) ...
Setting up ubuntu-release-upgrader-core (1:0.220.5) ...
Setting up python-gi-cairo (3.12.0-1ubuntu1) ...
Setting up python-gobject (3.12.0-1ubuntu1) ...
Setting up dbus-x11 (1.6.18-0ubuntu4.2) ...
Setting up aptitude (0.6.8.2-1ubuntu4) ...
update-alternatives: using /usr/bin/aptitude-curses to provide /usr/bin/aptitude (aptitude) in auto mode
Setting up python3-apport (2.14.1-0ubuntu3.4) ...
Setting up gir1.2-freedesktop (1.40.0-1ubuntu0.2) ...
Setting up xserver-xorg-video-intel (2:2.99.910-0ubuntu1.1) ...
Setting up ubuntu-drivers-common (1:0.2.91.7) ...
Setting up python3-gi-cairo (3.12.0-1ubuntu1) ...
Setting up apport (2.14.1-0ubuntu3.4) ...
apport start/running
Setting up libkrb5-3:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up python3-aptdaemon (1.1.1-1ubuntu5.1) ...
Setting up libgssapi-krb5-2:i386 (1.12+dfsg-2ubuntu4.2) ...
Setting up accountsservice (0.6.35-0ubuntu7.1) ...
Setting up systemd-services (204-5ubuntu20.6) ...
Setting up libpam-systemd:i386 (204-5ubuntu20.6) ...
systemd-logind start/running, process 16271
Setting up libcups2:i386 (1.7.2-0ubuntu1.2) ...
Setting up samba-libs:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up python-samba (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libcurl3:i386 (7.35.0-1ubuntu2.1) ...
Setting up aptdaemon (1.1.1-1ubuntu5.1) ...
Setting up samba-common-bin (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libcupscgi1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libcupsppdc1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libcupsimage2:i386 (1.7.2-0ubuntu1.2) ...
Setting up python3-aptdaemon.pkcompat (1.1.1-1ubuntu5.1) ...
Setting up cups-ppdc (1.7.2-0ubuntu1.2) ...
Setting up libcurl3-gnutls:i386 (7.35.0-1ubuntu2.1) ...
Setting up cups-client (1.7.2-0ubuntu1.2) ...
Setting up apt-transport-https (1.0.1ubuntu2.4.1) ...
Setting up libcupsmime1:i386 (1.7.2-0ubuntu1.2) ...
Setting up libsmbclient:i386 (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libgtk-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up smbclient (2:4.1.6+dfsg-1ubuntu2.14.04.3) ...
Setting up libunity-gtk3-parser0:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up libgtk-3-bin (3.10.8-0ubuntu1.2) ...
Setting up libnm-gtk0 (0.9.8.8-0ubuntu4.3) ...
Setting up unity-gtk3-module:i386 (0.0.0+14.04.20140403-0ubuntu2) ...
Setting up cups-daemon (1.7.2-0ubuntu1.2) ...
Setting up cups-bsd (1.7.2-0ubuntu1.2) ...
Setting up gir1.2-gtk-3.0 (3.10.8-0ubuntu1.2) ...
Setting up network-manager-gnome (0.9.8.8-0ubuntu4.3) ...
Setting up usb-creator-gtk (0.2.56.2) ...
Setting up python3-aptdaemon.gtk3widgets (1.1.1-1ubuntu5.1) ...
Setting up libgail-3-0:i386 (3.10.8-0ubuntu1.2) ...
Setting up apport-gtk (2.14.1-0ubuntu3.4) ...
Setting up unity-services (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up libwebkitgtk-3.0-0:i386 (2.4.4-1~ubuntu1) ...
Setting up cups-core-drivers (1.7.2-0ubuntu1.2) ...
Setting up gir1.2-webkit-3.0 (2.4.4-1~ubuntu1) ...
Setting up libunity-core-6.0-9 (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up cups (1.7.2-0ubuntu1.2) ...
Updating PPD files for cups ...
Updating PPD files for cups-filters ...
Updating PPD files for foomatic-db-compressed-ppds ...
Updating PPD files for openprinting-ppds ...
Updating PPD files for c2esp ...
Updating PPD files for foo2zjs-common ...
Updating PPD files for gutenprint ...
Updating PPD files for hpcups ...
Updating PPD files for postscript-hp ...
Updating PPD files for ptouch ...
Updating PPD files for pxljr ...
Updating PPD files for sag-gdi ...
Updating PPD files for splix ...
Setting up ubuntu-release-upgrader-gtk (1:0.220.5) ...
Setting up shotwell (0.18.0-0ubuntu4.2) ...
Setting up unity (7.2.2+14.04.20140714-0ubuntu1.1) ...
Setting up tasksel-data (2.88ubuntu15) ...
Setting up libnss3-nssdb (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up tasksel (2.88ubuntu15) ...
Setting up libnss3:i386 (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up libreoffice-core (1:4.2.6.3-0ubuntu1) ...
Setting up python3-uno (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-math (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-base-core (1:4.2.6.3-0ubuntu1) ...
Setting up libcamel-1.2-45 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-pdfimport (1:4.2.6.3-0ubuntu1) ...
Setting up libnss3-1d:i386 (2:3.17.1-0ubuntu0.14.04.1) ...
Setting up libreoffice-avmedia-backend-gstreamer (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-gtk (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-draw (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-calc (1:4.2.6.3-0ubuntu1) ...
Setting up libedataserver-1.2-18 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-impress (1:4.2.6.3-0ubuntu1) ...
Setting up libreoffice-writer (1:4.2.6.3-0ubuntu1) ...
Setting up libebook-contacts-1.2-0 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-gnome (1:4.2.6.3-0ubuntu1) ...
Setting up libebackend-1.2-7 (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-edataserver-1.2 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-presentation-minimizer (1:4.2.6.3-0ubuntu1) ...
Setting up libedata-book-1.2-20 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-ogltrans (1:4.2.6.3-0ubuntu1) ...
Setting up libebook-1.2-14 (3.10.4-0ubuntu1.2) ...
Setting up libreoffice-help-en-us (1:4.2.6.3-0ubuntu1) ...
Setting up libecal-1.2-16 (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-ebookcontacts-1.2 (3.10.4-0ubuntu1.2) ...
Setting up evolution-data-server-online-accounts (3.10.4-0ubuntu1.2) ...
Setting up libedata-cal-1.2-23 (3.10.4-0ubuntu1.2) ...
Setting up evolution-data-server (3.10.4-0ubuntu1.2) ...
Setting up gir1.2-ebook-1.2 (3.10.4-0ubuntu1.2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.3) ...
Processing triggers for ureadahead (0.100.0-16) ...
Processing triggers for libreoffice-common (1:4.2.6.3-0ubuntu1) ...
Errors were encountered while processing:
 thunderbird-gnome-support
 ubiquity-frontend-debconf
 ubiquity-frontend-gtk
 ubiquity

```

---

### Post by Bashing-om on 2014-09-27
lcbmac; Good Morning !


Let's address this issue, as disk space if the 1st and greatest priority:
> 
The fact That the error was Low dist space baffles to why.##

Let's look and see where that space is being consumed ( ?boot ??).
```

df -h
df -i
dpkg -l | grep linux-
cd /
sudo du -sx * | sort -n
cd

```
If you need to drill down further, use 'cd' to move to a directory of interest then repeat the 'du' command.
The results are in megabytes. We often find it is the /boot partition that is low on space due to many old kernels still in residence. These commnads will relate the disk space usage, and  confirm that the culprit is installed kernels.

Once we have restored operating overhead we will return to ->
thunderbird-gnome-support
 ubiquity-frontend-debconf
 ubiquity-frontend-gtk
 ubiquity
And see what it will take to make the package manager happy.

so far ->
[INDENT][INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-28
Good morning Bashing-om

okay so here are the results but I'm not sure at all how to do what you have asked about drilling down further using the CD.

```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow           1004M  852M  152M  85% /
none            4.0K     0  4.0K   0% /sys/fs/cgroup
udev            994M  4.0K  994M   1% /dev
tmpfs          1004M  1.1M 1003M   1% /tmp
tmpfs           201M  1.2M  200M   1% /run
none            5.0M  4.0K  5.0M   1% /run/lock
none           1004M  208K 1004M   1% /run/shm
none            100M   88K  100M   1% /run/user
/dev/sr0        987M  987M     0 100% /cdrom
/dev/loop0      952M  952M     0 100% /rofs
/dev/sdb1       3.8G  988M  2.8G  26% /media/ubuntu/UNTITLED

```

```

 df-i
No command 'df-i' found, did you mean:
 Command 'dfi' from package 'seqan-apps' (universe)
df-i: command not found

```

```

dpkg -l |grep linux-
ii  linux-firmware                                        1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.13.0-32                               3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                       3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                   3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-libc-dev:i386                                   3.13.0-36.63                                        i386         Linux Kernel Headers for development
ii  linux-sound-base                                      1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                       3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                       2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies

```

```

cd/
bash: cd/: No such file or directory

```

```

ubuntu@ubuntu:~$ cd/
bash: cd/: No such file or directory
ubuntu@ubuntu:~$ sudo du -sx * |sort -n
0    Desktop
0    Documents
0    Downloads
0    Music
0    Pictures
0    Public
0    Templates
0    Videos

```


I hope I have done this right and as you needed.

---

### Post by lcbmac on 2014-09-28
Hi Bashing-om Sorry I did see one thing I mist or at least miss typed which i have corrected from 
```

cd /
sudo du -sx * | sort -n

```

Here it is the correction for you

```

ubuntu@ubuntu:~$ cd /

```
```

ubuntu@ubuntu:/$ sudo du -sx * | sort -n
du: cannot access &#8216;proc/19734/task/19734/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/19734/task/19734/fdinfo/4&#8217;: No such file or directory
du: cannot access &#8216;proc/19734/fd/4&#8217;: No such file or directory
du: cannot access &#8216;proc/19734/fdinfo/4&#8217;: No such file or directory
0    bin
0    boot
0    etc
0    home
0    initrd.img
0    lib
0    media
0    mnt
0    opt
0    proc
0    root
0    sbin
0    srv
0    sys
0    tmp
0    usr
0    var
4    dev
1188    run
1009134    cdrom
2712039    rofs

```

Hope this rectifies the what you are looking at.

---

### Post by Bashing-om on 2014-09-28
lcbmac; Nope,

Just confuses the issue even more:
for reference my outputs:
```

sysop@1404mini:/$ sudo du -sx * | sort -n
[sudo] password for sysop: 
du: cannot access ‘proc/2007/task/2007/fd/4’: No such file or directory
du: cannot access ‘proc/2007/task/2007/fdinfo/4’: No such file or directory
du: cannot access ‘proc/2007/fd/4’: No such file or directory
du: cannot access ‘proc/2007/fdinfo/4’: No such file or directory
0       forcefsdk
0       initrd.img
0       initrd.img.old
0       proc
0       sys
0       vmlinuz
0       vmlinuz.old
4       dev
4       lib64
4       srv
4       test
4       work
12      media
12      tmp
16      lost+found
736     run
1824    root
4984    grub
6148    etc
8644    mnt
9448    sbin
9824    bin
103700  boot
182032  opt
382772  var
669488  lib
1108104 usr
1286804 home
sysop@1404mini:/$ 

```
Note in yours we still have reference to an outside booting source:
> 
 1009134    cdrom
2712039    rofs

and NONE of your system directories are shown to be populated ! YUK ! What in the world is going on here ???
Lemme have time to clear my mind, and look things over again. See what I can do to get a clear perspective on what is not going on here.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I just do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-28
Hi Bashing-om

This Is why I asked for help. It doesn't make sense all For any of this to go on like this but yet it does. 
Thank you for all the help thus so far. I know it must be quite frustrating.

---

### Post by Bashing-om on 2014-09-28
lcbmac; Hey;

Just hang loose, and tighten up when required. We will get to the bottom of this - and I hope you learn from the experience, becoming even more comfortable with this our operating system by choice. I have not to this time had the time to review, as soon as I can get to that point in my own mind, we will continue.
I want this as my focus, and have my undivided attention. Here details ARE important.

[INDENT][INDENT]we will make it happen
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-09-28
lcbmac; Hey;Back for a short short;

OK, how are you booting the system ?
I want that you go into bios, and insure that the hard drive that contains the operating system is set as the 1st boot priority.

Now, when you boot, do you boot to grub's boot menu ? Must you depress and hold the shift key to obtain this menu ( no big deal at all if that is what is required). 
What results when you select the most current kernel to boot up ?
What results when you select an OLD kernel to boot up ?

Not able to boot, the next thing is to try and boot from a liveDVD IF with boot priority reset to hard drive can not boot.

[INDENT][INDENT]reduce to simplest terms
[INDENT][INDENT][INDENT]then proceed
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-28
Hi Bashing-om

Okay so as I would normally do so.
Switch the Laptop on and let it run into Ubuntu. Type in a password and thats it.
However in the last month. I would have to press escape during the start-up to load into the Grub. Then Select Advanced Ubuntu and select one of the top 3 recovery modes and then let it Boot into Ubuntu that way. but the last week -/ week and a half my updates stopped and the Laptop said it is read only.
Last one being it did not work and now this is where we are.

The Laptop only has one HDD drive and it was set to Boot on 1st boot with the HDD. After the system refused to Boot up to Ubuntu I changed it to Boot up with 1st Boot with the CD drive.

The last week Of the system going to read only it automatically boot to the Grub Menu and still does if I leave it to do so. So no there is no pressing shift key down. However in order to load this up using the CD onto the CD, I do Have to hold down the shift key.

Once I Get to the Grub Menu and select the Advance Ubuntu  menu. Yes and No, I do Select and have selected  the most recent and even tried the others to see if it maybe something else. Recent being at the top and oldest being the lower ones on the menu I'm Assuming.
All have ended in the same Result select goes through a reading menu that says okay or error as the pic below shows, and that is where it stops.
And that is where I am now. :-)[ATTACH=CONFIG]256780[/ATTACH]

---

### Post by lcbmac on 2014-09-28
Oh and I have to use the LiveDVD in order to Run Ubuntu so that I can do this and ad what you need for the terminal.

I dont now how else to get it to work.

Is there away to clean up the Kernal  and get the system to work on READ / READ WRITE instead of read and then try it that way to see if maybe there is something wrong that can fix the Start Code/Loading Code For it boot up.
Just thinking If there is away to repair the boot  menu and start up code it might fix the problem.
sorry I'm just spit balling here but I think the problem lays in the start up code

---

### Post by Bashing-om on 2014-09-28
lcbmac; Hey,

Agreed, a booting issue derived from a full /boot partition. The system then has no operating head room, and as such the system then goes into read only mode to protect it's self.

so:
1) Look, remove old kernels
2) run - from the livedvd - ubuntu's file system check/repair
3) (re-)install the boot code - again from the liveDVD.

Let's look
boot up the liveDVD to terminal:
Post back the results:
```

sudo fdisk -lu
sudo parted -l

```
so I know where the root partition of the install is, and we mount it and look.

OK, we know where/what and next is to do a full change root into the install from the liveDVD and remove those kernels.

But 1 step at a time .. let's look and see, then do.

[INDENT][INDENT][INDENT]we have a plan
[/INDENT][/INDENT][/INDENT]

---

### Post by jeff7240 on 2014-09-28
hi 
I have a similar problem which I will be  documenting  .I have one question  are you trying to boot on battery power? and one suggestion .try another disk or usb with ubuntu 13.04 see if that will load

---

### Post by JeQhdMD on 2014-09-28
Wow, what a thread.   In case this hasn't already been done, I would suggest it's just easier to start from absolute scratch (the beginning), and ensure you have a good DVD disk of Ubuntu 14.04.1.    Then, absolutely ensure your boot order is correct - that the hard disk drive is listed as the top priority for loading ubuntu, instead of the CD/DVD optical disk.   Then, if you have any data on the hard drive, next step is to use a live CD (parted magic works _very well and fast_), and once you have your files transferred to a suitable flash-stick, just do a complete re-install and let the Ubuntu installer use the whole hard drive.   Somehow, all your rescue mode attempts have messed up your drive partition tables and where the grub bootloader is installed (it should be installed to sda1).   A fresh new install seems a lot simpler and less work than what you are doing now. . . . .

---

### Post by lcbmac on 2014-09-29
Hi Bashing-om

Okay So here is the results:

```

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000f21fe

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   308406271   154202112   83  Linux
/dev/sda2       308408318   312580095     2085889    5  Extended
/dev/sda5       308408320   312580095     2085888   82  Linux swap / Solaris

Disk /dev/sdb: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897087 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63     7897049     3948493+   b  W95 FAT32

```


```

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA Hitachi HTS54321 (scsi)
Disk /dev/sda: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  158GB  158GB   primary   ext4            boot
 2      158GB   160GB  2136MB  extended
 5      158GB   160GB  2136MB  logical   linux-swap(v1)


Model: Ut163 USB2FlashStorage (scsi)
Disk /dev/sdb: 4043MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  4043MB  4043MB  primary  fat32


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!

```

Does this help??

How Do I remove the old Kernels and the rest of the steps or Is that next?




----------------------------------------------------------------------------------------


Hi Richardgjeff

It wont work off a USB and the CD is a LiveDVD which is how I am able to sort thing out right now.

-------------------------------------------------------------------------

Hi JeQhdMD

I would but I could not get the the CD working and the the system would not allow a reinstall at the time. no to mention I cant get to the info of my HDD till we have some how sorted a boot that takes me into my original Ubuntu so I can at least get some of the important files i need before I reinstall my Ubuntu. Hopefully.

---

### Post by Bashing-om on 2014-09-29
lcbmac; OK;

Making progress, we know where to look now:
So let's "look":
Boot the liveDVD to terminal:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -al /mnt/work
ls -al /mnt/work/boot
ls -la /mnt/work/home
ls -la /mnt/work/home/<your_user_name>

```
Example: ls -la /mnt/work/home/lcbmac
We will see what kernels are installed, and IF you can pull "your" files from off the hard drive.
When all done ->
As we have mounted a file system (sda1) manually we MUST (UN)mount it else file system corruption may result !!
```

sudo umount /mnt/work

```

And is now safe to shut down.

[INDENT][INDENT][INDENT]roll our sleeves up
[INDENT][INDENT][INDENT][INDENT]and go to work
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-29
Hi Bashing-om

okay this is going to sound dumb and prefibly put me on the map for doffness, but how do I move my files across when they show in terminal to my external drive, 

I am assuming that how i need to do it because it does not show in my files.

---

### Post by lcbmac on 2014-09-29
before I Forget

I think this is what you wanted to see in order to know what is going on.
I hope it helps. and I have not unmounted anything yet.

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/work

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work

ubuntu@ubuntu:~$ ls -al /mnt/work
ls: cannot access /mnt/work/etc: Input/output error
total 112
drwxr-xr-x  23 root root  4096 Sep 11 20:16 .
drwxr-xr-x   1 root root    60 Sep 29 17:57 ..
drwxr-xr-x   2 root root  4096 Aug 27 07:53 bin
drwxr-xr-x   3 root root 12288 Aug 27 07:54 boot
drwxr-xr-x   2 root root  4096 May  8  2012 cdrom
drwxr-xr-x   5 root root  4096 Apr 23  2012 dev
d?????????   ? ?    ?        ?            ? etc
-rw-r--r--   1 root root     0 Sep 11 20:16 forcefsch
drwxr-xr-x   3 root root  4096 May  8  2012 home
lrwxrwxrwx   1 root root    33 Aug 21 21:56 initrd.img -> boot/initrd.img-3.13.0-35-generic
lrwxrwxrwx   1 root root    33 Aug 14 17:17 initrd.img.old -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  24 root root  4096 Aug 29 07:56 lib
drwx------ 149 root root 16384 May  8  2012 lost+found
drwxr-xr-x   4 root root  4096 Sep  9  2013 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   4 root root  4096 Apr  6 18:05 opt
drwxr-xr-x   2 root root  4096 Apr 19  2012 proc
drwx------   9 root root  4096 Sep  1 11:51 root
drwxr-xr-x   8 root root  4096 Apr 23  2012 run
drwxr-xr-x   2 root root 12288 Aug 29 07:55 sbin
drwxr-xr-x   2 root root  4096 Apr 23  2012 srv
drwxr-xr-x   2 root root  4096 Apr 14  2012 sys
drwxrwxrwt   8 root root  4096 Sep 18 07:13 tmp
drwxrwxrwt   9 root root  4096 Sep  6 23:20 tmp_old
drwxr-xr-x  10 root root  4096 Apr 23  2012 usr
drwxr-xr-x  15 root root  4096 Oct 12  2013 var
lrwxrwxrwx   1 root root    30 Aug 21 21:56 vmlinuz -> boot/vmlinuz-3.13.0-35-generic
lrwxrwxrwx   1 root root    30 Aug 14 17:17 vmlinuz.old -> boot/vmlinuz-3.13.0-34-generic

```

```

ubuntu@ubuntu:~$ ls al /mnt/work/boot
ls: cannot access al: No such file or directory
/mnt/work/boot:
abi-3.11.0-13-generic                  initrd.img-3.13.0-29-generic
abi-3.11.0-14-generic                  initrd.img-3.13.0-30-generic
abi-3.11.0-15-generic                  initrd.img-3.13.0-31-generic
abi-3.11.0-17-generic                  initrd.img-3.13.0-32-generic
abi-3.11.0-18-generic                  initrd.img-3.13.0-33-generic
abi-3.11.0-19-generic                  initrd.img-3.13.0-34-generic
abi-3.11.0-20-generic                  initrd.img-3.13.0-35-generic
abi-3.13.0-24-generic                  initrd.img-3.2.0-53-generic-pae
abi-3.13.0-26-generic                  initrd.img-3.5.0-40-generic
abi-3.13.0-27-generic                  initrd.img-3.8.0-32-generic
abi-3.13.0-29-generic                  memtest86+.bin
abi-3.13.0-30-generic                  memtest86+.elf
abi-3.13.0-31-generic                  memtest86+_multiboot.bin
abi-3.13.0-32-generic                  System.map-3.11.0-13-generic
abi-3.13.0-33-generic                  System.map-3.11.0-14-generic
abi-3.13.0-34-generic                  System.map-3.11.0-15-generic
abi-3.13.0-35-generic                  System.map-3.11.0-17-generic
abi-3.2.0-53-generic-pae               System.map-3.11.0-18-generic
abi-3.5.0-40-generic                   System.map-3.11.0-19-generic
abi-3.8.0-32-generic                   System.map-3.11.0-20-generic
config-3.11.0-13-generic               System.map-3.13.0-24-generic
config-3.11.0-14-generic               System.map-3.13.0-26-generic
config-3.11.0-15-generic               System.map-3.13.0-27-generic
config-3.11.0-17-generic               System.map-3.13.0-29-generic
config-3.11.0-18-generic               System.map-3.13.0-30-generic
config-3.11.0-19-generic               System.map-3.13.0-31-generic
config-3.11.0-20-generic               System.map-3.13.0-32-generic
config-3.13.0-24-generic               System.map-3.13.0-33-generic
config-3.13.0-26-generic               System.map-3.13.0-34-generic
config-3.13.0-27-generic               System.map-3.13.0-35-generic
config-3.13.0-29-generic               System.map-3.2.0-53-generic-pae
config-3.13.0-30-generic               System.map-3.5.0-40-generic
config-3.13.0-31-generic               System.map-3.8.0-32-generic
config-3.13.0-32-generic               vmlinuz-3.11.0-13-generic
config-3.13.0-33-generic               vmlinuz-3.11.0-14-generic
config-3.13.0-34-generic               vmlinuz-3.11.0-15-generic
config-3.13.0-35-generic               vmlinuz-3.11.0-17-generic
config-3.2.0-53-generic-pae            vmlinuz-3.11.0-18-generic
config-3.5.0-40-generic                vmlinuz-3.11.0-19-generic
config-3.8.0-32-generic                vmlinuz-3.11.0-20-generic
grub                                   vmlinuz-3.13.0-24-generic
initrd.img-3.11.0-13-generic           vmlinuz-3.13.0-26-generic
initrd.img-3.11.0-14-generic           vmlinuz-3.13.0-27-generic
initrd.img-3.11.0-15-generic           vmlinuz-3.13.0-29-generic
initrd.img-3.11.0-17-generic           vmlinuz-3.13.0-30-generic
initrd.img-3.11.0-18-generic           vmlinuz-3.13.0-31-generic
initrd.img-3.11.0-19-generic           vmlinuz-3.13.0-32-generic
initrd.img-3.11.0-19-generic.old-dkms  vmlinuz-3.13.0-33-generic
initrd.img-3.11.0-20-generic           vmlinuz-3.13.0-34-generic
initrd.img-3.13.0-24-generic           vmlinuz-3.13.0-35-generic
initrd.img-3.13.0-24-generic.old-dkms  vmlinuz-3.2.0-53-generic-pae
initrd.img-3.13.0-26-generic           vmlinuz-3.5.0-40-generic
initrd.img-3.13.0-27-generic           vmlinuz-3.8.0-32-generic

```

```

ubuntu@ubuntu:~$ ls -la /mnt/work/home
total 20
drwxr-xr-x  3 root root  4096 May  8  2012 .
drwxr-xr-x 23 root root  4096 Sep 11 20:16 ..
drwxr-xr-x 74 1000 1000 12288 Sep 17 07:28 nordic

```

---

### Post by Bashing-om on 2014-09-29
lcbmac; Yepper,

> 
I think this is what you wanted to see in order to know what is going on.
I hope it helps. 

That tells the tale .
There are way too many old kernels and in addition is this the biggy:
> 
drwxr-xr-x 74 1000 1000 12288 Sep 17 07:28 nordic


I find it much easier to copy off individual files from the file manager in the liveDVD's file manager. In the left hand pane I expect there to be a icon for "sda1" or some such. Open 2 instances of the file manager window and just drag and drop files.

To the situation at hand to fix the booting/desktop:
Will be much easier to work in the install.
Let's see if we can boot the install:
Reboot and as soon as the bios screen clears, depress and hold the right -shift- key -> grub boot menu, with the latest kernel highlighted press the 'e' key for edit mode -> boot options screen.
Arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes.
Key combo ctl+x to continue the boot process to a textual terminal (TTY1).

Can you log in here with your username followed by the requested password ? - there will be no response to the screen here, security reasons .

IF you can log in here at TTY1 we can easily fix things.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-29
Hi Bashing-om

I could not copy over all the stuff and 80% of it is what I needed to trancefere to my external drive.
If I delete the stuff i dont need will that help in sorting out the next level of what is needed in the next step with out loosing the other stuff.

Yes this is my biggy

```

drwxr-xr-x 74 1000 1000 12288 Sep 17 07:28 nordic

```

---

### Post by Bashing-om on 2014-09-29
lcbmac; Huh ?
> **lcbmac said:**
> Hi Bashing-om

I could not copy over all the stuff and 80% of it is what I needed to trancefere to my external drive.
If I delete the stuff i dont need will that help in sorting out the next level of what is needed in the next step with out loosing the other stuff.

I have no point of reference to base any advise on ! .. How about exercising your communications skills ( mine reek bad too) and try with complete sentences, with proper punctuation. Run-on, run-together thoughts do not convey good information.

"I could not copy over all the stuff" -> what stuff & where on the source ?
"80% of it is what I needed to trancefere to my external drive." Where and what is the source, do you mean that the destination drive can not hold all the files from the "source" ?

"If I delete the stuff i dont need" That depends on what method you are using to copy the source.// deleting stuff I don't need -> always a good thing to do !

"will that help in sorting out the next level of what is needed in the next step with out loosing the other stuff." -> Your personal data has nothing to do with the system data or what we are going to do.
------------------------------------
There are about as many ways to copy data as there are people copying data. For a new user/inexperienced, the GUI file manager from the liveDVD is an excellent choice. As you gain knowledge and experience these will dictate what tools "YOU" prefer to use. If you want to take your time, and know what is being copied, there is nothing better then a a simple 'cp -p' terminal command.
 Study:
Terminal command:
```

man cp

``` Because reading is good.
-----------------------
As of now I am awaiting to know if you can log into the system on TTY1. IF you can. Then we look at your authorization to access the GUI, and see about getting rid of old kernels, and then a final clean up of system files.

[INDENT][INDENT]it is all a process of learning
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-29
Hi Bashing-om

Sorry about that. Okay so what I have a problem with is trying to copy the file off the Laptops HDD and transfer /copy it to my External Drive as it keeps say in need permission to copy/read it. 80% of the files I'm trying to copy are the ones I actually need. The rest of which I don't have a problem losing.

It turns out I can't delete the file as I don't have permission for that either. 


Alright So I have tried what you have asked me to do -

[COLOR=#000000]To the situation at hand to fix the booting/desktop:[/COLOR]
[COLOR=#000000]Will be much easier to work in the install.[/COLOR]
[COLOR=#000000]Let's see if we can boot the install:[/COLOR]
[COLOR=#000000]Reboot and as soon as the bios screen clears, depress and hold the right -shift- key -> grub boot menu, with the latest kernel highlighted press the 'e' key for edit mode -> boot options screen.[/COLOR]
[COLOR=#000000]Arrow down and across to the terms "quiet splash" and replace them with the term "text" - without the quotes.[/COLOR]
[COLOR=#000000]Key combo ctl+x to continue the boot process to a textual terminal (TTY1).[/COLOR]

[COLOR=#000000]Can you log in here with your username followed by the requested password ? - there will be no response to the screen here, security reasons .

[/COLOR]Once the editing has been done and I have Pressed ctrl+x it boots up. Once it starts up with the booting it stops half way.

There are a few files that say In similar sentence:
[13.288375] EXT4-fs error (device sda1): ext4_lookup:1437: inode #2: comm init: delete inode referenced: 3670017

The first number does change. If it helps and i hope they do. They are:

13.283051
13.283996
15.400432
15.400999
15.402187
15.402712
15.403247
15.403743
307.164097
307.164196
307.164360

---

### Post by Bashing-om on 2014-09-29
lcbmac; Understandable, and not yet to sweat over.


1) Access permissions: this:
> 
drwxr-xr-x 74 [color=red]1000 1000[/color] 12288 Sep 17 07:28 nordic

says "you" do not have authorization.
compare:
```

drwxr-xr-x 28 [color=green]sysop sysop[/color]  4096 Sep 29 17:43 sysop

```
Where 'sysop' is my username.
We can work around this, and we will fix it !
IF you start the file manager up with elevated authority, you can copy those files off.
Now I am not sure - as gksudo is being depreciated - how to start up the file manager as we need to, but we will find out how !
for now try:
```

gksudo nautilus

``` If it fails with an error that "such and such" is not installed; we will need to install it;  post back here with what that such and such is if you need advise on how to proceed.

2)EXT4-fs error (device sda1) // UnGood [fs error = File System error ] and has become our priority, why we can not boot to terminal - see, posting errors in context is a GOOD thing !- Presently I am considering what is the better approach to taking care of this ... Can we repair the file system with no operating head room in boot ? do not think so !
can we remove files to get some head room, if we do that, will the file system check function ? Let's do this to get an idea of what to do:
Boot the liveDVD to terminal 
post back the outputs:
```

df -h
df -i

```
and we consider greatly removing kernels via a full Change Root environment ! .. 

[INDENT][INDENT][INDENT]when it is broke
[INDENT][INDENT][INDENT][INDENT]we fix
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-30
HI Bashing-om

Sorry I have to ask but when you sent the last post what time was it. just out of curiosity.

okay so it said to:

```

ubuntu@ubuntu:~$ gksudo nautilus
The program 'gksudo' is currently not installed. You can install it by typing:
sudo apt-get install gksu
You will have to enable the component called 'universe'

```

which I have done but It says now:

```

ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gksu

```

This is the reply I get on terminal. 


As for the secon part of what you asked for:

```

ubuntu@ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/cow           1004M  121M  884M  12% /
udev            994M  4.0K  994M   1% /dev
tmpfs           201M  1.2M  200M   1% /run
/dev/sr0        987M  987M     0 100% /cdrom
/dev/loop0      952M  952M     0 100% /rofs
none            4.0K     0  4.0K   0% /sys/fs/cgroup
tmpfs          1004M   60K 1004M   1% /tmp
none            5.0M     0  5.0M   0% /run/lock
none           1004M  148K 1004M   1% /run/shm
none            100M   80K  100M   1% /run/user
/dev/sdb1       3.8G  1.9M  3.8G   1% /media/ubuntu/UNTITLED
/dev/sda1       145G   60M  138G   1% /mnt/work

```

```

ubuntu@ubuntu:~$ df -i
Filesystem      Inodes  IUsed   IFree IUse% Mounted on
/cow            220160   1549  218611    1% /
udev            214984    494  214490    1% /dev
tmpfs           220160    522  219638    1% /run
/dev/sr0             0      0       0     - /cdrom
/dev/loop0      184259 184259       0  100% /rofs
none            220160      2  220158    1% /sys/fs/cgroup
tmpfs           220160     17  220143    1% /tmp
none            220160      1  220159    1% /run/lock
none            220160      6  220154    1% /run/shm
none            220160     36  220124    1% /run/user
/dev/sdb1            0      0       0     - /media/ubuntu/UNTITLED
/dev/sda1      9641984     11 9641973    1% /mnt/work

```

You have me really curious.
Can I ask you what Is a good Bood to download of buy for learning all of this codeing.
I did get _**Byte of Python**_ but it is one of the files I cant get into or copy across and it is very interesting. love the read of it though. At untill my Laptop did this.

---

### Post by Bashing-om on 2014-09-30
lcbmac; Good day ?

As to the time difference; I am at GMT minus 5 hours. Presently it is 01:27 PM my time and it is 18:27 GMT ( also known as UTC).

gksudo: Did you note:
> 
You will have to enable the component called 'universe'

Open 'Software Sources' and make sure that component is enabled . Then try again.

Learning resources; There are many, 3 means the I recommend:
[http://ubuntuguide.org/wiki/Ubuntu_Trusty](http://ubuntuguide.org/wiki/Ubuntu_Trusty)
[http://ubuntu-manual.org/downloads](http://ubuntu-manual.org/downloads)
[http://mywiki.wooledge.org/ProcessManagement](http://mywiki.wooledge.org/ProcessManagement)
In addition see the link for 'Popular Pages' in my sig. The tutorials are current, and the search engine is great.

-------------------
When you get caught up, we go back to work on fixing the file system and regaining access to the install.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]it is fixable
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-09-30
Hi Bashing-om

Alright so to answer you responce and what it has given me so far is.

```

ubuntu@ubuntu:~$ sudo apt-get install gksu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libgksu2-0
The following NEW packages will be installed:
  gksu libgksu2-0
0 upgraded, 2 newly installed, 0 to remove and 175 not upgraded.
Need to get 98.9 kB of archives.
After this operation, 728 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty/universe libgksu2-0 i386 2.0.13~pre1-6ubuntu4 [71.4 kB]
Get:2 http://archive.ubuntu.com/ubuntu/ trusty/universe gksu i386 2.0.2-6ubuntu2 [27.5 kB]
Fetched 98.9 kB in 2s (36.0 kB/s)
Selecting previously unselected package libgksu2-0.
(Reading database ... 174317 files and directories currently installed.)
Preparing to unpack .../libgksu2-0_2.0.13~pre1-6ubuntu4_i386.deb ...
Unpacking libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
Selecting previously unselected package gksu.
Preparing to unpack .../gksu_2.0.2-6ubuntu2_i386.deb ...
Unpacking gksu (2.0.2-6ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1) ...
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support (3.54ubuntu1) ...
Setting up libgksu2-0 (2.0.13~pre1-6ubuntu4) ...
update-alternatives: using /usr/share/libgksu/debian/gconf-defaults.libgksu-sudo to provide /usr/share/gconf/defaults/10_libgksu (libgksu-gconf-defaults) in auto mode
Processing triggers for gconf2 (3.2.6-0ubuntu2) ...
Setting up gksu (2.0.2-6ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6) ...

```

Right the next part is as follows:-

```

 gksudo nautilus
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

evince-thumbnailer couldn't process file: 'file:///mnt/work/home/nordic/Confordents%20.pdf'
Reason: Took too much time to process.

(nautilus:8419): GnomeDesktop-WARNING **: Unable to create loader for mime type application/pdf: Unrecognized image file format

(nautilus:8419): GnomeDesktop-WARNING **: Error creating thumbnail for file:///mnt/work/home/nordic/Confordents%20.pdf: Unrecognized image file format
**
ERROR:nautilus-properties-window.c:1839:schedule_owner_change_timeout: assertion failed: (NAUTILUS_IS_FILE (file))

```

I hope this is correctly done but I need to find out some of the things and it took a while.

Thank you for the Web address I will use them to carry out more learning.

---

### Post by Bashing-om on 2014-10-01
lcbmac; Morning ;

Hey, that looks to me like you are working from the installed operating system's terminal - great -; I had thought we were working from the liveDVD.

How samba plays into this, you will have to tell us what you have done !
> 
returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


Are you indeed working from the installed Operating system ?

None the less, where you are working from, still, just a matter of opening nautilus, pointing to the source directory, open another window in that same instance and point it to the target -> copy and paste files between the 2 open windows.

[INDENT][INDENT]sometimes I wonder
[INDENT][INDENT][INDENT]other times I do not know
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-01
Evening Bashing-om

No I'm working off the LiveCD Not the the system but I still have not unmounted the other system.
I think that is why it seems like it.

---

### Post by Bashing-om on 2014-10-01
lcbmac; Humm,

I would not think having the partition mounted prior would be a problem; but, we can (un-)mount it and see if then we can start nautilus (gksudo).
unmount:
```

sudo umount /mnt/work

```

make sure 'nautilus' is not currently running:
```

ps -e | grep nautilus

```and if so close it out and restart it to clear the memory.

Now in easy stages, what results with nautilus restarted:
```

gksudo nautilus

```
when you select 'sda1' - the operating system partition - from the left pane ?

If that opens with no problems. -> new window and select the USB drive in that left pane. ( maybe now open a particular folder ) .
Drag and drop files from the 1st window into that 2nd window. 

[INDENT][INDENT]should workie great
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-01
Ho Bashing-om

okay so here is it hope it helps

```

ubuntu@ubuntu:~$ sudo umount /mnt/work

```

Before with the nautilus:

```

ubuntu@ubuntu:~$ ps e | grep nautilus
 9513 pts/10   D+     0:00 grep --color=auto nautilus XDG_VTNR=7 SSH_AGENT_PID=2192 XDG_SESSION_ID=c7 CLUTTER_IM_MODULE=xim SELINUX_INIT=YES XDG_GREETER_DATA_DIR=/var/lib/lightdm-data/ubuntu GPG_AGENT_INFO=/run/user/999/keyring-Muoien/gpg:0:1 TERM=xterm SHELL=/bin/bash VTE_VERSION=3409 SSH_AGENT_LAUNCHER=upstart WINDOWID=54535922 UPSTART_SESSION=unix:abstract=/com/ubuntu/upstart-session/999/2119 GNOME_KEYRING_CONTROL=/run/user/999/keyring-Muoien GTK_MODULES=overlay-scrollbar:unity-gtk-module USER=ubuntu LS_COLORS=rs=0:di=01;34:ln=01;36:mh=00:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:ca=30;41:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.tlz=01;31:*.txz=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.lz=01;31:*.xz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.war=01;31:*.ear=01;31:*.sar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.svgz=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.webm=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.flv=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.cgm=01;35:*.emf=01;35:*.axv=01;35:*.anx=01;35:*.ogv=01;35:*.ogx=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:*.axa=00;36:*.oga=00;36:*.spx=00;36:*.xspf=00;36: XDG_SESSION_PATH=/org/freedesktop/DisplayManager/Session0 XDG_SEAT_PATH=/org/freedesktop/DisplayManager/Seat0 SSH_AUTH_SOCK=/run/user/999/keyring-Muoien/ssh DEFAULTS_PATH=/usr/share/gconf/ubuntu.default.path XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/usr/share/upstart/xdg:/etc/xdg PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games DESKTOP_SESSION=ubuntu QT_IM_MODULE=ibus QT_QPA_PLATFORMTHEME=appmenu-qt5 JOB=gnome-session PWD=/home/ubuntu XMODIFIERS=@im=ibus LANG=en_US.UTF-8 MANDATORY_PATH=/usr/share/gconf/ubuntu.mandatory.path UBUNTU_MENUPROXY=1 IM_CONFIG_PHASE=1 COMPIZ_CONFIG_PROFILE=ubuntu GDMSESSION=ubuntu SESSIONTYPE=gnome-session SHLVL=1 XDG_SEAT=seat0 HOME=/home/ubuntu GNOME_DESKTOP_SESSION_ID=this-is-deprecated UPSTART_INSTANCE= UPSTART_EVENTS=started starting LOGNAME=ubuntu QT4_IM_MODULE=xim XDG_DATA_DIRS=/usr/share/ubuntu:/usr/share/gnome:/usr/local/share/:/usr/share/ DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-45UNv2W0Sc LESSOPEN=| /usr/bin/lesspipe %s INSTANCE=Unity UPSTART_JOB=unity-settings-daemon TEXTDOMAIN=im-config XDG_RUNTIME_DIR=/run/user/999 DISPLAY=:0 XDG_CURRENT_DESKTOP=Unity GTK_IM_MODULE=ibus LESSCLOSE=/usr/bin/lesspipe %s %s TEXTDOMAINDIR=/usr/share/locale/ COLORTERM=gnome-terminal XAUTHORITY=/home/ubuntu/.Xauthority _=/bin/grep

```

After with the nautilus once restarted terminal

```

ubuntu@ubuntu:~$ ps -e | grep nautilus
 3287 ?        00:00:52 nautilus

```

okay so typing in the code was this.
```

ubuntu@ubuntu:~$ gksudo nautilus

(nautilus:9561): GLib-GIO-WARNING **: Missing callback called fullpath = /root/.config/user-dirs.dirs


(nautilus:9561): GLib-CRITICAL **: Source ID 171 was not found when attempting to remove it

(nautilus:9561): GLib-CRITICAL **: Source ID 172 was not found when attempting to remove it

(nautilus:9561): GLib-CRITICAL **: Source ID 173 was not found when attempting to remove it

```

There was and error saying it cant find the mount and the files manager popped up. No sda1

Then I redid it with my usb in and no error occurred but the file manager still popped up. I moved a file from one to another and no issue. but the terninal is still hanging on the coded line.

did i do something wrong??

---

### Post by Bashing-om on 2014-10-01
lcbmac; Nope

Ya doing nothing wrong,, and as to the terminal "hanging" .. that is normal as in this invocation 'nautilus' has the full focus of the terminal.
NOW, if you want a terminal operative with nautilus running there are, to my knowledge, 2 things that one can do.
1) start 'nautilus' as a background process:
```

gksudo nautilus &

```
Where the "&" does that for us, puts that terminal process as a background process, and one can continue to use the terminal.

2) start another instance of a terminal ( ctl+alt+t ).

For the errors/warnings that are generated when 'nautilus' is started, beats me. If they do not interfere with the operation of coping files, let's not worry over it. Copy the files and get on with restoring this install.

[INDENT][INDENT]patience, Bashing-om, is a virtue
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-02
Hi Bashing-om

There is only so much I can get off my Laptop. However there are 1 or 2 files I need first then. The rest or irrelevant as I have run out of space with my other 2 drives. At the same time. Now my Laptop won't let me after transferring a hell of a lot of information Transfer any more.
Instead it hung and then shut down and now this is what comes up when i try to start again:

```
ubuntu@ubuntu:~$ gksudo nautilus
Could not register the application: Timeout was reached

```

Is it okay or can we go further with out any more problems.

Oh yes and I hae deleted a few more GB to free up space after the transfers

---

### Post by Bashing-om on 2014-10-02
lcbmac; Humm ??

I am glad to say I have no idea as to " Could not register the application: Timeout was reached" . I have never seen that advisory !
Maybe, reboot the liveDVD and if the problem persist then I would - from the boot menu -> "check disk for defects", then maybe consider burning a new copy from a NEW .iso ( check with md5sum, always ). 

Now this:
> 
Oh yes and I hae deleted a few more GB to free up space after the transfers

is cause to make me pause. What have you deleted ? and how ?  System files MUST be managed by the package manager or will induce additional problems. I do hope these are all "personal" files you have deleted.

[INDENT][INDENT]we do, as we need to do
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-02
lcbmac; Humm ??

I am glad to say I have no idea as to " Could not register the application: Timeout was reached" . I have never seen that advisory !
Maybe, reboot the liveDVD and if the problem persist then I would - from the boot menu -> "check disk for defects", then maybe consider burning a new copy from a NEW .iso ( check with md5sum, always ). 

Now this:
> 
Oh yes and I hae deleted a few more GB to free up space after the transfers

is cause to make me pause. What have you deleted ? and how ?  System files MUST be managed by the package manager or will induce additional problems. I do hope these are all "personal" files you have deleted.

[INDENT][INDENT]we do, as we need to do
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-03
Hi Bashing-om

LOL yes it is only personal files. I have left anything that may be Ubuntu Or even might seem suspiciously like or could be and Ubuntu file.
as for the the liveDVD I shall do so.

---

### Post by lcbmac on 2014-10-03
Hi Bashing-om

Okay so I have tried the LiveDVD. Reset the Laptop used a new fresh cut LiveDVD and now I can't see HDD after that freezing incident.

Right so what do we do from here. and again it was only personal files that i deleted.

---

### Post by Bashing-om on 2014-10-03
lcbmac; Yukkie;

OK, let's presume that this is an aspect of the file system corrupted.
Try this to "fix" the file system:
Make sure we know what drive and partition we are working with:
```

sudo fdisk -lu

```
In that output is ONE line that has  a '*' in it. We want to mount that partition from the liveDVD.
And as well make sure "swap" is turned off - > from the liveDVD in the utility GParted, right click on the swap partition and "swap off".
- # = my comments, not to be entered into the terminal -
```

#change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p tries fixes where a response not required
##Run this code 1st##

sudo e2fsck -C0 -p -f -v /dev/sda1

#if errors: -y auto answers yes for fixes needing response see: man e2fsck
##also now run this code:##

sudo e2fsck -f -y -v /dev/sda1

```

Pay close attention to what the system tells you, and post those outputs back to the thread here on the forum for our inspection.
I still have some reservations about 'e2fsck' able to work, we may have to work on the /boot directory, maybe .

[INDENT][INDENT]all we can do is try
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-03
Hi Bashing.

Okay so this is what I have done and ther was something it told me to do inbetween  so I have posted it here to.
 

Okay well this is embarecing. I can only give you this much and I hoe it helps. This is what the Terminal said to do: something about reading it in short hand. sp I retyped the code as 

```

sudo e2fsck -C0 -f -v /dev/sda1

```

This is the result

```

Fix<y>? yes
Directories count wrong for group #673 (0, counted=373).
Fix<y>? yes
Free inodes count wrong for group #674 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #674 (0, counted=400).
Fix<y>? yes
Free inodes count wrong for group #675 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #675 (0, counted=412).
Fix<y>? yes
Free inodes count wrong for group #676 (8192, counted=3).
Fix<y>? yes
Directories count wrong for group #676 (0, counted=500).
Fix<y>? yes
Free inodes count wrong for group #677 (8192, counted=22).
Fix<y>? yes
Directories count wrong for group #677 (0, counted=601).
Fix<y>? yes
Free inodes count wrong for group #678 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #678 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #679 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #679 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #680 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #680 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #681 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #681 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #682 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #682 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #683 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #683 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #684 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #684 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #685 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #685 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #686 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #686 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #687 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #687 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #688 (8192, counted=35).
Fix<y>? yes
Directories count wrong for group #688 (0, counted=395).
Fix<y>? yes
Free inodes count wrong for group #689 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #689 (0, counted=406).
Fix<y>? yes
Free inodes count wrong for group #690 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #690 (0, counted=435).
Fix<y>? yes
Free inodes count wrong for group #691 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #691 (0, counted=454).
Fix<y>? yes
Free inodes count wrong for group #692 (8192, counted=3).
Fix<y>? yes
Directories count wrong for group #692 (0, counted=518).
Fix<y>? yes
Free inodes count wrong for group #693 (8192, counted=5474).
Fix<y>? yes
Directories count wrong for group #693 (0, counted=671).
Fix<y>? yes
Free inodes count wrong for group #694 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #694 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #695 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #695 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #696 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #696 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #697 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #697 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #698 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #698 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #699 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #699 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #700 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #700 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #701 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #701 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #702 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #702 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #703 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #703 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #704 (8192, counted=2).
Fix<y>? yes
Directories count wrong for group #704 (0, counted=179).
Fix<y>? yes
Free inodes count wrong for group #705 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #705 (0, counted=491).
Fix<y>? yes
Free inodes count wrong for group #706 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #706 (0, counted=519).
Fix<y>? yes
Free inodes count wrong for group #707 (8192, counted=2).
Fix<y>? yes
Directories count wrong for group #707 (0, counted=532).
Fix<y>? yes
Free inodes count wrong for group #708 (8192, counted=2985).
Fix<y>? yes
Directories count wrong for group #708 (0, counted=548).
Fix<y>? yes
Free inodes count wrong for group #709 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #709 (0, counted=566).
Fix<y>? yes
Free inodes count wrong for group #710 (8192, counted=6708).
Fix<y>? yes
Directories count wrong for group #710 (0, counted=566).
Fix<y>? yes
Free inodes count wrong for group #711 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #711 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #712 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #712 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #713 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #713 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #714 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #714 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #715 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #715 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #716 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #716 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #717 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #717 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #718 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #718 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #719 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #719 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #720 (8192, counted=23).
Fix<y>? yes
Directories count wrong for group #720 (0, counted=266).
Fix<y>? yes
Free inodes count wrong for group #721 (8192, counted=22).
Fix<y>? yes
Directories count wrong for group #721 (0, counted=47).
Fix<y>? yes
Free inodes count wrong for group #722 (8192, counted=0).
Fix<y>? yes
Free inodes count wrong for group #723 (8192, counted=75).
Fix<y>? yes
Directories count wrong for group #723 (0, counted=430).
Fix<y>? yes
Free inodes count wrong for group #724 (8192, counted=2820).
Fix<y>? yes
Directories count wrong for group #724 (0, counted=667).
Fix<y>? yes
Free inodes count wrong for group #725 (8192, counted=3698).
Fix<y>? yes
Directories count wrong for group #725 (0, counted=128).
Fix<y>? yes
Free inodes count wrong for group #726 (8192, counted=1522).
Fix<y>? yes
Directories count wrong for group #726 (0, counted=566).
Fix<y>? yes
Free inodes count wrong for group #727 (8192, counted=205).
Fix<y>? yes
Directories count wrong for group #727 (0, counted=579).
Fix<y>? yes
Free inodes count wrong for group #728 (8192, counted=6915).
Fix<y>? yes
Directories count wrong for group #728 (0, counted=599).
Fix<y>? yes
Free inodes count wrong for group #729 (8192, counted=7438).
Fix<y>? yes
Directories count wrong for group #729 (0, counted=754).
Fix<y>? yes
Free inodes count wrong for group #730 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #730 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #731 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #731 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #732 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #732 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #733 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #733 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #734 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #734 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #735 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #735 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #736 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #736 (0, counted=136).
Fix<y>? yes
Free inodes count wrong for group #737 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #737 (0, counted=111).
Fix<y>? yes
Free inodes count wrong for group #738 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #738 (0, counted=134).
Fix<y>? yes
Free inodes count wrong for group #739 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #739 (0, counted=118).
Fix<y>? yes
Free inodes count wrong for group #740 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #740 (0, counted=65).
Fix<y>? yes
Free inodes count wrong for group #741 (8192, counted=3030).
Fix<y>? yes
Free inodes count wrong for group #742 (8192, counted=5436).
Fix<y>? yes
Free inodes count wrong for group #743 (8192, counted=5196).
Fix<y>? yes
Directories count wrong for group #743 (0, counted=5).
Fix<y>? yes
Free inodes count wrong for group #744 (8192, counted=3796).
Fix<y>? yes
Directories count wrong for group #744 (0, counted=601).
Fix<y>? yes
Free inodes count wrong for group #745 (8192, counted=5347).
Fix<y>? yes
Directories count wrong for group #745 (0, counted=601).
Fix<y>? yes
Free inodes count wrong for group #746 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #746 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #747 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #747 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #748 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #748 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #749 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #749 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #750 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #750 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #751 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #751 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #752 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #752 (0, counted=710).
Fix<y>? yes
Free inodes count wrong for group #753 (8192, counted=0).
Fix<y>? yes
Free inodes count wrong for group #754 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #754 (0, counted=671).
Fix<y>? yes
Free inodes count wrong for group #755 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #755 (0, counted=686).
Fix<y>? yes
Free inodes count wrong for group #756 (8192, counted=0).
Fix<y>? yes
Directories count wrong for group #756 (0, counted=739).
Fix<y>? yes
Free inodes count wrong for group #757 (8192, counted=7287).
Fix<y>? yes
Directories count wrong for group #757 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #758 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #758 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #759 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #759 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #760 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #760 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #761 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #761 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #762 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #762 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #763 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #763 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #764 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #764 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #765 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #765 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #766 (8192, counted=7439).
Fix<y>? yes
Directories count wrong for group #766 (0, counted=753).
Fix<y>? yes
Free inodes count wrong for group #767 (8192, counted=7971).
Fix<y>? yes
Directories count wrong for group #767 (0, counted=221).
Fix<y>? yes
Free inodes count wrong for group #768 (8192, counted=52).
Fix<y>? yes
Directories count wrong for group #768 (0, counted=383).
Fix<y>? yes
Free inodes count wrong for group #769 (8192, counted=1291).
Fix<y>? yes
Directories count wrong for group #769 (0, counted=90).
Fix<y>? yes
Free inodes count wrong for group #770 (8192, counted=7268).
Fix<y>? yes
Directories count wrong for group #770 (0, counted=1).
Fix<y>? yes
Free inodes count wrong for group #771 (8192, counted=8189).
Fix<y>? yes
Directories count wrong for group #771 (0, counted=3).
Fix<y>? yes
Free inodes count wrong for group #784 (8192, counted=5365).
Fix<y>? yes
Directories count wrong for group #784 (0, counted=265).
Fix<y>? yes
Free inodes count wrong for group #785 (8192, counted=8190).
Fix<y>? yes
Directories count wrong for group #785 (0, counted=2).
Fix<y>? yes
Free inodes count wrong for group #786 (8192, counted=8173).
Fix<y>? yes
Directories count wrong for group #786 (0, counted=19).
Fix<y>? yes
Free inodes count wrong for group #800 (8192, counted=6941).
Fix<y>? yes
Directories count wrong for group #800 (0, counted=117).
Fix<y>? yes
Free inodes count wrong for group #801 (8192, counted=8155).
Fix<y>? yes
Directories count wrong for group #801 (0, counted=17).
Fix<y>? yes
Free inodes count wrong for group #802 (8192, counted=8185).
Fix<y>? yes
Directories count wrong for group #802 (0, counted=7).
Fix<y>? yes
Free inodes count wrong for group #816 (8192, counted=7134).
Fix<y>? yes
Directories count wrong for group #816 (0, counted=94).
Fix<y>? yes
Free inodes count wrong for group #817 (8192, counted=8182).
Fix<y>? yes
Directories count wrong for group #817 (0, counted=10).
Fix<y>? yes
Free inodes count wrong for group #832 (8192, counted=5208).
Fix<y>? yes
Directories count wrong for group #832 (0, counted=71).
Fix<y>? yes
Free inodes count wrong for group #833 (8192, counted=8177).
Fix<y>? yes
Directories count wrong for group #833 (0, counted=15).
Fix<y>? yes
Free inodes count wrong for group #848 (8192, counted=5296).
Fix<y>? yes
Directories count wrong for group #848 (0, counted=77).
Fix<y>? yes
Free inodes count wrong for group #849 (8192, counted=8191).
Fix<y>? yes
Directories count wrong for group #849 (0, counted=1).
Fix<y>? yes
Free inodes count wrong for group #864 (8192, counted=7527).
Fix<y>? yes
Directories count wrong for group #864 (0, counted=83).
Fix<y>? yes
Free inodes count wrong for group #865 (8192, counted=8182).
Fix<y>? yes
Directories count wrong for group #865 (0, counted=10).
Fix<y>? yes
Free inodes count wrong for group #880 (8192, counted=7981).
Fix<y>? yes
Directories count wrong for group #880 (0, counted=86).
Fix<y>? yes
Free inodes count wrong for group #896 (8192, counted=7142).
Fix<y>? yes
Directories count wrong for group #896 (0, counted=86).
Fix<y>? yes
Free inodes count wrong for group #898 (8192, counted=8191).
Fix<y>? yes
Directories count wrong for group #898 (0, counted=1).
Fix<y>? yes
Free inodes count wrong for group #912 (8192, counted=8010).
Fix<y>? yes
Directories count wrong for group #912 (0, counted=86).
Fix<y>? yes
Free inodes count wrong for group #928 (8192, counted=6749).
Fix<y>? yes
Directories count wrong for group #928 (0, counted=266).
Fix<y>? yes
Free inodes count wrong for group #929 (8192, counted=8025).
Fix<y>? yes
Directories count wrong for group #929 (0, counted=167).
Fix<y>? yes
Free inodes count wrong for group #960 (8192, counted=7802).
Fix<y>? yes
Directories count wrong for group #960 (0, counted=3).
Fix<y>? yes
Free inodes count wrong for group #961 (8192, counted=8190).
Fix<y>? yes
Directories count wrong for group #961 (0, counted=2).
Fix<y>? yes
Free inodes count wrong for group #992 (8192, counted=8157).
Fix<y>? yes
Directories count wrong for group #992 (0, counted=11).
Fix<y>? yes
Free inodes count wrong for group #993 (8192, counted=8185).
Fix<y>? yes
Directories count wrong for group #993 (0, counted=7).
Fix<y>? yes
Free inodes count wrong for group #1024 (8192, counted=8191).
Fix<y>? yes
Directories count wrong for group #1024 (0, counted=1).
Fix<y>? yes
Free inodes count wrong (9647491, counted=8778081).
Fix<y>? yes
y
/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

      863903 inodes used (8.96%, out of 9641984)
        2030 non-contiguous files (0.2%)
        1297 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 5/4/5
             Extent depth histogram: 791830/1028/9
    25978275 blocks used (67.39%, out of 38550528)
           0 bad blocks
           2 large files

      646103 regular files
      123085 directories
          58 character device files
          26 block device files
           6 fifos
  4294967119 links
       94606 symbolic links (70927 fast symbolic links)
          14 sockets
------------
      863194 files

```


```

ubuntu@ubuntu:~$ sudo e2fsck -f -y -v /dev/sda1
e2fsck 1.42.9 (4-Feb-2014)
Pass 1: Checking inodes, blocks, and sizes
Pass 2: Checking directory structure
Pass 3: Checking directory connectivity
Pass 4: Checking reference counts
Pass 5: Checking group summary information
Error reading block 27787269 (Attempt to read block from filesystem resulted in short read) while reading inode and block bitmaps.  Ignore error? yes

Force rewrite? yes

Block bitmap differences:  +(27951104--27957372) +(27957397--27957637) +(27957760--27958014) +(27958016--27958131) +(27958144--27958244) +(27958247--27958512) +(27958528--27958647) +(27958656--27958776) +(27959296--27983871)
Fix? yes


/dev/sda1: ***** FILE SYSTEM WAS MODIFIED *****

      863903 inodes used (8.96%, out of 9641984)
        2031 non-contiguous files (0.2%)
        1298 non-contiguous directories (0.2%)
             # of inodes with ind/dind/tind blocks: 4/3/4
             Extent depth histogram: 791826/1028/9
    25978275 blocks used (67.39%, out of 38550528)
           0 bad blocks
           2 large files

      646099 regular files
      123085 directories
          58 character device files
          26 block device files
           6 fifos
         219 links
       94606 symbolic links (70927 fast symbolic links)
          14 sockets
------------
      864113 files

```


I hope that helps

---

### Post by Bashing-om on 2014-10-03
lcbmac; Hey;

Looks promising !

Have you rebooted into the install and see what condition the condition is in ?

IF you can now boot to the desk top, all we need to do now is get shed of those old kernels and insure the system has the operating overhead.

[INDENT][INDENT]maybe yes ?
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-04
Hi Bashing-om

Alright do I tried to reboot and see where is goes but It goes as far as it did be for Except noe the filles missing does not come up.
The only Install is the the one where you told me to do with the right shift key. That is how I am talking to you now.

---

### Post by Bashing-om on 2014-10-04
lcbmac; Huh ?

Can not tell where you are in the operating system.

You booted to grub, yes ?
'e' key and edit the boot parameter line "text" are now @ the TTY1 terminal ? -> and the GUI does not start ?

Else are you now in "recovery mode ) ??

(are we now back to removing old kernels from the /boot directory ?)

---

### Post by lcbmac on 2014-10-04
I get to the Grub menu go into the advanced Ubuntu menu which is the one with all the kernels. Half being recovery mode and halfbeing  without the recovery mode.
Go to the 1st recovery mode on the list and press enter. It starts the recovery mode and it reads a list and stops 3/4 of the way through.

Thats it. Thats where I am I had not done the edit yet so I shall start is now and try that out.

---

### Post by Bashing-om on 2014-10-04
lcbmac; OK;

Understand now .. Appreciate the clarification.

OK, to effect any change in the operating system ( change the driver) requires the the file system be mounted "read/write".
In recovery mode - that does not activate for you - one would have to mount the file system "read/write" from 'root's' terminal.

My preferred method to get a terminal interface is through the grub menu ( edit boot parameters -> text). Once you have a terminal then you may execute the terminal commands to change the graphics driver.

Let us know how it is going, how else we can assist to get you there.

[INDENT][INDENT]but, there is more than one path
[INDENT][INDENT][INDENT]to an end
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-05
Hi Bashing-om

Okay so I have done the change but I need to just run it by you because It has stopped in the same place both ways I have done it as I was not sure doing it if i did it right

The both ways I did it started the same way. Start the Laptop and let it run to the GNU GRUB Menu.
alright then I went to the Advanced Ubuntu Menu and  pressed "e" to key the edit in on the command menu.

Alright so this is where I did the 2 different ways.
1st. one. On the command line I changed the "quiet splash" to "text" then crl+x and let it boot. Stopping where the pic shows below.
2nd one. On the command line I changed the "ro  quiet splash" to "rw  text" then crl+x and let it boot. Stopping where the pic shows below.
[ATTACH=CONFIG]256954[/ATTACH]
I can only hope i have done it right. 
If you can please let me know I have done it right or if I Have to do it another way.

---

### Post by Bashing-om on 2014-10-05
lcbmac; Hey;

I guess it is I that is not making myself clear.
In this attempt to boot to terminal from grub, the kernel line you need to use is a Non-advanced NON-recovery kernel ( in this case of getting to a terminal).

Boot to grub. I expect that the latest top entry in the list has a 'asterisk' (*) to the left. With this entry so highlighted press the 'e' key for edit mode.
Next is the boot options screen, in this screen arrow down and across to the terms "quiet splash" and insert the term "text" - with out the quotes.
Now press key combo ctl+x .

Do you now boot to the terminal (TTY1) 
OR are you still hanging up in the boot process ?

And yes ! A picture is worth a thousand words.

[INDENT][INDENT][INDENT]try and try again
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-05
Hi Bashing-om

Okay Yes I have done that as You have instructed and exactly the same thing as shown before in that pic. :-)

---

### Post by Bashing-om on 2014-10-05
lcbmac; Uhh,

I am about out of ideas .

But, what results when you boot the liveDVD to the boot options screen and select the option " boot from first hard disk " ?

I need to get a handle on what the command 'df -h' relates to us, and get 'ubiquity' straight, and as well look at /boot.
All this means we need to access the system from some terminal means, somehow, some way.

[INDENT][INDENT]'til we can look and see and know
[INDENT][INDENT][INDENT][INDENT]there is not a thing we can do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-05
Hi Bashing -om

Alright once I select the option [COLOR=#000000]" boot from first hard disk "[/COLOR]
It goes into the Grub menu again if I alter it with quiet splash with 'text' it only does a half boots. If I dont change the anything it just goes to a blank screen with a flashing underline on the top left

---

### Post by Bashing-om on 2014-10-05
lcbmac; UnGood !

I have but one last suggestion to allow access to the operating system:
From the liveDVD, let's TRY a full CHange Root ! -> looking for some way to access a terminal !
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo chroot /mnt/ /bin/bash

```

For now I am only interested in IF you can access the install through this means.

Now back out and close things out gracefully ! .. Got enough problems with out the added problems of a "dirty" un-mount !
```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Now you are back in the liveDVD terminal (environment).

Seeing what results ->
[INDENT][INDENT][INDENT]opinions reserved
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-05
HI Bashing-om

Alright is it doing something but not quite sure just yet.  it is saying somehting like 
```

bash-4.3#

```
There is something blinking after that but not sure and the cd starts and stops and now just not doing any thing.
Is that what you are looking for and how can one access the install via this way.
For now I have left it till I am sure what to do.

---

### Post by Bashing-om on 2014-10-05
lcbmac; Hey !

Not too sure, but that might indeed be the CHroot prompt:
what presently returns:
```

ls -al /boot
ls -al /home

```
to see if in fact we are in the install from that liveDVD !

It could happen

---

### Post by lcbmac on 2014-10-05
Hi Bashing-om

okay this is what comes up
```

bash-4.3# ls -al /boot
total 565212
drwxr-xr-x  3 0 0    12288 Aug 27 07:54 .
drwxr-xr-x 22 0 0     4096 Oct  2 11:30 ..
-rw-r--r--  1 0 0  1010091 Oct 23  2013 abi-3.11.0-13-generic
-rw-r--r--  1 0 0  1010091 Nov 12  2013 abi-3.11.0-14-generic
-rw-r--r--  1 0 0  1010148 Jan 30  2014 abi-3.11.0-15-generic
-rw-r--r--  1 0 0  1010381 Feb  3  2014 abi-3.11.0-17-generic
-rw-r--r--  1 0 0  1011333 Feb 18  2014 abi-3.11.0-18-generic
-rw-r--r--  1 0 0  1011333 Mar 11  2014 abi-3.11.0-19-generic
-rw-r--r--  1 0 0  1011742 Apr  1  2014 abi-3.11.0-20-generic
-rw-r--r--  1 0 0  1162233 May  3 00:40 abi-3.13.0-24-generic
-rw-r--r--  1 0 0  1165930 May  8 00:38 abi-3.13.0-26-generic
-rw-r--r--  1 0 0  1165930 May 15 19:16 abi-3.13.0-27-generic
-rw-r--r--  1 0 0  1165981 Jun  4 21:49 abi-3.13.0-29-generic
-rw-r--r--  1 0 0  1166474 Jul  4 22:52 abi-3.13.0-30-generic
-rw-r--r--  1 0 0  1166929 Jul  1 16:41 abi-3.13.0-31-generic
-rw-r--r--  1 0 0  1166929 Jul 15 05:06 abi-3.13.0-32-generic
-rw-r--r--  1 0 0  1166929 Jul 29 17:34 abi-3.13.0-33-generic
-rw-r--r--  1 0 0  1166929 Aug 13 16:58 abi-3.13.0-34-generic
-rw-r--r--  1 0 0  1168075 Aug 15 03:09 abi-3.13.0-35-generic
-rw-r--r--  1 0 0   804726 Aug 22  2013 abi-3.2.0-53-generic-pae
-rw-r--r--  1 0 0   861648 Aug 22  2013 abi-3.5.0-40-generic
-rw-r--r--  1 0 0   926513 Oct  1  2013 abi-3.8.0-32-generic
-rw-r--r--  1 0 0   168537 Oct 23  2013 config-3.11.0-13-generic
-rw-r--r--  1 0 0   168537 Nov 12  2013 config-3.11.0-14-generic
-rw-r--r--  1 0 0   168527 Jan 30  2014 config-3.11.0-15-generic
-rw-r--r--  1 0 0   168512 Feb  3  2014 config-3.11.0-17-generic
-rw-r--r--  1 0 0   168540 Feb 18  2014 config-3.11.0-18-generic
-rw-r--r--  1 0 0   168540 Mar 11  2014 config-3.11.0-19-generic
-rw-r--r--  1 0 0   168540 Apr  1  2014 config-3.11.0-20-generic
-rw-r--r--  1 0 0   169631 May  3 00:40 config-3.13.0-24-generic
-rw-r--r--  1 0 0   169659 May  8 00:38 config-3.13.0-26-generic
-rw-r--r--  1 0 0   169642 May 15 19:16 config-3.13.0-27-generic
-rw-r--r--  1 0 0   169665 Jun  4 21:49 config-3.13.0-29-generic
-rw-r--r--  1 0 0   169697 Jul  4 22:52 config-3.13.0-30-generic
-rw-r--r--  1 0 0   169732 Jul  1 16:41 config-3.13.0-31-generic
-rw-r--r--  1 0 0   169732 Jul 15 05:06 config-3.13.0-32-generic
-rw-r--r--  1 0 0   169732 Jul 29 17:34 config-3.13.0-33-generic
-rw-r--r--  1 0 0   169732 Aug 13 16:58 config-3.13.0-34-generic
-rw-r--r--  1 0 0   169722 Aug 15 03:09 config-3.13.0-35-generic
-rw-r--r--  1 0 0   147576 Aug 22  2013 config-3.2.0-53-generic-pae
-rw-r--r--  1 0 0   154704 Aug 22  2013 config-3.5.0-40-generic
-rw-r--r--  1 0 0   160909 Oct  1  2013 config-3.8.0-32-generic
drwxr-xr-x  5 0 0    12288 Sep 14 11:39 grub
-rw-r--r--  1 0 0 16941485 Nov  4  2013 initrd.img-3.11.0-13-generic
-rw-r--r--  1 0 0 16941208 Nov 17  2013 initrd.img-3.11.0-14-generic
-rw-r--r--  1 0 0 17052155 Feb  1  2014 initrd.img-3.11.0-15-generic
-rw-r--r--  1 0 0 17055604 Feb 23  2014 initrd.img-3.11.0-17-generic
-rw-r--r--  1 0 0 17057132 Feb 25  2014 initrd.img-3.11.0-18-generic
-rw-r--r--  1 0 0 17054097 Mar 27  2014 initrd.img-3.11.0-19-generic
-rw-r--r--  1 0 0 17054097 Apr 25 22:13 initrd.img-3.11.0-19-generic.old-dkms
-rw-r--r--  1 0 0 17045668 Apr 18 15:43 initrd.img-3.11.0-20-generic
-rw-r--r--  1 0 0 18659449 May  8 13:16 initrd.img-3.13.0-24-generic
-rw-r--r--  1 0 0 18611271 May  6 15:14 initrd.img-3.13.0-24-generic.old-dkms
-rw-r--r--  1 0 0 18663265 May 11 23:56 initrd.img-3.13.0-26-generic
-rw-r--r--  1 0 0 18663763 May 20 12:24 initrd.img-3.13.0-27-generic
-rw-r--r--  1 0 0 18667315 Jun  7 15:23 initrd.img-3.13.0-29-generic
-rw-r--r--  1 0 0 18718621 Jul  6 07:40 initrd.img-3.13.0-30-generic
-rw-r--r--  1 0 0 18719337 Jul  7 09:18 initrd.img-3.13.0-31-generic
-rw-r--r--  1 0 0 18720405 Aug  6 10:23 initrd.img-3.13.0-32-generic
-rw-r--r--  1 0 0 18720244 Aug  9 10:06 initrd.img-3.13.0-33-generic
-rw-r--r--  1 0 0 18719947 Aug 14 17:25 initrd.img-3.13.0-34-generic
-rw-r--r--  1 0 0 18723539 Aug 27 07:54 initrd.img-3.13.0-35-generic
-rw-r--r--  1 0 0 14243572 Sep  7  2013 initrd.img-3.2.0-53-generic-pae
-rw-r--r--  1 0 0 15327160 Sep 21  2013 initrd.img-3.5.0-40-generic
-rw-r--r--  1 0 0 16227905 Oct 19  2013 initrd.img-3.8.0-32-generic
-rw-r--r--  1 0 0   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 0 0   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 0 0   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 0 0  2621288 Oct 23  2013 System.map-3.11.0-13-generic
-rw-------  1 0 0  2621446 Nov 12  2013 System.map-3.11.0-14-generic
-rw-------  1 0 0  2627916 Jan 30  2014 System.map-3.11.0-15-generic
-rw-------  1 0 0  2628001 Feb  3  2014 System.map-3.11.0-17-generic
-rw-------  1 0 0  2629740 Feb 18  2014 System.map-3.11.0-18-generic
-rw-------  1 0 0  2629933 Mar 11  2014 System.map-3.11.0-19-generic
-rw-------  1 0 0  2630177 Apr  1  2014 System.map-3.11.0-20-generic
-rw-------  1 0 0  2685850 May  3 00:40 System.map-3.13.0-24-generic
-rw-------  1 0 0  2689758 May  8 00:38 System.map-3.13.0-26-generic
-rw-------  1 0 0  2689758 May 15 19:16 System.map-3.13.0-27-generic
-rw-------  1 0 0  2690461 Jun  4 21:49 System.map-3.13.0-29-generic
-rw-------  1 0 0  2690773 Jul  4 22:52 System.map-3.13.0-30-generic
-rw-------  1 0 0  2693057 Jul  1 16:41 System.map-3.13.0-31-generic
-rw-------  1 0 0  2693057 Jul 15 05:06 System.map-3.13.0-32-generic
-rw-------  1 0 0  2693057 Jul 29 17:34 System.map-3.13.0-33-generic
-rw-------  1 0 0  2693057 Aug 13 16:58 System.map-3.13.0-34-generic
-rw-------  1 0 0  2697306 Aug 15 03:09 System.map-3.13.0-35-generic
-rw-------  1 0 0  2321335 Aug 22  2013 System.map-3.2.0-53-generic-pae
-rw-------  1 0 0  2323087 Aug 22  2013 System.map-3.5.0-40-generic
-rw-------  1 0 0  2445627 Oct  1  2013 System.map-3.8.0-32-generic
-rw-------  1 0 0  5633040 Oct 23  2013 vmlinuz-3.11.0-13-generic
-rw-------  1 0 0  5633232 Nov 12  2013 vmlinuz-3.11.0-14-generic
-rw-------  1 0 0  5663888 Jan 30  2014 vmlinuz-3.11.0-15-generic
-rw-------  1 0 0  5664656 Feb  3  2014 vmlinuz-3.11.0-17-generic
-rw-------  1 0 0  5667920 Feb 18  2014 vmlinuz-3.11.0-18-generic
-rw-------  1 0 0  5669328 Mar 11  2014 vmlinuz-3.11.0-19-generic
-rw-------  1 0 0  5667344 Apr  1  2014 vmlinuz-3.11.0-20-generic
-rw-------  1 0 0  5800496 May  3 00:40 vmlinuz-3.13.0-24-generic
-rw-------  1 0 0  5814832 May  8 00:38 vmlinuz-3.13.0-26-generic
-rw-------  1 0 0  5814832 May 15 19:16 vmlinuz-3.13.0-27-generic
-rw-------  1 0 0  5813456 Jun  4 21:49 vmlinuz-3.13.0-29-generic
-rw-------  1 0 0  5813328 Jul  4 22:52 vmlinuz-3.13.0-30-generic
-rw-------  1 0 0  5817968 Jul  1 16:41 vmlinuz-3.13.0-31-generic
-rw-------  1 0 0  5820336 Jul 15 05:06 vmlinuz-3.13.0-32-generic
-rw-------  1 0 0  5820336 Jul 29 17:34 vmlinuz-3.13.0-33-generic
-rw-------  1 0 0  5820592 Aug 13 16:58 vmlinuz-3.13.0-34-generic
-rw-------  1 0 0  5826864 Aug 15 03:09 vmlinuz-3.13.0-35-generic
-rw-------  1 0 0  5028480 Aug 22  2013 vmlinuz-3.2.0-53-generic-pae
-rw-------  1 0 0  5174640 Aug 22  2013 vmlinuz-3.5.0-40-generic
-rw-------  1 0 0  5375088 Oct  1  2013 vmlinuz-3.8.0-32-generic

```

and then this

```

bash-4.3# ls -al /home
total 20
drwxr-xr-x  3    0    0  4096 May  8  2012 .
drwxr-xr-x 22    0    0  4096 Oct  2 11:30 ..
drwxr-xr-x 72 1000 1000 12288 Oct  2 11:48 nordic

```

---

### Post by Bashing-om on 2014-10-05
lcbmac; We are !

We are "IN" the install !

OK, next is how smart is the network driver ? -> do you have internet connectivity now ?
Are you on a wired connection ?
What returns ?
```

ping -c3 8.8.8.8
ping -c3 google.com

```

IF we DO NOT have connection, will have to back out of the CHroot, and reconfigure to have the internet.

now we are cooking
[INDENT][INDENT][INDENT]with Crisco
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-05
Hi  Bashing-om

Wi-Fi actually but yes a great connection ill just quickly show you the code then see where we go from here.

```

bash-4.3# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=190 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=186 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=208 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 186.418/195.165/208.742/9.745 ms

```

```

bash-4.3# ping -c3 google.com
ping: unknown host google.com

```

---

### Post by Bashing-om on 2014-10-05
lcbmac; Well !

Good news is that we do have connectivity,
bad news is that we have no Domain Name Resolution. 
Fixable with some configuration.

Back out of the change root - back to the liveDVD environment:
```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```
Reconfigure the CHange Root:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
mount --bind /etc/resolv.conf /$CHROOT/run/resolvconf/resolv.conf
sudo chroot /mnt/ /bin/bash

```
Test again that we have Full internet access now !
```

ping -c3 8.8.8.8
ping -c3 google.com

```

Once we can talk on the 'net, we can proceed to try and fix the install !

To gracefully back out -When we are all done - -> back the the liveDVD:
```

exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt/etc/resolv.conf
sudo umount /mnt

```

[INDENT][INDENT]look'n more promise'n alla the time
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-06
Hi Bashing-om

Okay this is what has happened so far.
Does not seem right but I thought I would check with you.

```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ mount --bind /etc/resolv.conf /$CHROOT/run/resolvconf/resolv.conf
mount: only root can do that
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
bash-4.3# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=338 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=182 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=550 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 182.364/357.044/550.683/150.962 ms
bash-4.3# ping -c3 google.com
ping: unknown host google.com

```

Is that right? I Copied it like you have above.

---

### Post by Bashing-om on 2014-10-06
lcbmac; Sheeeshh,

Nope not right ! Let's try a different - more complex - configuration.
I presently do not know why that former invocation is not positive .

Back out of the install by doing the unmount routine.
Back in the liveDVD environment, do like so:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo cp /mnt/etc/hosts /mnt/etc/hosts.old
sudo cp /etc/hosts /mnt/etc/hosts
sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
sudo chroot /mnt/ /bin/bash

```
see now if we have full interneting.
```

ping -c3 8.8.8.8
ping -c3 google.com

```

When ready to back out of the CHroot routine:
```

cp /etc/hosts.old /etc/hosts
exit
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Before we can do else, we must have that internet connection !

[INDENT][INDENT]it can be done
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-06
Hi Bashing-om

Okay this is what happened

I thought it best you see it.
```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo cp /mnt/etc/hosts /mnt/etc/hosts.old
cp: cannot stat &#8216;/mnt/etc/hosts&#8217;: No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/hosts /mnt/etc/hosts
cp: cannot create regular file &#8216;/mnt/etc/hosts&#8217;: No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/resolv.conf /mnt/etc/resolv.conf
cp: cannot create regular file &#8216;/mnt/etc/resolv.conf&#8217;: No such file or directory
ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash
bash-4.3# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=437 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=632 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 1999ms
rtt min/avg/max/mdev = 437.926/535.278/632.630/97.352 ms
bash-4.3# ping -c3 google.com
ping: unknown host google.com
bash-4.3# 

```

its not quite right I think

---

### Post by Bashing-om on 2014-10-06
lcbmac; Hummm ??

Lemme have a bit if time here to clear my mind ( reset the registers ) . Take another look at this, do a bit of home work, see if I can determine where my thinking is going off into space.

Must establish that connection with full DNS recognition.


[INDENT][INDENT]one way or another 
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-06
lcbmac; Hey !

I do not see an apparent fault in my logic.
What I do see:
> 
ubuntu@ubuntu:~$ sudo cp /mnt/etc/hosts /mnt/etc/hosts.old
cp: cannot stat ‘/mnt/etc/hosts’: No such file or directory
ubuntu@ubuntu:~$ sudo cp /etc/hosts /mnt/etc/hosts
cp: cannot create regular file ‘/mnt/etc/hosts’: No such file or directory
<snip>

Is that the 'required' file does not exist ???? to start with.

Let's verify through an alternate method that this file " /etc/hosts" is not in existence. And IF it does not exist ... make it up !
From the liveDVD:
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -al /mnt/work/etc/hosts
ls -al /mnt/work/etc/hostname

```
ReMemBer: manually  mounted, must be (UN)mounted !
```

sudo umount /mnt/work

```
Then we see - when this story is portrayed - what to do
[INDENT][INDENT]oh what to do
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-06
Hi Bashing-om

Okay here are the ways i have done it so you can see.

```

ubuntu@ubuntu:~$ sudo mkdir /mnt/work

```
```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work

```
```

ubuntu@ubuntu:~$ ls -al /mnt/work/home/nordic
total 660
drwxr-xr-x 72 1000 1000  12288 Oct  2 13:48 .
drwxr-xr-x  3 root root   4096 May  8  2012 ..
drwx------  3 1000 1000   4096 May  8  2012 .adobe
-rw-rw-r--  1 1000 1000    109 Aug  2  2013 .apport-ignore.xml
drwxrwxr-x  2 1000 1000   4096 Jul  3  2012 .arduino
drwxrwxr-x  3 1000 1000   4096 Nov 22  2012 .avidemux
-rw-------  1 1000 1000   4348 Sep  7 02:09 .bash_history
-rw-r--r--  1 1000 1000    220 May  8  2012 .bash_logout
-rw-r--r--  1 1000 1000   3486 May  8  2012 .bashrc
drwx------ 62 1000 1000   4096 Sep 11 21:12 .cache
drwx------  3 1000 1000   4096 Sep 23  2013 .compiz
drwxrwxr-x  3 1000 1000   4096 May  8  2012 .compiz-1
drwx------ 44 1000 1000   4096 Sep  3 22:17 .config
drwx------  3 1000 1000   4096 May  8  2012 .dbus
drwxrwxr-x  5 1000 1000   4096 Jan 23  2014 .dc++
drwxr-xr-x  2 1000 1000   4096 Jul 18 08:18 Desktop
-rw-r--r--  1 1000 1000     34 Apr 19 23:56 .dmrc
drwxr-xr-x 22 1000 1000  20480 Oct  2 21:38 Documents
drwx------  2 1000 1000   4096 Oct 15  2013 .dosbox
drwxr-xr-x  3 1000 1000  12288 Oct  2 13:30 Downloads
drwx------  3 1000 1000   4096 Sep  7  2013 .dropbox
drwx------  9 1000 1000   4096 Sep  7  2013 Dropbox
drwxr-xr-x  5 1000 1000   4096 Aug  2  2013 .dropbox-dist
drwxr-xr-x  3 1000 1000  20480 Jul 12  2013 dwhelper
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .eclipse
-rw-r--r--  1 1000 1000  11888 May  8  2012 .face
drwxrwxr-x  3 1000 1000   4096 May  9 13:05 .flush
drwxr-xr-x  2 1000 1000   4096 Sep  8  2013 fontconfig
drwxr-xr-x  2 1000 1000   4096 Sep  8  2013 .fontconfig
drwx------  5 1000 1000   4096 Sep 17 09:28 .gconf
drwx------  4 1000 1000   4096 May 13  2012 .gegl-0.0
drwxr-xr-x 22 1000 1000   4096 Jul 31  2013 .gimp-2.6
drwxr-xr-x 24 1000 1000   4096 May 12 15:24 .gimp-2.8
-rw-r-----  1 1000 1000      0 Apr 25 23:39 .gksu.lock
drwx------  5 1000 1000   4096 Aug 24 16:17 .gnome2
drwx------  2 1000 1000   4096 May 23  2012 .gnome2_private
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-08AFIW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-09I9FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-0AYZJW
-rw-------  1 1000 1000      0 Jul  9  2012 .goutputstream-0WH1GW
-rw-------  1 1000 1000      0 Dec 31  2012 .goutputstream-1SP7PW
-rw-------  1 1000 1000      0 Aug 24  2012 .goutputstream-1V6OJW
-rw-------  1 1000 1000      0 Jul 29  2012 .goutputstream-1Y87HW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-1Z0CIW
-rw-------  1 1000 1000      0 Jun  5  2012 .goutputstream-2PM3EW
-rw-------  1 1000 1000      0 Jul 21  2012 .goutputstream-2QPIHW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-38WYDW
-rw-------  1 1000 1000      0 May  8  2012 .goutputstream-3EVUDW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-3HE2HW
-rw-------  1 1000 1000      0 Jul 13  2012 .goutputstream-3RCQHW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-3V36GW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-4FI9YW
-rw-------  1 1000 1000      0 Jun 24  2012 .goutputstream-4ZS8FW
-rw-------  1 1000 1000      0 Sep  4  2012 .goutputstream-5AMAKW
-rw-------  1 1000 1000      0 Sep 16  2012 .goutputstream-64FZKW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-6NNSEW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-75XYLW
-rw-------  1 1000 1000      0 Aug 19  2012 .goutputstream-7PECJW
-rw-------  1 1000 1000      0 Aug  2  2012 .goutputstream-8IDJIW
-rw-------  1 1000 1000      0 Oct  4  2012 .goutputstream-8P6OLW
-rw-------  1 1000 1000      0 Dec  4  2012 .goutputstream-9JHPOW
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-9M0FEW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-9UI8HW
-rw-------  1 1000 1000      0 Oct 10  2012 .goutputstream-A1Y3LW
-rw-------  1 1000 1000      0 Aug  9  2013 .goutputstream-AAWX1W
-rw-------  1 1000 1000      0 Aug 28  2012 .goutputstream-APBPJW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-BK3WDW
-rw-------  1 1000 1000      0 Jul 14  2012 .goutputstream-CAVEHW
-rw-------  1 1000 1000      0 Jun 14  2012 .goutputstream-CKD2FW
-rw-------  1 1000 1000      0 Jul 20  2012 .goutputstream-CQDHHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-CTXNYW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-DEBTLW
-rw-------  1 1000 1000      0 May  9  2012 .goutputstream-DLRNDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-E5O9EW
-rw-------  1 1000 1000      0 Mar 20  2013 .goutputstream-E5PWTW
-rw-------  1 1000 1000      0 May 31  2012 .goutputstream-E7E6EW
-rw-------  1 1000 1000      0 Dec  6  2012 .goutputstream-EIF1OW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-ENN0YW
-rw-------  1 1000 1000      0 Jun 15  2012 .goutputstream-F1EYFW
-rw-------  1 1000 1000      0 Aug 30  2013 .goutputstream-G4OO2W
-rw-------  1 1000 1000      0 Aug 12  2012 .goutputstream-GH02IW
-rw-------  1 1000 1000      0 Aug 24  2013 .goutputstream-GRYJ2W
-rw-------  1 1000 1000      0 Aug  4  2012 .goutputstream-GUW8HW
-rw-------  1 1000 1000      0 May 11  2012 .goutputstream-H7LSDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-HA47EW
-rw-------  1 1000 1000      0 Dec 29  2012 .goutputstream-HOBWPW
-rw-------  1 1000 1000      0 Dec 14  2012 .goutputstream-HXWHPW
-rw-------  1 1000 1000      0 Aug  5  2013 .goutputstream-I6VB1W
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-IOOUEW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-IPG4GW
-rw-------  1 1000 1000      0 Sep 12  2012 .goutputstream-IPMWKW
-rw-------  1 1000 1000      0 Jun  4  2012 .goutputstream-J0G0EW
-rw-------  1 1000 1000      0 Aug 13  2012 .goutputstream-JHSQIW
-rw-------  1 1000 1000      0 Jul 23  2012 .goutputstream-K0KWHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-KLXDYW
-rw-------  1 1000 1000      0 Sep  7  2013 .goutputstream-KTJO2W
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-L88HGW
-rw-------  1 1000 1000      0 Aug 29  2012 .goutputstream-M2LIJW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-MCWCHW
-rw-------  1 1000 1000      0 Aug 11  2013 .goutputstream-MUAT1W
-rw-------  1 1000 1000      0 Jul  2  2013 .goutputstream-NDKQZW
-rw-------  1 1000 1000      0 Jul  4  2012 .goutputstream-OCK3GW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-OFOODW
-rw-------  1 1000 1000      0 Jan 17  2013 .goutputstream-OM43QW
-rw-------  1 1000 1000      0 Feb  4  2013 .goutputstream-PCLSRW
-rw-------  1 1000 1000      0 Nov 26  2012 .goutputstream-PE8MOW
-rw-------  1 1000 1000      0 Sep  5  2013 .goutputstream-PN4M2W
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-Q7F9XW
-rw-------  1 1000 1000      0 Jun 25  2013 .goutputstream-R0DVYW
-rw-------  1 1000 1000      0 Aug  9  2012 .goutputstream-R2OPIW
-rw-------  1 1000 1000      0 Nov  9  2012 .goutputstream-RBE6MW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-RGX3HW
-rw-------  1 1000 1000      0 Dec  9  2012 .goutputstream-RSK5OW
-rw-------  1 1000 1000      0 Jun 10  2012 .goutputstream-SE5RFW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-SGYIEW
-rw-------  1 1000 1000      0 May 30  2013 .goutputstream-SIH5XW
-rw-------  1 1000 1000      0 Nov  5  2012 .goutputstream-SM25MW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-SNBBGW
-rw-------  1 1000 1000      0 Jul 10  2012 .goutputstream-TAU9GW
-rw-------  1 1000 1000      0 Jul 11  2012 .goutputstream-TLECHW
-rw-------  1 1000 1000      0 Aug  1  2012 .goutputstream-UARKIW
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-UCZ4FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-UEZCKW
-rw-------  1 1000 1000      0 Sep  5  2012 .goutputstream-UUW5JW
-rw-------  1 1000 1000      0 Aug 20  2012 .goutputstream-VWUBJW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-VZM8GW
-rw-------  1 1000 1000      0 Jul  2  2012 .goutputstream-WBD5GW
-rw-------  1 1000 1000      0 May 24  2013 .goutputstream-WXNHXW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-X1BHKW
-rw-------  1 1000 1000      0 Jun  7  2013 .goutputstream-YCEPYW
-rw-------  1 1000 1000      0 Apr  9  2013 .goutputstream-ZFDOVW
drwx------  2 1000 1000   4096 Jun 23  2012 .gphoto
drwxrwxr-x  3 1000 1000   4096 May  2 21:02 .gstreamer-0.10
-rw-rw-r--  1 1000 1000    255 Sep 20  2013 .gtk-bookmarks
-rw-r--r--  1 1000 1000    941 Mar 11  2014 .gtk-recordmydesktop
drwx------  2 1000 1000   4096 May  8  2012 .gvfs
-rw-------  1 1000 1000 134754 Sep 17 09:28 .ICEauthority
drwx------  2 1000 1000   4096 Apr 14 00:09 .icons
drwxr-xr-x  3 1000 1000   4096 Mar 24  2014 .java
drwx------  3 1000 1000   4096 May 20  2012 .kde
drwxr-xr-x  5 1000 1000   4096 May 23  2012 kdenlive
drwx------  3 1000 1000   4096 Jul 31  2013 .kompozer.net
drwx------  3 1000 1000   4096 Aug 15  2012 .launchpadlib
drwxr-xr-x  3 1000 1000   4096 May  8  2012 .local
drwx------  3 1000 1000   4096 May  9  2012 .macromedia
drwx------  2 1000 1000   4096 Sep 21  2013 .mission-control
drwxrwxr-x  4 1000 1000   4096 Nov 12  2012 .moovida
drwx------  4 1000 1000   4096 May  8  2012 .mozilla
drwxr-xr-x 31 1000 1000  20480 Aug 27 23:44 Music
drwxr-xr-x  2 1000 1000   4096 Nov  7  2012 .ocp
drwxr-x---  6 1000 1000   4096 Aug 26  2012 .openshot
-rw-r--r--  1 1000 1000    248 Oct  4  2012 .pam_environment
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .pdfedit
drwxr-xr-x 22 1000 1000  81920 Sep 12 12:41 Pictures
drwx------  3 1000 1000   4096 May  8  2012 .pki
-rw-r--r--  1 1000 1000    675 Oct  4  2012 .profile
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Public
drwx------  2 1000 1000   4096 Sep 13 14:22 .pulse
-rw-------  1 1000 1000    256 May  8  2012 .pulse-cookie
drwxrwxr-x  3 1000 1000   4096 Nov 12  2012 .python-eggs
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .qt
drwxr-xr-x  2 1000 1000   4096 Dec  4  2013 .redeclipse
drwxrwxr-x  7 1000 1000   4096 Apr 26 00:11 rtl8192cu-fixes
drwxrwxr-x  4 1000 1000   4096 Jul  6  2012 sketchbook
drwx------  6 1000 1000   4096 Aug 20  2013 .Skype
drwxr-xr-x 12 1000 1000   4096 Jul  4  2013 slimboat
drwxrwxr-x  3 1000 1000   4096 Jun 28  2012 .slimrat
drwx------  4 1000 1000   4096 Oct  4  2012 .speech-dispatcher
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .swt
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Templates
drwx------  5 1000 1000   4096 Aug 17  2012 .thumbnails
drwx------  4 1000 1000   4096 May  8  2012 .thunderbird
drwx------  2 1000 1000   4096 Nov  5  2012 .tor
drwxrwxr-x  2 1000 1000   4096 May  8  2012 Ubuntu One
drwxrwxr-x  2 1000 1000   4096 Nov  5  2012 .vidalia
drwxr-xr-x 12 1000 1000  12288 Sep  9 00:04 Videos
-rw-------  1 1000 1000    842 Sep  7 01:06 .viminfo
drwxrwxr-x  2 1000 1000   4096 Mar 11  2014 .VirtualBox
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 workspace
-rw-------  1 1000 1000     51 Sep 17 09:28 .Xauthority
drwxr-xr-x  2 1000 1000   4096 Apr 30 17:03 .xine
-rw-rw-r--  1 1000 1000    131 Jul  4 10:58 .xinputrc
drwxrwxr-x  2 1000 1000   4096 Aug 23  2012 .xmltv
-rw-------  1 1000 1000     35 Sep 17 09:28 .xsession-errors
-rw-------  1 1000 1000     35 Sep 16 20:48 .xsession-errors.old

```

```

ubuntu@ubuntu:~$ sudo umount /mnt/work

```

hope it helps

---

### Post by Bashing-om on 2014-10-06
lcbmac; Hello;

Not the commands I requested that you do, to see if the file(s) we need are in existence.
```

sudo mkdir /mnt/work
sudo mount /dev/sda1 /mnt/work
ls -al /mnt/work/etc/hosts
ls -al /mnt/work/etc/hostname

```
where we want to see "/etc/hosts" and "/etc/hostname". 
If they exist we will want to examine the contents, next.
When done UN-mount.
```

sudo umount /mnt/work

```


But;
There is in fact a fallacy in my logic ! 
I have booted up the liveDVD and attempted to CHange Root into my install .. In copying the network files, there is now a symlink that I have yet to determine a way around it to get the files to copy. I am to this time unable to get networking working !

You can bet I will be hard at it to find the method to get networking working in that CHange Root environment.
-------------------------------
Off topic: In the process' this day, I have broke my grub. (RE-)installing grub is presently my 1st priority. I am not much if I can not boot my work station !

[INDENT][INDENT]trials, troubles and tribulations
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-07
Hi Bashing-om
okay as you requested exactly i have copied it and this is the resualt:

[code]
ubuntu@ubuntu:~$ sudo mkdir /mnt/work
mkdir: cannot create directory &#8216;/mnt/work&#8217;: File exists
ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/work
ubuntu@ubuntu:~$ ls -al /mnt/work/etc/hosts
ls: cannot access /mnt/work/etc/hosts: No such file or directory
ubuntu@ubuntu:~$ ls -al /mnt/work/etc/hostname
ls: cannot access /mnt/work/etc/hostname: No such file or directory
ubuntu@ubuntu:~$ sudo umount /mnt/work
[/code

If this is still not right then you might have to simplify it for me. Sorry but 3 hours of sleep a night is killing me. so the brain ant working to well.

---

### Post by Bashing-om on 2014-10-07
lcbmac; Yeah ....

(a closing ']' is needed on "[/code" to put that output as 'code' into a code box)


That is the output I needed to see. And yeah - for some reason those files are not present ! ..Will have to build them. This adds to the aggravation factor (on your behalf) ... You have been fighting this restoration for 2 weeks now and we are making progress.
But, if you are loosing sleep over this, it is but a matter of minutes to back up your data and do a clean fresh install - and copy your files back in place.

I have found the cause of networking to fail in the CHange Root environment. I have not to this time made up the time to test my solution , IF we are going to continue this process of restoration - and your learning in general - I will promote that job to a higher priority. When we continue we -> Mount the root partition, We then create the required files with the proper content ( backup files might even be present ), CHroot into the install, fix permissions, clean up /boot, and finally (re-)install grub.

So long as you want I am committed to restoration of your system.


[INDENT][INDENT]no steps for a stepper
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-07
Hi -Bashing-om

Sorry about that was suppose to  add the ] to the [/code] 
I would like to continue learning obviously and education is the key to a greater future. :-)
and smarter way of solving problems. So where do we go from here. I like the back up Idea. How does that work?

---

### Post by lcbmac on 2014-10-07
Hi Bashing-om

If I didn't make myself clear and I do somethings say things wrong.

'Mount the root partition, We then create the required files with the  proper content ( backup files might even be present ), CHroot into the  install, fix permissions, clean up /boot, and finally (re-)install grub.'

This is what I want to do.

---

### Post by Bashing-om on 2014-10-07
lcbmac; Ho Kay !

On with the fix'n and the learning process.

For me I have to test mounting /run in the change root environment and copying the network file to the CHroot.
For you:
You may backup your files, if you so desire:
The easiest way, in my opinion ->
From the liveDVD 
in software sources enable the 'universe' repository so we can:
```

sudo apt-get install gksu

``` 
This gets you the ability to use a graphical application with elevated privileges ,
Plug in a USB thumb drive.
Once installed:
```

gksudo nautilus

```
Opens the file manager with "root" access.
Now open a second window in the file manager Pointed to the USB drive, and simply copy/paste files from the install to the USB drive in that window. 

--------------------
When you are ready to proceed, we look and see if there are any backup files available to replace the missing '/etc/hosts, /etc/hostname' files.
If not, we make them up from scratch. ( hey yes you can do that !) .

I will in the meantime be testing to have networking in the CHroot environment. I have installed a standard 14.04 ubuntu with which to do these testings. All I have to do is get my other obligations met here on the forum, and (RE-)boot into 14.04 ubuntu. Test away to my heart's content.
-----------------------
I am pleased you want to learn, believe me
[INDENT][INDENT][INDENT]we are all at some point on that learning curve
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-07
Hi Bashing-om

Okay took some Screen-shots that I thought you might want to see some discrepancies I have found.
Weather I am right of wrong Its still worth taking a look at.

The right window has some things that don't match the left window. Right window is My actual system 'Nordic' and the Left window is the LiveDVD.
[ATTACH=CONFIG]257023[/ATTACH][ATTACH=CONFIG]257024[/ATTACH][ATTACH=CONFIG]257025[/ATTACH]

May this be a helping solution.

---

### Post by Bashing-om on 2014-10-07
lcbmac; Welp; 

The two are different operating systems ! .. So yes the files on the 2 are different. In this case all you are interested in is saving "your" personal files.
Take a look in /home/Nordic. See what is in the subdirectories that you want. ANY system files are of no concern to you. These files will be in that new install - in the unlikely event that a (RE-)install is undertaken.
You are only interested in saving files that can not be replaced, A power user that has made significant changes to the Operating system "might" save some of the config files. I do not consider that you fit into this category .

[INDENT][INDENT]regards
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-08
lcbmac;; On a good note ;

I have got full networking in the CHange Root environment working !

So when you are caught up, we can proceed.

[INDENT]now that was a step for this stepper 
[/INDENT]

---

### Post by lcbmac on 2014-10-09
Hi Bashing-om

Okay Im ready when you are. unfortunatly i cant download all my stuff as the files are to big according to my system and I have run our of space.

---

### Post by Bashing-om on 2014-10-09
lcbmac; OK ;

Backups are a good thing !
I do not expect to bork your install, but, Never can tell what might happen !

For re-starters, from the liveDVD in that CHange Root environment; We are first only going to "look" and see what is to be done.
boot up the CHroot:
```

sudo mount /dev/sda1 /mnt/
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo mount --bind /dev/pts /mnt/dev/pts
sudo mount --bind /run /mnt/run

sudo chroot /mnt/ /bin/bash

```
Where I am adding the "mount --bind" for /run as formerly the link for '/etc/resolv.conf' becomes broke.

Now make sure we have networking - do not be put off if we don't, as I expect we must create a couple of files!
```

ping -c3 8.8.8.8
ping -c3 google.com

```

And now we "look". - nothing here requires networking. 
Post back the outputs of:
```

ls -al .Xauthority
ls -al .ICEauthority
ls -al /home
ls -al /home/nordic
ls -al /etc/host*
ls -al /boot
cat -n /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
lspci -nnk | grep -iA3 vga
sudo lshw -C display

```
Where :
a) we are checking that "you" have authority to access your /home directory;
b) What we can do about enabling networking ( I do expect, 'till this is fixed that there is not DNS);
c) Again, a ready reference for the kernels we are going to remove;
d) Looking at the package manager's source list(s);
e) What is the graphics situation ? .....+

Once all this is known we can start cleaning up and re-doing -> get you booting !

OK, all done, back out of the CHroot, gracefully :
```

exit
sudo umount /mnt/run 
sudo umount /mnt/dev/pts
sudo umount /mnt/sys
sudo umount /mnt/proc
sudo umount /mnt/dev
sudo umount /mnt

```

Now back in the liveDVD.
Standby, and we see what we are going to do to get you booting.

[INDENT][INDENT]lots of steps here;
[INDENT][INDENT][INDENT]but, easy does it[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-09
Hi Bashing-om

Okay I did not see this earlier and I thought it was done already. But I just have a few more files copying over to my Flash drive. But it says 51hrs to 1.6Gb. does that sound right??

Anyway Once it is done I shall Start on what you have sent me and move forward with the results copied over here to you.

Thank you again

---

### Post by Bashing-om on 2014-10-09
lcbmac; Yuk;

Yeah, that is slow - what means are you employing to 'copy" and why such a great amount ? (songs, and movies ??).
Again, you are only interested in saving your "personal" data.

How fast is the port (USB) that you are copying through ? ... a large amount of data is best done with rsync:
> 
Description-en: fast, versatile, remote (and local) file-copying tool
 rsync is a fast and versatile file-copying tool which can copy locally
 and to/from a remote host. It offers many options to control its behavior,
 and its remote-update protocol can minimize network traffic to make
 transferring updates between machines fast and efficient.


Again, time to do homework, if you decide 'rsync' is the tool to use.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-09
Hi Bashing-om

Yes It is Sloooooow But it is Small vids about 36mb-112mbs thats it.
The only way is Drag and drop the files into the USB.

---

### Post by lcbmac on 2014-10-10
Hi Bashing-om

Okay so here are the results and I think you will be quite happy with the results. :-)

```

ubuntu@ubuntu:~$ sudo mount /dev/sdxY /mnt/
mount: special device /dev/sdxY does not exist
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
mount: mount point /mnt/dev does not exist
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
mount: mount point /mnt/proc does not exist
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
mount: mount point /mnt/sys does not exist
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
mount: mount point /mnt/dev/pts does not exist
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/run
mount: mount point /mnt/run does not exist

```


```

ubuntu@ubuntu:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=204 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=217 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=214 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 204.747/212.294/217.928/5.561 ms
ubuntu@ubuntu:~$ ping -c3 google.com
PING google.com (66.8.14.38) 56(84) bytes of data.
64 bytes from google.com (66.8.14.38): icmp_seq=1 ttl=54 time=54.0 ms
64 bytes from google.com (66.8.14.38): icmp_seq=2 ttl=54 time=37.5 ms
64 bytes from google.com (66.8.14.38): icmp_seq=3 ttl=54 time=139 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 37.518/76.878/139.061/44.485 ms

```

I thought you might want to see this part most of all

```

ubuntu@ubuntu:~$ ls -al .Xauthority
-rw------- 1 ubuntu ubuntu 51 Oct  8 11:23 .Xauthority

```
```

ubuntu@ubuntu:~$ ls -al .ICEauthority
-rw------- 1 ubuntu ubuntu 318 Oct  8 11:23 .ICEauthority

```
```

ubuntu@ubuntu:~$ ls -al /home
total 0
drwxr-xr-x  1 root   root    60 Oct  8 11:19 .
drwxr-xr-x  1 root   root   260 Oct  8 11:18 ..
drwxr-xr-x 16 ubuntu ubuntu 460 Oct  8 19:55 ubuntu

```
```

ubuntu@ubuntu:~$ ls -al /home/nordic
ls: cannot access /home/nordic: No such file or directory

```
```

ubuntu@ubuntu:~$ ls -al /ect/host*
ls: cannot access /ect/host*: No such file or directory

```

---

### Post by Bashing-om on 2014-10-10
lcbmac; Hey !

OK, we are seeing the results from the liveDVD and not the install ..

WHY -> because of my failure to correct my general paste of "sdxY" to specific "sda1" // corrected now //.

2nd lesson in the administration of your system, always pay attention to what the system is telling you, and try to think through what is not going on.
here you have:
> 
ubuntu@ubuntu:~$ sudo mount /dev/sdxY /mnt/
[color=red]mount: special device /dev/sdxY does not exist[/color]

Where the system is telling you, no can do !
Subsequently, none of the other mounts will work.

so ....... back up and try again:
"sudo mount /dev/sda1 /mnt/" is the corrected syntax.

[INDENT][INDENT]sorry 'bout that
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-10
Hi Bashing-om

Okay this seems to be better:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo mount --bind /dev /mnt/dev
ubuntu@ubuntu:~$ sudo mount --bind /proc /mnt/proc
ubuntu@ubuntu:~$ sudo mount --bind /sys /mnt/sys
ubuntu@ubuntu:~$ sudo mount --bind /dev/pts /mnt/dev/pts
ubuntu@ubuntu:~$ sudo mount --bind /run /mnt/run

```
```

ubuntu@ubuntu:~$ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=206 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=209 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=224 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 206.232/213.335/224.352/7.907 ms
ubuntu@ubuntu:~$ ping -c3 google.com
PING google.com (66.8.14.26) 56(84) bytes of data.
64 bytes from google.com (66.8.14.26): icmp_seq=1 ttl=54 time=20.1 ms
64 bytes from google.com (66.8.14.26): icmp_seq=2 ttl=54 time=64.9 ms
64 bytes from google.com (66.8.14.26): icmp_seq=3 ttl=54 time=87.1 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 20.124/57.412/87.155/27.880 ms

```


```

ubuntu@ubuntu:~$ ls -al .Xauthority
-rw------- 1 ubuntu ubuntu 51 Oct  8 11:23 .Xauthority

```
```

ubuntu@ubuntu:~$ ls -al .ICEauthority
-rw------- 1 ubuntu ubuntu 318 Oct  8 11:23 .ICEauthority

```
```

ubuntu@ubuntu:~$ ls -al /home
total 0
drwxr-xr-x  1 root   root    60 Oct  8 11:19 .
drwxr-xr-x  1 root   root   260 Oct  8 11:18 ..
drwxr-xr-x 16 ubuntu ubuntu 460 Oct  8 19:55 ubuntu

```

> Okay so here is a little Issue.. Not sure but but hopfully this helps.

```

ubuntu@ubuntu:~$ ls -al /home/nordic
ls: cannot access /home/nordic: No such file or directory

```

---

### Post by Bashing-om on 2014-10-10
lcbmac; Yuk ! sheesshh !

I still have an error in my logic to implement the CHange Root ! .. I forgot to 'change' into it !
The sequence is now amended.

If you are still in the liveDVD. do at this time:
```

sudo chroot /mnt/ /bin/bash

```
And pick back up at the ping .. let's see where we stand now (??) .

How do I know that you did not "change root" you may ask ?
it is in the output:
> 
 ubuntu@ubuntu:~$ ls -al .Xauthority
-rw------- 1 [color=red]ubuntu ubuntu[/color] 51 Oct  8 11:23 .Xauthority

where "ubuntu ibuntu" is the liveDVD.

If you do not succeed
[INDENT][INDENT][INDENT]blame Bashing-om
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-10
Hi Bashiong-om

No Biggy. I have been on the road for 14hrs today so I can understand where you are coming from.
Alright so here are the rest asfter the fix with the fix.

```

ubuntu@ubuntu:~$ sudo chroot /mnt/ /bin/bash

```
```

root@ubuntu:/# ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_seq=1 ttl=46 time=203 ms
64 bytes from 8.8.8.8: icmp_seq=2 ttl=46 time=191 ms
64 bytes from 8.8.8.8: icmp_seq=3 ttl=46 time=180 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2000ms
rtt min/avg/max/mdev = 180.812/191.725/203.287/9.200 ms
root@ubuntu:/# ping -c3 google.com

```
```

PING google.com (66.8.14.38) 56(84) bytes of data.
64 bytes from google.com (66.8.14.38): icmp_seq=1 ttl=54 time=17.5 ms
64 bytes from google.com (66.8.14.38): icmp_seq=2 ttl=54 time=17.5 ms
64 bytes from google.com (66.8.14.38): icmp_seq=3 ttl=54 time=17.0 ms

--- google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 17.092/17.389/17.553/0.236 ms

```
```

root@ubuntu:/# ls -al .Xauthority
ls: cannot access .Xauthority: No such file or directory
root@ubuntu:/# ls -al /home/nordic
total 660
drwxr-xr-x 72 1000 1000  12288 Oct  2 11:48 .
drwxr-xr-x  3 root root   4096 May  8  2012 ..
drwx------  3 1000 1000   4096 May  8  2012 .adobe
-rw-rw-r--  1 1000 1000    109 Aug  2  2013 .apport-ignore.xml
drwxrwxr-x  2 1000 1000   4096 Jul  3  2012 .arduino
drwxrwxr-x  3 1000 1000   4096 Nov 22  2012 .avidemux
-rw-------  1 1000 1000   4348 Sep  7 00:09 .bash_history
-rw-r--r--  1 1000 1000    220 May  8  2012 .bash_logout
-rw-r--r--  1 1000 1000   3486 May  8  2012 .bashrc
drwx------ 62 1000 1000   4096 Sep 11 19:12 .cache
drwx------  3 1000 1000   4096 Sep 22  2013 .compiz
drwxrwxr-x  3 1000 1000   4096 May  8  2012 .compiz-1
drwx------ 44 1000 1000   4096 Sep  3 20:17 .config
drwx------  3 1000 1000   4096 May  8  2012 .dbus
drwxrwxr-x  5 1000 1000   4096 Jan 23  2014 .dc++
drwxr-xr-x  2 1000 1000   4096 Jul 18 06:18 Desktop
-rw-r--r--  1 1000 1000     34 Apr 19 21:56 .dmrc
drwxr-xr-x 22 1000 1000  20480 Oct  8 08:45 Documents
drwx------  2 1000 1000   4096 Oct 15  2013 .dosbox
drwxr-xr-x  3 1000 1000  12288 Oct  2 11:30 Downloads
drwx------  3 1000 1000   4096 Sep  7  2013 .dropbox
drwx------  9 1000 1000   4096 Sep  7  2013 Dropbox
drwxr-xr-x  5 1000 1000   4096 Aug  2  2013 .dropbox-dist
drwxr-xr-x  3 1000 1000  20480 Jul 11  2013 dwhelper
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .eclipse
-rw-r--r--  1 1000 1000  11888 May  8  2012 .face
drwxrwxr-x  3 1000 1000   4096 May  9 11:05 .flush
drwxr-xr-x  2 1000 1000   4096 Sep  7  2013 fontconfig
drwxr-xr-x  2 1000 1000   4096 Sep  7  2013 .fontconfig
drwx------  5 1000 1000   4096 Sep 17 07:28 .gconf
drwx------  4 1000 1000   4096 May 13  2012 .gegl-0.0
drwxr-xr-x 22 1000 1000   4096 Jul 31  2013 .gimp-2.6
drwxr-xr-x 24 1000 1000   4096 May 12 13:24 .gimp-2.8
-rw-r-----  1 1000 1000      0 Apr 25 21:39 .gksu.lock
drwx------  5 1000 1000   4096 Aug 24 14:17 .gnome2
drwx------  2 1000 1000   4096 May 23  2012 .gnome2_private
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-08AFIW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-09I9FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-0AYZJW
-rw-------  1 1000 1000      0 Jul  9  2012 .goutputstream-0WH1GW
-rw-------  1 1000 1000      0 Dec 30  2012 .goutputstream-1SP7PW
-rw-------  1 1000 1000      0 Aug 24  2012 .goutputstream-1V6OJW
-rw-------  1 1000 1000      0 Jul 29  2012 .goutputstream-1Y87HW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-1Z0CIW
-rw-------  1 1000 1000      0 Jun  5  2012 .goutputstream-2PM3EW
-rw-------  1 1000 1000      0 Jul 21  2012 .goutputstream-2QPIHW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-38WYDW
-rw-------  1 1000 1000      0 May  8  2012 .goutputstream-3EVUDW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-3HE2HW
-rw-------  1 1000 1000      0 Jul 13  2012 .goutputstream-3RCQHW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-3V36GW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-4FI9YW
-rw-------  1 1000 1000      0 Jun 24  2012 .goutputstream-4ZS8FW
-rw-------  1 1000 1000      0 Sep  4  2012 .goutputstream-5AMAKW
-rw-------  1 1000 1000      0 Sep 15  2012 .goutputstream-64FZKW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-6NNSEW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-75XYLW
-rw-------  1 1000 1000      0 Aug 19  2012 .goutputstream-7PECJW
-rw-------  1 1000 1000      0 Aug  2  2012 .goutputstream-8IDJIW
-rw-------  1 1000 1000      0 Oct  4  2012 .goutputstream-8P6OLW
-rw-------  1 1000 1000      0 Dec  4  2012 .goutputstream-9JHPOW
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-9M0FEW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-9UI8HW
-rw-------  1 1000 1000      0 Oct 10  2012 .goutputstream-A1Y3LW
-rw-------  1 1000 1000      0 Aug  8  2013 .goutputstream-AAWX1W
-rw-------  1 1000 1000      0 Aug 28  2012 .goutputstream-APBPJW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-BK3WDW
-rw-------  1 1000 1000      0 Jul 14  2012 .goutputstream-CAVEHW
-rw-------  1 1000 1000      0 Jun 14  2012 .goutputstream-CKD2FW
-rw-------  1 1000 1000      0 Jul 20  2012 .goutputstream-CQDHHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-CTXNYW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-DEBTLW
-rw-------  1 1000 1000      0 May  9  2012 .goutputstream-DLRNDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-E5O9EW
-rw-------  1 1000 1000      0 Mar 20  2013 .goutputstream-E5PWTW
-rw-------  1 1000 1000      0 May 31  2012 .goutputstream-E7E6EW
-rw-------  1 1000 1000      0 Dec  6  2012 .goutputstream-EIF1OW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-ENN0YW
-rw-------  1 1000 1000      0 Jun 15  2012 .goutputstream-F1EYFW
-rw-------  1 1000 1000      0 Aug 30  2013 .goutputstream-G4OO2W
-rw-------  1 1000 1000      0 Aug 12  2012 .goutputstream-GH02IW
-rw-------  1 1000 1000      0 Aug 23  2013 .goutputstream-GRYJ2W
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-GUW8HW
-rw-------  1 1000 1000      0 May 11  2012 .goutputstream-H7LSDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-HA47EW
-rw-------  1 1000 1000      0 Dec 29  2012 .goutputstream-HOBWPW
-rw-------  1 1000 1000      0 Dec 14  2012 .goutputstream-HXWHPW
-rw-------  1 1000 1000      0 Aug  4  2013 .goutputstream-I6VB1W
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-IOOUEW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-IPG4GW
-rw-------  1 1000 1000      0 Sep 12  2012 .goutputstream-IPMWKW
-rw-------  1 1000 1000      0 Jun  4  2012 .goutputstream-J0G0EW
-rw-------  1 1000 1000      0 Aug 13  2012 .goutputstream-JHSQIW
-rw-------  1 1000 1000      0 Jul 23  2012 .goutputstream-K0KWHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-KLXDYW
-rw-------  1 1000 1000      0 Sep  7  2013 .goutputstream-KTJO2W
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-L88HGW
-rw-------  1 1000 1000      0 Aug 29  2012 .goutputstream-M2LIJW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-MCWCHW
-rw-------  1 1000 1000      0 Aug 10  2013 .goutputstream-MUAT1W
-rw-------  1 1000 1000      0 Jul  2  2013 .goutputstream-NDKQZW
-rw-------  1 1000 1000      0 Jul  4  2012 .goutputstream-OCK3GW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-OFOODW
-rw-------  1 1000 1000      0 Jan 17  2013 .goutputstream-OM43QW
-rw-------  1 1000 1000      0 Feb  4  2013 .goutputstream-PCLSRW
-rw-------  1 1000 1000      0 Nov 26  2012 .goutputstream-PE8MOW
-rw-------  1 1000 1000      0 Sep  5  2013 .goutputstream-PN4M2W
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-Q7F9XW
-rw-------  1 1000 1000      0 Jun 25  2013 .goutputstream-R0DVYW
-rw-------  1 1000 1000      0 Aug  9  2012 .goutputstream-R2OPIW
-rw-------  1 1000 1000      0 Nov  9  2012 .goutputstream-RBE6MW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-RGX3HW
-rw-------  1 1000 1000      0 Dec  9  2012 .goutputstream-RSK5OW
-rw-------  1 1000 1000      0 Jun 10  2012 .goutputstream-SE5RFW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-SGYIEW
-rw-------  1 1000 1000      0 May 30  2013 .goutputstream-SIH5XW
-rw-------  1 1000 1000      0 Nov  5  2012 .goutputstream-SM25MW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-SNBBGW
-rw-------  1 1000 1000      0 Jul 10  2012 .goutputstream-TAU9GW
-rw-------  1 1000 1000      0 Jul 11  2012 .goutputstream-TLECHW
-rw-------  1 1000 1000      0 Aug  1  2012 .goutputstream-UARKIW
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-UCZ4FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-UEZCKW
-rw-------  1 1000 1000      0 Sep  5  2012 .goutputstream-UUW5JW
-rw-------  1 1000 1000      0 Aug 20  2012 .goutputstream-VWUBJW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-VZM8GW
-rw-------  1 1000 1000      0 Jul  2  2012 .goutputstream-WBD5GW
-rw-------  1 1000 1000      0 May 24  2013 .goutputstream-WXNHXW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-X1BHKW
-rw-------  1 1000 1000      0 Jun  7  2013 .goutputstream-YCEPYW
-rw-------  1 1000 1000      0 Apr  9  2013 .goutputstream-ZFDOVW
drwx------  2 1000 1000   4096 Jun 23  2012 .gphoto
drwxrwxr-x  3 1000 1000   4096 May  2 19:02 .gstreamer-0.10
-rw-rw-r--  1 1000 1000    255 Sep 20  2013 .gtk-bookmarks
-rw-r--r--  1 1000 1000    941 Mar 11  2014 .gtk-recordmydesktop
drwx------  2 1000 1000   4096 May  8  2012 .gvfs
-rw-------  1 1000 1000 134754 Sep 17 07:28 .ICEauthority
drwx------  2 1000 1000   4096 Apr 13 22:09 .icons
drwxr-xr-x  3 1000 1000   4096 Mar 24  2014 .java
drwx------  3 1000 1000   4096 May 20  2012 .kde
drwxr-xr-x  5 1000 1000   4096 May 23  2012 kdenlive
drwx------  3 1000 1000   4096 Jul 31  2013 .kompozer.net
drwx------  3 1000 1000   4096 Aug 15  2012 .launchpadlib
drwxr-xr-x  3 1000 1000   4096 May  8  2012 .local
drwx------  3 1000 1000   4096 May  9  2012 .macromedia
drwx------  2 1000 1000   4096 Sep 21  2013 .mission-control
drwxrwxr-x  4 1000 1000   4096 Nov 12  2012 .moovida
drwx------  4 1000 1000   4096 May  8  2012 .mozilla
drwxr-xr-x 31 1000 1000  20480 Aug 27 21:44 Music
drwxr-xr-x  2 1000 1000   4096 Nov  7  2012 .ocp
drwxr-x---  6 1000 1000   4096 Aug 25  2012 .openshot
-rw-r--r--  1 1000 1000    248 Oct  4  2012 .pam_environment
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .pdfedit
drwxr-xr-x 22 1000 1000  81920 Sep 12 10:41 Pictures
drwx------  3 1000 1000   4096 May  8  2012 .pki
-rw-r--r--  1 1000 1000    675 Oct  4  2012 .profile
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Public
drwx------  2 1000 1000   4096 Sep 13 12:22 .pulse
-rw-------  1 1000 1000    256 May  8  2012 .pulse-cookie
drwxrwxr-x  3 1000 1000   4096 Nov 12  2012 .python-eggs
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .qt
drwxr-xr-x  2 1000 1000   4096 Dec  4  2013 .redeclipse
drwxrwxr-x  7 1000 1000   4096 Apr 25 22:11 rtl8192cu-fixes
drwxrwxr-x  4 1000 1000   4096 Jul  5  2012 sketchbook
drwx------  6 1000 1000   4096 Aug 20  2013 .Skype
drwxr-xr-x 12 1000 1000   4096 Jul  4  2013 slimboat
drwxrwxr-x  3 1000 1000   4096 Jun 28  2012 .slimrat
drwx------  4 1000 1000   4096 Oct  4  2012 .speech-dispatcher
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .swt
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Templates
drwx------  5 1000 1000   4096 Aug 17  2012 .thumbnails
drwx------  4 1000 1000   4096 May  8  2012 .thunderbird
drwx------  2 1000 1000   4096 Nov  5  2012 .tor
drwxrwxr-x  2 1000 1000   4096 May  8  2012 Ubuntu One
drwxrwxr-x  2 1000 1000   4096 Nov  5  2012 .vidalia
drwxr-xr-x 11 1000 1000  12288 Oct  8 19:59 Videos
-rw-------  1 1000 1000    842 Sep  6 23:06 .viminfo
drwxrwxr-x  2 1000 1000   4096 Mar 11  2014 .VirtualBox
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 workspace
-rw-------  1 1000 1000     51 Sep 17 07:28 .Xauthority
drwxr-xr-x  2 1000 1000   4096 Apr 30 15:03 .xine
-rw-rw-r--  1 1000 1000    131 Jul  4 08:58 .xinputrc
drwxrwxr-x  2 1000 1000   4096 Aug 23  2012 .xmltv
-rw-------  1 1000 1000     35 Sep 17 07:28 .xsession-errors
-rw-------  1 1000 1000     35 Sep 16 18:48 .xsession-errors.old

```
```

root@ubuntu:/# ls -al /etc/host*
-rw-r--r-- 1 root root  92 Feb 20  2014 /etc/host.conf
-rw-r--r-- 1 root root   7 Oct  7 17:29 /etc/hostname
-rw-r--r-- 1 root root 243 Oct  7 17:29 /etc/hosts
-rw-r--r-- 1 root root 411 Jul 22 22:12 /etc/hosts.allow
-rw-r--r-- 1 root root 711 Jul 22 22:12 /etc/hosts.deny
root@ubuntu:/# ls -al /boot

```
```

total 565212
drwxr-xr-x  3 root root    12288 Aug 27 07:54 .
drwxr-xr-x 24 root root     4096 Oct  8 19:59 ..
-rw-r--r--  1 root root  1010091 Oct 23  2013 abi-3.11.0-13-generic
-rw-r--r--  1 root root  1010091 Nov 12  2013 abi-3.11.0-14-generic
-rw-r--r--  1 root root  1010148 Jan 30  2014 abi-3.11.0-15-generic
-rw-r--r--  1 root root  1010381 Feb  3  2014 abi-3.11.0-17-generic
-rw-r--r--  1 root root  1011333 Feb 18  2014 abi-3.11.0-18-generic
-rw-r--r--  1 root root  1011333 Mar 11  2014 abi-3.11.0-19-generic
-rw-r--r--  1 root root  1011742 Apr  1  2014 abi-3.11.0-20-generic
-rw-r--r--  1 root root  1162233 May  3 00:40 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1165930 May  8 00:38 abi-3.13.0-26-generic
-rw-r--r--  1 root root  1165930 May 15 19:16 abi-3.13.0-27-generic
-rw-r--r--  1 root root  1165981 Jun  4 21:49 abi-3.13.0-29-generic
-rw-r--r--  1 root root  1166474 Jul  4 22:52 abi-3.13.0-30-generic
-rw-r--r--  1 root root  1166929 Jul  1 16:41 abi-3.13.0-31-generic
-rw-r--r--  1 root root  1166929 Jul 15 05:06 abi-3.13.0-32-generic
-rw-r--r--  1 root root  1166929 Jul 29 17:34 abi-3.13.0-33-generic
-rw-r--r--  1 root root  1166929 Aug 13 16:58 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1168075 Aug 15 03:09 abi-3.13.0-35-generic
-rw-r--r--  1 root root   804726 Aug 22  2013 abi-3.2.0-53-generic-pae
-rw-r--r--  1 root root   861648 Aug 22  2013 abi-3.5.0-40-generic
-rw-r--r--  1 root root   926513 Oct  1  2013 abi-3.8.0-32-generic
-rw-r--r--  1 root root   168537 Oct 23  2013 config-3.11.0-13-generic
-rw-r--r--  1 root root   168537 Nov 12  2013 config-3.11.0-14-generic
-rw-r--r--  1 root root   168527 Jan 30  2014 config-3.11.0-15-generic
-rw-r--r--  1 root root   168512 Feb  3  2014 config-3.11.0-17-generic
-rw-r--r--  1 root root   168540 Feb 18  2014 config-3.11.0-18-generic
-rw-r--r--  1 root root   168540 Mar 11  2014 config-3.11.0-19-generic
-rw-r--r--  1 root root   168540 Apr  1  2014 config-3.11.0-20-generic
-rw-r--r--  1 root root   169631 May  3 00:40 config-3.13.0-24-generic
-rw-r--r--  1 root root   169659 May  8 00:38 config-3.13.0-26-generic
-rw-r--r--  1 root root   169642 May 15 19:16 config-3.13.0-27-generic
-rw-r--r--  1 root root   169665 Jun  4 21:49 config-3.13.0-29-generic
-rw-r--r--  1 root root   169697 Jul  4 22:52 config-3.13.0-30-generic
-rw-r--r--  1 root root   169732 Jul  1 16:41 config-3.13.0-31-generic
-rw-r--r--  1 root root   169732 Jul 15 05:06 config-3.13.0-32-generic
-rw-r--r--  1 root root   169732 Jul 29 17:34 config-3.13.0-33-generic
-rw-r--r--  1 root root   169732 Aug 13 16:58 config-3.13.0-34-generic
-rw-r--r--  1 root root   169722 Aug 15 03:09 config-3.13.0-35-generic
-rw-r--r--  1 root root   147576 Aug 22  2013 config-3.2.0-53-generic-pae
-rw-r--r--  1 root root   154704 Aug 22  2013 config-3.5.0-40-generic
-rw-r--r--  1 root root   160909 Oct  1  2013 config-3.8.0-32-generic
drwxr-xr-x  5 root root    12288 Sep 14 11:39 grub
-rw-r--r--  1 root root 16941485 Nov  4  2013 initrd.img-3.11.0-13-generic
-rw-r--r--  1 root root 16941208 Nov 17  2013 initrd.img-3.11.0-14-generic
-rw-r--r--  1 root root 17052155 Feb  1  2014 initrd.img-3.11.0-15-generic
-rw-r--r--  1 root root 17055604 Feb 23  2014 initrd.img-3.11.0-17-generic
-rw-r--r--  1 root root 17057132 Feb 25  2014 initrd.img-3.11.0-18-generic
-rw-r--r--  1 root root 17054097 Mar 27  2014 initrd.img-3.11.0-19-generic
-rw-r--r--  1 root root 17054097 Apr 25 22:13 initrd.img-3.11.0-19-generic.old-dkms
-rw-r--r--  1 root root 17045668 Apr 18 15:43 initrd.img-3.11.0-20-generic
-rw-r--r--  1 root root 18659449 May  8 13:16 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 18611271 May  6 15:14 initrd.img-3.13.0-24-generic.old-dkms
-rw-r--r--  1 root root 18663265 May 11 23:56 initrd.img-3.13.0-26-generic
-rw-r--r--  1 root root 18663763 May 20 12:24 initrd.img-3.13.0-27-generic
-rw-r--r--  1 root root 18667315 Jun  7 15:23 initrd.img-3.13.0-29-generic
-rw-r--r--  1 root root 18718621 Jul  6 07:40 initrd.img-3.13.0-30-generic
-rw-r--r--  1 root root 18719337 Jul  7 09:18 initrd.img-3.13.0-31-generic
-rw-r--r--  1 root root 18720405 Aug  6 10:23 initrd.img-3.13.0-32-generic
-rw-r--r--  1 root root 18720244 Aug  9 10:06 initrd.img-3.13.0-33-generic
-rw-r--r--  1 root root 18719947 Aug 14 17:25 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18723539 Aug 27 07:54 initrd.img-3.13.0-35-generic
-rw-r--r--  1 root root 14243572 Sep  7  2013 initrd.img-3.2.0-53-generic-pae
-rw-r--r--  1 root root 15327160 Sep 21  2013 initrd.img-3.5.0-40-generic
-rw-r--r--  1 root root 16227905 Oct 19  2013 initrd.img-3.8.0-32-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2621288 Oct 23  2013 System.map-3.11.0-13-generic
-rw-------  1 root root  2621446 Nov 12  2013 System.map-3.11.0-14-generic
-rw-------  1 root root  2627916 Jan 30  2014 System.map-3.11.0-15-generic
-rw-------  1 root root  2628001 Feb  3  2014 System.map-3.11.0-17-generic
-rw-------  1 root root  2629740 Feb 18  2014 System.map-3.11.0-18-generic
-rw-------  1 root root  2629933 Mar 11  2014 System.map-3.11.0-19-generic
-rw-------  1 root root  2630177 Apr  1  2014 System.map-3.11.0-20-generic
-rw-------  1 root root  2685850 May  3 00:40 System.map-3.13.0-24-generic
-rw-------  1 root root  2689758 May  8 00:38 System.map-3.13.0-26-generic
-rw-------  1 root root  2689758 May 15 19:16 System.map-3.13.0-27-generic
-rw-------  1 root root  2690461 Jun  4 21:49 System.map-3.13.0-29-generic
-rw-------  1 root root  2690773 Jul  4 22:52 System.map-3.13.0-30-generic
-rw-------  1 root root  2693057 Jul  1 16:41 System.map-3.13.0-31-generic
-rw-------  1 root root  2693057 Jul 15 05:06 System.map-3.13.0-32-generic
-rw-------  1 root root  2693057 Jul 29 17:34 System.map-3.13.0-33-generic
-rw-------  1 root root  2693057 Aug 13 16:58 System.map-3.13.0-34-generic
-rw-------  1 root root  2697306 Aug 15 03:09 System.map-3.13.0-35-generic
-rw-------  1 root root  2321335 Aug 22  2013 System.map-3.2.0-53-generic-pae
-rw-------  1 root root  2323087 Aug 22  2013 System.map-3.5.0-40-generic
-rw-------  1 root root  2445627 Oct  1  2013 System.map-3.8.0-32-generic
-rw-------  1 root root  5633040 Oct 23  2013 vmlinuz-3.11.0-13-generic
-rw-------  1 root root  5633232 Nov 12  2013 vmlinuz-3.11.0-14-generic
-rw-------  1 root root  5663888 Jan 30  2014 vmlinuz-3.11.0-15-generic
-rw-------  1 root root  5664656 Feb  3  2014 vmlinuz-3.11.0-17-generic
-rw-------  1 root root  5667920 Feb 18  2014 vmlinuz-3.11.0-18-generic
-rw-------  1 root root  5669328 Mar 11  2014 vmlinuz-3.11.0-19-generic
-rw-------  1 root root  5667344 Apr  1  2014 vmlinuz-3.11.0-20-generic
-rw-------  1 root root  5800496 May  3 00:40 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5814832 May  8 00:38 vmlinuz-3.13.0-26-generic
-rw-------  1 root root  5814832 May 15 19:16 vmlinuz-3.13.0-27-generic
-rw-------  1 root root  5813456 Jun  4 21:49 vmlinuz-3.13.0-29-generic
-rw-------  1 root root  5813328 Jul  4 22:52 vmlinuz-3.13.0-30-generic
-rw-------  1 root root  5817968 Jul  1 16:41 vmlinuz-3.13.0-31-generic
-rw-------  1 root root  5820336 Jul 15 05:06 vmlinuz-3.13.0-32-generic
-rw-------  1 root root  5820336 Jul 29 17:34 vmlinuz-3.13.0-33-generic
-rw-------  1 root root  5820592 Aug 13 16:58 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5826864 Aug 15 03:09 vmlinuz-3.13.0-35-generic
-rw-------  1 root root  5028480 Aug 22  2013 vmlinuz-3.2.0-53-generic-pae
-rw-------  1 root root  5174640 Aug 22  2013 vmlinuz-3.5.0-40-generic
-rw-------  1 root root  5375088 Oct  1  2013 vmlinuz-3.8.0-32-generic

```
```

root@ubuntu:/# cat -n /etc/apt/sources.list
     1    deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted
     2    deb http://archive.ubuntu.com/ubuntu/ trusty main restricted universe
     3    deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe
     4    deb http://archive.ubuntu.com/ubuntu/ trusty-updates main restricted universe
     5    

```

Okay here is another problem

```

root@ubuntu:/# cat /etc/apt/sources.list.d/*.list
cat: /etc/apt/sources.list.d/*.list: No such file or directory

```

Ps I dont blame people.

---

### Post by Bashing-om on 2014-10-10
lcbmac; OK, Much better !

We do have internet connectivity in the "chroot", great !
internet files for DNS are present, so we do not have that to worry over.

We do have to  make "you" the owner of your /home, we will get to that.

That is some strange "/etc/apt/sources.list" file ! .. Will take a bit of time to see what we are going to do.

OK, still pending :.. in that CHange Root environment; We need to know about the file ".ICEauthority"
```

ls -al .ICEauthority

```
Maybe not a lot to do !

[INDENT][INDENT]we be step'n
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-10
lcbmac; Hey !

I have a plan .

show me from the CHroot into the install from the liveDVD:
```

ls -al .ICEauthority
uname -a
ls -al  /
dpkg -l | grep linux-

```
we will - when all the info is gathered:
Allow "you" access to your /home directory
Remove the old kernels that are not now a part of the boot process
Setup the sources.list file to something more resonable

Then I expect you can boot ... not determined is if the file .Xauthority will be automagically created with the change in permissions, or if we will have to create it.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay this is what I have gotten from the input so far

```

root@ubuntu:/# uname -a
Linux ubuntu 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

```
```

root@ubuntu:/# ls -al  /
total 124
drwxr-xr-x  24 root root  4096 Oct  8 19:59 .
drwxr-xr-x  24 root root  4096 Oct  8 19:59 ..
drwxr-xr-x   2 root root  4096 Aug 27 07:53 bin
drwxr-xr-x   3 root root 12288 Aug 27 07:54 boot
drwxr-xr-x   2 root root  4096 May  8  2012 cdrom
drwxr-xr-x  15 root root  4080 Oct 10 19:57 dev
drwxr-xr-x 131 root root 12288 Oct  7 20:45 etc
-rw-r--r--   1 root root     0 Sep 11 20:16 forcefsch
drwxr-xr-x   3 root root  4096 May  8  2012 home
lrwxrwxrwx   1 root root    33 Aug 21 21:56 initrd.img -> boot/initrd.img-3.13.0-35-generic
lrwxrwxrwx   1 root root    33 Aug 14 17:17 initrd.img.old -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  24 root root  4096 Aug 29 07:56 lib
drwx------ 349 root root 24576 May  8  2012 lost+found
drwxr-xr-x   4 root root  4096 Sep  9  2013 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   4 root root  4096 Apr  6  2014 opt
dr-xr-xr-x 196 root root     0 Oct  8 11:18 proc
drwx------   9 root root  4096 Sep  1 11:51 root
drwxr-xr-x  23 root root   740 Oct  9 17:44 run
drwxr-xr-x   2 root root 12288 Aug 29 07:55 sbin
drwxr-xr-x   2 root root  4096 Apr 23  2012 srv
dr-xr-xr-x  13 root root     0 Oct  8 11:18 sys
drwxrwxrwt   8 root root  4096 Sep 18 07:13 tmp
drwxrwxrwt   9 root root  4096 Sep  6 23:20 tmp_old
drwx------   4 root root  4096 Oct  8 19:59 .Trash-0
drwxr-xr-x  10 root root  4096 Apr 23  2012 usr
drwxr-xr-x  15 root root  4096 Oct 12  2013 var
lrwxrwxrwx   1 root root    30 Aug 21 21:56 vmlinuz -> boot/vmlinuz-3.13.0-35-generic
lrwxrwxrwx   1 root root    30 Aug 14 17:17 vmlinuz.old -> boot/vmlinuz-3.13.0-34-generic

```
```

root@ubuntu:/# dpkg -l | grep linux-
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
ii  linux-headers-3.11.0-13                                     3.11.0-13.20                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-13-generic                             3.11.0-13.20                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-14                                     3.11.0-14.21                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-14-generic                             3.11.0-14.21                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-15                                     3.11.0-15.25                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic                             3.11.0-15.25                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-17                                     3.11.0-17.31                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-17-generic                             3.11.0-17.31                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-18                                     3.11.0-18.32                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-18-generic                             3.11.0-18.32                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-19                                     3.11.0-19.33                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-19-generic                             3.11.0-19.33                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.11.0-20                                     3.11.0-20.34                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-20-generic                             3.11.0-20.34                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-26                                     3.13.0-26.48                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-26-generic                             3.13.0-26.48                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-27                                     3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                             3.13.0-27.50                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-29                                     3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                             3.13.0-29.53                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                             3.13.0-30.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-31                                     3.13.0-31.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-31-generic                             3.13.0-31.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-33                                     3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                             3.13.0-33.58                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                                      3.8.0-32.47                                         all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-generic                                       3.13.0.35.42                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                                   3.13.0.35.42                                        i386         Transitional package
rc  linux-image-3.11.0-12-generic                               3.11.0-12.19                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-13-generic                               3.11.0-13.20                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-14-generic                               3.11.0-14.21                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-15-generic                               3.11.0-15.25                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-17-generic                               3.11.0-17.31                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-18-generic                               3.11.0-18.32                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-19-generic                               3.11.0-19.33                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.11.0-20-generic                               3.11.0-20.34                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-26-generic                               3.13.0-26.48                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-27-generic                               3.13.0-27.50                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-29-generic                               3.13.0-29.53                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-31-generic                               3.13.0-31.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic                               3.13.0-33.58                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-23-generic-pae                            3.2.0-23.36                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic-pae                            3.2.0-24.39                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-25-generic-pae                            3.2.0-25.40                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-26-generic-pae                            3.2.0-26.41                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-27-generic-pae                            3.2.0-27.43                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic-pae                            3.2.0-29.46                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-30-generic-pae                            3.2.0-30.48                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-generic-pae                            3.2.0-31.50                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae                            3.2.0-32.51                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae                            3.2.0-33.52                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae                            3.2.0-34.53                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae                            3.2.0-35.55                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae                            3.2.0-37.58                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic-pae                            3.2.0-38.61                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic-pae                            3.2.0-39.62                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic-pae                            3.2.0-40.64                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic-pae                            3.2.0-41.66                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic-pae                            3.2.0-43.68                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-44-generic-pae                            3.2.0-44.69                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-45-generic-pae                            3.2.0-45.70                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic-pae                            3.2.0-48.74                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic-pae                            3.2.0-49.75                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic-pae                            3.2.0-51.77                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic-pae                            3.2.0-52.78                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae                            3.2.0-53.81                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-40-generic                                3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-31-generic                                3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-32-generic                                3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                         3.11.0-12.19                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-13-generic                         3.11.0-13.20                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-14-generic                         3.11.0-14.21                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-15-generic                         3.11.0-15.25                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-17-generic                         3.11.0-17.31                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-18-generic                         3.11.0-18.32                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic                         3.11.0-19.33                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-20-generic                         3.11.0-20.34                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-26-generic                         3.13.0-26.48                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                         3.13.0-27.50                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                         3.13.0-29.53                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                         3.13.0-30.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-31-generic                         3.13.0-31.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic                         3.13.0-33.58                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-40-generic                          3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic                          3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-32-generic                          3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.35.42                                        i386         Generic Linux kernel image
ii  linux-image-generic-pae                                     3.13.0.35.42                                        i386         Transitional package
ii  linux-libc-dev:i386                                         3.13.0-35.62                                        i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies

```

Okay is that all right and can I do the reboot or do we have more to go.
I mean do I go back to the previous code and umount or do we leave it open before rebooting?

This is interesting. :-)

---

### Post by Bashing-om on 2014-10-11
lcbmac; Yeah.

Interesting ! ..the system from " uname -a " says booting the "3.13.0-32-generic" ; BUT, the boot path says :
> 
lrwxrwxrwx   1 root root    30 Aug 21 21:56 vmlinuz -> boot/vmlinuz-3.13.0-35-generic


We will do all our work from the CHroot environment to get the old kernels removed , permissions reset for /home, sources.list file corrected.

Then see about booting.

so back to permissions/access, still need to know about the file .ICEauthority.
```

ls -al .ICEauthority

``` try'n to keep my head on straight.

[INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay this is it.

```

root@ubuntu:/# ls -al .ICEauthority
ls: cannot access .ICEauthority: No such file or directory

```

---

### Post by Bashing-om on 2014-10-11
lcbmac; Humm;

I do not know YET, what we are going to do about the missing .Xauthority and .ICEauthority files.

But for now, let's focus on removing the old kernels, and gettin us some operating head room !
in the CHroot do:
```

dpkg -P linux-image-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic
dpkg -P linux-image-extra-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic
dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}
dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic

```
Once these are run I want to see an update of what is and then we remove all those 'rc' flagged files.
```

dpkg -l | grep linux-

```

One thing at a time is all my little mind can cope with reliably .. we get to the others in due time.

[INDENT][INDENT]one small step forward for nordic
[INDENT][INDENT][INDENT]a huge step forward for Bashing-om
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

okay so here is what we have so far
```

root@ubuntu:/# dpkg -P linux-image-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic
dpkg: dependency problems prevent removal of linux-image-3.11.0-13-generic:
 linux-image-extra-3.11.0-13-generic depends on linux-image-3.11.0-13-generic.

dpkg: error processing package linux-image-3.11.0-13-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-14-generic:
 linux-image-extra-3.11.0-14-generic depends on linux-image-3.11.0-14-generic.

dpkg: error processing package linux-image-3.11.0-14-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-15-generic:
 linux-image-extra-3.11.0-15-generic depends on linux-image-3.11.0-15-generic.

dpkg: error processing package linux-image-3.11.0-15-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-17-generic:
 linux-image-extra-3.11.0-17-generic depends on linux-image-3.11.0-17-generic.

dpkg: error processing package linux-image-3.11.0-17-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-18-generic:
 linux-image-extra-3.11.0-18-generic depends on linux-image-3.11.0-18-generic.

dpkg: error processing package linux-image-3.11.0-18-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-19-generic:
 linux-image-extra-3.11.0-19-generic depends on linux-image-3.11.0-19-generic.

dpkg: error processing package linux-image-3.11.0-19-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-20-generic:
 linux-image-extra-3.11.0-20-generic depends on linux-image-3.11.0-20-generic.

dpkg: error processing package linux-image-3.11.0-20-generic (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-image-3.11.0-24-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.11.0-26-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.11.0-27-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.11.0-29-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.11.0-30-generic which isn't installed
dpkg: warning: ignoring request to remove linux-image-3.11.0-31-generic which isn't installed
Errors were encountered while processing:
 linux-image-3.11.0-13-generic
 linux-image-3.11.0-14-generic
 linux-image-3.11.0-15-generic
 linux-image-3.11.0-17-generic
 linux-image-3.11.0-18-generic
 linux-image-3.11.0-19-generic
 linux-image-3.11.0-20-generic

```

```

root@ubuntu:/# dpkg -P linux-image-extra-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```
```

root@ubuntu:/# dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}
dpkg: dependency problems prevent removal of linux-headers-3.11.0-13:
 linux-headers-3.11.0-13-generic depends on linux-headers-3.11.0-13.

dpkg: error processing package linux-headers-3.11.0-13 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-14:
 linux-headers-3.11.0-14-generic depends on linux-headers-3.11.0-14.

dpkg: error processing package linux-headers-3.11.0-14 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-15:
 linux-headers-3.11.0-15-generic depends on linux-headers-3.11.0-15.

dpkg: error processing package linux-headers-3.11.0-15 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-17:
 linux-headers-3.11.0-17-generic depends on linux-headers-3.11.0-17.

dpkg: error processing package linux-headers-3.11.0-17 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-18:
 linux-headers-3.11.0-18-generic depends on linux-headers-3.11.0-18.

dpkg: error processing package linux-headers-3.11.0-18 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-19:
 linux-headers-3.11.0-19-generic depends on linux-headers-3.11.0-19.

dpkg: error processing package linux-headers-3.11.0-19 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-20:
 linux-headers-3.11.0-20-generic depends on linux-headers-3.11.0-20.

dpkg: error processing package linux-headers-3.11.0-20 (--purge):
 dependency problems - not removing
dpkg: warning: ignoring request to remove linux-headers-3.11.0-24 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-3.11.0-26 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-3.11.0-27 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-3.11.0-29 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-3.11.0-30 which isn't installed
dpkg: warning: ignoring request to remove linux-headers-3.11.0-31 which isn't installed
Errors were encountered while processing:
 linux-headers-3.11.0-13
 linux-headers-3.11.0-14
 linux-headers-3.11.0-15
 linux-headers-3.11.0-17
 linux-headers-3.11.0-18
 linux-headers-3.11.0-19
 linux-headers-3.11.0-20

```

```

root@ubuntu:/# dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19,20,24,26,27,29,30,31}-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```

```

root@ubuntu:/# dpkg -l | grep linux-
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
pi  linux-headers-3.11.0-13                                     3.11.0-13.20                                        all          Header files related to Linux kernel version 3.11.0
pi  linux-headers-3.11.0-13-generic                             3.11.0-13.20                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-14                                     3.11.0-14.21                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-14-generic                             3.11.0-14.21                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-15                                     3.11.0-15.25                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic                             3.11.0-15.25                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-17                                     3.11.0-17.31                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-17-generic                             3.11.0-17.31                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-18                                     3.11.0-18.32                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-18-generic                             3.11.0-18.32                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-19                                     3.11.0-19.33                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-19-generic                             3.11.0-19.33                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-20                                     3.11.0-20.34                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-20-generic                             3.11.0-20.34                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-26                                     3.13.0-26.48                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-26-generic                             3.13.0-26.48                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-27                                     3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                             3.13.0-27.50                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-29                                     3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                             3.13.0-29.53                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                             3.13.0-30.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-31                                     3.13.0-31.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-31-generic                             3.13.0-31.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-33                                     3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                             3.13.0-33.58                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                                      3.8.0-32.47                                         all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-generic                                       3.13.0.35.42                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                                   3.13.0.35.42                                        i386         Transitional package
rc  linux-image-3.11.0-12-generic                               3.11.0-12.19                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-13-generic                               3.11.0-13.20                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-14-generic                               3.11.0-14.21                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-15-generic                               3.11.0-15.25                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-17-generic                               3.11.0-17.31                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-18-generic                               3.11.0-18.32                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-19-generic                               3.11.0-19.33                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-20-generic                               3.11.0-20.34                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-26-generic                               3.13.0-26.48                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-27-generic                               3.13.0-27.50                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-29-generic                               3.13.0-29.53                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-31-generic                               3.13.0-31.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic                               3.13.0-33.58                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-23-generic-pae                            3.2.0-23.36                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic-pae                            3.2.0-24.39                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-25-generic-pae                            3.2.0-25.40                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-26-generic-pae                            3.2.0-26.41                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-27-generic-pae                            3.2.0-27.43                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic-pae                            3.2.0-29.46                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-30-generic-pae                            3.2.0-30.48                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-generic-pae                            3.2.0-31.50                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae                            3.2.0-32.51                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae                            3.2.0-33.52                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae                            3.2.0-34.53                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae                            3.2.0-35.55                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae                            3.2.0-37.58                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic-pae                            3.2.0-38.61                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic-pae                            3.2.0-39.62                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic-pae                            3.2.0-40.64                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic-pae                            3.2.0-41.66                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic-pae                            3.2.0-43.68                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-44-generic-pae                            3.2.0-44.69                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-45-generic-pae                            3.2.0-45.70                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic-pae                            3.2.0-48.74                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic-pae                            3.2.0-49.75                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic-pae                            3.2.0-51.77                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic-pae                            3.2.0-52.78                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae                            3.2.0-53.81                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-40-generic                                3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-31-generic                                3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-32-generic                                3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                         3.11.0-12.19                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-extra-3.11.0-13-generic                         3.11.0-13.20                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-14-generic                         3.11.0-14.21                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-15-generic                         3.11.0-15.25                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-17-generic                         3.11.0-17.31                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-18-generic                         3.11.0-18.32                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic                         3.11.0-19.33                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-20-generic                         3.11.0-20.34                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-26-generic                         3.13.0-26.48                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                         3.13.0-27.50                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                         3.13.0-29.53                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                         3.13.0-30.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-31-generic                         3.13.0-31.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic                         3.13.0-33.58                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-40-generic                          3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic                          3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-32-generic                          3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.35.42                                        i386         Generic Linux kernel image
ii  linux-image-generic-pae                                     3.13.0.35.42                                        i386         Transitional package
ii  linux-libc-dev:i386                                         3.13.0-35.62                                        i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies
root@ubuntu:/# 

```


I see a few problem but i thought ir best you see them to above.

---

### Post by Bashing-om on 2014-10-11
lcbmac; Hummm ....

New one on me, maybe I got the horse before the cart ?

Try from the CHroot:
```

dpkg -P linux-image-extra-3.11.0-14-generic 

``` as a test to see what results.

That last totally unexpected;
[INDENT][INDENT][INDENT]I hate when that happens
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Alright here are hte results

```

root@ubuntu:/# dpkg -P linux-image-extra-3.11.0-14-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```

---

### Post by Bashing-om on 2014-10-11
lcbmac; Yikes !

I am stuck hard ; I never once anticipated this kind of a hurdle.

What is the world ! How can it be that there is any relation between:
> 
dpkg -P [color=green]linux-image-extra-3.11.0-14[/color]-generic

and the resulting error condition:
> 
dpkg: unrecoverable fatal error, aborting:
 reading files list for package '[color=red]linux-headers-3.13.0-24[/color]': Input/output error

2 completely different versions !

Inconsistent control files ?
I just no longer know ! .. are we really looking at hard disk failure " Input/output error"

Let's poke at it and see what now results :
```

apt-get purge linux-{headers,image}-3.11.0-{14,15}-generic linux-headers-3.11.0-{14,15} linux-image-extra

```

As I hope we are not digging ourselves in deeper !

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay so here are the results

```

root@ubuntu:/# dpkg -P linux-image-extra-3.11.0-14-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```

Okay so I did as what was told here are the results
[/code]
root@ubuntu:/# apt-get purge linux-{headers,image}-3.11.0-{14,15}-generic linux-headers-3.11.0-{14,15} linux-image-extra
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# sudo dpkg

dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !
[/code]


I have stopped there as I am not sure is i should carry on from here

---

### Post by Bashing-om on 2014-10-11
lcbmac;

Well, no worse for wear, that is one good thing.
Still, not sure how best to proceed. But, let's take the package manager's advise and see what results.
```

dpkg --configure -a

```

see if we get additional hints as to where the real problem is.

And I do have a couple of other ideas of what might be productive to try.
1st though I must see that the sources.list file is up to it.

see what " --configure " will tell us.

[INDENT][INDENT]this time, I really do not know
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay here it is

```

root@ubuntu:/# dpkg --configure -a
root@ubuntu:/# 

```

---

### Post by Bashing-om on 2014-10-11
lcbmac; shucks, 

Did not tell us nothing !

OK, plan B, let me have a few to check what you have for a sources.list,
I know at the lest that the 1st line requires 'commenting out' let me check that the remainder is usable,

Be back in a bit. So, hold your horses.

[INDENT][INDENT]yukkie poo
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-11
lcbmac; OK,

All I see that might be considered missing in the sources.list file are entries for 'multverse, partners, and extras ', none of which concern us at this time.

All that is required to do the next in my order of operations is to edit the file and "comment out" the 1st line .
```

cp /etc/apt/sources.list /etc/apt/sources.list-11oct2014
gedit /etc/apt/sources.list

```

The editor opens the file, place a "#" character at the start of the line referencing the CDrom
such that it looks like this:
```

#deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

```
save the file and exit back to terminal.

If this goes well and when completed, we next remove the control files and rebuild them, see if that helps us in removing the old kernels.

[INDENT][INDENT]now inquiring minds want to know
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

okayh here is what has happend

```

root@ubuntu:/# cp /etc/apt/sources.list /etc/apt/sources.list-11oct2014
root@ubuntu:/# gedit /etc/apt/sources.list
No protocol specified

** (gedit:16876): WARNING **: Could not open X display
No protocol specified
error: XDG_RUNTIME_DIR not set in the environment.

(gedit:16876): Gtk-WARNING **: cannot open display: :0

```

lol this machine is on its own mission.

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Tel me does this restart the installation after 30minutes
cause it has started

---

### Post by Bashing-om on 2014-10-11
lcbmac; sorry;

Again I was not seeing the tree for the forest. I failed to think it through.
Start 2 instances of a terminal.
You can run graphical applications within a chroot, but you need to provide an X server for them to run in first. The easiest way to do this is to set the display of the chroot system to be identical to the root display of your system's main X server and provide access to it.
In other words, in the chroot - in that 1st terminal - shell type:
```

export DISPLAY=:0.0

```
And in the system shell - this is the 2nd terminal - type: 
```

xhost +

```
Any X command you type will now ( gedit ) gets its own window as you're used to, but as it is running inside the chroot jail it will not be able to see your normal file system. 

Now I expect 'gedit' will run in the display.

[INDENT][INDENT]I do get tunnel vision and scatter brained, huh ?
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay here are the 2 seperate Codes done

```

root@ubuntu:/# export DISPLAY=:0.0

```

```

ubuntu@ubuntu:~$ xhost +
access control disabled, clients can connect from any host

```

Is that right??

---

### Post by Bashing-om on 2014-10-11
lcbmac; Yeah,

I think so. What now happens in the CHroot terminal with:
```

gedit /etc/apt/sources.list

``` been some time since I have been in a chroot and tried to use a GUI application; but I think should work.

[INDENT][INDENT]maybe yes ( are we having fun now ?) 
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-11
Hi Bashing-om

Okay this is what comes up on a Text Editor

Sources.list

deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty main restricted universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security main restricted universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates main restricted universe

---

### Post by Bashing-om on 2014-10-11
lcbmac; Yepper !

Put a '#' at the start of that 1st line, and save the file and exit back to the CHroot terminal.

Now let's test the waters with a toe, before jumping in. Get an idea of the overall status of the package manager:
```

apt-get update
apt-get upgrade

```

Maybe get some hints on where the problems lie.

[INDENT][INDENT]no step for a stepper
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-12
Hi Bashing-om

Here is the latest results for the codes

```

root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty Release.gpg
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty Release
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_GB
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.ubuntu.com trusty InRelease 
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Ign http://archive.ubuntu.com trusty-updates InRelease    
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]             
Hit http://archive.ubuntu.com trusty Release.gpg                               
Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]             
Hit http://archive.ubuntu.com trusty Release                                   
Get:4 http://archive.ubuntu.com trusty-updates Release [59.7 kB]               
Get:5 http://security.ubuntu.com trusty-security/main i386 Packages [142 kB]   
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Get:6 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:7 http://security.ubuntu.com trusty-security/universe i386 Packages [49.7 kB]
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/main Translation-en_GB                    
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en_GB              
Get:8 http://security.ubuntu.com trusty-security/main Translation-en [72.4 kB] 
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Hit http://archive.ubuntu.com trusty/universe Translation-en_GB                
Get:9 http://archive.ubuntu.com trusty-updates/main i386 Packages [333 kB]     
Get:10 http://security.ubuntu.com trusty-security/restricted Translation-en [14 B]
Get:11 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:12 http://security.ubuntu.com trusty-security/universe Translation-en [29.0 kB]
Get:13 http://archive.ubuntu.com trusty-updates/universe i386 Packages [211 kB]
Get:14 http://archive.ubuntu.com trusty-updates/main Translation-en [151 kB]   
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Get:15 http://archive.ubuntu.com trusty-updates/universe Translation-en [106 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,221 kB in 1min 3s (19.3 kB/s)                                        
W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

root@ubuntu:/# apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# sudo dpkg --configure -a
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-headers-generic linux-headers-generic-pae linux-image-generic
  linux-image-generic-pae
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bash bsdutils
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra cups
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common dbus dbus-x11 evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts file
  firefox firefox-globalmenu firefox-locale-en firefox-locale-zh-hans
  fonts-droid fonts-opensymbol gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-gudev-1.0 icedtea-7-jre-jamvm
  language-selector-common language-selector-gnome libapt-inst1.5
  libapt-pkg4.12 libblkid1 libcamel-1.2-45 libcups2 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libcurl3-nss libdbus-1-3
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libgcrypt11
  libgudev-1.0-0 liblua5.1-0 libmagic1 libmount1 libnspr4 libnspr4-0d libnss3
  libnss3-1d libnss3-nssdb liboxideqt-qmlplugin liboxideqtcore0 libpam-systemd
  libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-java-common libreoffice-kde libreoffice-l10n-tr libreoffice-math
  libreoffice-officebean libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-presenter-console
  libreoffice-report-builder-bin libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb libreoffice-style-human libreoffice-style-oxygen
  libreoffice-style-tango libreoffice-writer libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 libunity-control-center1
  libuuid1 libvncserver0 linux-firmware linux-libc-dev man-db mount
  myspell-en-gb myspell-en-za mythes-en-us nvidia-common openjdk-7-jdk
  openjdk-7-jre openjdk-7-jre-headless openoffice.org-hyphenation
  oxideqt-codecs-extra procmail python-apport python-numpy
  python-problem-report python3-apport python3-distupgrade
  python3-problem-report python3-uno rsyslog systemd-services thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk udev unity-control-center uno-libs3 ure
  util-linux uuid-runtime
144 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 211 MB/321 MB of archives.
After this operation, 22.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mount i386 2.20.1-5.1ubuntu20.2 [113 kB]
Get:2 http://security.ubuntu.com/ubuntu/ trusty-security/main bash i386 4.3-7ubuntu1.5 [549 kB]
Get:3 http://archive.ubuntu.com/ubuntu/ trusty-updates/main util-linux i386 2.20.1-5.1ubuntu20.2 [452 kB]
Get:4 http://security.ubuntu.com/ubuntu/ trusty-security/main libapt-pkg4.12 i386 1.0.1ubuntu2.5 [634 kB]
Get:5 http://archive.ubuntu.com/ubuntu/ trusty-updates/main bsdutils i386 1:2.20.1-5.1ubuntu20.2 [34.0 kB]
Get:6 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.2 [11.5 kB]
Get:7 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libblkid1 i386 2.20.1-5.1ubuntu20.2 [67.4 kB]
Get:8 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libmount1 i386 2.20.1-5.1ubuntu20.2 [59.7 kB]
Get:9 http://security.ubuntu.com/ubuntu/ trusty-security/main apt i386 1.0.1ubuntu2.5 [953 kB]
Get:10 http://archive.ubuntu.com/ubuntu/ trusty-updates/main udev i386 204-5ubuntu20.7 [737 kB]
Get:11 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libudev1 i386 204-5ubuntu20.7 [34.2 kB]
Get:12 http://security.ubuntu.com/ubuntu/ trusty-security/main libapt-inst1.5 i386 1.0.1ubuntu2.5 [58.3 kB]
Get:13 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-selector-gnome all 0.129.3 [18.6 kB]
Get:14 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-login0 i386 204-5ubuntu20.7 [27.1 kB]
Get:15 http://security.ubuntu.com/ubuntu/ trusty-security/main file i386 1:5.14-2ubuntu3.2 [18.4 kB]
Get:16 http://security.ubuntu.com/ubuntu/ trusty-security/main libmagic1 i386 1:5.14-2ubuntu3.2 [185 kB]
Get:17 http://archive.ubuntu.com/ubuntu/ trusty-updates/main language-selector-common all 0.129.3 [204 kB]
Get:18 http://security.ubuntu.com/ubuntu/ trusty-security/main libdbus-1-3 i386 1.6.18-0ubuntu4.2 [132 kB]
Get:19 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libpam-systemd i386 204-5ubuntu20.7 [25.3 kB]
Get:20 http://security.ubuntu.com/ubuntu/ trusty-security/main dbus i386 1.6.18-0ubuntu4.2 [233 kB]
Get:21 http://archive.ubuntu.com/ubuntu/ trusty-updates/main systemd-services i386 204-5ubuntu20.7 [198 kB]
Get:22 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-daemon0 i386 204-5ubuntu20.7 [9,750 B]
Get:23 http://archive.ubuntu.com/ubuntu/ trusty-updates/main man-db i386 2.6.7.1-1ubuntu1 [852 kB]
Get:24 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3-gnutls i386 7.35.0-1ubuntu2.1 [166 kB]
Get:25 http://security.ubuntu.com/ubuntu/ trusty-security/universe chromium-browser-l10n all 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [2,975 kB]
Get:26 http://archive.ubuntu.com/ubuntu/ trusty-updates/main fonts-droid all 1:4.3-3ubuntu1.1 [3,040 kB]
Get:27 http://security.ubuntu.com/ubuntu/ trusty-security/universe libnspr4-0d i386 2:4.10.7-0ubuntu0.14.04.1 [6,586 B]
Get:28 http://security.ubuntu.com/ubuntu/ trusty-security/main libnspr4 i386 2:4.10.7-0ubuntu0.14.04.1 [111 kB]
Get:29 http://security.ubuntu.com/ubuntu/ trusty-security/main libnss3-nssdb all 2:3.17.1-0ubuntu0.14.04.1 [10.6 kB]
Get:30 http://security.ubuntu.com/ubuntu/ trusty-security/main libnss3-1d i386 2:3.17.1-0ubuntu0.14.04.1 [9,304 B]
Get:31 http://security.ubuntu.com/ubuntu/ trusty-security/main libnss3 i386 2:3.17.1-0ubuntu0.14.04.1 [1,056 kB]
Get:32 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libgudev-1.0-0 i386 1:204-5ubuntu20.7 [13.8 kB]
Get:33 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libsystemd-journal0 i386 204-5ubuntu20.7 [53.9 kB]
Get:34 http://archive.ubuntu.com/ubuntu/ trusty-updates/main uuid-runtime i386 2.20.1-5.1ubuntu20.2 [12.1 kB]
Get:35 http://security.ubuntu.com/ubuntu/ trusty-security/universe chromium-codecs-ffmpeg-extra i386 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [837 kB]
Get:36 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.5 [9,098 B]
Get:37 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python3-apport all 2.14.1-0ubuntu3.5 [74.9 kB]
Get:38 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apport all 2.14.1-0ubuntu3.5 [179 kB]
Get:39 http://archive.ubuntu.com/ubuntu/ trusty-updates/main apport-gtk all 2.14.1-0ubuntu3.5 [9,504 B]
Get:40 http://archive.ubuntu.com/ubuntu/ trusty-updates/main gir1.2-gudev-1.0 i386 1:204-5ubuntu20.7 [5,490 B]
Get:41 http://archive.ubuntu.com/ubuntu/ trusty-updates/main libunity-control-center1 i386 14.04.3+14.04.20140922-0ubuntu1 [80.7 kB]
Get:42 http://archive.ubuntu.com/ubuntu/ trusty-updates/main myspell-en-gb all 1:4.2.1-0ubuntu1.1 [210 kB]
Get:43 http://security.ubuntu.com/ubuntu/ trusty-security/universe chromium-browser i386 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [46.7 MB]
Get:44 http://archive.ubuntu.com/ubuntu/ trusty-updates/main myspell-en-za all 1:4.2.1-0ubuntu1.1 [233 kB]
Get:45 http://archive.ubuntu.com/ubuntu/ trusty-updates/main mythes-en-us all 1:4.2.1-0ubuntu1.1 [3,024 kB]
Get:46 http://archive.ubuntu.com/ubuntu/ trusty-updates/main openoffice.org-hyphenation all 0.7.1 [192 kB]
Get:47 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-problem-report all 2.14.1-0ubuntu3.5 [9,020 B]
Get:48 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-apport all 2.14.1-0ubuntu3.5 [74.8 kB]
Get:49 http://archive.ubuntu.com/ubuntu/ trusty-updates/main python-numpy i386 1:1.8.2-0ubuntu0.1 [1,586 kB]
Get:50 http://archive.ubuntu.com/ubuntu/ trusty-updates/main unity-control-center i386 14.04.3+14.04.20140922-0ubuntu1 [722 kB]
Get:51 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3 i386 7.35.0-1ubuntu2.1 [174 kB]
Get:52 http://security.ubuntu.com/ubuntu/ trusty-security/main libcurl3-nss i386 7.35.0-1ubuntu2.1 [177 kB]
Get:53 http://security.ubuntu.com/ubuntu/ trusty-security/main openjdk-7-jdk i386 7u65-2.5.2-3~14.04 [16.1 MB]
Get:54 http://security.ubuntu.com/ubuntu/ trusty-security/main icedtea-7-jre-jamvm i386 7u65-2.5.2-3~14.04 [425 kB]
Get:55 http://security.ubuntu.com/ubuntu/ trusty-security/main openjdk-7-jre i386 7u65-2.5.2-3~14.04 [179 kB]
Get:56 http://security.ubuntu.com/ubuntu/ trusty-security/main openjdk-7-jre-headless i386 7u65-2.5.2-3~14.04 [41.3 MB]
Get:57 http://security.ubuntu.com/ubuntu/ trusty-security/main libvncserver0 i386 0.9.9+dfsg-1ubuntu1.1 [163 kB]
Get:58 http://security.ubuntu.com/ubuntu/ trusty-security/main apt-utils i386 1.0.1ubuntu2.5 [172 kB]
Get:59 http://security.ubuntu.com/ubuntu/ trusty-security/main rsyslog i386 7.4.4-1ubuntu2.3 [351 kB]
Get:60 http://security.ubuntu.com/ubuntu/ trusty-security/main apt-transport-https i386 1.0.1ubuntu2.5 [25.4 kB]
Get:61 http://security.ubuntu.com/ubuntu/ trusty-security/main dbus-x11 i386 1.6.18-0ubuntu4.2 [18.5 kB]
Get:62 http://security.ubuntu.com/ubuntu/ trusty-security/main firefox i386 32.0.3+build1-0ubuntu0.14.04.1 [34.4 MB]
Get:63 http://security.ubuntu.com/ubuntu/ trusty-security/main firefox-globalmenu i386 32.0.3+build1-0ubuntu0.14.04.1 [8,326 B]
Get:64 http://security.ubuntu.com/ubuntu/ trusty-security/main firefox-locale-en i386 32.0.3+build1-0ubuntu0.14.04.1 [601 kB]
Get:65 http://security.ubuntu.com/ubuntu/ trusty-security/main firefox-locale-zh-hans i386 32.0.3+build1-0ubuntu0.14.04.1 [397 kB]
Get:66 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-firmware all 1.127.7 [20.4 MB]
Get:67 http://security.ubuntu.com/ubuntu/ trusty-security/main linux-libc-dev i386 3.13.0-37.64 [800 kB]
Get:68 http://security.ubuntu.com/ubuntu/ trusty-security/main thunderbird-locale-en i386 1:31.1.2+build1-0ubuntu0.14.04.1 [346 kB]
Get:69 http://security.ubuntu.com/ubuntu/ trusty-security/main thunderbird i386 1:31.1.2+build1-0ubuntu0.14.04.1 [27.8 MB]
Get:70 http://security.ubuntu.com/ubuntu/ trusty-security/main thunderbird-gnome-support i386 1:31.1.2+build1-0ubuntu0.14.04.1 [8,534 B]
Get:71 http://security.ubuntu.com/ubuntu/ trusty-security/main thunderbird-globalmenu i386 1:31.1.2+build1-0ubuntu0.14.04.1 [8,224 B]
Get:72 http://security.ubuntu.com/ubuntu/ trusty-security/main thunderbird-locale-en-us all 1:31.1.2+build1-0ubuntu0.14.04.1 [9,960 B]
Fetched 211 MB in 1h 41min 39s (34.6 kB/s)                                     
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: unrecoverable fatal error, aborting:
 syntax error: unknown group 'landscape' in statoverride file
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by Bashing-om on 2014-10-12
lcbmac; Yuk .

This gets deeper and more convoluted the more we look into it.

This:
> 
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease

implies that you have not commented out the sources.list line. That must be done so we can proceed in any direction.

Now we also have issues the 'statoverride file ' to deal with in addition to the kernels that have been purged but still installed and kernels that have been removed but config files still remain;
Permissions for your /home directory;
missing .Xauthority and .ICEauthority files.

I will be doing my homework on the statoverride file, see if I can determine the why of that ...

[INDENT][INDENT]still getting our work cut out for us
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-19
Hi Bashing-om

I was wondering how things were coming around.
Sorry I have not been on but All of a sudden work has become quite Loooong. 18hrs a day long.

---

### Post by Bashing-om on 2014-10-19
lcbmac; Hey !

Not a problem as we work on this at your pace. One has to get some sleep sometimes else the mind does strange things !

I have lost track of where we are, and what is the current situation.

Can you now boot the system - even to a terminal from grub ?
OR are we still accessing the install from the CHroot environment ?
Have you edited out the CDrom entry in " /etc/apt/sources.list " ???


[INDENT][INDENT]poor folks have poor ways
[INDENT][INDENT][INDENT]but we can learn better
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-19
Hi Bashing-om

Okay to answer all the question one at a time

> Can you now boot the system - even to a terminal from grub?
 only to the grub not to the terminal

> OR are we still accessing the install from the CHroot environment ?
I'm still in the root system in Terminal

> Have you edited out the CDrom entry in " /etc/apt/sources.list " ???
No Because it didn't work

---

### Post by Bashing-om on 2014-10-19
lcbmac; OK;

My post #131, still refers.
> 
No Because it didn't work
 relays no usable info - where is the failure and in what aspect is the failure ?
2 open terminals, right ?

If there are continued problems to activate gedit ( you are running ubuntu,yes ? where gedit as the text editor is the default), I will reboot later this night and confirm the procedure.

The 1st thing is to get the package manager in a happy happy state.

[INDENT][INDENT]small steps
[INDENT][INDENT]even so, we will get there
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-20
Hi Bashing-om

yes the two terminals are open. here is the from the las to now and where we are now.

```

root@ubuntu:/# apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
root@ubuntu:/# sudo dpkg --configure -a
[code]

```
root@ubuntu:/# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.13.0-24 linux-headers-3.13.0-24-generic
  linux-image-3.13.0-24-generic linux-image-extra-3.13.0-24-generic
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-headers-generic linux-headers-generic-pae linux-image-generic
  linux-image-generic-pae
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bash bsdutils
  chromium-browser chromium-browser-l10n chromium-codecs-ffmpeg-extra cups
  cups-bsd cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common dbus dbus-x11 evolution-data-server
  evolution-data-server-common evolution-data-server-online-accounts file
  firefox firefox-globalmenu firefox-locale-en firefox-locale-zh-hans
  fonts-droid fonts-opensymbol gir1.2-ebook-1.2 gir1.2-ebookcontacts-1.2
  gir1.2-edataserver-1.2 gir1.2-gudev-1.0 icedtea-7-jre-jamvm
  language-selector-common language-selector-gnome libapt-inst1.5
  libapt-pkg4.12 libblkid1 libcamel-1.2-45 libcups2 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libcurl3-nss libdbus-1-3
  libebackend-1.2-7 libebook-1.2-14 libebook-contacts-1.2-0 libecal-1.2-16
  libedata-book-1.2-20 libedata-cal-1.2-23 libedataserver-1.2-18 libgcrypt11
  libgudev-1.0-0 liblua5.1-0 libmagic1 libmount1 libnspr4 libnspr4-0d libnss3
  libnss3-1d libnss3-nssdb liboxideqt-qmlplugin liboxideqtcore0 libpam-systemd
  libreoffice libreoffice-avmedia-backend-gstreamer libreoffice-base
  libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge
  libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress
  libreoffice-java-common libreoffice-kde libreoffice-l10n-tr libreoffice-math
  libreoffice-officebean libreoffice-ogltrans libreoffice-pdfimport
  libreoffice-presentation-minimizer libreoffice-presenter-console
  libreoffice-report-builder-bin libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb libreoffice-style-human libreoffice-style-oxygen
  libreoffice-style-tango libreoffice-writer libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 libunity-control-center1
  libuuid1 libvncserver0 linux-firmware linux-libc-dev man-db mount
  myspell-en-gb myspell-en-za mythes-en-us nvidia-common openjdk-7-jdk
  openjdk-7-jre openjdk-7-jre-headless openoffice.org-hyphenation
  oxideqt-codecs-extra procmail python-apport python-numpy
  python-problem-report python3-apport python3-distupgrade
  python3-problem-report python3-uno rsyslog systemd-services thunderbird
  thunderbird-globalmenu thunderbird-gnome-support thunderbird-locale-en
  thunderbird-locale-en-us ubuntu-drivers-common ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk udev unity-control-center uno-libs3 ure
  util-linux uuid-runtime
144 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 211 MB/321 MB of archives.
After this operation, 22.7 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main mount i386 2.20.1-5.1ubuntu20.2 [113 kB]
Get:2 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main bash i386 4.3-7ubuntu1.5 [549 kB]
Get:3 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main util-linux i386 2.20.1-5.1ubuntu20.2 [452 kB]
Get:4 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libapt-pkg4.12 i386 1.0.1ubuntu2.5 [634 kB]
Get:5 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main bsdutils i386 1:2.20.1-5.1ubuntu20.2 [34.0 kB]
Get:6 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libuuid1 i386 2.20.1-5.1ubuntu20.2 [11.5 kB]
Get:7 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libblkid1 i386 2.20.1-5.1ubuntu20.2 [67.4 kB]
Get:8 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libmount1 i386 2.20.1-5.1ubuntu20.2 [59.7 kB]
Get:9 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main apt i386 1.0.1ubuntu2.5 [953 kB]
Get:10 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main udev i386 204-5ubuntu20.7 [737 kB]
Get:11 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libudev1 i386 204-5ubuntu20.7 [34.2 kB]
Get:12 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libapt-inst1.5 i386 1.0.1ubuntu2.5 [58.3 kB]
Get:13 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main language-selector-gnome all 0.129.3 [18.6 kB]
Get:14 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libsystemd-login0 i386 204-5ubuntu20.7 [27.1 kB]
Get:15 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main file i386 1:5.14-2ubuntu3.2 [18.4 kB]
Get:16 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libmagic1 i386 1:5.14-2ubuntu3.2 [185 kB]
Get:17 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main language-selector-common all 0.129.3 [204 kB]
Get:18 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libdbus-1-3 i386 1.6.18-0ubuntu4.2 [132 kB]
Get:19 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libpam-systemd i386 204-5ubuntu20.7 [25.3 kB]
Get:20 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main dbus i386 1.6.18-0ubuntu4.2 [233 kB]
Get:21 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main systemd-services i386 204-5ubuntu20.7 [198 kB]
Get:22 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libsystemd-daemon0 i386 204-5ubuntu20.7 [9,750 B]
Get:23 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main man-db i386 2.6.7.1-1ubuntu1 [852 kB]
Get:24 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libcurl3-gnutls i386 7.35.0-1ubuntu2.1 [166 kB]
Get:25 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe chromium-browser-l10n all 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [2,975 kB]
Get:26 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main fonts-droid all 1:4.3-3ubuntu1.1 [3,040 kB]
Get:27 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe libnspr4-0d i386 2:4.10.7-0ubuntu0.14.04.1 [6,586 B]
Get:28 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnspr4 i386 2:4.10.7-0ubuntu0.14.04.1 [111 kB]
Get:29 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnss3-nssdb all 2:3.17.1-0ubuntu0.14.04.1 [10.6 kB]
Get:30 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnss3-1d i386 2:3.17.1-0ubuntu0.14.04.1 [9,304 B]
Get:31 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libnss3 i386 2:3.17.1-0ubuntu0.14.04.1 [1,056 kB]
Get:32 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libgudev-1.0-0 i386 1:204-5ubuntu20.7 [13.8 kB]
Get:33 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libsystemd-journal0 i386 204-5ubuntu20.7 [53.9 kB]
Get:34 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main uuid-runtime i386 2.20.1-5.1ubuntu20.2 [12.1 kB]
Get:35 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe chromium-codecs-ffmpeg-extra i386 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [837 kB]
Get:36 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python3-problem-report all 2.14.1-0ubuntu3.5 [9,098 B]
Get:37 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python3-apport all 2.14.1-0ubuntu3.5 [74.9 kB]
Get:38 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main apport all 2.14.1-0ubuntu3.5 [179 kB]
Get:39 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main apport-gtk all 2.14.1-0ubuntu3.5 [9,504 B]
Get:40 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main gir1.2-gudev-1.0 i386 1:204-5ubuntu20.7 [5,490 B]
Get:41 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main libunity-control-center1 i386 14.04.3+14.04.20140922-0ubuntu1 [80.7 kB]
Get:42 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main myspell-en-gb all 1:4.2.1-0ubuntu1.1 [210 kB]
Get:43 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/universe chromium-browser i386 37.0.2062.120-0ubuntu0.14.04.1~pkg1049 [46.7 MB]
Get:44 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main myspell-en-za all 1:4.2.1-0ubuntu1.1 [233 kB]
Get:45 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main mythes-en-us all 1:4.2.1-0ubuntu1.1 [3,024 kB]
Get:46 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main openoffice.org-hyphenation all 0.7.1 [192 kB]
Get:47 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python-problem-report all 2.14.1-0ubuntu3.5 [9,020 B]
Get:48 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python-apport all 2.14.1-0ubuntu3.5 [74.8 kB]
Get:49 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main python-numpy i386 1:1.8.2-0ubuntu0.1 [1,586 kB]
Get:50 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main unity-control-center i386 14.04.3+14.04.20140922-0ubuntu1 [722 kB]
Get:51 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libcurl3 i386 7.35.0-1ubuntu2.1 [174 kB]
Get:52 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libcurl3-nss i386 7.35.0-1ubuntu2.1 [177 kB]
Get:53 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main openjdk-7-jdk i386 7u65-2.5.2-3~14.04 [16.1 MB]
Get:54 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main icedtea-7-jre-jamvm i386 7u65-2.5.2-3~14.04 [425 kB]
Get:55 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main openjdk-7-jre i386 7u65-2.5.2-3~14.04 [179 kB]
Get:56 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main openjdk-7-jre-headless i386 7u65-2.5.2-3~14.04 [41.3 MB]
Get:57 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main libvncserver0 i386 0.9.9+dfsg-1ubuntu1.1 [163 kB]
Get:58 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main apt-utils i386 1.0.1ubuntu2.5 [172 kB]
Get:59 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main rsyslog i386 7.4.4-1ubuntu2.3 [351 kB]
Get:60 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main apt-transport-https i386 1.0.1ubuntu2.5 [25.4 kB]
Get:61 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main dbus-x11 i386 1.6.18-0ubuntu4.2 [18.5 kB]
Get:62 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main firefox i386 32.0.3+build1-0ubuntu0.14.04.1 [34.4 MB]
Get:63 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main firefox-globalmenu i386 32.0.3+build1-0ubuntu0.14.04.1 [8,326 B]
Get:64 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main firefox-locale-en i386 32.0.3+build1-0ubuntu0.14.04.1 [601 kB]
Get:65 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main firefox-locale-zh-hans i386 32.0.3+build1-0ubuntu0.14.04.1 [397 kB]
Get:66 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-firmware all 1.127.7 [20.4 MB]
Get:67 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main linux-libc-dev i386 3.13.0-37.64 [800 kB]
Get:68 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main thunderbird-locale-en i386 1:31.1.2+build1-0ubuntu0.14.04.1 [346 kB]
Get:69 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main thunderbird i386 1:31.1.2+build1-0ubuntu0.14.04.1 [27.8 MB]
Get:70 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main thunderbird-gnome-support i386 1:31.1.2+build1-0ubuntu0.14.04.1 [8,534 B]
Get:71 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main thunderbird-globalmenu i386 1:31.1.2+build1-0ubuntu0.14.04.1 [8,224 B]
Get:72 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main thunderbird-locale-en-us all 1:31.1.2+build1-0ubuntu0.14.04.1 [9,960 B]
Fetched 211 MB in 1h 41min 39s (34.6 kB/s)                                     
Extracting templates from packages: 100%
Preconfiguring packages ...
[/code]

That was the last of  of where we were. do I need to post what was from the other terminal??
Yes I am running Ubuntu and I have not ended the Chroot session yet.switched off yet ad we were still seeing where to go from here. :-)

Hope this helps

---

### Post by Bashing-om on 2014-10-20
lcbmac; Hey hey !

I did go back and confirm that the instruction to start gedit is proper. As you see it is .. There are warnings that you can safely ignore.

looks good !

I take it from that output that:
> 
deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)]/ trusty main restricted

has been "commented out" in " /etc/apt/sources.list" (??)

As such, then. let's move on:
show me once more:
```

ls -al .Xauthority
ls -al .ICEauthoruty
ls -al /home
ls -al /home/lcbmac

```

we get that straightened out, then see what we can do about starting the desk top from the install.
the :
> 
The following packages have been kept back:
  linux-headers-generic linux-headers-generic-pae linux-image-generic
  linux-image-generic-pae

will await the final cleanup.
[Fetched 211 MB in 1h 41min 39s (34.6 kB/s)] -> mighty slow internet connection ! always this slow ?

[INDENT][INDENT]still with small steps
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-20
Hi Bashing-om

Okay so here are the results

```

root@ubuntu:/# ls -al .Xauthority
ls: cannot access .Xauthority: No such file or directory

```
```

root@ubuntu:/# ls -al .ICEauthoruty
ls: cannot access .ICEauthoruty: No such file or directory

```
```

root@ubuntu:/# ls -al /home
total 24
drwxr-xr-x  4 root root  4096 Oct 11 23:15 .
drwxr-xr-x 24 root root  4096 Oct  8 19:59 ..
drwxr-xr-x 72 1000 1000 12288 Oct  2 11:48 nordic
drwx------  7 root root  4096 Oct 12 00:22 ubuntu

```
```

root@ubuntu:/# ls -al /home/lcbmac
ls: cannot access /home/lcbmac: No such file or directory

```

---

### Post by Bashing-om on 2014-10-20
lcbmac; As I flog my failing memory;

OK, with no .Xauthority or .ICEauthority files, I can see where "YOU" can not obtain the access to your desktop.

In my lapsing memory I failed to recall your system username.
What results:
```

ls -al /home/nordic

``` just to make sure of the next command: As
we know:
> 
root@ubuntu:/# ls -al /home ->> drwxr-xr-x 72 1000 1000 12288 Oct  2 11:48 nordic

is not the permissions we want to see.

We are going to fix that next.

[INDENT][INDENT][INDENT]small steps, small steps
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-20
Hi Bashing-om

Okay here are the new results

```

root@ubuntu:/# ls -al /home/nordic
total 660
drwxr-xr-x 72 1000 1000  12288 Oct  2 11:48 .
drwxr-xr-x  4 root root   4096 Oct 11 23:15 ..
drwx------  3 1000 1000   4096 May  8  2012 .adobe
-rw-rw-r--  1 1000 1000    109 Aug  2  2013 .apport-ignore.xml
drwxrwxr-x  2 1000 1000   4096 Jul  3  2012 .arduino
drwxrwxr-x  3 1000 1000   4096 Nov 22  2012 .avidemux
-rw-------  1 1000 1000   4348 Sep  7 00:09 .bash_history
-rw-r--r--  1 1000 1000    220 May  8  2012 .bash_logout
-rw-r--r--  1 1000 1000   3486 May  8  2012 .bashrc
drwx------ 62 1000 1000   4096 Sep 11 19:12 .cache
drwx------  3 1000 1000   4096 Sep 22  2013 .compiz
drwxrwxr-x  3 1000 1000   4096 May  8  2012 .compiz-1
drwx------ 44 1000 1000   4096 Sep  3 20:17 .config
drwx------  3 1000 1000   4096 May  8  2012 .dbus
drwxrwxr-x  5 1000 1000   4096 Jan 23  2014 .dc++
drwxr-xr-x  2 1000 1000   4096 Jul 18 06:18 Desktop
-rw-r--r--  1 1000 1000     34 Apr 19  2014 .dmrc
drwxr-xr-x 22 1000 1000  20480 Oct 12 00:22 Documents
drwx------  2 1000 1000   4096 Oct 15  2013 .dosbox
drwxr-xr-x  3 1000 1000  12288 Oct  2 11:30 Downloads
drwx------  3 1000 1000   4096 Sep  7  2013 .dropbox
drwx------  9 1000 1000   4096 Sep  7  2013 Dropbox
drwxr-xr-x  5 1000 1000   4096 Aug  2  2013 .dropbox-dist
drwxr-xr-x  3 1000 1000  20480 Jul 11  2013 dwhelper
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .eclipse
-rw-r--r--  1 1000 1000  11888 May  8  2012 .face
drwxrwxr-x  3 1000 1000   4096 May  9 11:05 .flush
drwxr-xr-x  2 1000 1000   4096 Sep  7  2013 fontconfig
drwxr-xr-x  2 1000 1000   4096 Sep  7  2013 .fontconfig
drwx------  5 1000 1000   4096 Sep 17 07:28 .gconf
drwx------  4 1000 1000   4096 May 13  2012 .gegl-0.0
drwxr-xr-x 22 1000 1000   4096 Jul 31  2013 .gimp-2.6
drwxr-xr-x 24 1000 1000   4096 May 12 13:24 .gimp-2.8
-rw-r-----  1 1000 1000      0 Apr 25 21:39 .gksu.lock
drwx------  5 1000 1000   4096 Aug 24 14:17 .gnome2
drwx------  2 1000 1000   4096 May 23  2012 .gnome2_private
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-08AFIW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-09I9FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-0AYZJW
-rw-------  1 1000 1000      0 Jul  9  2012 .goutputstream-0WH1GW
-rw-------  1 1000 1000      0 Dec 30  2012 .goutputstream-1SP7PW
-rw-------  1 1000 1000      0 Aug 24  2012 .goutputstream-1V6OJW
-rw-------  1 1000 1000      0 Jul 29  2012 .goutputstream-1Y87HW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-1Z0CIW
-rw-------  1 1000 1000      0 Jun  5  2012 .goutputstream-2PM3EW
-rw-------  1 1000 1000      0 Jul 21  2012 .goutputstream-2QPIHW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-38WYDW
-rw-------  1 1000 1000      0 May  8  2012 .goutputstream-3EVUDW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-3HE2HW
-rw-------  1 1000 1000      0 Jul 13  2012 .goutputstream-3RCQHW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-3V36GW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-4FI9YW
-rw-------  1 1000 1000      0 Jun 24  2012 .goutputstream-4ZS8FW
-rw-------  1 1000 1000      0 Sep  4  2012 .goutputstream-5AMAKW
-rw-------  1 1000 1000      0 Sep 15  2012 .goutputstream-64FZKW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-6NNSEW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-75XYLW
-rw-------  1 1000 1000      0 Aug 19  2012 .goutputstream-7PECJW
-rw-------  1 1000 1000      0 Aug  2  2012 .goutputstream-8IDJIW
-rw-------  1 1000 1000      0 Oct  4  2012 .goutputstream-8P6OLW
-rw-------  1 1000 1000      0 Dec  4  2012 .goutputstream-9JHPOW
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-9M0FEW
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-9UI8HW
-rw-------  1 1000 1000      0 Oct 10  2012 .goutputstream-A1Y3LW
-rw-------  1 1000 1000      0 Aug  8  2013 .goutputstream-AAWX1W
-rw-------  1 1000 1000      0 Aug 28  2012 .goutputstream-APBPJW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-BK3WDW
-rw-------  1 1000 1000      0 Jul 14  2012 .goutputstream-CAVEHW
-rw-------  1 1000 1000      0 Jun 14  2012 .goutputstream-CKD2FW
-rw-------  1 1000 1000      0 Jul 20  2012 .goutputstream-CQDHHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-CTXNYW
-rw-------  1 1000 1000      0 Oct 11  2012 .goutputstream-DEBTLW
-rw-------  1 1000 1000      0 May  9  2012 .goutputstream-DLRNDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-E5O9EW
-rw-------  1 1000 1000      0 Mar 20  2013 .goutputstream-E5PWTW
-rw-------  1 1000 1000      0 May 31  2012 .goutputstream-E7E6EW
-rw-------  1 1000 1000      0 Dec  6  2012 .goutputstream-EIF1OW
-rw-------  1 1000 1000      0 Jun 23  2013 .goutputstream-ENN0YW
-rw-------  1 1000 1000      0 Jun 15  2012 .goutputstream-F1EYFW
-rw-------  1 1000 1000      0 Aug 30  2013 .goutputstream-G4OO2W
-rw-------  1 1000 1000      0 Aug 12  2012 .goutputstream-GH02IW
-rw-------  1 1000 1000      0 Aug 23  2013 .goutputstream-GRYJ2W
-rw-------  1 1000 1000      0 Aug  3  2012 .goutputstream-GUW8HW
-rw-------  1 1000 1000      0 May 11  2012 .goutputstream-H7LSDW
-rw-------  1 1000 1000      0 May 27  2012 .goutputstream-HA47EW
-rw-------  1 1000 1000      0 Dec 29  2012 .goutputstream-HOBWPW
-rw-------  1 1000 1000      0 Dec 14  2012 .goutputstream-HXWHPW
-rw-------  1 1000 1000      0 Aug  4  2013 .goutputstream-I6VB1W
-rw-------  1 1000 1000      0 May 23  2012 .goutputstream-IOOUEW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-IPG4GW
-rw-------  1 1000 1000      0 Sep 12  2012 .goutputstream-IPMWKW
-rw-------  1 1000 1000      0 Jun  4  2012 .goutputstream-J0G0EW
-rw-------  1 1000 1000      0 Aug 13  2012 .goutputstream-JHSQIW
-rw-------  1 1000 1000      0 Jul 23  2012 .goutputstream-K0KWHW
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-KLXDYW
-rw-------  1 1000 1000      0 Sep  7  2013 .goutputstream-KTJO2W
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-L88HGW
-rw-------  1 1000 1000      0 Aug 29  2012 .goutputstream-M2LIJW
-rw-------  1 1000 1000      0 Jul  7  2012 .goutputstream-MCWCHW
-rw-------  1 1000 1000      0 Aug 10  2013 .goutputstream-MUAT1W
-rw-------  1 1000 1000      0 Jul  2  2013 .goutputstream-NDKQZW
-rw-------  1 1000 1000      0 Jul  4  2012 .goutputstream-OCK3GW
-rw-------  1 1000 1000      0 May 10  2012 .goutputstream-OFOODW
-rw-------  1 1000 1000      0 Jan 17  2013 .goutputstream-OM43QW
-rw-------  1 1000 1000      0 Feb  4  2013 .goutputstream-PCLSRW
-rw-------  1 1000 1000      0 Nov 26  2012 .goutputstream-PE8MOW
-rw-------  1 1000 1000      0 Sep  5  2013 .goutputstream-PN4M2W
-rw-------  1 1000 1000      0 Jun 16  2013 .goutputstream-Q7F9XW
-rw-------  1 1000 1000      0 Jun 25  2013 .goutputstream-R0DVYW
-rw-------  1 1000 1000      0 Aug  9  2012 .goutputstream-R2OPIW
-rw-------  1 1000 1000      0 Nov  9  2012 .goutputstream-RBE6MW
-rw-------  1 1000 1000      0 Jul 26  2012 .goutputstream-RGX3HW
-rw-------  1 1000 1000      0 Dec  9  2012 .goutputstream-RSK5OW
-rw-------  1 1000 1000      0 Jun 10  2012 .goutputstream-SE5RFW
-rw-------  1 1000 1000      0 May 22  2012 .goutputstream-SGYIEW
-rw-------  1 1000 1000      0 May 30  2013 .goutputstream-SIH5XW
-rw-------  1 1000 1000      0 Nov  5  2012 .goutputstream-SM25MW
-rw-------  1 1000 1000      0 Jun 29  2012 .goutputstream-SNBBGW
-rw-------  1 1000 1000      0 Jul 10  2012 .goutputstream-TAU9GW
-rw-------  1 1000 1000      0 Jul 11  2012 .goutputstream-TLECHW
-rw-------  1 1000 1000      0 Aug  1  2012 .goutputstream-UARKIW
-rw-------  1 1000 1000      0 Jun 22  2012 .goutputstream-UCZ4FW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-UEZCKW
-rw-------  1 1000 1000      0 Sep  5  2012 .goutputstream-UUW5JW
-rw-------  1 1000 1000      0 Aug 20  2012 .goutputstream-VWUBJW
-rw-------  1 1000 1000      0 Jul 12  2012 .goutputstream-VZM8GW
-rw-------  1 1000 1000      0 Jul  2  2012 .goutputstream-WBD5GW
-rw-------  1 1000 1000      0 May 24  2013 .goutputstream-WXNHXW
-rw-------  1 1000 1000      0 Sep  6  2012 .goutputstream-X1BHKW
-rw-------  1 1000 1000      0 Jun  7  2013 .goutputstream-YCEPYW
-rw-------  1 1000 1000      0 Apr  9  2013 .goutputstream-ZFDOVW
drwx------  2 1000 1000   4096 Jun 23  2012 .gphoto
drwxrwxr-x  3 1000 1000   4096 May  2 19:02 .gstreamer-0.10
-rw-rw-r--  1 1000 1000    255 Sep 20  2013 .gtk-bookmarks
-rw-r--r--  1 1000 1000    941 Mar 11  2014 .gtk-recordmydesktop
drwx------  2 1000 1000   4096 May  8  2012 .gvfs
-rw-------  1 1000 1000 134754 Sep 17 07:28 .ICEauthority
drwx------  2 1000 1000   4096 Apr 13  2014 .icons
drwxr-xr-x  3 1000 1000   4096 Mar 24  2014 .java
drwx------  3 1000 1000   4096 May 20  2012 .kde
drwxr-xr-x  5 1000 1000   4096 May 23  2012 kdenlive
drwx------  3 1000 1000   4096 Jul 31  2013 .kompozer.net
drwx------  3 1000 1000   4096 Aug 15  2012 .launchpadlib
drwxr-xr-x  3 1000 1000   4096 May  8  2012 .local
drwx------  3 1000 1000   4096 May  9  2012 .macromedia
drwx------  2 1000 1000   4096 Sep 21  2013 .mission-control
drwxrwxr-x  4 1000 1000   4096 Nov 12  2012 .moovida
drwx------  4 1000 1000   4096 May  8  2012 .mozilla
drwxr-xr-x 31 1000 1000  20480 Aug 27 21:44 Music
drwxr-xr-x  2 1000 1000   4096 Nov  7  2012 .ocp
drwxr-x---  6 1000 1000   4096 Aug 25  2012 .openshot
-rw-r--r--  1 1000 1000    248 Oct  4  2012 .pam_environment
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .pdfedit
drwxr-xr-x 22 1000 1000  81920 Sep 12 10:41 Pictures
drwx------  3 1000 1000   4096 May  8  2012 .pki
-rw-r--r--  1 1000 1000    675 Oct  4  2012 .profile
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Public
drwx------  2 1000 1000   4096 Sep 13 12:22 .pulse
-rw-------  1 1000 1000    256 May  8  2012 .pulse-cookie
drwxrwxr-x  3 1000 1000   4096 Nov 12  2012 .python-eggs
drwxrwxr-x  2 1000 1000   4096 Nov 20  2012 .qt
drwxr-xr-x  2 1000 1000   4096 Dec  4  2013 .redeclipse
drwxrwxr-x  7 1000 1000   4096 Apr 25 22:11 rtl8192cu-fixes
drwxrwxr-x  4 1000 1000   4096 Jul  5  2012 sketchbook
drwx------  6 1000 1000   4096 Aug 20  2013 .Skype
drwxr-xr-x 12 1000 1000   4096 Jul  4  2013 slimboat
drwxrwxr-x  3 1000 1000   4096 Jun 28  2012 .slimrat
drwx------  4 1000 1000   4096 Oct  4  2012 .speech-dispatcher
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 .swt
drwxr-xr-x  2 1000 1000   4096 May  8  2012 Templates
drwx------  5 1000 1000   4096 Aug 17  2012 .thumbnails
drwx------  4 1000 1000   4096 May  8  2012 .thunderbird
drwx------  2 1000 1000   4096 Nov  5  2012 .tor
drwxrwxr-x  2 1000 1000   4096 May  8  2012 Ubuntu One
drwxrwxr-x  2 1000 1000   4096 Nov  5  2012 .vidalia
drwxr-xr-x 11 1000 1000  12288 Oct  8 19:59 Videos
-rw-------  1 1000 1000    842 Sep  6 23:06 .viminfo
drwxrwxr-x  2 1000 1000   4096 Mar 11  2014 .VirtualBox
drwxr-xr-x  3 1000 1000   4096 Dec  4  2013 workspace
-rw-------  1 1000 1000     51 Sep 17 07:28 .Xauthority
drwxr-xr-x  2 1000 1000   4096 Apr 30 15:03 .xine
-rw-rw-r--  1 1000 1000    131 Jul  4 08:58 .xinputrc
drwxrwxr-x  2 1000 1000   4096 Aug 23  2012 .xmltv
-rw-------  1 1000 1000     35 Sep 17 07:28 .xsession-errors
-rw-------  1 1000 1000     35 Sep 16 18:48 .xsession-errors.old

```

---

### Post by Bashing-om on 2014-10-20
lcbmac; OK !

Do from the CHroot :
```

chmod -R a+rwX,o-w /home/nordic

```
Which changes in mass all files in /home to defaults.

While still in the CHroot, I want to get us some operating headroom by purging the old unused kernels:
post back:
```

ls -al /
ls -al /boot
uname -r
dpkg -l |grep linux-

```
And then I will craft up the commands to make that happen.

Then I have an idea to try that might be easiest and best to get the .Xauthority and .ICEauthority files (RE-)created (maybe ). 

[INDENT][INDENT]try'n to think things through
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-21
Hi Bashing-om

Here is the results
```

root@ubuntu:/# chmod -R a+rwX,o-w /home/nordic
root@ubuntu:/# ls -al /
total 124
drwxr-xr-x  24 root root  4096 Oct  8 19:59 .
drwxr-xr-x  24 root root  4096 Oct  8 19:59 ..
drwxr-xr-x   2 root root  4096 Aug 27 07:53 bin
drwxr-xr-x   3 root root 12288 Aug 27 07:54 boot
drwxr-xr-x   2 root root  4096 May  8  2012 cdrom
drwxr-xr-x  15 root root  4160 Oct 21 17:24 dev
drwxr-xr-x 131 root root 12288 Oct 11 23:15 etc
-rw-r--r--   1 root root     0 Sep 11 20:16 forcefsch
drwxr-xr-x   4 root root  4096 Oct 11 23:15 home
lrwxrwxrwx   1 root root    33 Aug 21 21:56 initrd.img -> boot/initrd.img-3.13.0-35-generic
lrwxrwxrwx   1 root root    33 Aug 14 17:17 initrd.img.old -> boot/initrd.img-3.13.0-34-generic
drwxr-xr-x  24 root root  4096 Aug 29 07:56 lib
drwx------ 349 root root 24576 May  8  2012 lost+found
drwxr-xr-x   4 root root  4096 Sep  9  2013 media
drwxr-xr-x   2 root root  4096 Apr 19  2012 mnt
drwxr-xr-x   4 root root  4096 Apr  6  2014 opt
dr-xr-xr-x 232 root root     0 Oct  8 11:18 proc
drwx------   9 root root  4096 Sep  1 11:51 root
drwxr-xr-x  23 root root   780 Oct 11 22:46 run
drwxr-xr-x   2 root root 12288 Aug 29 07:55 sbin
drwxr-xr-x   2 root root  4096 Apr 23  2012 srv
dr-xr-xr-x  13 root root     0 Oct  8 11:18 sys
drwxrwxrwt   8 root root  4096 Oct 12 02:09 tmp
drwxrwxrwt   9 root root  4096 Sep  6 23:20 tmp_old
drwx------   4 root root  4096 Oct  8 19:59 .Trash-0
drwxr-xr-x  10 root root  4096 Apr 23  2012 usr
drwxr-xr-x  15 root root  4096 Oct 12  2013 var
lrwxrwxrwx   1 root root    30 Aug 21 21:56 vmlinuz -> boot/vmlinuz-3.13.0-35-generic
lrwxrwxrwx   1 root root    30 Aug 14 17:17 vmlinuz.old -> boot/vmlinuz-3.13.0-34-generic

```

```

root@ubuntu:/# ls -al /boot
total 565212
drwxr-xr-x  3 root root    12288 Aug 27 07:54 .
drwxr-xr-x 24 root root     4096 Oct  8 19:59 ..
-rw-r--r--  1 root root  1010091 Oct 23  2013 abi-3.11.0-13-generic
-rw-r--r--  1 root root  1010091 Nov 12  2013 abi-3.11.0-14-generic
-rw-r--r--  1 root root  1010148 Jan 30  2014 abi-3.11.0-15-generic
-rw-r--r--  1 root root  1010381 Feb  3  2014 abi-3.11.0-17-generic
-rw-r--r--  1 root root  1011333 Feb 18  2014 abi-3.11.0-18-generic
-rw-r--r--  1 root root  1011333 Mar 11  2014 abi-3.11.0-19-generic
-rw-r--r--  1 root root  1011742 Apr  1  2014 abi-3.11.0-20-generic
-rw-r--r--  1 root root  1162233 May  3 00:40 abi-3.13.0-24-generic
-rw-r--r--  1 root root  1165930 May  8 00:38 abi-3.13.0-26-generic
-rw-r--r--  1 root root  1165930 May 15 19:16 abi-3.13.0-27-generic
-rw-r--r--  1 root root  1165981 Jun  4 21:49 abi-3.13.0-29-generic
-rw-r--r--  1 root root  1166474 Jul  4 22:52 abi-3.13.0-30-generic
-rw-r--r--  1 root root  1166929 Jul  1 16:41 abi-3.13.0-31-generic
-rw-r--r--  1 root root  1166929 Jul 15 05:06 abi-3.13.0-32-generic
-rw-r--r--  1 root root  1166929 Jul 29 17:34 abi-3.13.0-33-generic
-rw-r--r--  1 root root  1166929 Aug 13 16:58 abi-3.13.0-34-generic
-rw-r--r--  1 root root  1168075 Aug 15 03:09 abi-3.13.0-35-generic
-rw-r--r--  1 root root   804726 Aug 22  2013 abi-3.2.0-53-generic-pae
-rw-r--r--  1 root root   861648 Aug 22  2013 abi-3.5.0-40-generic
-rw-r--r--  1 root root   926513 Oct  1  2013 abi-3.8.0-32-generic
-rw-r--r--  1 root root   168537 Oct 23  2013 config-3.11.0-13-generic
-rw-r--r--  1 root root   168537 Nov 12  2013 config-3.11.0-14-generic
-rw-r--r--  1 root root   168527 Jan 30  2014 config-3.11.0-15-generic
-rw-r--r--  1 root root   168512 Feb  3  2014 config-3.11.0-17-generic
-rw-r--r--  1 root root   168540 Feb 18  2014 config-3.11.0-18-generic
-rw-r--r--  1 root root   168540 Mar 11  2014 config-3.11.0-19-generic
-rw-r--r--  1 root root   168540 Apr  1  2014 config-3.11.0-20-generic
-rw-r--r--  1 root root   169631 May  3 00:40 config-3.13.0-24-generic
-rw-r--r--  1 root root   169659 May  8 00:38 config-3.13.0-26-generic
-rw-r--r--  1 root root   169642 May 15 19:16 config-3.13.0-27-generic
-rw-r--r--  1 root root   169665 Jun  4 21:49 config-3.13.0-29-generic
-rw-r--r--  1 root root   169697 Jul  4 22:52 config-3.13.0-30-generic
-rw-r--r--  1 root root   169732 Jul  1 16:41 config-3.13.0-31-generic
-rw-r--r--  1 root root   169732 Jul 15 05:06 config-3.13.0-32-generic
-rw-r--r--  1 root root   169732 Jul 29 17:34 config-3.13.0-33-generic
-rw-r--r--  1 root root   169732 Aug 13 16:58 config-3.13.0-34-generic
-rw-r--r--  1 root root   169722 Aug 15 03:09 config-3.13.0-35-generic
-rw-r--r--  1 root root   147576 Aug 22  2013 config-3.2.0-53-generic-pae
-rw-r--r--  1 root root   154704 Aug 22  2013 config-3.5.0-40-generic
-rw-r--r--  1 root root   160909 Oct  1  2013 config-3.8.0-32-generic
drwxr-xr-x  5 root root    12288 Sep 14 11:39 grub
-rw-r--r--  1 root root 16941485 Nov  4  2013 initrd.img-3.11.0-13-generic
-rw-r--r--  1 root root 16941208 Nov 17  2013 initrd.img-3.11.0-14-generic
-rw-r--r--  1 root root 17052155 Feb  1  2014 initrd.img-3.11.0-15-generic
-rw-r--r--  1 root root 17055604 Feb 23  2014 initrd.img-3.11.0-17-generic
-rw-r--r--  1 root root 17057132 Feb 25  2014 initrd.img-3.11.0-18-generic
-rw-r--r--  1 root root 17054097 Mar 27  2014 initrd.img-3.11.0-19-generic
-rw-r--r--  1 root root 17054097 Apr 25 22:13 initrd.img-3.11.0-19-generic.old-dkms
-rw-r--r--  1 root root 17045668 Apr 18  2014 initrd.img-3.11.0-20-generic
-rw-r--r--  1 root root 18659449 May  8 13:16 initrd.img-3.13.0-24-generic
-rw-r--r--  1 root root 18611271 May  6 15:14 initrd.img-3.13.0-24-generic.old-dkms
-rw-r--r--  1 root root 18663265 May 11 23:56 initrd.img-3.13.0-26-generic
-rw-r--r--  1 root root 18663763 May 20 12:24 initrd.img-3.13.0-27-generic
-rw-r--r--  1 root root 18667315 Jun  7 15:23 initrd.img-3.13.0-29-generic
-rw-r--r--  1 root root 18718621 Jul  6 07:40 initrd.img-3.13.0-30-generic
-rw-r--r--  1 root root 18719337 Jul  7 09:18 initrd.img-3.13.0-31-generic
-rw-r--r--  1 root root 18720405 Aug  6 10:23 initrd.img-3.13.0-32-generic
-rw-r--r--  1 root root 18720244 Aug  9 10:06 initrd.img-3.13.0-33-generic
-rw-r--r--  1 root root 18719947 Aug 14 17:25 initrd.img-3.13.0-34-generic
-rw-r--r--  1 root root 18723539 Aug 27 07:54 initrd.img-3.13.0-35-generic
-rw-r--r--  1 root root 14243572 Sep  7  2013 initrd.img-3.2.0-53-generic-pae
-rw-r--r--  1 root root 15327160 Sep 21  2013 initrd.img-3.5.0-40-generic
-rw-r--r--  1 root root 16227905 Oct 19  2013 initrd.img-3.8.0-32-generic
-rw-r--r--  1 root root   176500 Mar 12  2014 memtest86+.bin
-rw-r--r--  1 root root   178176 Mar 12  2014 memtest86+.elf
-rw-r--r--  1 root root   178680 Mar 12  2014 memtest86+_multiboot.bin
-rw-------  1 root root  2621288 Oct 23  2013 System.map-3.11.0-13-generic
-rw-------  1 root root  2621446 Nov 12  2013 System.map-3.11.0-14-generic
-rw-------  1 root root  2627916 Jan 30  2014 System.map-3.11.0-15-generic
-rw-------  1 root root  2628001 Feb  3  2014 System.map-3.11.0-17-generic
-rw-------  1 root root  2629740 Feb 18  2014 System.map-3.11.0-18-generic
-rw-------  1 root root  2629933 Mar 11  2014 System.map-3.11.0-19-generic
-rw-------  1 root root  2630177 Apr  1  2014 System.map-3.11.0-20-generic
-rw-------  1 root root  2685850 May  3 00:40 System.map-3.13.0-24-generic
-rw-------  1 root root  2689758 May  8 00:38 System.map-3.13.0-26-generic
-rw-------  1 root root  2689758 May 15 19:16 System.map-3.13.0-27-generic
-rw-------  1 root root  2690461 Jun  4 21:49 System.map-3.13.0-29-generic
-rw-------  1 root root  2690773 Jul  4 22:52 System.map-3.13.0-30-generic
-rw-------  1 root root  2693057 Jul  1 16:41 System.map-3.13.0-31-generic
-rw-------  1 root root  2693057 Jul 15 05:06 System.map-3.13.0-32-generic
-rw-------  1 root root  2693057 Jul 29 17:34 System.map-3.13.0-33-generic
-rw-------  1 root root  2693057 Aug 13 16:58 System.map-3.13.0-34-generic
-rw-------  1 root root  2697306 Aug 15 03:09 System.map-3.13.0-35-generic
-rw-------  1 root root  2321335 Aug 22  2013 System.map-3.2.0-53-generic-pae
-rw-------  1 root root  2323087 Aug 22  2013 System.map-3.5.0-40-generic
-rw-------  1 root root  2445627 Oct  1  2013 System.map-3.8.0-32-generic
-rw-------  1 root root  5633040 Oct 23  2013 vmlinuz-3.11.0-13-generic
-rw-------  1 root root  5633232 Nov 12  2013 vmlinuz-3.11.0-14-generic
-rw-------  1 root root  5663888 Jan 30  2014 vmlinuz-3.11.0-15-generic
-rw-------  1 root root  5664656 Feb  3  2014 vmlinuz-3.11.0-17-generic
-rw-------  1 root root  5667920 Feb 18  2014 vmlinuz-3.11.0-18-generic
-rw-------  1 root root  5669328 Mar 11  2014 vmlinuz-3.11.0-19-generic
-rw-------  1 root root  5667344 Apr  1  2014 vmlinuz-3.11.0-20-generic
-rw-------  1 root root  5800496 May  3 00:40 vmlinuz-3.13.0-24-generic
-rw-------  1 root root  5814832 May  8 00:38 vmlinuz-3.13.0-26-generic
-rw-------  1 root root  5814832 May 15 19:16 vmlinuz-3.13.0-27-generic
-rw-------  1 root root  5813456 Jun  4 21:49 vmlinuz-3.13.0-29-generic
-rw-------  1 root root  5813328 Jul  4 22:52 vmlinuz-3.13.0-30-generic
-rw-------  1 root root  5817968 Jul  1 16:41 vmlinuz-3.13.0-31-generic
-rw-------  1 root root  5820336 Jul 15 05:06 vmlinuz-3.13.0-32-generic
-rw-------  1 root root  5820336 Jul 29 17:34 vmlinuz-3.13.0-33-generic
-rw-------  1 root root  5820592 Aug 13 16:58 vmlinuz-3.13.0-34-generic
-rw-------  1 root root  5826864 Aug 15 03:09 vmlinuz-3.13.0-35-generic
-rw-------  1 root root  5028480 Aug 22  2013 vmlinuz-3.2.0-53-generic-pae
-rw-------  1 root root  5174640 Aug 22  2013 vmlinuz-3.5.0-40-generic
-rw-------  1 root root  5375088 Oct  1  2013 vmlinuz-3.8.0-32-generic

```

```

root@ubuntu:/# uname -r
3.13.0-32-generic

```

```

root@ubuntu:/# dpkg -l |grep linux-
ii  linux-firmware                                              1.127.5                                             all          Firmware for Linux kernel drivers
pi  linux-headers-3.11.0-13                                     3.11.0-13.20                                        all          Header files related to Linux kernel version 3.11.0
pi  linux-headers-3.11.0-13-generic                             3.11.0-13.20                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-14                                     3.11.0-14.21                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-14-generic                             3.11.0-14.21                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-15                                     3.11.0-15.25                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-15-generic                             3.11.0-15.25                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-17                                     3.11.0-17.31                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-17-generic                             3.11.0-17.31                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-18                                     3.11.0-18.32                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-18-generic                             3.11.0-18.32                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-19                                     3.11.0-19.33                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-19-generic                             3.11.0-19.33                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
pi  linux-headers-3.11.0-20                                     3.11.0-20.34                                        all          Header files related to Linux kernel version 3.11.0
ii  linux-headers-3.11.0-20-generic                             3.11.0-20.34                                        i386         Linux kernel headers for version 3.11.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-24                                     3.13.0-24.47                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-24-generic                             3.13.0-24.47                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-26                                     3.13.0-26.48                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-26-generic                             3.13.0-26.48                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-27                                     3.13.0-27.50                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-27-generic                             3.13.0-27.50                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-29                                     3.13.0-29.53                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-29-generic                             3.13.0-29.53                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-30                                     3.13.0-30.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-30-generic                             3.13.0-30.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-31                                     3.13.0-31.55                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-31-generic                             3.13.0-31.55                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-32                                     3.13.0-32.57                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-32-generic                             3.13.0-32.57                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-33                                     3.13.0-33.58                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-33-generic                             3.13.0-33.58                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-34                                     3.13.0-34.60                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-34-generic                             3.13.0-34.60                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.13.0-35                                     3.13.0-35.62                                        all          Header files related to Linux kernel version 3.13.0
ii  linux-headers-3.13.0-35-generic                             3.13.0-35.62                                        i386         Linux kernel headers for version 3.13.0 on 32 bit x86 SMP
ii  linux-headers-3.8.0-32                                      3.8.0-32.47                                         all          Header files related to Linux kernel version 3.8.0
ii  linux-headers-generic                                       3.13.0.35.42                                        i386         Generic Linux kernel headers
ii  linux-headers-generic-pae                                   3.13.0.35.42                                        i386         Transitional package
rc  linux-image-3.11.0-12-generic                               3.11.0-12.19                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-13-generic                               3.11.0-13.20                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-14-generic                               3.11.0-14.21                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-15-generic                               3.11.0-15.25                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-17-generic                               3.11.0-17.31                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-18-generic                               3.11.0-18.32                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-19-generic                               3.11.0-19.33                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-3.11.0-20-generic                               3.11.0-20.34                                        i386         Linux kernel image for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-24-generic                               3.13.0-24.47                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-26-generic                               3.13.0-26.48                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-27-generic                               3.13.0-27.50                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-29-generic                               3.13.0-29.53                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-30-generic                               3.13.0-30.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-31-generic                               3.13.0-31.55                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-32-generic                               3.13.0-32.57                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-33-generic                               3.13.0-33.58                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-34-generic                               3.13.0-34.60                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-3.13.0-35-generic                               3.13.0-35.62                                        i386         Linux kernel image for version 3.13.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-23-generic-pae                            3.2.0-23.36                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-24-generic-pae                            3.2.0-24.39                                         i386         Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-25-generic-pae                            3.2.0-25.40                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-26-generic-pae                            3.2.0-26.41                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-27-generic-pae                            3.2.0-27.43                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-29-generic-pae                            3.2.0-29.46                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-30-generic-pae                            3.2.0-30.48                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-31-generic-pae                            3.2.0-31.50                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-32-generic-pae                            3.2.0-32.51                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-33-generic-pae                            3.2.0-33.52                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-34-generic-pae                            3.2.0-34.53                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-35-generic-pae                            3.2.0-35.55                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-37-generic-pae                            3.2.0-37.58                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-38-generic-pae                            3.2.0-38.61                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-39-generic-pae                            3.2.0-39.62                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-40-generic-pae                            3.2.0-40.64                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-41-generic-pae                            3.2.0-41.66                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-43-generic-pae                            3.2.0-43.68                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-44-generic-pae                            3.2.0-44.69                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-45-generic-pae                            3.2.0-45.70                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-48-generic-pae                            3.2.0-48.74                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-49-generic-pae                            3.2.0-49.75                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-51-generic-pae                            3.2.0-51.77                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
rc  linux-image-3.2.0-52-generic-pae                            3.2.0-52.78                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.2.0-53-generic-pae                            3.2.0-53.81                                         i386         Linux kernel image for version 3.2.0 on 32 bit x86 SMP
ii  linux-image-3.5.0-40-generic                                3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-3.8.0-31-generic                                3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-3.8.0-32-generic                                3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
rc  linux-image-extra-3.11.0-12-generic                         3.11.0-12.19                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-extra-3.11.0-13-generic                         3.11.0-13.20                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
pi  linux-image-extra-3.11.0-14-generic                         3.11.0-14.21                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-15-generic                         3.11.0-15.25                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-17-generic                         3.11.0-17.31                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-18-generic                         3.11.0-18.32                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-19-generic                         3.11.0-19.33                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.11.0-20-generic                         3.11.0-20.34                                        i386         Linux kernel extra modules for version 3.11.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-24-generic                         3.13.0-24.47                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-26-generic                         3.13.0-26.48                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-27-generic                         3.13.0-27.50                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-29-generic                         3.13.0-29.53                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-30-generic                         3.13.0-30.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-31-generic                         3.13.0-31.55                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-32-generic                         3.13.0-32.57                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-33-generic                         3.13.0-33.58                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-34-generic                         3.13.0-34.60                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.13.0-35-generic                         3.13.0-35.62                                        i386         Linux kernel extra modules for version 3.13.0 on 32 bit x86 SMP
ii  linux-image-extra-3.5.0-40-generic                          3.5.0-40.62                                         i386         Linux kernel image for version 3.5.0 on 32 bit x86 SMP
rc  linux-image-extra-3.8.0-31-generic                          3.8.0-31.46                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-extra-3.8.0-32-generic                          3.8.0-32.47                                         i386         Linux kernel image for version 3.8.0 on 32 bit x86 SMP
ii  linux-image-generic                                         3.13.0.35.42                                        i386         Generic Linux kernel image
ii  linux-image-generic-pae                                     3.13.0.35.42                                        i386         Transitional package
ii  linux-libc-dev:i386                                         3.13.0-35.62                                        i386         Linux Kernel Headers for development
ii  linux-sound-base                                            1.0.25+dfsg-0ubuntu4                                all          base package for ALSA and OSS sound systems
ii  syslinux-common                                             3:4.05+dfsg-6+deb8u1                                all          collection of boot loaders (common files)
ii  syslinux-legacy                                             2:3.63+dfsg-2ubuntu5                                i386         Bootloader for Linux/i386 using MS-DOS floppies

```

I hope this help

---

### Post by Bashing-om on 2014-10-21
lcbmac; Welp;

Upfront I have never encountered the situation as the package manager is depicting here. All I know to to is TRY and see what results:

Let's give this a whirl : - from the CHroot ->
```

dpkg -P linux-image-3.11.0-{13,14,15,17,18,19}-generic
dpkg -P linux-image-extra-3.11.0-{13,14,15,17,18,19}-generic
dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19}
dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19}-generic

```
Depending on how these go, we still have to deal with the 3.8 kernels, the 3.13 kernels, and those  marked 'rc'. It is my hope that the kernels marked 'pi' are dealt with and behind us.

We still have to resolve the why booting the 3.13.0-32-generic kernel, when '/' is directing " lrwxrwxrwx   1 root root    30 Aug 21 21:56 vmlinuz -> boot/vmlinuz-3.13.0-35-generic" . IF we get the kernels situation under control, I do have a thought in mind to try to get the later kernel as the boot kernel.

Again. all I know to do is try and see what we can make work .. TRY and work within the package management system and not make the situation worse than it is now.

[INDENT][INDENT][INDENT]maybe yes
[INDENT][INDENT][INDENT][INDENT]maybe not so yes
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-21
Hi Bashing-om

Her are the results. lol

```

root@ubuntu:/# dpkg -P linux-image-3.11.0-{13,14,15,17,18,19}-generic
dpkg: dependency problems prevent removal of linux-image-3.11.0-13-generic:
 linux-image-extra-3.11.0-13-generic depends on linux-image-3.11.0-13-generic.

dpkg: error processing package linux-image-3.11.0-13-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-14-generic:
 linux-image-extra-3.11.0-14-generic depends on linux-image-3.11.0-14-generic.

dpkg: error processing package linux-image-3.11.0-14-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-15-generic:
 linux-image-extra-3.11.0-15-generic depends on linux-image-3.11.0-15-generic.

dpkg: error processing package linux-image-3.11.0-15-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-17-generic:
 linux-image-extra-3.11.0-17-generic depends on linux-image-3.11.0-17-generic.

dpkg: error processing package linux-image-3.11.0-17-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-18-generic:
 linux-image-extra-3.11.0-18-generic depends on linux-image-3.11.0-18-generic.

dpkg: error processing package linux-image-3.11.0-18-generic (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-image-3.11.0-19-generic:
 linux-image-extra-3.11.0-19-generic depends on linux-image-3.11.0-19-generic.

dpkg: error processing package linux-image-3.11.0-19-generic (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-image-3.11.0-13-generic
 linux-image-3.11.0-14-generic
 linux-image-3.11.0-15-generic
 linux-image-3.11.0-17-generic
 linux-image-3.11.0-18-generic
 linux-image-3.11.0-19-generic

```

```

root@ubuntu:/# dpkg -P linux-image-extra-3.11.0-{13,14,15,17,18,19}-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```

```

root@ubuntu:/# dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19}
dpkg: dependency problems prevent removal of linux-headers-3.11.0-13:
 linux-headers-3.11.0-13-generic depends on linux-headers-3.11.0-13.

dpkg: error processing package linux-headers-3.11.0-13 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-14:
 linux-headers-3.11.0-14-generic depends on linux-headers-3.11.0-14.

dpkg: error processing package linux-headers-3.11.0-14 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-15:
 linux-headers-3.11.0-15-generic depends on linux-headers-3.11.0-15.

dpkg: error processing package linux-headers-3.11.0-15 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-17:
 linux-headers-3.11.0-17-generic depends on linux-headers-3.11.0-17.

dpkg: error processing package linux-headers-3.11.0-17 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-18:
 linux-headers-3.11.0-18-generic depends on linux-headers-3.11.0-18.

dpkg: error processing package linux-headers-3.11.0-18 (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of linux-headers-3.11.0-19:
 linux-headers-3.11.0-19-generic depends on linux-headers-3.11.0-19.

dpkg: error processing package linux-headers-3.11.0-19 (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 linux-headers-3.11.0-13
 linux-headers-3.11.0-14
 linux-headers-3.11.0-15
 linux-headers-3.11.0-17
 linux-headers-3.11.0-18
 linux-headers-3.11.0-19

```

```

root@ubuntu:/# dpkg -P linux-headers-3.11.0-{13,14,15,17,18,19}-generic
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'linux-headers-3.13.0-24': Input/output error

```

Okay I Hope it help

---

### Post by Bashing-om on 2014-10-21
lcbmac; Yuk,

Nope it does not help. but shows us how bad the situation is. I am going to have to think on this, as to how we can stay within the package manager's oversight and clean this up.

For contingency purposes, do we have unused kernels ?
```

ls -al  /lib/modules

```

[INDENT][INDENT]stuck, I hate when that happens
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2014-10-22
lcbmac; Welp;

In addition to:
```

ls -al  /lib/modules

```
Le't see what "might" happen when files that the system "thinks" are obsolete are removed. Maybe get an idea of where to go to. The system is in such a state I am hesitant to make it worse.
```

apt-get -s autoremove

```
where the 's' is "simulate" what it would do if it were implemented.

Depending on these outputs, we might try and see if "fix broken" and "configure "from within the package manager will help us.
Then consider manually removing the kernels, and later fixing the damage done to the package manager.

[INDENT][INDENT]right wrong or otherwise;
[INDENT][INDENT][INDENT]do something[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-22
Hi Bashing-om

Okay here IS the new Results.

```

root@ubuntu:/# ls -al  /lib/modules
total 88
drwxr-xr-x 22 root root 4096 Aug 21 21:52 .
drwxr-xr-x 24 root root 4096 Aug 29 07:56 ..
drwxr-xr-x  4 root root 4096 Apr 18  2014 3.11.0-13-generic
drwxr-xr-x  4 root root 4096 Apr 18  2014 3.11.0-14-generic
drwxr-xr-x  4 root root 4096 Apr 18  2014 3.11.0-15-generic
drwxr-xr-x  4 root root 4096 Apr 18  2014 3.11.0-17-generic
drwxr-xr-x  4 root root 4096 Apr 18  2014 3.11.0-18-generic
drwxr-xr-x  5 root root 4096 Apr 25 22:13 3.11.0-19-generic
drwxr-xr-x  5 root root 4096 May  1 22:03 3.11.0-20-generic
drwxr-xr-x  5 root root 4096 May  6 15:14 3.13.0-24-generic
drwxr-xr-x  5 root root 4096 May  9 08:12 3.13.0-26-generic
drwxr-xr-x  5 root root 4096 May 20 12:23 3.13.0-27-generic
drwxr-xr-x  5 root root 4096 Jun  7 15:22 3.13.0-29-generic
drwxr-xr-x  6 root root 4096 Jul  6 07:40 3.13.0-30-generic
drwxr-xr-x  6 root root 4096 Jul  7 09:17 3.13.0-31-generic
drwxr-xr-x  6 root root 4096 Jul 19 01:05 3.13.0-32-generic
drwxr-xr-x  6 root root 4096 Aug  9 10:06 3.13.0-33-generic
drwxr-xr-x  6 root root 4096 Aug 14 17:24 3.13.0-34-generic
drwxr-xr-x  6 root root 4096 Aug 21 22:04 3.13.0-35-generic
drwxr-xr-x  4 root root 4096 Sep 21  2013 3.2.0-53-generic-pae
drwxr-xr-x  4 root root 4096 Oct 19  2013 3.5.0-40-generic
drwxr-xr-x  4 root root 4096 May  2 06:38 3.8.0-32-generic

```

```

root@ubuntu:/# apt-get -s autoremove
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

Okay and this is what happens when I followed the instructions

```

root@ubuntu:/# sudo dpkg
dpkg: error: need an action option

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use 'apt' or 'aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through 'less' or 'more' !

```

Is that right???

---

### Post by Bashing-om on 2014-10-22
lcbmac; Humm ??

"/lib/modules" looks proper - I had expected to find fault ..

OK, how about:
```

ls -al /usr/src

``` insure the headers files are present.

Then once looked at, and all still proper, I am all for trying the " sudo dpkg --configure -a " and "install -f " commands, see if that helps us.

Then if no other idea pops into place, go ahead and bite the bullet and take matters into our own hands and manually remove kernels.

Try'n not to dig a hole so deep
[INDENT][INDENT][INDENT]we can not apt-get out of
[/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-22
Hi Bashing-om

here is the Result

```

root@ubuntu:/# ls -al /usr/src
total 164
drwxr-xr-x 41 root root 4096 Aug 21 21:54 .
drwxr-xr-x 10 root root 4096 Apr 23  2012 ..
drwxr-xr-x  6 root root 4096 Apr 25 22:11 8192cu-1.8
drwxr-xr-x  5 root root 4096 Apr 18  2014 bcmwl-6.30.223.141+bdcom
drwxr-xr-x 24 root root 4096 Nov  4  2013 linux-headers-3.11.0-13
drwxr-xr-x  7 root root 4096 Nov  4  2013 linux-headers-3.11.0-13-generic
drwxr-xr-x 24 root root 4096 Nov 17  2013 linux-headers-3.11.0-14
drwxr-xr-x  7 root root 4096 Nov 17  2013 linux-headers-3.11.0-14-generic
drwxr-xr-x 24 root root 4096 Feb  1  2014 linux-headers-3.11.0-15
drwxr-xr-x  7 root root 4096 Feb  1  2014 linux-headers-3.11.0-15-generic
drwxr-xr-x 24 root root 4096 Feb 23  2014 linux-headers-3.11.0-17
drwxr-xr-x  7 root root 4096 Feb 23  2014 linux-headers-3.11.0-17-generic
drwxr-xr-x 24 root root 4096 Feb 25  2014 linux-headers-3.11.0-18
drwxr-xr-x  7 root root 4096 Feb 25  2014 linux-headers-3.11.0-18-generic
drwxr-xr-x 23 root root 4096 Mar 27  2014 linux-headers-3.11.0-19
drwxr-xr-x  7 root root 4096 Mar 27  2014 linux-headers-3.11.0-19-generic
drwxr-xr-x 24 root root 4096 Apr 12  2014 linux-headers-3.11.0-20
drwxr-xr-x  7 root root 4096 Apr 12  2014 linux-headers-3.11.0-20-generic
drwxr-xr-x 24 root root 4096 May  6 15:10 linux-headers-3.13.0-24
drwxr-xr-x  7 root root 4096 May  6 15:11 linux-headers-3.13.0-24-generic
drwxr-xr-x 24 root root 4096 May  9 08:06 linux-headers-3.13.0-26
drwxr-xr-x  7 root root 4096 May  9 08:06 linux-headers-3.13.0-26-generic
drwxr-xr-x 24 root root 4096 May 20 12:19 linux-headers-3.13.0-27
drwxr-xr-x  7 root root 4096 May 20 12:20 linux-headers-3.13.0-27-generic
drwxr-xr-x 24 root root 4096 Jun  7 08:15 linux-headers-3.13.0-29
drwxr-xr-x  7 root root 4096 Jun  7 08:16 linux-headers-3.13.0-29-generic
drwxr-xr-x 24 root root 4096 Jul  6 07:37 linux-headers-3.13.0-30
drwxr-xr-x  7 root root 4096 Jul  6 07:38 linux-headers-3.13.0-30-generic
drwxr-xr-x 24 root root 4096 Jul  7 09:10 linux-headers-3.13.0-31
drwxr-xr-x  7 root root 4096 Jul  7 09:10 linux-headers-3.13.0-31-generic
drwxr-xr-x 24 root root 4096 Jul 19 01:00 linux-headers-3.13.0-32
drwxr-xr-x  7 root root 4096 Jul 19 01:00 linux-headers-3.13.0-32-generic
drwxr-xr-x 24 root root 4096 Aug  9 10:00 linux-headers-3.13.0-33
drwxr-xr-x  7 root root 4096 Aug  9 10:00 linux-headers-3.13.0-33-generic
drwxr-xr-x 24 root root 4096 Aug 14 17:16 linux-headers-3.13.0-34
drwxr-xr-x  7 root root 4096 Aug 14 17:17 linux-headers-3.13.0-34-generic
drwxr-xr-x 24 root root 4096 Aug 21 21:54 linux-headers-3.13.0-35
drwxr-xr-x  7 root root 4096 Aug 21 21:54 linux-headers-3.13.0-35-generic
drwxr-xr-x 24 root root 4096 Oct 15  2013 linux-headers-3.8.0-32
drwxr-xr-x  2 root root 4096 Apr 25 21:28 ndiswrapper-1.59
drwxr-xr-x 12 root root 4096 May  1 21:49 virtualbox-4.3.10

```

---

### Post by Bashing-om on 2014-10-22
lcbmac; Sheessshh.

No fault found there either:

As we now have this indicator:
> 
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.


Let's try this to "fix":
from the CHroot : Do;
```

apt-get autoclean 
apt-get autoremove
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get -f install
dpkg --configure -a

```

[INDENT][INDENT][INDENT]fingers crossed, 
[INDENT][INDENT][INDENT]let the package manager do it's magic
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-22
Hi Bashing-om

Okay so here is the next lot of results.

```

root@ubuntu:/# apt-get autoclean
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

root@ubuntu:/# apt-get autoremove
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```


```

root@ubuntu:/# apt-get clean

```

```

root@ubuntu:/# apt-get update
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty Release.gpg
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty Release
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted i386 Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/main Translation-en_GB
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_US
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty/restricted Translation-en_GB
Ign http://archive.ubuntu.com trusty InRelease                                 
Ign http://security.ubuntu.com trusty-security InRelease                       
Ign http://archive.ubuntu.com trusty-updates InRelease
Get:1 http://security.ubuntu.com trusty-security Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty Release.gpg          
Get:2 http://security.ubuntu.com trusty-security Release [59.7 kB]
Get:3 http://archive.ubuntu.com trusty-updates Release.gpg [933 B]
Hit http://archive.ubuntu.com trusty Release                        
Get:4 http://archive.ubuntu.com trusty-updates Release [59.7 kB]               
Hit http://archive.ubuntu.com trusty/main i386 Packages                        
Hit http://archive.ubuntu.com trusty/restricted i386 Packages                  
Get:5 http://security.ubuntu.com trusty-security/main i386 Packages [143 kB]   
Hit http://archive.ubuntu.com trusty/universe i386 Packages                    
Hit http://archive.ubuntu.com trusty/main Translation-en                       
Hit http://archive.ubuntu.com trusty/main Translation-en_GB                    
Hit http://archive.ubuntu.com trusty/restricted Translation-en                 
Hit http://archive.ubuntu.com trusty/restricted Translation-en_GB              
Get:6 http://security.ubuntu.com trusty-security/restricted i386 Packages [14 B]
Get:7 http://security.ubuntu.com trusty-security/universe i386 Packages [50.3 kB]
Hit http://archive.ubuntu.com trusty/universe Translation-en                   
Hit http://archive.ubuntu.com trusty/universe Translation-en_GB                
Get:8 http://archive.ubuntu.com trusty-updates/main i386 Packages [336 kB]     
Get:9 http://security.ubuntu.com trusty-security/main Translation-en [72.9 kB] 
Hit http://security.ubuntu.com trusty-security/restricted Translation-en       
Get:10 http://security.ubuntu.com trusty-security/universe Translation-en [29.7 kB]
Get:11 http://archive.ubuntu.com trusty-updates/restricted i386 Packages [5,820 B]
Get:12 http://archive.ubuntu.com trusty-updates/universe i386 Packages [215 kB]
Get:13 http://archive.ubuntu.com trusty-updates/main Translation-en [153 kB]   
Hit http://archive.ubuntu.com trusty-updates/restricted Translation-en         
Get:14 http://archive.ubuntu.com trusty-updates/universe Translation-en [108 kB]
Ign http://archive.ubuntu.com trusty/main Translation-en_US                    
Ign http://archive.ubuntu.com trusty/restricted Translation-en_US              
Ign http://archive.ubuntu.com trusty/universe Translation-en_US                
Fetched 1,235 kB in 26s (47.2 kB/s)                                            
W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2)/dists/trusty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download. They have been ignored, or old ones used instead.
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

root@ubuntu:/# apt-get upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

root@ubuntu:/# apt-get dist-upgrade
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 

```

```

root@ubuntu:/# apt-get -f install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.

```

```

root@ubuntu:/# dpkg --configure -a

```

---

### Post by Bashing-om on 2014-10-22
lcbmac; Shheesshh, At a loss.

Minor thing in respect to all the others, but -
Why are we back to this ? .. Is not that entry commented out ? 
> 
Ign cdrom://Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release i386 (20140722.2) trusty InRelease

in the file "/etc/apt/sources.list" ?

And there is no return from the terminal command:
> 
root@ubuntu:/# dpkg --configure -a
 ??


Sad state of affairs, here. Presently I do not know how to proceed when all attempts are failing and we get no useful information.

I am not about to suggest a manual intervention in removing kernels with the package manager in this state.

[INDENT][INDENT][INDENT]try'n to think
[INDENT][INDENT][INDENT][INDENT]what to do, OH what to do
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-23
Hi Bashing-om

Okay so how do we do a Manual intervention removal

---

### Post by Bashing-om on 2014-10-23
lcbmac; Hey:

> **lcbmac said:**
> Hi Bashing-om

Okay so how do we do a Manual intervention removal

With the package manager in this state, we don't. Would have no means to recover.

I ask again:
"Why are we back to this ? .. Is not that entry commented out ? " -> We MUST not have the CDrom enabled;
"And there is no return from the terminal command: -> dpkg --configure -a" ????

[INDENT][INDENT]I presently see no way forward.
[/INDENT][/INDENT]

---

### Post by lcbmac on 2014-10-23
Hi Bashing-om

does this mean i should try and do a reinstall from the CD. Obviously I would lose all my data. right?? If so. Dam lol

---

### Post by Bashing-om on 2014-10-23
lcbmac; Welp:

Looks that way. If = as i keep asking -
```

dpkg --configure -a

```
in the CHroot environment
has a null return. I can not conceive of a way forward.
And with the CD access enabled, will only cause additional problems IF old software is installed into the present installed system.

I had thought that you had your data copied off the install ..if that is not the case, can still be done.

It is a rare thing, but as is
[INDENT][INDENT][INDENT][INDENT]I am advising to take the "nuclear solution", and 
[INDENT][INDENT][INDENT](RE-)install
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by gvelim on 2015-01-28
It appears the install script cannot restart the service, so a brutal approach is

1) sudo apt-get install -f
2) open new terminal and type in sudo gnome-system-monitor
3) find the rsyslogd process and kill it

you'll find the apt-get command will execute and the rsyslogd process will be restarted.

done

---

### Post by Jonathan Precise on 2015-01-28
Sorry, not too experienced with this situation in particular, but even if "dpkg --configure -a" didn't return anything, try running it and then running apt, and see if it still complains. In other words, run this from the Chroot environment:

```
dpkg --configure --pending
apt-get -s autoremove
apt-get autoclean
apt-get clean
apt-get update
apt-get upgrade
apt-get dist-upgrade
apt-get -f install
```

It is essential that once the first command starts, this process should not finish until the last command completes.

---


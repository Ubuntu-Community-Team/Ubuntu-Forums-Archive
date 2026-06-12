---
title: "Update Maneger Problem"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by ChrisB111 on 2008-11-15
I am running ubuntu 8.10 off a live usb stick. I have just updated my system using the update manger but after it had finished it crashed. I brought it back up but when I try to start the update manger it comes up with this message, the synaptic package manger also comes up with a error message as well:

```

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Read error - read (21 Is a directory), E:Problem opening /var/lib/apt/lists/Ubuntu%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081029.5)_dists_intrepid_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'
```

Thanks,

Chris

---

### Post by ibizatunes on 2008-11-15
This normally mean that a update has failed dependency
run from the terminal

sudo apt-get update && sudo apt-get upgrade


That should fix it!

---

### Post by ChrisB111 on 2008-11-15
Thanks for your very prompt response, I tried what you said but it came up with more problems.

I think it has something to do with this directory (see attached picture), from what I can infer form the error message the folder with the mouse over it shouldn't be there as there is a file with the same name.

Thanks,

Chris

```

chris@ubuntu:~$ sudo apt-get update
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/main Translation-en_US
Ign cdrom://Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) intrepid/restricted Translation-en_US
Err http://security.ubuntu.com intrepid-security Release.gpg                   
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/main Translation-en_US        
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://security.ubuntu.com intrepid-security/universe Translation-en_US    
  Could not connect to security.ubuntu.com:80 (91.189.88.37). - connect (111 Connection refused)
Err http://archive.ubuntu.com intrepid Release.gpg                             
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid-updates Release.gpg
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid-updates/main Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid-updates/restricted Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Err http://archive.ubuntu.com intrepid-updates/universe Translation-en_US
  Could not connect to archive.ubuntu.com:80 (91.189.88.31). - connect (111 Connection refused) [IP: 91.189.88.31 80]
Reading package lists... Error!
E: Read error - read (21 Is a directory)
E: Problem opening /var/lib/apt/lists/Ubuntu%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081029.5)_dists_intrepid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
chris@ubuntu:~$ sudo apt-get upgrade
Reading package lists... Error!
E: Read error - read (21 Is a directory)
E: Problem opening /var/lib/apt/lists/Ubuntu%208.10%20%5fIntrepid%20Ibex%5f%20-%20Release%20i386%20(20081029.5)_dists_intrepid_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
```

---

### Post by ibizatunes on 2008-11-15
Im sort of guessing now, try changing your sever from US to main 
system > software source > update ubuntu > select MAIN

---

### Post by ibizatunes on 2008-11-15
go the the terminal and type
```
sudo gedit /etc/apt/sources.list
```

DELETE YOUR TEXT and copy in this text - replacing your deleted text with this

```
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081029.2)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu intrepid partner
# deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb-src http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb-src http://security.ubuntu.com/ubuntu intrepid-security multiverse
```

---

### Post by ibizatunes on 2008-11-15
Then do this

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by ChrisB111 on 2008-11-15
I am trying that now

---

### Post by ChrisB111 on 2008-11-15
That seams to have solved the problem.

Thanks,

Chris

---

### Post by ibizatunes on 2008-11-15
Your welcome!!

---

### Post by viaciofano on 2008-11-15
i am hoping you can help me fix mine. i have lost the system bar then rebooted. now its back but
when i try to update my system or upgrade my opera browser it tells me the update manger is running. i get the error below. can you help?
regards Vinny


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by Patrick793 on 2008-11-15
> **viaciofano said:**
> i am hoping you can help me fix mine. i have lost the system bar then rebooted. now its back but
when i try to update my system or upgrade my opera browser it tells me the update manger is running. i get the error below. can you help?
regards Vinny


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
Open a terminal and enter this.
```
sudo dpkg --configure -a
```

---

### Post by viaciofano on 2008-11-15
ive done that thanks
but its asking me to choose????


    &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508;  &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
    &#9474; A new version of /boot/grub/menu.lst is available, but the version   &#9474; 
    &#9474; installed currently has been locally modified.                       &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474; What would you like to do about menu.lst?                            &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;      install the package maintainer's version                        &#9474; 
    &#9474;      keep the local version currently installed                      &#9474; 
    &#9474;      show the differences between the versions                       &#9474; 
    &#9474;      show a side-by-side difference between the versions             &#9474; 
    &#9474;      show a 3-way difference between available versions              &#9474; 
    &#9474;      do a 3-way merge between available versions (experimental)      &#9474; 
    &#9474;      start a new shell to examine the situation                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                                                      &#9474; 
    &#9474;                                <Ok>

---

### Post by krzysz00 on 2008-11-15
That is a really nice error message. It mostly explains what to do. (You have to add sudo though). Just in case you haven't learned this yet (not trying to insult you, just saying) here's what to do:
[LIST=1]
[*]Click on the Applications menu
[*]Open the Accessories menu
[*]Click on the menu entry "Terminal"
[*]Type in "sudo dpkg --configure -a"
[*]Type your password (it won't show up as stars of dots or anything, that's how it's supposed to work)
[*]Hit Enter and follow the prompts (there's about ONE)
[*]Sit back, relax, and enjoy the show
[/LIST]
You won't need to rerun update manager the command (what you typed into the terminal) finished what Update Manager was doing when its work was interrupted.

---

### Post by krzysz00 on 2008-11-15
Sorry, forgot to read rst of thread. You msy proceed to safely ignore my advice.

---

### Post by deveraux on 2008-11-15
hi ubuntu community, I am very new to ubuntu. I don't even know if i am doing this post correctly.  how do i ask questions? and look for the answers?  I recently installed ubuntu with wubi on windows and seemed to install fine, but on the routine scan the next time i restarted, it gave me fail messages and i don't know what else.  it was i guess in dos mode, as i only saw text.  i rebooted ubuntu and skipped the routine scan and the ubuntu desktop came up fine, but when I tried to update files as i was prompted to, it didn't install everything and gave me some more error messages. I also have to go online to view my info that requires flash to view.  I was lead to adobe to download flash by this website. when i clicked on the link to download and install, it started but in the end gave me another error message.  the main error message i am getting is E:dpkg is interrupted, you must manually run dpkg. i tried the sudo command as i read on an earlier post and it asked me for a password and that was it i couldn't type anymore.  i tried entering my password for ubuntu install and nothing happened.  

can you please help me

---

### Post by viaciofano on 2008-11-16
its ok i understand but i am a newbie to linux. 
i chose to use the new package.
now my sound card is not working....i have the following error..

The volume control did not find any elements and/or devices to control. This means either that you don't have the right GStreamer plugins installed, or that you don't have a sound card configured.

You can remove the volume control from the panel by right-clicking the speaker icon on the panel and selecting "Remove From Panel" from the menu

---

### Post by viaciofano on 2008-11-16
one issue fixed but no sound now....

---

### Post by viaciofano on 2008-12-06
its happened again and i have no track of how i solved last time. anyone know why every time i update my system i loose either sound or display....
now i have no sound...

root@dell-desktopi530:/home/viaciofano# lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation 82G33/G31/P35/P31 Express PCI Express Root Port (rev 02)
00:19.0 Ethernet controller: Intel Corporation 82562V-2 10/100 Network Connection (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 92)
00:1f.0 ISA bridge: Intel Corporation 82801IR (ICH9R) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801IR/IO/IH (ICH9R/DO/DH) 4 port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801I (ICH9 Family) 2 port SATA IDE Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc RV610 video device [Radeon HD 2400 PRO]
root@dell-desktopi530:/home/viaciofano# aadebug > aadebug.txt 2>&1
root@dell-desktopi530:/home/viaciofano# modprobe snd_hda_intel
FATAL: Module snd_hda_intel not found.
root@dell-desktopi530:/home/viaciofano#

root@dell-desktopi530:/home/viaciofano# aplay -l 
aplay: device_list:205: no soundcards found...
root@dell-desktopi530:/home/viaciofano# lspci | grep Audio
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
root@dell-desktopi530:/home/viaciofano#

---


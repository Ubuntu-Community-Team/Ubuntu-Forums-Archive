---
title: "How to uprade ubuntu 11.10 to current version"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by wachimanikire on 2013-06-19
I am a newby to ubunrtu. I installed ubuntu 11.10 and after installation, received that version is no longer supported. I googled how to upgrade using terminal and i tried the commands I got. Now I do not know how to proceed to finish the up grade. here is a print out of what I got and showing where I am stuck

  ```
wachimanikire@wachimanikire-Advent-Series:~$ sudo apt-get update && sudo apt-get upgrade -y && sudo apt-get dist-upgrade -y && sudo apt-get autoclean -y && sudo apt-get autoremove -y 
 [sudo] password for wachimanikire:  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise InRelease 
 Ign [http://security.ubuntu.com](http://security.ubuntu.com) precise-security InRelease 
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise InRelease 
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates InRelease 
 Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports InRelease 
 Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release.gpg [72 B] 
 Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release.gpg [198 B] 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release.gpg 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise Release    
 Get:3 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release.gpg [198 B] 
 Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security Release [49.6 kB] 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release.gpg                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise Release                                
 Get:5 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates Release [49.6 kB] 
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Sources                               
 Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Sources [80.9 kB]        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports Release                      
 Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main i386 Packages                         
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main TranslationIndex                      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Sources                           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Sources                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Sources                       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Sources                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main i386 Packages                     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted i386 Packages               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe i386 Packages                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse i386 Packages               
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main TranslationIndex                  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse TranslationIndex 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted TranslationIndex 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe TranslationIndex 
 Get:7 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Sources [396 kB] 
 Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Sources [2,494 B] 
 Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Sources [26.3 kB]    
 Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Sources [1,383 B] 
 Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main i386 Packages [307 kB]  
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en_GB                     
 Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) precise/main Translation-en                        
 Get:12 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted i386 Packages [4,620 B] 
 Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe i386 Packages [78.6 kB] 
 Get:14 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Sources [5,467 B] 
 Get:15 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Sources [90.9 kB]  
 Get:16 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse i386 Packages [2,367 B] 
 Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main TranslationIndex [74 B] 
 Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse TranslationIndex [71 B] 
 Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted TranslationIndex [72 B] 
 Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe TranslationIndex [73 B] 
 Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/main Translation-en [141 kB] 
 Get:22 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Sources [6,571 B] 
 Get:23 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main i386 Packages [657 kB] 
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/multiverse Translation-en       
 Hit [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/restricted Translation-en       
 Get:24 [http://security.ubuntu.com](http://security.ubuntu.com) precise-security/universe Translation-en [48.0 kB] 
 Get:25 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted i386 Packages [10.0 kB] 
 Get:26 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe i386 Packages [209 kB] 
 Get:27 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse i386 Packages [13.8 kB] 
 Get:28 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main TranslationIndex [3,564 B] 
 Get:29 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse TranslationIndex [2,605 B] 
 Get:30 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted TranslationIndex [2,461 B] 
 Get:31 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe TranslationIndex [2,850 B] 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Sources                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Sources           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Sources             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Sources           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main i386 Packages           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted i386 Packages     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe i386 Packages       
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse i386 Packages     
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main TranslationIndex        
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse TranslationIndex  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted TranslationIndex  
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe TranslationIndex    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en_GB                 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/main Translation-en                    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en_GB           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/multiverse Translation-en              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en_GB           
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/restricted Translation-en              
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en_GB             
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise/universe Translation-en                
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en_GB         
 Get:32 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/main Translation-en [291 kB] 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en_GB   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/multiverse Translation-en      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en_GB   
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/restricted Translation-en      
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en_GB     
 Get:33 [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-updates/universe Translation-en [121 kB] 
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/main Translation-en          
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/multiverse Translation-en    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/restricted Translation-en    
 Hit [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) precise-backports/universe Translation-en      
 Fetched 2,605 kB in 10s (242 kB/s)                                              
 E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 wachimanikire@wachimanikire-Advent-Series:~$ sudo dpkg --configure -a 
 Setting up initramfs-tools (0.99ubuntu13.1) ... 
 update-initramfs: deferring update (trigger activated) 
 Setting up grub-common (1.99-21ubuntu3.9) ... 
 Installing new version of config file /etc/bash_completion.d/grub ... 
 Installing new version of config file /etc/grub.d/20_linux_xen ... 
 Installing new version of config file /etc/grub.d/00_header ... 
 Installing new version of config file /etc/grub.d/10_linux ... 
 Installing new version of config file /etc/grub.d/30_os-prober ... 
 Setting up grub-pc-bin (1.99-21ubuntu3.9) ... 
 Setting up libc-dev-bin (2.15-0ubuntu10.4) ... 
 Setting up libdbus-1-dev (1.4.18-1ubuntu1.4) ... 
 Setting up libpcre3 (8.12-4) ... 
 Setting up friendly-recovery (0.2.25) ... 
 Installing new version of config file /etc/init/friendly-recovery.conf ... 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-3.0.0-32-generic 
 Found initrd image: /boot/initrd.img-3.0.0-32-generic 
 Found linux image: /boot/vmlinuz-3.0.0-12-generic 
 Found initrd image: /boot/initrd.img-3.0.0-12-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Microsoft Windows XP Home Edition on /dev/sda1 
 done 
 Setting up libpcrecpp0 (8.12-4) ... 
 Setting up grub2-common (1.99-21ubuntu3.9) ... 
 Setting up libglib2.0-0 (2.32.3-0ubuntu1) ... 
 Setting up libc6-dev (2.15-0ubuntu10.4) ... 
 Setting up libpango1.0-0 (1.30.0-0ubuntu3.1) ... 
 Setting up gir1.2-pango-1.0 (1.30.0-0ubuntu3.1) ... 
 Setting up plymouth-label (0.8.2-2ubuntu31.1) ... 
 Setting up libglib2.0-bin (2.32.3-0ubuntu1) ... 
 Removing obsolete conffile /etc/etc/bash_completion.d/gdbus-bash-completion.sh ... 
 Removing obsolete conffile /etc/etc/bash_completion.d/gsettings-bash-completion.sh ... 
 Setting up grub-pc (1.99-21ubuntu3.9) ... 
 Installing new version of config file /etc/kernel/postrm.d/zz-update-grub ... 
 Installing new version of config file /etc/kernel/postinst.d/zz-update-grub ... 
 Installation finished. No error reported. 
 Generating grub.cfg ... 
 Found linux image: /boot/vmlinuz-3.0.0-32-generic 
 Found initrd image: /boot/initrd.img-3.0.0-32-generic 
 Found linux image: /boot/vmlinuz-3.0.0-12-generic 
 Found initrd image: /boot/initrd.img-3.0.0-12-generic 
 Found memtest86+ image: /boot/memtest86+.bin 
 Found Microsoft Windows XP Home Edition on /dev/sda1 
 done 
 Setting up libpcre3-dev (8.12-4) ... 
 Setting up libglib2.0-dev (2.32.3-0ubuntu1) ... 
 Setting up libpango1.0-dev (1.30.0-0ubuntu3.1) ... 
 Processing triggers for initramfs-tools ... 
 update-initramfs: Generating /boot/initrd.img-3.0.0-32-generic 
 Processing triggers for libc-bin ... 
 ldconfig deferred processing now taking place 
 wachimanikire@wachimanikire-Advent-Series:~$  
```

I do not know what to put in after the last prompt.

Someboody please help

---

### Post by MidnightGrey on 2013-06-19
> **wachimanikire said:**
> sudo apt-get update && sudo apt-get upgrade -y && sudo  apt-get dist-upgrade -y && sudo apt-get autoclean -y &&  sudo apt-get autoremove -y

Apply those list of commands one at a time in this order:
```

sudo apt-get update
sudo apt-get upgrade -y
sudo apt-get dis-upgrade -y
sudo apt-get autoclean -y && sudo apt-get autoremove

```
after each command take note of any 'errors' or 'did not complete' or anything that looks like a failed process before executing the next command. If so paste the output here so we can see what happened.

or try and do it using the GUI:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_11.10](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#Upgrading_from_Ubuntu_11.10)

---

### Post by TheFu on 2013-06-19
If you are running WUBI (Ubuntu inside Windows), I don't know the answer.  Add WUBI to your title and ask again. Wubi installs behave a little differently and I've never used it. Best to ask that specific question and get a wubi-specific answer.

Those commands didn't upgrade to any new distro.  You have completely updated your current system and removed any older packages that aren't used anymore.  At least that is the theory.  You are still on 11.10, regardless.  If you read the man page for apt-get, this stuff is all explained.   **man apt-get** is what you need to type. Almost every command on the system will have a comprehensive man page. Learn it, know it, love it.

First you need to get to 12.04, which is an LTS release and will be supported for 5 years.  This is probably where YOU (and I) should stop.  At least until the next LTS release 14.04 happens in a year.  Only people prepared to update every 6-9 months should run anything later than 12.04 - PERIOD.  All of my desktops and servers run LTS releases - 10.04 or 12.04. I don't bother with intermediate releases. It isn't necessary, IMHO.  Especially for end-users like us.

Ok, so you should rerun:
$ **sudo apt-get update && sudo apt-get dist-upgrade**
to ensure your system is 100% current, then run
$ **sudo do-release-upgrade**
within an hour or so. This should take an 11.10 system to 12.04.  Be aware that some things have changed in 12.04 - especially related to networking.  Before doing any distribution upgrade, it is always highly recommended that you try out the new distro using a LiveCD or USB Flash drive first to ensure it likes your hardware still.  If there is any issues running the liveCD, research the solutions before you do the do-release-upgrade.  Some times the release upgrade will break the graphics and you'll be left staring at a blank, black screen after the upgrade. Be prepared.

Also, always, always, always have a 100% perfect backup that you know how to recover before starting this process. Unless you are prepared to loose your data. If that is the case - have at it.

-------------------------

Ok - upgrades between LTS releases work, so 8.04 --> 10.04 --> 12.04 --> 14.04 will work. No need to hit the intermediate releases.
However, if you are on 11.10 and want to get to 13.04 (why?), then you'll need to go through every release.
11.10 --> 12.04 --> 12.10 --> 13.04
Clear?

Or you could just make good backups of your data and perform a fresh install of 13.04, which would be easier.

---

### Post by grahammechanical on 2013-06-19
Please read the offical advice.

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

Note the section headed Network Upgrade for Ubuntu Desktops 11.10 to 12.04 LTS (recommended)
> 

[LIST=1]
[*=left][FONT=inherit]Run the **Update Manager** application from the **Unity Dash**[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]In Update Manager, click the **Settings&#8230;** button, and enter your password to start the Software Sources application.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Select the sub menu **Updates** from the Software Sources application.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]Check the &#8220;**Release upgrade** - Show new distribution releases&#8221; drop down to make sure &#8220;**Normal releases**&#8221; is selected, and change it if otherwise.[FONT=inherit][/FONT][/FONT]

[*=left]Close the Software Sources application and return to Update Manager.[FONT=inherit][/FONT]
[*=left][FONT=inherit]In Update Manager, click the **Check** button to check for new updates.[FONT=inherit][/FONT][/FONT]

[*=left][FONT=inherit]If there are any updates to install, use the **Install Updates** button to install them, and press **Check** again after that is complete.[FONT=inherit][/FONT][/FONT]

[*=left]A message will appear informing you of the availability of the new release.[FONT=inherit][/FONT]
[*=left][FONT=inherit]Click **Upgrade**.[FONT=inherit][/FONT][/FONT]

[*=left]Follow the on-screen instructions.
[/LIST]



Ubuntu is for humans. Why, oh why, do we insist on doing it the hard way when Ubuntu has easier ways of doing things?

Regards.

---

### Post by Paqman on 2013-06-19
> **grahammechanical said:**
> 
Ubuntu is for humans. Why, oh why, do we insist on doing it the hard way when Ubuntu has easier ways of doing things?


Couldn't agree more.

As for Wubi installs, they upgrade exactly the same way as traditional installs. There's really very little difference between the two.

---

### Post by phinole on 2013-09-10
I'm having the same problem upgrading Ubuntu 11.10 to 12.04.  The machine was running very well as a VM on a Windows Server 2008 R2 platform under Hyper-V, but the host was upgraded to Windows Server 2012 and that has sent (so I think from what I've found online) the system into a tailspin.  

I'm able to successfully run [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get update.[/FONT][/COLOR]

Here's my output after running [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get upgrade -y[/FONT][/COLOR]:

```

root@nix01:/var/log/apache2# sudo apt-get upgrade -y
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be upgraded:
  python-ubuntuone-client python-ubuntuone-storageprotocol ubuntu-sso-client ubuntuone-client
4 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 390 kB of archives.
After this operation, 4,096 B disk space will be freed.
Get:1 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main ubuntu-sso-client all 1.4.1-0ubuntu1.1 [57.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main ubuntuone-client all 2.0.1-0ubuntu1.1 [46.2 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main python-ubuntuone-storageprotocol all 2.0.1-0ubuntu1.1 [52.2 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ oneiric-updates/main python-ubuntuone-client all 2.0.1-0ubuntu1.1 [234 kB]
Fetched 390 kB in 13s (28.7 kB/s)
Reading changelogs... Done
apt-listchanges: Mailing root: apt-listchanges: changelogs for nix01.bluefirecreative.com
(Reading database ... 168540 files and directories currently installed.)
Preparing to replace ubuntu-sso-client 1.4.0-0ubuntu1 (using .../ubuntu-sso-client_1.4.1-0ubuntu1.1_all.deb) ...
Unpacking replacement ubuntu-sso-client ...
Preparing to replace ubuntuone-client 2.0.0-0ubuntu2.3 (using .../ubuntuone-client_2.0.1-0ubuntu1.1_all.deb) ...
Unpacking replacement ubuntuone-client ...
Preparing to replace python-ubuntuone-storageprotocol 2.0.0-0ubuntu1 (using .../python-ubuntuone-storageprotocol_2.0.1-0ubuntu1.1_all.deb) ...
Unpacking replacement python-ubuntuone-storageprotocol ...
Preparing to replace python-ubuntuone-client 2.0.0-0ubuntu2.3 (using .../python-ubuntuone-client_2.0.1-0ubuntu1.1_all.deb) ...
Unpacking replacement python-ubuntuone-client ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Setting up linux-image-3.0.0-32-server (3.0.0-32.51) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
cp: cannot stat `/boot/initrd.img-3.0.0-32-server': No such file or directory
Failed to copy /boot/initrd.img-3.0.0-32-server to /initrd.img .
dpkg: error processing linux-image-3.0.0-32-server (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-image-server:
 linux-image-server depends on linux-image-3.0.0-32-server; however:
  Package linux-image-3.0.0-32-server is not configured yet.
dpkg: error processing linux-image-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-server:
 linux-server depends on linux-image-server (= 3.0.0.32.36); however:
  Package linux-image-server is not configured yet.
dpkg: error processing linux-server (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-sso-client (1.4.1-0ubuntu1.1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                              Setting up python-ubuntuone-storageprotocol (2.0.1-0ubuntu1.1) ...
Setting up python-ubuntuone-client (2.0.1-0ubuntu1.1) ...
Installing new version of config file /etc/xdg/ubuntuone/syncdaemon.conf ...
Setting up ubuntuone-client (2.0.1-0ubuntu1.1) ...
Errors were encountered while processing:
 linux-image-3.0.0-32-server
 linux-image-server
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by craig10x on 2013-09-10
I know that most of the time it is suggested that they upgrade either using the update manager or using terminal command as was previously suggested to you 2 newbies posting on this thread, but ANOTHER way is to download and burn and iso for 12.04 and it will offer (as one of the options) to upgrade 11.10 to 12.04...

I had never used the upgrade method before and recently did it to move from 13.04 to 13.10 development and it worked great...all my programs and data was transferred over and only lost 2 programs that i had to re-install (both which require license agreements) which was Google Chrome and the Microsoft Core Fonts...

Not sure if that would work with WUBI though...i don't think you guys mentioned if you had actual hard drive installs or a wubi install...

If you can use that method...you can upgrade to each newer version of ubuntu using that same method...(burn an iso for that version, run it live and use the upgrade feature on the installer)...

---

### Post by Jonathan Precise on 2013-09-10
Try

```
do-release-upgrade
```

---


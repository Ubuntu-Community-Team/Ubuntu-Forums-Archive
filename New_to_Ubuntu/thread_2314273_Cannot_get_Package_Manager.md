---
title: "Cannot get Package Manager"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by rob160 on 2016-02-19
Running Ubuntu 14.04.  I get a red circle with a white bar at the right of the title bar which says: An error occurred, please run Package Manager from the right-click menu ... to see what is wrong ...
I don't know WHAT to right-click: neither the desktop, the error message, the dash or anything gives me a menu when right-clicked. 

 I try to install Synaptic from the Ubuntu Software Center because that seems to be a Package Manager, but it won't install -- it freezes with a circle of dots, center screen.

I've tried to run  apt-get check  from a terminal window and get:
E: Could not open lock file  /var/lib/dpkg/lock  -  open (permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg), are you root?

I don't know what any of this means, nor whether these two errors are related.

Any advice?   ~Rob

---

### Post by westie457 on 2016-02-19
Welcome to the fora.

To run an 'apt-get' command and mostly any package management command you need to use 'sudo' (SuperUserDO). you will be asked for your password, nothing will show on the screen, just type and hit enter.

Give these commands a try one at a time```
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get dist-upgrade
```
If any errors post them here for further help.

---

### Post by grahammechanical on 2016-02-19
> please run Package Manager from the right-click menu ... to see what is wrong ...

Did you try right clicking the icon? The one with the red circle and a white bar.

Actually, right clicking the desktop will bring up a menu. Not the menu that you needed but most definitely it is a right click menu. You were being asked to run Software Updater/Update Manager. Searching for either of those terms should have brought up an icon to click which would have run a GUI front end for the default installed package manager.

Regards

---

### Post by rob160 on 2016-02-24
Thank you Westie

Here's my session: (... refers to many lines omitted)

rob@pcuser-6410:~$ sudo apt-get install -f 

 Reading package lists... Error! 

 E: Encountered a section with no Package: header 

 E: Problem with MergeList /var/lib/apt/lists/nz.archive.ubuntu.com_ubuntu_dists_trusty_main_i18n_Translation-en 

 E: The package lists or status file could not be parsed or opened. 

 rob@pcuser-6410:~$  

 

 sudo apt-get update  

 ...

 Get:75 [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe Translation-en [4,089 kB]   
 Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/main Translation-en_NZ                  
 Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/multiverse Translation-en_NZ            
 Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/restricted Translation-en_NZ            
 Ign [http://nz.archive.ubuntu.com](http://nz.archive.ubuntu.com) trusty/universe Translation-en_NZ              
 Fetched 32.5 MB in 3min 23s (159 kB/s)                                          
 Reading package lists... Done 
 

 

 sudo apt-get dist-upgrade
 rob@pcuser-6410:~$ sudo apt-get dist-upgrade 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 

 Calculating upgrade... Done 
 The following packages were automatically installed and are no longer required: 
   kde-l10n-engb thunderbird-locale-en thunderbird-locale-en-gb 
   thunderbird-locale-en-us 
 Use 'apt-get autoremove' to remove them. 
 The following NEW packages will be installed: 
   libandroid-properties1 linux-headers-3.13.0-79 
   linux-headers-3.13.0-79-generic linux-image-3.13.0-79-generic 
   linux-image-extra-3.13.0-79-generic 

 The following packages will be upgraded: 

   apt apt-transport-https apt-utils base-files bcmwl-kernel-source bind9-host

 …

  thunderbird-locale-en-us udev unity-lens-music unity-scope-musicstores 

   uno-libs3 ure 

 154 upgraded, 5 newly installed, 0 to remove and 0 not upgraded. 

 Need to get 323 MB of archives. 

 After this operation, 290 MB of additional disk space will be used. 

 Do you want to continue? [Y/n]  

 

 I selected no

 However the Red Error Circle with White Bar disappeared, so I suppose something was fixed.

 

 I'd be grateful if you could briefly explain what had happened (perhaps how the error appeared) and which command fixed it and how.  Maybe also how I should proceed – is your apt-get update a generic fix for these kind of problems.  Or if the forum is not the place for this, then maybe a URL

 

 Should I also run "apt-get autoremove" ?

Many Thanks   Cheers   ~Rob

---

### Post by ian-weisser on 2016-02-24
What happened is that you had a corrupted file in your local package database.

Run dist-upgrade again, select yes.
Then run autoremove.

---


---
title: "msttcorefonts errors during skype install"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by Knot_Sharpe on 2008-09-30
Hello all!

I'm trying to install skype and I keep getting msstcorefonts errors. I also saw these errors when I tried to install mythTV, got frustrated and quit. I have tried to remove msstcorefonts and reinstall, but I still get error messages.

This is what I tried

sudo apt-get clean
sudo apt-get update
sudo apt-get purge msttcorefonts
sudo apt-get install msttcorefonts

this is what I got:

sudo apt-get clean
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
gary@gary-ibm:~$ sudo apt-get update
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]             
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_CA     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_CA           
Ign [http://download.skype.com](http://download.skype.com) stable Release.gpg                               
Get:2 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                    
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                
Ign [http://download.skype.com](http://download.skype.com) stable/non-free Translation-en_CA      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                       
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release.gpg [189B]               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Translation-en_CA       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Translation-en_CA             
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Translation-en_CA         
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Translation-en_CA       
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                       
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_CA                     
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_CA                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_CA               
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [189B]    
Ign [http://download.skype.com](http://download.skype.com) stable Release                         
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources               
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_CA
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_CA
Hit [http://download.skype.com](http://download.skype.com) stable/non-free Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_CA
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Fetched 5B in 1s (3B/s)  
Reading package lists... Done
gary@gary-ibm:~$ sudo apt-get purge msttcorefonts
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  msttcorefonts*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
gary@gary-ibm:~$ sudo apt-get install msttcorefonts

Any ideas or suggestions would be much appreciated.
Thanks,
Gary

---

### Post by talsemgeest on 2008-10-01
That means that some other package manager is running, like the add/remove programs, synaptic package manager, update manager... Make sure any of those are closed then try again.

---

### Post by Sycron on 2008-10-01
Be sure to close all that applications that talsemgeest mentioned.

---


---
title: "Getting the error Error:BrokenCount&gt;0 after installing the packages"
date: 2011-10-22
forum: New to Ubuntu
---

### Post by Pulkit1993 on 2011-10-22
I am getting the following error in the top menu bar:

"An error occurred.Please run the Package Manger form the right-click menu or apt-get in a terminal to see what is wrong.The error message was:'Error:BrokenCount>0'.This usually means that your installed packages have unmet dependencies."

I tried using sudo apt-get -f install in the terminal.I got the following:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libasound2-plugins:i386
The following packages will be upgraded:
  libasound2-plugins:i386
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0 B/66.4 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? Y

(Reading database ... 143622 files and directories currently installed.)
Preparing to replace libasound2-plugins:i386 1.0.24-0ubuntu6 (using .../libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb) ...
Unpacking replacement libasound2-plugins:i386 ...
dpkg: error processing /var/cache/apt/archives/libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb (--unpack):
 './usr/share/doc/libasound2-plugins/changelog.Debian.gz' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Then i tried using sudo apt-get update.I got the following:


Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric InRelease                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security InRelease                      
Get:1 [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release.gpg [72 B]            
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric InRelease                            
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates InRelease
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports InRelease
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release.gpg
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release   
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric Release.gpg                  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Sources                     
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates Release.gpg
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Sources
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main amd64 Packages
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main i386 Packages                        
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports Release.gpg                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Sources               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Sources             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main amd64 Packages            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted amd64 Packages      
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main TranslationIndex                     
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric Release                               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe amd64 Packages        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse amd64 Packages      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main i386 Packages             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main TranslationIndex          
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted TranslationIndex    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe TranslationIndex      
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates Release                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/main Translation-en            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/multiverse Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/restricted Translation-en      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) oneiric-security/universe Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports Release
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/main Sources                 
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/restricted Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/universe Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/multiverse Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/main amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/restricted amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/universe amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/multiverse amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/main i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/restricted i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/universe i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/multiverse i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/main TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/multiverse TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/restricted TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/universe TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/main Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/restricted Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/universe Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/multiverse Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/main amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/main i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en_US
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/universe i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/main TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/multiverse TranslationIndex
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric/main Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/restricted TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/universe TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse Sources
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe i386 Packages
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main TranslationIndex
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse TranslationIndex
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted TranslationIndex
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe TranslationIndex
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/main Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/multiverse Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/restricted Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric/universe Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/main Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/multiverse Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/restricted Translation-en
Hit [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-updates/universe Translation-en
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main Translation-en_US
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/main Translation-en
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse Translation-en_US
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/multiverse Translation-en
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted Translation-en_US
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/restricted Translation-en
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe Translation-en_US
Ign [http://lk.archive.ubuntu.com](http://lk.archive.ubuntu.com) oneiric-backports/universe Translation-en
Fetched 72 B in 34s (2 B/s)
Reading package lists... Done


When i am opening Ubuntu Software Centre,it is giving me the following message:

Items cannot be installed or removed until the package catalog is repaired.Do you want to repair it now?

I clicked on the repair button.It gave me the following message in a dialog box:

"Package operation failed.
The installation or removal of a software package failed"
On opening the details in the dialog box,it showed me the following:

installArchives() failed: (Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 143622 files and directories currently installed.)
Preparing to replace libasound2-plugins:i386 1.0.24-0ubuntu6 (using .../libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb) ...
Unpacking replacement libasound2-plugins:i386 ...
dpkg: error processing /var/cache/apt/archives/libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb (--unpack):
 './usr/share/doc/libasound2-plugins/changelog.Debian.gz' is different from the same file on the system
Errors were encountered while processing:
 /var/cache/apt/archives/libasound2-plugins_1.0.24-0ubuntu6.1_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)
dpkg: error processing libasound2-plugins (--configure):
 libasound2-plugins:amd64 1.0.24-0ubuntu6.1 cannot be configured because libasound2-plugins:i386 is in a different version (1.0.24-0ubuntu6)
dpkg: error processing libasound2-plugins:i386 (--configure):
 libasound2-plugins:i386 1.0.24-0ubuntu6 cannot be configured because libasound2-plugins:amd64 is in a different version (1.0.24-0ubuntu6.1)


Please help!!

---


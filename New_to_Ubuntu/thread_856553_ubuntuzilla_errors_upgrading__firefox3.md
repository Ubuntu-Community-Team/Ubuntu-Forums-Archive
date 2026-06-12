---
title: "ubuntuzilla errors upgrading  firefox3"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by formachs on 2008-07-11
I've pasted the the install process from the command prompt I'm totally new at this 
Thanks in advance
[guy@ubuntu-laptop:~]$ ubuntuzilla.py -a install -p firefox -d
Your commandline options:
{'mirrors': ['releases.mozilla.org/pub/mozilla.org/', 'mozilla.isc.org/pub/mozilla.org/', 'mozilla.ussg.indiana.edu/pub/mozilla.org/', 'ftp.osuosl.org/pub/mozilla.org/', 'mozilla.cs.utah.edu/pub/mozilla.org/', 'mozilla.mirrors.tds.net/pub/mozilla.org/', 'ftp.scarlet.be/pub/mozilla.org/', 'ftp.uni-erlangen.de/pub/mozilla.org/', 'sunsite.rediris.es/pub/mozilla.org/'], 'package': 'firefox', 'debug': True, 'localization': 'en-US', 'skipgpg': False, 'test': False, 'skipbackup': False, 'action': 'install', 'unattended': False, 'keyservers': ['subkeys.pgp.net', 'pgpkeys.mit.edu', 'pgp.mit.edu', 'wwwkeys.pgp.net', 'keymaster.veridis.com'], 'targetdir': '/opt'}
Debug mode ON.

Welcome to the Ubuntuzilla Firefox script version 4.5.1

This script installs the latest release of the official Mozilla build of Firefox on Ubuntu Linux. If you run into any problems using this script, or have feature requests, suggestions, or general comments, please visit our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) 

Apt package name: firefox
Retrieving the version of the latest release of Firefox from the Mozilla website...
The most recent release of Firefox is detected to be 3.0. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.org/](http://www.mozilla.org/))
If no version number shows, if the version shown is not the latest, or if you would like to install an older release, press 'n', and you'll be given the option to enter the version manually. Otherwise, press 'y', and proceed with installation. [y/n]? 
Please enter 'y' or 'n': y
['Index of [ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/\n](ftp://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0/\n)', 'linux-i686/\n', '\n', '[Upper Directory]\n', 'af/. . . . . . . . . Jun 17 17:27\n', 'ar/. . . . . . . . . Jun 17 17:27\n', 'be/. . . . . . . . . Jun 17 17:27\n', 'ca/. . . . . . . . . Jun 17 17:27\n', 'cs/. . . . . . . . . Jun 17 17:27\n', 'da/. . . . . . . . . Jun 17 17:27\n', 'de/. . . . . . . . . Jun 17 17:27\n', 'el/. . . . . . . . . Jun 17 17:27\n', 'en-GB/ . . . . . . . Jun 17 17:27\n', 'en-US/ . . . . . . . Jun 17 17:27\n', 'es-AR/ . . . . . . . Jun 17 17:27\n', 'es-ES/ . . . . . . . Jun 17 17:27\n', 'eu/. . . . . . . . . Jun 17 17:27\n', 'fi/. . . . . . . . . Jun 17 17:27\n', 'fr/. . . . . . . . . Jun 17 17:27\n', 'fy-NL/ . . . . . . . Jun 17 17:27\n', 'ga-IE/ . . . . . . . Jun 17 17:27\n', 'gu-IN/ . . . . . . . Jun 17 17:27\n', 'he/. . . . . . . . . Jun 17 17:27\n', 'hu/. . . . . . . . . Jun 17 17:27\n', 'id/. . . . . . . . . Jun 17 17:27\n', 'it/. . . . . . . . . Jun 17 17:27\n', 'ja/. . . . . . . . . Jun 17 17:27\n', 'ka/. . . . . . . . . Jun 17 17:27\n', 'ko/. . . . . . . . . Jun 17 17:27\n', 'ku/. . . . . . . . . Jun 17 17:27\n', 'lt/. . . . . . . . . Jun 17 17:27\n', 'mk/. . . . . . . . . Jun 17 17:27\n', 'mn/. . . . . . . . . Jun 17 17:27\n', 'nb-NO/ . . . . . . . Jun 17 17:27\n', 'nl/. . . . . . . . . Jun 17 17:27\n', 'nn-NO/ . . . . . . . Jun 17 17:27\n', 'pa-IN/ . . . . . . . Jun 17 17:27\n', 'pl/. . . . . . . . . Jun 17 17:27\n', 'pt-BR/ . . . . . . . Jun 17 17:27\n', 'pt-PT/ . . . . . . . Jun 17 17:27\n', 'ro/. . . . . . . . . Jun 17 17:27\n', 'ru/. . . . . . . . . Jun 17 17:27\n', 'si/. . . . . . . . . Jun 17 17:27\n', 'sk/. . . . . . . . . Jun 17 17:27\n', 'sl/. . . . . . . . . Jun 17 17:27\n', 'sq/. . . . . . . . . Jun 17 17:27\n', 'sr/. . . . . . . . . Jun 17 17:27\n', 'sv-SE/ . . . . . . . Jun 17 17:27\n', 'tr/. . . . . . . . . Jun 17 17:27\n', 'uk/. . . . . . . . . Jun 17 17:27\n', 'xpi/ . . . . . . . . Jun 17 17:27\n', 'zh-CN/ . . . . . . . Jun 17 17:27\n', 'zh-TW/ . . . . . . . Jun 17 17:27\n', '\n']
Retrieving list of available localizations for Firefox ...
Please choose the localization (language) for Firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please check the help section of our website at [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/) for steps you can take to resolve this problem.]
  0. af           1. ar           2. be           3. ca        
  4. cs           5. da           6. de           7. el        
  8. en-GB        9. en-US       10. es-AR       11. es-ES     
 12. eu          13. fi          14. fr          15. fy-NL     
 16. ga-IE       17. gu-IN       18. he          19. hu        
 20. id          21. it          22. ja          23. ka        
 24. ko          25. ku          26. lt          27. mk        
 28. mn          29. nb-NO       30. nl          31. nn-NO     
 32. pa-IN       33. pl          34. pt-BR       35. pt-PT     
 36. ro          37. ru          38. si          39. sk        
 40. sl          41. sq          42. sr          43. sv-SE     
 44. tr          45. uk          46. zh-CN       47. zh-TW     

Enter your choice of localization (integer, from 0 to 47): 9
You have chosen localization en-US. Is that correct [y/n]? 
Please enter 'y' or 'n': y
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US      
Ign [http://apt.wicd.net](http://apt.wicd.net) gutsy Release.gpg                                                                                                                   
Ign [http://apt.wicd.net](http://apt.wicd.net) gutsy/extras Translation-en_US                                                                                                      
Hit [http://apt.wicd.net](http://apt.wicd.net) gutsy Release                                                                                                                       
Hit [http://apt.wicd.net](http://apt.wicd.net) gutsy/extras Packages                                                                                                               
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]                                                                                                    
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US                                                                                              
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US                                                                                            
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [189B]                                                                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_US                                                                   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_US                                                             
Get:3 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]                                                                           
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US                                                                         
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release.gpg [191B]                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Translation-en_US                                                                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                                                                         
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                                                                              
Get:5 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]                                                                            
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US                                                                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release.gpg                                                                                         
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release                                                                                            
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_US                                                              
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_US                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release                                                                                  
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US                                                                     
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources                                                                                       
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Translation-en_US                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Translation-en_US                                                                     
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Translation-en_US                                                                   
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release.gpg [189B]                                                                   
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Translation-en_US                                                                 
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Translation-en_US                                                           
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release                                                                                        
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages                                                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Translation-en_US                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                                                                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Translation-en_US                                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_US                                      
Get:7 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release.gpg [189B]                                             
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US                                                           
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages                                                                                  
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages                                                                                
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages                                                                                
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages                                                                      
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Sources                                                                       
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Sources                                                                             
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy Release                                                                                             
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages                                                                                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Translation-en_US                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US                                                           
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Translation-en_US                                                             
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy Release                                                                                         
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates Release                                                                                 
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources                                                                                                        
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources                                                                                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Sources                                                 
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed Release                                                          
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Sources                                     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Sources                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages                            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages                          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages                                           
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages                                  
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Sources                                       
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Sources                                   
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Packages                                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Sources
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) gutsy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) gutsy-proposed/universe Sources
Fetched 7B in 2s (3B/s)  
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox is already the newest version.
The following packages were automatically installed and are no longer required:
  libsdl-gfx1.2-4 kdebase-data java-common kicker unixodbc odbcinst1debian1 kfind kmplayer-base libsdl-image1.2 libsmpeg0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Backing up old Firefox preferences

availableForBackup, KB: 129973624
requiredForBackup, KB: 74044
Slack, KB: 129899580
cp: cannot open `/home/guy/.mozilla/firefox/ifhzv4xz.default/Cache/_CACHE_MAP_' for reading: Permission denied
cp: cannot open `/home/guy/.mozilla/firefox/ifhzv4xz.default/Cache/_CACHE_002_' for reading: Permission denied
cp: cannot open `/home/guy/.mozilla/firefox/ifhzv4xz.default/Cache/_CACHE_003_' for reading: Permission denied
cp: cannot open `/home/guy/.mozilla/firefox/ifhzv4xz.default/Cache/_CACHE_001_' for reading: Permission denied
cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)
Failed to back up profile.
Process returned code 1
Traceback (most recent call last):
  File "/usr/local/bin/ubuntuzilla.py", line 1090, in <module>
    bs.start()
  File "/usr/local/bin/ubuntuzilla.py", line 209, in start
    fi.start()
  File "/usr/local/bin/ubuntuzilla.py", line 236, in start
    self.install()
  File "/usr/local/bin/ubuntuzilla.py", line 537, in install
    self.backupProfile()
  File "/usr/local/bin/ubuntuzilla.py", line 685, in backupProfile
    self.util.execSystemCommand(executionstring="cp -R ~/.mozilla ~/.mozilla_backup_$(date -Iseconds)", errormessage="Failed to back up profile.")
  File "/usr/local/bin/ubuntuzilla.py", line 140, in execSystemCommand
    raise SystemCommandExecutionError, "Command has not completed successfully. If this problem persists, please seek help at our website, " + self.version.url
__main__.SystemCommandExecutionError: Command has not completed successfully. If this problem persists, please seek help at our website, [http://ubuntuzilla.sourceforge.net/](http://ubuntuzilla.sourceforge.net/)
[guy@ubuntu-laptop:~]$

---

### Post by sdowney717 on 2008-07-11
try sudo

sudo ubuntuzilla.py -a install -p firefox -d

you error said cant open due to permissions. sudo ought to fix that

---

### Post by nanotube on 2008-07-11
> **sdowney717 said:**
> try sudo

sudo ubuntuzilla.py -a install -p firefox -d

you error said cant open due to permissions. sudo ought to fix that

hey, no, don't do that. the problem is caused by root ownership of some files in your firefox profile directory - probably because you ran firefox as "sudo firefox" at some point. so to be proper, just restore permissions, and then run ubuntuzilla again as normal, without sudo. so:

```
sudo chown -R guy:guy /home/guy/.mozilla
ubuntuzilla.py -a install -p firefox
```

---


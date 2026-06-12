---
title: "Unmet dependencies on 12.04 Can not update"
date: 2014-03-05
forum: New to Ubuntu
---

### Post by tusi on 2014-03-05
Hello. I have been trying to update my ubuntu server, but no luck for now. This is what I get:


```
janko@ubuntu:/var/cache/apt/archives$ sudo apt-get update && sudo apt-get upgradeIgn http://si.archive.ubuntu.com precise InRelease
Ign http://si.archive.ubuntu.com precise-updates InRelease
Ign http://si.archive.ubuntu.com precise-backports InRelease
Ign http://security.ubuntu.com precise-security InRelease
Hit http://si.archive.ubuntu.com precise Release.gpg  
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://si.archive.ubuntu.com precise-updates Release.gpg
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://si.archive.ubuntu.com precise-backports Release.gpg
Hit http://si.archive.ubuntu.com precise Release     
Hit http://si.archive.ubuntu.com precise-updates Release                                                     
Hit http://si.archive.ubuntu.com precise-backports Release                                                   
Hit http://si.archive.ubuntu.com precise/main Sources                         
Get:3 http://security.ubuntu.com precise-security/main Sources [98.1 kB]     
Hit http://si.archive.ubuntu.com precise/restricted Sources                        
Hit http://si.archive.ubuntu.com precise/universe Sources                          
Hit http://si.archive.ubuntu.com precise/multiverse Sources
Hit http://si.archive.ubuntu.com precise/main amd64 Packages
Hit http://si.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://si.archive.ubuntu.com precise/universe amd64 Packages
Hit http://si.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://si.archive.ubuntu.com precise/main i386 Packages
Hit http://si.archive.ubuntu.com precise/restricted i386 Packages
Hit http://si.archive.ubuntu.com precise/universe i386 Packages
Hit http://si.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://si.archive.ubuntu.com precise/main TranslationIndex
Hit http://si.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://si.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://si.archive.ubuntu.com precise/universe TranslationIndex
Hit http://si.archive.ubuntu.com precise-updates/main Sources
Hit http://si.archive.ubuntu.com precise-updates/restricted Sources
Hit http://si.archive.ubuntu.com precise-updates/universe Sources
Hit http://si.archive.ubuntu.com precise-updates/multiverse Sources
Hit http://si.archive.ubuntu.com precise-updates/main amd64 Packages
Hit http://si.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://si.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://si.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://si.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://si.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://si.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://si.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://si.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://si.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://si.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://si.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://si.archive.ubuntu.com precise-backports/main Sources
Hit http://si.archive.ubuntu.com precise-backports/restricted Sources
Hit http://si.archive.ubuntu.com precise-backports/universe Sources
Hit http://si.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://si.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://si.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://si.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://si.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://si.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://si.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://si.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://si.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://si.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://si.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://si.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://si.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://si.archive.ubuntu.com precise/main Translation-en
Hit http://si.archive.ubuntu.com precise/multiverse Translation-en
Hit http://si.archive.ubuntu.com precise/restricted Translation-en
Hit http://si.archive.ubuntu.com precise/universe Translation-en      
Get:4 http://security.ubuntu.com precise-security/restricted Sources [2494 B]
Get:5 http://security.ubuntu.com precise-security/universe Sources [30.9 kB] 
Hit http://si.archive.ubuntu.com precise-updates/main Translation-en        
Hit http://si.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://si.archive.ubuntu.com precise-updates/restricted Translation-en
Get:6 http://security.ubuntu.com precise-security/multiverse Sources [1782 B]
Get:7 http://security.ubuntu.com precise-security/main amd64 Packages [364 kB]                           
Hit http://si.archive.ubuntu.com precise-updates/universe Translation-en                                   
Hit http://si.archive.ubuntu.com precise-backports/main Translation-en               
Hit http://si.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://si.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                        
Hit http://si.archive.ubuntu.com precise-backports/universe Translation-en                                                                                          
Get:8 http://security.ubuntu.com precise-security/restricted amd64 Packages [4627 B]                                                                                
Get:9 http://security.ubuntu.com precise-security/universe amd64 Packages [91.0 kB]                                                                                 
Get:10 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2443 B]                                                                               
Get:11 http://security.ubuntu.com precise-security/main i386 Packages [388 kB]                                                                                      
Get:12 http://security.ubuntu.com precise-security/restricted i386 Packages [4620 B]                                                                                
Get:13 http://security.ubuntu.com precise-security/universe i386 Packages [95.5 kB]                                                                                 
Get:14 http://security.ubuntu.com precise-security/multiverse i386 Packages [2641 B]                                                                                
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                               
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                                         
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                                         
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                           
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                 
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                           
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                           
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                             
Fetched 1135 kB in 10s (107 kB/s)                                                                                                                                   
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 plymouth : Depends: libplymouth2 (= 0.8.2-2ubuntu30) but 0.8.2-2ubuntu31.1 is installed
            Recommends: plymouth-theme-ubuntu-text but it is not installed or
                        plymouth-theme
E: Unmet dependencies. Try using -f.
```

When I run 'apt-get -f install' I get this:

```
janko@ubuntu:/var/cache/apt/archives$ sudo apt-get -f installReading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  plymouth
Recommended packages:
  plymouth-theme-ubuntu-text plymouth-theme
The following packages will be upgraded:
  plymouth
1 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
10 not fully installed or removed.
Need to get 123 kB of archives.
After this operation, 1024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://si.archive.ubuntu.com/ubuntu/ precise-updates/main plymouth amd64 0.8.2-2ubuntu31.1 [123 kB]
Fetched 123 kB in 0s (265 kB/s) 
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
    LANGUAGE = "en_US:en",
    LC_ALL = (unset),
    LC_TIME = "sl_SI.UTF-8",
    LC_MONETARY = "sl_SI.UTF-8",
    LC_ADDRESS = "sl_SI.UTF-8",
    LC_TELEPHONE = "sl_SI.UTF-8",
    LC_NAME = "sl_SI.UTF-8",
    LC_MEASUREMENT = "sl_SI.UTF-8",
    LC_IDENTIFICATION = "sl_SI.UTF-8",
    LC_NUMERIC = "sl_SI.UTF-8",
    LC_PAPER = "sl_SI.UTF-8",
    LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_ALL to default locale: No such file or directory
(Reading database ... 62226 files and directories currently installed.)
Preparing to replace plymouth 0.8.2-2ubuntu30 (using .../plymouth_0.8.2-2ubuntu31.1_amd64.deb) ...
Unpacking replacement plymouth ...
dpkg: error processing /var/cache/apt/archives/plymouth_0.8.2-2ubuntu31.1_amd64.deb (--unpack):
 unable to stat `./lib/plymouth/script.so' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/plymouth_0.8.2-2ubuntu31.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Info about the system:
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise

Thanks for helping me!

---

### Post by phidia on 2014-03-05
Try issuing > locale and checking what locales you need. Also refer to [this thread]("http://askubuntu.com/questions/162391/how-do-i-fix-my-locale-issue").

---

### Post by tusi on 2014-03-05
Tried some things, no luck:

```
janko@ubuntu:/var/cache/apt/archives$ localelocale: Cannot set LC_ALL to default locale: No such file or directory
LANG=en_US.UTF-8
LANGUAGE=en_US:en
LC_CTYPE="en_US.UTF-8"
LC_NUMERIC=sl_SI.UTF-8
LC_TIME=sl_SI.UTF-8
LC_COLLATE="en_US.UTF-8"
LC_MONETARY=sl_SI.UTF-8
LC_MESSAGES="en_US.UTF-8"
LC_PAPER=sl_SI.UTF-8
LC_NAME=sl_SI.UTF-8
LC_ADDRESS=sl_SI.UTF-8
LC_TELEPHONE=sl_SI.UTF-8
LC_MEASUREMENT=sl_SI.UTF-8
LC_IDENTIFICATION=sl_SI.UTF-8
LC_ALL=
janko@ubuntu:/var/cache/apt/archives$ sudo locale-gen sl_SI.UTF-8
Generating locales...
  sl_SI.UTF-8... done
Generation complete.
janko@ubuntu:/var/cache/apt/archives$ sudo dpkg-reconfigure locales
Generating locales...
  en_AG.UTF-8... done
  en_AU.UTF-8... done
  en_BW.UTF-8... done
  en_CA.UTF-8... done
  en_DK.UTF-8... done
  en_GB.UTF-8... done
  en_HK.UTF-8... done
  en_IE.UTF-8... done
  en_IN.UTF-8... done
  en_NG.UTF-8... done
  en_NZ.UTF-8... done
  en_PH.UTF-8... done
  en_SG.UTF-8... done
  en_US.UTF-8... done
  en_ZA.UTF-8... done
  en_ZM.UTF-8... done
  en_ZW.UTF-8... done
  sl_SI.UTF-8... up-to-date
Generation complete.
janko@ubuntu:/var/cache/apt/archives$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  plymouth
Recommended packages:
  plymouth-theme-ubuntu-text plymouth-theme
The following packages will be upgraded:
  plymouth
1 upgraded, 0 newly installed, 0 to remove and 190 not upgraded.
10 not fully installed or removed.
Need to get 0 B/123 kB of archives.
After this operation, 1024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 62226 files and directories currently installed.)
Preparing to replace plymouth 0.8.2-2ubuntu30 (using .../plymouth_0.8.2-2ubuntu31.1_amd64.deb) ...
Unpacking replacement plymouth ...
dpkg: error processing /var/cache/apt/archives/plymouth_0.8.2-2ubuntu31.1_amd64.deb (--unpack):
 unable to stat `./lib/plymouth/script.so' (which I was about to install): Input/output error
Errors were encountered while processing:
 /var/cache/apt/archives/plymouth_0.8.2-2ubuntu31.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by sandyd on 2014-03-05
```

Input/output error
```
sounds like an HDD error - Have you checked your HDD's smart status?

---

### Post by tusi on 2014-03-05
I have a system installed on USB disk.

Check of the system:
```
janko@ubuntu:~$ smartctl -H /dev/sdc
smartctl 5.41 2011-06-09 r3365 [x86_64-linux-3.2.0-23-generic] (local build)
Copyright (C) 2002-11 by Bruce Allen, http://smartmontools.sourceforge.net


/dev/sdc: Unsupported USB bridge [0x04cf:0x8818 (0xa305)]
Smartctl: please specify device type with the -d option.


Use smartctl -h to get a usage summary


janko@ubuntu:~$ sudo badblocks -v /dev/sdc > bad-blocks-result
Checking blocks 0 to 9903599
Checking for bad blocks (read-only test): done                                                 
Pass completed, 0 bad blocks found. (0/0/0 errors)
```

I also copied the system with dd to USB stick and run it from there and I got the same error.

---

### Post by tusi on 2014-03-11
Anyone else with any idea?

---

### Post by ibjsb4 on 2014-03-11
I feel it cannot be assumed, so sorry if this sounds real basic, but ..

Have you tried cleaning the cache?

```
sudo apt-get clean
```

Since this is a production machine I think it should be backed up first.

```
sudo cp -r /var/cache /var/cache.old
```

---


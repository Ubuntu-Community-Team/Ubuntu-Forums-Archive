---
title: "Software Center and Update Manager does not open, Ubuntu 12.04"
date: 2012-10-23
forum: New to Ubuntu
---

### Post by Paari on 2012-10-23
Hi. I'm a complete newbie to linux. I'm currently using ubuntu 12.04. I tried to install jdk in my linux and I strrongly believe that i've crashed my software center.  I've edited my "sources.list" with  Ubuntu Sources List Generator and tried to update with the following code
```

sudo apt-get update && sudo apt-get upgrade -y

```

I get the following error:popcorn:
```

paari@ubuntu:~/Desktop$ sudo apt-get update && sudo apt-get upgrade -y
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release.gpg         
Get:2 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:3 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release                   
Get:4 http://archive.ubuntu.com precise-updates Release [49.6 kB]              
Get:5 http://security.ubuntu.com precise-security/main amd64 Packages [177 kB]
Hit http://archive.ubuntu.com precise/main amd64 Packages     
Hit http://archive.ubuntu.com precise/restricted amd64 Packages
Hit http://archive.ubuntu.com precise/universe amd64 Packages
Hit http://archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://archive.ubuntu.com precise/main i386 Packages
Hit http://archive.ubuntu.com precise/restricted i386 Packages
Hit http://archive.ubuntu.com precise/universe i386 Packages
Hit http://archive.ubuntu.com precise/multiverse i386 Packages
Hit http://archive.ubuntu.com precise/main TranslationIndex
Hit http://archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://archive.ubuntu.com precise/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise/universe TranslationIndex        
Get:6 http://archive.ubuntu.com precise-updates/main amd64 Packages [405 kB]
Get:7 http://security.ubuntu.com precise-security/restricted amd64 Packages [3,969 B]
Get:8 http://security.ubuntu.com precise-security/universe amd64 Packages [48.6 kB]
Get:9 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,188 B]
Get:10 http://security.ubuntu.com precise-security/main i386 Packages [183 kB] 
Get:11 http://security.ubuntu.com precise-security/restricted i386 Packages [3,968 B]
Get:12 http://security.ubuntu.com precise-security/universe i386 Packages [48.7 kB]
Get:13 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,357 B]
Hit http://security.ubuntu.com precise-security/main TranslationIndex          
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:14 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [8,215 B]
Get:15 http://archive.ubuntu.com precise-updates/universe amd64 Packages [149 kB]
Get:16 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,948 B]
Get:17 http://archive.ubuntu.com precise-updates/main i386 Packages [410 kB]   
Get:18 http://archive.ubuntu.com precise-updates/restricted i386 Packages [8,218 B]
Get:19 http://archive.ubuntu.com precise-updates/universe i386 Packages [149 kB]
Get:20 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [9,930 B]
Hit http://archive.ubuntu.com precise-updates/main TranslationIndex            
Hit http://archive.ubuntu.com precise-updates/multiverse TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/restricted TranslationIndex      
Hit http://archive.ubuntu.com precise-updates/universe TranslationIndex        
Hit http://archive.ubuntu.com precise/main Translation-en                      
Hit http://archive.ubuntu.com precise/multiverse Translation-en                
Hit http://archive.ubuntu.com precise/restricted Translation-en                
Hit http://archive.ubuntu.com precise/universe Translation-en                  
Hit http://archive.ubuntu.com precise-updates/main Translation-en              
Hit http://archive.ubuntu.com precise-updates/multiverse Translation-en        
Hit http://archive.ubuntu.com precise-updates/restricted Translation-en        
Hit http://archive.ubuntu.com precise-updates/universe Translation-en          
Fetched 1,717 kB in 25s (68.4 kB/s)                                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  accountsservice apparmor apport apport-gtk bind9-host dnsutils firefox
  firefox-globalmenu firefox-gnome-support libaccountsservice0 libbind9-80
  libdns81 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa libglu1-mesa
  libgnome2-common libisc83 libisccc80 libisccfg82 liblwres80
  libparted0debian1 libxatracker1 login multiarch-support onboard parted
  passwd python-apport python-problem-report sessioninstaller thunderbird
  thunderbird-globalmenu thunderbird-gnome-support update-manager
  update-manager-core update-notifier update-notifier-common wpasupplicant
  x11-utils xserver-xorg-video-intel xterm
42 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
10 not fully installed or removed.
Need to get 0 B/54.1 MB of archives.
After this operation, 2,130 kB of additional disk space will be used.
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 172334 files and directories currently installed.)
Preparing to replace software-center 5.2.6 (using .../software-center_5.2.6_all.deb) ...
/var/lib/dpkg/info/software-center.prerm: 6: /var/lib/dpkg/info/software-center.prerm: pyclean: not found
dpkg: warning: subprocess old pre-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/prerm: 6: /var/lib/dpkg/tmp.ci/prerm: pyclean: not found
dpkg: error processing /var/cache/apt/archives/software-center_5.2.6_all.deb (--unpack):
 subprocess new pre-removal script returned error exit status 127
/var/lib/dpkg/info/software-center.postinst: 8: /var/lib/dpkg/info/software-center.postinst: pycompile: not found
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 127
Preparing to replace login 1:4.1.4.2+svn3283-3ubuntu5 (using .../login_1%3a4.1.4.2+svn3283-3ubuntu5.1_amd64.deb) ...
Unpacking replacement login ...
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/software-center_5.2.6_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
paari@ubuntu:~/Desktop$

```

Can somebody help me out. Thanks in advance:)

---

### Post by NikTh on 2012-10-23
Hi, 
try 
```
sudo apt-get remove --purge software-center software-center-aptdaemon-plugins
sudo apt-get clean all 
sudo apt-get autoclean 
sudo dpkg --configure -a 
sudo apt-get update && sudo apt-get dist-upgrade 
sudo apt-get install software-center
```Thanks

---

### Post by Paari on 2012-10-26
Thank you NiKTh. That worked I'm saved Thanks a lot !!! :) :) :)  I've tried all the last 5 lines except 
```

sudo apt-get remove --purge software-center software-centre-aptdaemon-plugins

```That one helped. Thank you:)

---


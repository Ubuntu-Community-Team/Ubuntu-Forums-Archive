---
title: "Package Manager error"
date: 2014-02-23
forum: New to Ubuntu
---

### Post by amkashirin on 2014-02-23
Hello,
I'm new ubuntu user. Please help resolve next error:
[ATTACH=CONFIG]250599[/ATTACH]

---

### Post by QIII on 2014-02-23
Hello!

Would you please run
```
sudo apt-get update
```

and

```
sudo apt-get upgrade
```

in the terminal and post the results back here.

When you post back, please use code tags:

1. If you are using New Reply button - highlight text and use the # button in the text box header.

2. If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by amkashirin on 2014-02-23
1.result of "sudo apt-get update":
```

yumoh@SDR:~$ sudo apt-get update
[sudo] password for yumoh: 
Ign http://mirror.yandex.ru stable InRelease
Ign http://ru.archive.ubuntu.com saucy InRelease                                                                
Hit http://mirror.yandex.ru stable Release.gpg                                                                  
Ign http://ru.archive.ubuntu.com saucy-updates InRelease                                   
Ign http://security.ubuntu.com saucy-security InRelease                                    
Ign http://extras.ubuntu.com saucy InRelease                                               
Ign http://archive.canonical.com saucy InRelease                                           
Ign http://ru.archive.ubuntu.com saucy-backports InRelease                                 
Hit http://mirror.yandex.ru stable Release                                                 
Hit http://security.ubuntu.com saucy-security Release.gpg                                                       
Get:1 http://extras.ubuntu.com saucy Release.gpg [72 B]                                    
Hit http://ru.archive.ubuntu.com saucy Release.gpg                                                              
Hit http://archive.canonical.com saucy Release.gpg                                         
Hit http://mirror.yandex.ru stable/main amd64 Packages                                     
Get:2 http://ru.archive.ubuntu.com saucy-updates Release.gpg [933 B]                       
Hit http://security.ubuntu.com saucy-security Release                                                           
Hit http://mirror.yandex.ru stable/non-free amd64 Packages                                                      
Hit http://extras.ubuntu.com saucy Release                                                                      
Hit http://archive.canonical.com saucy Release                                                                  
Hit http://ru.archive.ubuntu.com saucy-backports Release.gpg                                                    
Hit http://mirror.yandex.ru stable/contrib amd64 Packages                                                       
Hit http://security.ubuntu.com saucy-security/main Sources                                 
Hit http://extras.ubuntu.com saucy/main Sources                                            
Hit http://mirror.yandex.ru stable/main i386 Packages                                      
Hit http://ru.archive.ubuntu.com saucy Release                                             
Hit http://security.ubuntu.com saucy-security/restricted Sources                                                
Hit http://extras.ubuntu.com saucy/main amd64 Packages                                                          
Hit http://archive.canonical.com saucy/partner Sources                                                          
Hit http://mirror.yandex.ru stable/non-free i386 Packages                                                       
Get:3 http://ru.archive.ubuntu.com saucy-updates Release [49,6 kB]                         
Hit http://security.ubuntu.com saucy-security/universe Sources                                                  
Hit http://mirror.yandex.ru stable/contrib i386 Packages                                                        
Hit http://archive.canonical.com saucy/partner amd64 Packages                                        
Hit http://extras.ubuntu.com saucy/main i386 Packages                                                
Hit http://mirror.yandex.ru stable/contrib Translation-en                                            
Hit http://security.ubuntu.com saucy-security/multiverse Sources                                                
Hit http://archive.canonical.com saucy/partner i386 Packages                                                    
Hit http://mirror.yandex.ru stable/main Translation-en                                               
Hit http://mirror.yandex.ru stable/non-free Translation-en                                                      
Hit http://security.ubuntu.com saucy-security/main amd64 Packages                                               
Hit http://ru.archive.ubuntu.com saucy-backports Release                                    
Hit http://ru.archive.ubuntu.com saucy/main Sources                                                             
Hit http://security.ubuntu.com saucy-security/restricted amd64 Packages                     
Hit http://ru.archive.ubuntu.com saucy/restricted Sources             
Hit http://ru.archive.ubuntu.com saucy/universe Sources               
Hit http://security.ubuntu.com saucy-security/universe amd64 Packages 
Hit http://ru.archive.ubuntu.com saucy/multiverse Sources             
Hit http://security.ubuntu.com saucy-security/multiverse amd64 Packages
Hit http://ru.archive.ubuntu.com saucy/main amd64 Packages            
Hit http://ru.archive.ubuntu.com saucy/restricted amd64 Packages      
Hit http://security.ubuntu.com saucy-security/main i386 Packages      
Hit http://ru.archive.ubuntu.com saucy/universe amd64 Packages        
Hit http://security.ubuntu.com saucy-security/restricted i386 Packages
Hit http://ru.archive.ubuntu.com saucy/multiverse amd64 Packages      
Hit http://security.ubuntu.com saucy-security/universe i386 Packages                        
Hit http://ru.archive.ubuntu.com saucy/main i386 Packages                                   
Hit http://security.ubuntu.com saucy-security/multiverse i386 Packages
Hit http://ru.archive.ubuntu.com saucy/restricted i386 Packages       
Hit http://ru.archive.ubuntu.com saucy/universe i386 Packages         
Ign http://extras.ubuntu.com saucy/main Translation-en_US             
Hit http://ru.archive.ubuntu.com saucy/multiverse i386 Packages       
Ign http://extras.ubuntu.com saucy/main Translation-en                                      
Ign http://archive.canonical.com saucy/partner Translation-en_US                            
Hit http://security.ubuntu.com saucy-security/main Translation-en     
Ign http://archive.canonical.com saucy/partner Translation-en
Hit http://ru.archive.ubuntu.com saucy/main Translation-en
Hit http://ru.archive.ubuntu.com saucy/multiverse Translation-en
Hit http://security.ubuntu.com saucy-security/multiverse Translation-en
Hit http://ru.archive.ubuntu.com saucy/restricted Translation-en
Hit http://ru.archive.ubuntu.com saucy/universe Translation-en
Hit http://security.ubuntu.com saucy-security/restricted Translation-en
Get:4 http://ru.archive.ubuntu.com saucy-updates/main Sources [71,8 kB]
Hit http://security.ubuntu.com saucy-security/universe Translation-en
Get:5 http://ru.archive.ubuntu.com saucy-updates/restricted Sources [14 B]
Get:6 http://ru.archive.ubuntu.com saucy-updates/universe Sources [66,8 kB]
Get:7 http://ru.archive.ubuntu.com saucy-updates/multiverse Sources [1 358 B]
Get:8 http://ru.archive.ubuntu.com saucy-updates/main amd64 Packages [203 kB]
Get:9 http://ru.archive.ubuntu.com saucy-updates/restricted amd64 Packages [14 B]
Get:10 http://ru.archive.ubuntu.com saucy-updates/universe amd64 Packages [153 kB]
Get:11 http://ru.archive.ubuntu.com saucy-updates/multiverse amd64 Packages [1 572 B]                           
Get:12 http://ru.archive.ubuntu.com saucy-updates/main i386 Packages [201 kB]                                   
Get:13 http://ru.archive.ubuntu.com saucy-updates/restricted i386 Packages [14 B]                               
Ign http://security.ubuntu.com saucy-security/main Translation-en_US                                            
Get:14 http://ru.archive.ubuntu.com saucy-updates/universe i386 Packages [154 kB]                               
Ign http://security.ubuntu.com saucy-security/multiverse Translation-en_US                                      
Ign http://security.ubuntu.com saucy-security/restricted Translation-en_US                                      
Ign http://security.ubuntu.com saucy-security/universe Translation-en_US                                        
Get:15 http://ru.archive.ubuntu.com saucy-updates/multiverse i386 Packages [1 763 B]                            
Hit http://ru.archive.ubuntu.com saucy-updates/main Translation-en                                              
Hit http://ru.archive.ubuntu.com saucy-updates/multiverse Translation-en                                        
Hit http://ru.archive.ubuntu.com saucy-updates/restricted Translation-en                                        
Hit http://ru.archive.ubuntu.com saucy-updates/universe Translation-en                                          
Hit http://ru.archive.ubuntu.com saucy-backports/main Sources                                                   
Hit http://ru.archive.ubuntu.com saucy-backports/restricted Sources                                             
Hit http://ru.archive.ubuntu.com saucy-backports/universe Sources                                               
Hit http://ru.archive.ubuntu.com saucy-backports/multiverse Sources                                             
Hit http://ru.archive.ubuntu.com saucy-backports/main amd64 Packages                                            
Hit http://ru.archive.ubuntu.com saucy-backports/restricted amd64 Packages                                      
Hit http://ru.archive.ubuntu.com saucy-backports/universe amd64 Packages                                        
Hit http://ru.archive.ubuntu.com saucy-backports/multiverse amd64 Packages                                      
Hit http://ru.archive.ubuntu.com saucy-backports/main i386 Packages                                             
Hit http://ru.archive.ubuntu.com saucy-backports/restricted i386 Packages                                       
Hit http://ru.archive.ubuntu.com saucy-backports/universe i386 Packages                                         
Hit http://ru.archive.ubuntu.com saucy-backports/multiverse i386 Packages                                       
Hit http://ru.archive.ubuntu.com saucy-backports/main Translation-en                                            
Hit http://ru.archive.ubuntu.com saucy-backports/multiverse Translation-en                                      
Hit http://ru.archive.ubuntu.com saucy-backports/restricted Translation-en                                      
Hit http://ru.archive.ubuntu.com saucy-backports/universe Translation-en                                        
Ign http://ru.archive.ubuntu.com saucy/main Translation-en_US                                                   
Ign http://ru.archive.ubuntu.com saucy/multiverse Translation-en_US                                             
Ign http://ru.archive.ubuntu.com saucy/restricted Translation-en_US                                             
Ign http://ru.archive.ubuntu.com saucy/universe Translation-en_US                                               
Ign http://ru.archive.ubuntu.com saucy-updates/main Translation-en_US                                           
Ign http://ru.archive.ubuntu.com saucy-updates/multiverse Translation-en_US                                     
Ign http://ru.archive.ubuntu.com saucy-updates/restricted Translation-en_US                                     
Ign http://ru.archive.ubuntu.com saucy-updates/universe Translation-en_US                                       
Ign http://ru.archive.ubuntu.com saucy-backports/main Translation-en_US                                         
Ign http://ru.archive.ubuntu.com saucy-backports/multiverse Translation-en_US                                   
Ign http://ru.archive.ubuntu.com saucy-backports/restricted Translation-en_US                                   
Ign http://ru.archive.ubuntu.com saucy-backports/universe Translation-en_US                                     
Fetched 905 kB in 17s (52,1 kB/s)                                                                               
Reading package lists... Done


```

2. result of "sudo apt-get upgrade":
```

yumoh@SDR:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  console-setup hunspell-en-us initramfs-tools initscripts keyboard-configuration libnih-dbus1 libnih1
  python-glade2 python-gtk2 speech-dispatcher ttf-punjabi-fonts xdg-utils xorg xserver-xorg-input-vmmouse
  xserver-xorg-video-all
The following packages will be upgraded:
  app-install-data dkms eog gstreamer0.10-plugins-bad gstreamer0.10-plugins-ugly libgstreamer-plugins-bad0.10-0
  libio-pty-perl libjpeg8 libjpeg8:i386 liblist-moreutils-perl libmpcdec6 libnet-libidn-perl
  libperlio-gzip-perl libquvi-scripts libsocket6-perl libspeechd2 libsub-identify-perl libsub-name-perl
  libtext-charwidth-perl libtiff5 libtiff5:i386 libxvmc1 linux-firmware myspell-en-gb myspell-en-za
  mythes-en-us nano nautilus-share obexd-client policykit-1-gnome ppp procps python-cairo python-openssl
  remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc rsyslog rtkit sysv-rc unattended-upgrades
  uuid-runtime wpasupplicant x11-common xserver-xorg xserver-xorg-input-all xterm
48 upgraded, 0 newly installed, 0 to remove and 15 not upgraded.
Need to get 51,2 MB of archives.
After this operation, 9 088 kB disk space will be freed.
Do you want to continue [Y/n]? Y 
Get:1 http://ru.archive.ubuntu.com/ubuntu/ saucy-updates/main eog amd64 3.8.2-1ubuntu1.1 [687 kB]
Get:2 http://mirror.yandex.ru/debian/ stable/main libjpeg8 i386 8d-1 [132 kB]
Get:3 http://mirror.yandex.ru/debian/ stable/main libjpeg8 amd64 8d-1 [134 kB]
Get:4 http://ru.archive.ubuntu.com/ubuntu/ saucy-updates/main linux-firmware all 1.116.2 [26,5 MB]
Get:5 http://mirror.yandex.ru/debian/ stable/main libmpcdec6 amd64 2:0.1~r459-4 [36,2 kB]                       
Get:6 http://mirror.yandex.ru/debian/ stable/main libtiff5 i386 4.0.2-6+deb7u2 [237 kB]                         
Get:7 http://mirror.yandex.ru/debian/ stable/main libtiff5 amd64 4.0.2-6+deb7u2 [234 kB]                        
Get:8 http://mirror.yandex.ru/debian/ stable/main gstreamer0.10-plugins-bad amd64 0.10.23-7.1 [1 977 kB]        
Get:9 http://mirror.yandex.ru/debian/ stable/main libgstreamer-plugins-bad0.10-0 amd64 0.10.23-7.1 [766 kB]     
Get:10 http://mirror.yandex.ru/debian/ stable/main sysv-rc all 2.88dsf-41+deb7u1 [81,8 kB]                      
Get:11 http://mirror.yandex.ru/debian/ stable/main nano amd64 2.2.6-1+b1 [586 kB]                               
Get:12 http://mirror.yandex.ru/debian/ stable/main procps amd64 1:3.3.3-3 [252 kB]                              
Get:13 http://mirror.yandex.ru/debian/ stable/main rsyslog amd64 5.8.11-3 [546 kB]                              
Get:14 http://mirror.yandex.ru/debian/ stable/main libtext-charwidth-perl amd64 0.04-7+b1 [11,2 kB]             
Get:15 http://mirror.yandex.ru/debian/ stable/main app-install-data all 2012.06.16.1 [9 416 kB]                 
Get:16 http://mirror.yandex.ru/debian/ stable/main dkms all 2.2.0.3-1.2 [77,4 kB]                               
Get:17 http://mirror.yandex.ru/debian/ stable/main gstreamer0.10-plugins-ugly amd64 0.10.19-2+b2 [495 kB]       
Get:18 http://mirror.yandex.ru/debian/ stable/main libio-pty-perl amd64 1:1.08-1+b2 [40,0 kB]                   
Get:19 http://mirror.yandex.ru/debian/ stable/main liblist-moreutils-perl amd64 0.33-1+b1 [52,5 kB]             
Get:20 http://mirror.yandex.ru/debian/ stable/main libnet-libidn-perl amd64 0.12.ds-1+b3 [21,2 kB]              
Get:21 http://mirror.yandex.ru/debian/ stable/main libperlio-gzip-perl amd64 0.18-1+b2 [19,0 kB]                
Get:22 http://mirror.yandex.ru/debian/ stable/main libsocket6-perl amd64 0.23-1+b2 [26,4 kB]                    
Get:23 http://mirror.yandex.ru/debian/ stable/main libspeechd2 amd64 0.7.1-6.2 [21,6 kB]                        
Get:24 http://mirror.yandex.ru/debian/ stable/main libsub-identify-perl amd64 0.04-1+b2 [9 736 B]               
Get:25 http://mirror.yandex.ru/debian/ stable/main libsub-name-perl amd64 0.05-1+b2 [10,2 kB]                   
Get:26 http://mirror.yandex.ru/debian/ stable/main x11-common all 1:7.7+3~deb7u1 [284 kB]                       
Get:27 http://mirror.yandex.ru/debian/ stable/main libxvmc1 amd64 2:1.0.7-1+deb7u2 [24,4 kB]                    
Get:28 http://mirror.yandex.ru/debian/ stable/main myspell-en-gb all 1:3.3.0-4 [252 kB]                         
Get:29 http://mirror.yandex.ru/debian/ stable/main myspell-en-za all 1:3.3.0-4 [280 kB]                         
Get:30 http://mirror.yandex.ru/debian/ stable/main mythes-en-us all 1:3.3.0-4 [5 144 kB]                        
Get:31 http://mirror.yandex.ru/debian/ stable/main nautilus-share amd64 0.7.3-1+b1 [73,2 kB]                    
Get:32 http://mirror.yandex.ru/debian/ stable/main obexd-client amd64 0.46-1+b1 [79,1 kB]                       
Get:33 http://mirror.yandex.ru/debian/ stable/main policykit-1-gnome amd64 0.105-2 [89,1 kB]                    
Get:34 http://mirror.yandex.ru/debian/ stable/main ppp amd64 2.4.5-5.1+b1 [382 kB]                              
Get:35 http://mirror.yandex.ru/debian/ stable/main python-cairo amd64 1.8.8-1+b2 [84,2 kB]                      
Get:36 http://mirror.yandex.ru/debian/ stable/main python-openssl amd64 0.13-2+deb7u1 [175 kB]                  
Get:37 http://mirror.yandex.ru/debian/ stable/main remmina-plugin-vnc amd64 1.0.0-4+deb7u1 [23,9 kB]            
Get:38 http://mirror.yandex.ru/debian/ stable/main remmina-plugin-rdp amd64 1.0.0-4+deb7u1 [36,0 kB]            
Get:39 http://mirror.yandex.ru/debian/ stable/main remmina amd64 1.0.0-4+deb7u1 [136 kB]                        
Get:40 http://mirror.yandex.ru/debian/ stable/main remmina-common all 1.0.0-4+deb7u1 [185 kB]                   
Get:41 http://mirror.yandex.ru/debian/ stable/main rtkit amd64 0.10-2+wheezy1 [36,9 kB]                         
Get:42 http://mirror.yandex.ru/debian/ stable/main unattended-upgrades all 0.79.5 [49,1 kB]                     
Get:43 http://mirror.yandex.ru/debian/ stable/main uuid-runtime amd64 2.20.1-5.3 [60,2 kB]                      
Get:44 http://mirror.yandex.ru/debian/ stable/main wpasupplicant amd64 1.0-3+b2 [608 kB]                        
Get:45 http://mirror.yandex.ru/debian/ stable/main xserver-xorg-input-all amd64 1:7.7+3~deb7u1 [36,1 kB]        
Get:46 http://mirror.yandex.ru/debian/ stable/main xserver-xorg amd64 1:7.7+3~deb7u1 [114 kB]                   
Get:47 http://mirror.yandex.ru/debian/ stable/main xterm amd64 278-4 [613 kB]                                   
Get:48 http://mirror.yandex.ru/debian/ stable/main libquvi-scripts all 0.4.19-1~deb7u1 [43,9 kB]                
Fetched 51,2 MB in 2min 31s (337 kB/s)                                                                          
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 240061 files and directories currently installed.)
Preparing to replace libjpeg8:i386 8c-2ubuntu8 (using .../libjpeg8_8d-1_i386.deb) ...
De-configuring libjpeg8:amd64 ...
Unpacking replacement libjpeg8:i386 ...
dpkg: error processing /var/cache/apt/archives/libjpeg8_8d-1_i386.deb (--unpack):
 trying to overwrite '/usr/lib/i386-linux-gnu/libjpeg.so.8', which is also in package libjpeg-turbo8:i386 1.3.0-0ubuntu1.1
Preparing to replace libjpeg8:amd64 8c-2ubuntu8 (using .../libjpeg8_8d-1_amd64.deb) ...
De-configuring libjpeg8:i386 ...
Unpacking replacement libjpeg8:amd64 ...
dpkg: error processing /var/cache/apt/archives/libjpeg8_8d-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libjpeg.so.8', which is also in package libjpeg-turbo8:amd64 1.3.0-0ubuntu1.1
Errors were encountered while processing:
 /var/cache/apt/archives/libjpeg8_8d-1_i386.deb
 /var/cache/apt/archives/libjpeg8_8d-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by amkashirin on 2014-02-25
Hello! Please help.

---

### Post by ptn107 on 2014-02-25
You are mixing Debian and Ubuntu sources.  They are _not_ compatible.  Remove all of the lines in your* /etc/apt/sources.list* file pertaining to *[http://mirror.yandex.ru/debian/](http://mirror.yandex.ru/debian/)* and try again.  If you don't see any in your * /etc/apt/sources.list* check the */etc/apt/sources.list.d/* folder.

---

### Post by amkashirin on 2014-02-25
Thanks!

---


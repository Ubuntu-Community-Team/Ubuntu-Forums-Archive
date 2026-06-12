---
title: "Cannot Run Update Manager"
date: 2013-04-02
forum: New to Ubuntu
---

### Post by candra on 2013-04-02
I am running Ubuntu 12.0.4 and can no longer run my update manager. This is the error I receive:

[I][B]The package system is broken

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f[/B][/I]

How do I get this fixed?

thanks 
Candra

---

### Post by alphacrucis2 on 2013-04-02
Did you try the suggested command (sudo apt-get install -f)? Post the output of that command.

---

### Post by candra on 2013-04-02
Here it is - pardon the delay - had some on-line issues....

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunistring0:i386 libqt4-designer:i386 calligra-l10n-engb libgomp1:i386
  libqt4-opengl:i386 calligra-l10n-zhcn libmp3lame0:i386 libcroco3:i386
  libqt4-svg:i386 libvorbisenc2:i386 libgettextpo0:i386 libvorbis0a:i386
  libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bamfdaemon libbamf0 libbamf3-0
The following packages will be upgraded:
  bamfdaemon libbamf0 libbamf3-0
3 upgraded, 0 newly installed, 0 to remove and 91 not upgraded.
1 not fully installed or removed.
Need to get 0 B/162 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 483647 files and directories currently installed.)
Preparing to replace libbamf0 0.2.124.2-0ubuntu1 (using .../libbamf0_0.2.126-0ubuntu1_amd64.deb) ...
Unpacking replacement libbamf0 ...
Preparing to replace libbamf3-0 0.2.124.2-0ubuntu1 (using .../libbamf3-0_0.2.126-0ubuntu1_amd64.deb) ...
Unpacking replacement libbamf3-0 ...
Preparing to replace bamfdaemon 0.2.124.2-0ubuntu1 (using .../bamfdaemon_0.2.126-0ubuntu1_amd64.deb) ...
Unpacking replacement bamfdaemon ...
Setting up bamfdaemon (0.2.126-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf.index...
Setting up libbamf0 (0.2.126-0ubuntu1) ...
Setting up libbamf3-0 (0.2.126-0ubuntu1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by candra on 2013-04-02
The matter is solved - the update manager seems to be functinoing properly - I am no longer getting that error message...thank you!!

---

### Post by ronald577 on 2013-04-03
Thank you for sharing the command. Even i was having the same problem with my update manager. But still its showing the error. Any command to fix it?

---

### Post by alphacrucis2 on 2013-04-03
> **ronald577 said:**
> Thank you for sharing the command. Even i was having the same problem with my update manager. But still its showing the error. Any command to fix it?

What error message to you get after you run the ```
sudo apt-get install -f
``` command as above. The error message or messages should give an indication of what the problem is.

---

### Post by candra2 on 2013-08-11
I am having the same problem, but this time when I type in *sudo apt-get install -f *the problem is not resolved. 

Rather I get this code:

sudo apt-get install -f
[sudo] password for ---: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb thunderbird-locale-en-us libqt4-designer:i386 calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386 libgettextpo0:i386
  thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libssl1.0.0 libssl1.0.0:i386
The following packages will be upgraded:
  libssl1.0.0 libssl1.0.0:i386
2 upgraded, 0 newly installed, 0 to remove and 110 not upgraded.
2 not fully installed or removed.
Need to get 2,057 kB of archives.
After this operation, 1,024 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libssl1.0.0 i386 1.0.1-4ubuntu5.10 [1,008 kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main libssl1.0.0 amd64 1.0.1-4ubuntu5.10 [1,048 kB]                                                                                                                                                                             
Fetched 2,057 kB in 23s (88.2 kB/s)                                                                                                                                                                                                                                                        
Preconfiguring packages ...
(Reading database ... 666818 files and directories currently installed.)
Preparing to replace libssl1.0.0 1.0.1-4ubuntu5.9 (using .../libssl1.0.0_1.0.1-4ubuntu5.10_amd64.deb) ...
Unpacking replacement libssl1.0.0 ...
dpkg: error processing libssl1.0.0 (--configure):
 libssl1.0.0:amd64 1.0.1-4ubuntu5.10 cannot be configured because libssl1.0.0:i386 is in a different version (1.0.1-4ubuntu5.9)
E: Sub-process /usr/bin/dpkg returned an error code (1)
---------Parallels-Ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb thunderbird-locale-en-us libqt4-designer:i386 calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386 libgettextpo0:i386
  thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be upgraded:
  libssl1.0.0:i386
1 upgraded, 0 newly installed, 0 to remove and 110 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,008 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libssl1.0.0

Anyone have any suggestions?

Also the update manager gives me this message:

The following packages have unmet dependencies:

libssl1.0.0: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is installed
             Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
libssl1.0.0:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed


Thanks, 
candra

---

### Post by candra2 on 2013-08-13
Please exuse the repost, but I am still struggling with this issue - any help is greatly appreciated...

Candra

---

### Post by ian-weisser on 2013-08-14
> **candra2 said:**
> [COLOR=#ff0000]libssl1.0.0[/COLOR]: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.4 is installed
             Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
[COLOR=#ff0000]libssl1.0.0:i386[/COLOR]: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.4 is installed
                  Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed

The system seems to be trying to tell you to not install two different versions of the same package.
It's right. Don't do that.

Run the command 'apt-cache policy' and post the entire result here.

---

### Post by philinux on 2013-08-14
> **candra2 said:**
> Please exuse the repost, but I am still struggling with this issue - any help is greatly appreciated...

Candra

Run this but do not hit the Y key blindly. Post back what it says it's going to do. And use the code wrap on the results. Highlight the output in your reply and click the # code tags button

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by candra2 on 2013-08-14
here is the output I got...


```
:~$ sudo apt-get update && sudo apt-get dist-upgrade
[sudo] password for d: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                   
Hit http://security.ubuntu.com precise-security Release.gpg          
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]            
Hit http://us.archive.ubuntu.com precise Release                                         
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                     
Hit http://security.ubuntu.com precise-security Release                                                                                       
Hit http://extras.ubuntu.com precise Release                                                                              
Hit http://us.archive.ubuntu.com precise-backports Release                                                                
Hit http://security.ubuntu.com precise-security/main Sources                                       
Hit http://extras.ubuntu.com precise/main Sources                                                                                                       
Hit http://us.archive.ubuntu.com precise/main Sources                                                                          
Hit http://us.archive.ubuntu.com precise/restricted Sources           
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://security.ubuntu.com precise-security/restricted Sources                          
Hit http://security.ubuntu.com precise-security/universe Sources                            
Hit http://security.ubuntu.com precise-security/multiverse Sources                          
Hit http://security.ubuntu.com precise-security/main amd64 Packages                         
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages                   
Hit http://us.archive.ubuntu.com precise/multiverse Sources                                 
Hit http://us.archive.ubuntu.com precise/main amd64 Packages                                
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages                          
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages                            
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages                          
Hit http://us.archive.ubuntu.com precise/main i386 Packages                                 
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages                           
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                             
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                           
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                              
Hit http://security.ubuntu.com precise-security/universe amd64 Packages                     
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages                   
Hit http://security.ubuntu.com precise-security/main i386 Packages                          
Hit http://security.ubuntu.com precise-security/restricted i386 Packages                    
Hit http://security.ubuntu.com precise-security/universe i386 Packages                      
Hit http://downloads.sourceforge.net all Release.gpg                                        
Hit http://extras.ubuntu.com precise/main amd64 Packages                                    
Hit http://extras.ubuntu.com precise/main i386 Packages               
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                      
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages                                                        
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                           
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                                            
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                        
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                          
Get:4 http://us.archive.ubuntu.com precise-updates/main Sources [412 kB]                    
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                        
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                        
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                          
Hit http://security.ubuntu.com precise-security/main Translation-en                                
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                          
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                             
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                               
Hit http://downloads.sourceforge.net all Release                                                                                      
Get:5 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                                  
Get:6 http://us.archive.ubuntu.com precise-updates/universe Sources [93.9 kB]
Hit http://downloads.sourceforge.net all/main amd64 Packages                                        
Get:7 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                                    
Get:8 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [671 kB]                    
Ign http://extras.ubuntu.com precise/main Translation-en_US                                         
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                                   
Ign http://downloads.sourceforge.net all/main TranslationIndex                                                                                                                                                                                                                             
Hit http://downloads.sourceforge.net all/main i386 Packages                                                                                                                                                                                                                                
Get:9 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]                                                                                                                                                                                                     
Ign http://downloads.sourceforge.net all/main Translation-en_US                                                                                                                                                                                                                            
Get:10 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [211 kB]                                                                                                                                                                                                       
Ign http://downloads.sourceforge.net all/main Translation-en                                                                                                                                                                                                                               
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]                                                                                                                                                                                                    
Get:12 http://us.archive.ubuntu.com precise-updates/main i386 Packages [692 kB]                                                                                                                                                                                                            
Get:13 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]                                                                                                                                                                                                     
Get:14 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [215 kB]                                                                                                                                                                                                        
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                                                                                                                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                                                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                                                                                                                                                                                                                        
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                                                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                                                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                                                                                                                                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                                                                                                                                                   
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                                                                                                                                             
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                                                                                                                                             
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                                                                                                                                                         
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                                                                                                                                                         
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                                                                                                                                                           
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                                                                                                                                                                                       
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                                                                                                                                                                   
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                                                                                                                                                                                                 
Fetched 2,405 kB in 29s (82.3 kB/s)                                                                                                                                                                                                                                                        
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is installed
E: Unmet dependencies. Try using -f.
:~$ 


```

---

### Post by SweetAurora on 2013-08-14
It looks like you will have to remove one of the libssl1 packages. Do you have any reason to have two installed? Like for some server duties?

---

### Post by candra2 on 2013-08-14
I have no idea why I have two libssl1 packages and as far as I know I have no need for them...
What about where it says this:

```
You might want to run 'apt-get -f install' to correct these.
```

Will that help solve the issue??

thanks, 
candra

---

### Post by ian-weisser on 2013-08-14
> **candra2 said:**
> ```
You might want to run 'apt-get -f install' to correct these.
```

Will that help solve the issue??

No.
The system has no way to know which of the two packages should be kept.
The system relies on the admin (you) to solve the problem.

Do you recall deliberately installing libssl? Or any special network packages?
What did you install from SourceForge? Are you still using it?

Please try the following two commands, and post the entire output of each.
```
apt-cache showpkg libssl1.0.0
apt-cache showpkg libssl1.0.0:i386
```

---

### Post by candra2 on 2013-08-14
> **ian-weisser said:**
> No.
The has no way to know which of the two packages should be kept.
The system relies on the admin (you) to solve the problem.

Do you recall deliberately installing libssl? Or any special network packages?
What did you install from SourceForge? Are you still using it?

Please try the following two commands, and post the entire output of each.
```
apt-cache showpkg libssl1.0.0
apt-cache showpkg libssl1.0.0:i386
```

I do not recall installing libssl. I do not even know what that is. 

I do not recall installing any network packages. 

I do not recall installing anything from SoureForge - and I hve no idea if I am using it or not. 

I will now run the two commands and share the result...

thank you

---

### Post by candra2 on 2013-08-14
When I typed this line: 
apt-cache showpkg libssl1.0.0

I got this result:

  ```
bacula-common,libssl1.0.0 1.0.0
  apache2.2-bin,libssl1.0.0 1.0.0
  apache2-utils,libssl1.0.0 1.0.0
  libssl1.0.0:i386,libssl1.0.0 1.0.1-4ubuntu3
  libssl1.0.0:i386,libssl1.0.0 1.0.1-4ubuntu3
  vmware-view-open-client,libssl1.0.0 1.0.0
  sfcb,libssl1.0.0 1.0.0
  libmyth-0.25-0,libssl1.0.0 1.0.0
  conserver-server,libssl1.0.0 1.0.0
  conserver-client,libssl1.0.0 1.0.0
  ckermit,libssl1.0.0 1.0.0
  znc,libssl1.0.0 1.0.0
  zfs-fuse,libssl1.0.0 1.0.0
  yate-core,libssl1.0.0 1.0.0
  yapet,libssl1.0.0 1.0.0
  xymon,libssl1.0.0 1.0.0
  xrdp,libssl1.0.0 1.0.0
  xorp,libssl1.0.0 1.0.0
  xmms2-plugin-airplay,libssl1.0.0 1.0.0
  xmail,libssl1.0.0 1.0.0
  xchat,libssl1.0.0 1.0.0
  xca,libssl1.0.0 1.0.0
  xbmc-bin,libssl1.0.0 1.0.0
  x3270,libssl1.0.0 1.0.0
  x11vnc,libssl1.0.0 1.0.0
  wine1.4-amd64,libssl1.0.0
  webauth-utils,libssl1.0.0 1.0.0
  vtun,libssl1.0.0 1.0.0
  voms-server,libssl1.0.0 1.0.0
  voms-mysql-plugin,libssl1.0.0 1.0.0
  voms-clients,libssl1.0.0 1.0.0
  virtualbox,libssl1.0.0 1.0.0
  vde2-cryptcab,libssl1.0.0 1.0.0
  unworkable,libssl1.0.0 1.0.0
  unbound-anchor,libssl1.0.0 1.0.0
  unbound,libssl1.0.0 1.0.0
  unar,libssl1.0.0 1.0.0
  transgui,libssl1.0.0
  trafficserver,libssl1.0.0 1.0.0
  tpm-tools,libssl1.0.0 1.0.0
  tor,libssl1.0.0 1.0.0
  tkrat,libssl1.0.0 1.0.0
  tinc,libssl1.0.0 1.0.0
  telnetd-ssl,libssl1.0.0 1.0.0
  telnet-ssl,libssl1.0.0 1.0.0
  tcl-trf,libssl1.0.0 1.0.0
  tcl-tls,libssl1.0.0 1.0.0
  tboot,libssl1.0.0 1.0.0
  syslog-ng-mod-sql,libssl1.0.0 1.0.0
  syslog-ng-core,libssl1.0.0 1.0.0
  sylpheed,libssl1.0.0 1.0.0
  suck,libssl1.0.0 1.0.0
  stunnel4,libssl1.0.0 1.0.0
  stud,libssl1.0.0 1.0.0
  stone,libssl1.0.0 1.0.0
  ssvnc,libssl1.0.0 1.0.0
  sslsniff,libssl1.0.0 1.0.0
  sslscan,libssl1.0.0 1.0.0
  spice-client,libssl1.0.0 1.0.0
  sofia-sip-bin,libssl1.0.0 1.0.0
  socat,libssl1.0.0 1.0.0
  slurm-llnl-basic-plugins,libssl1.0.0 1.0.0
  skipfish,libssl1.0.0 1.0.0
  sipcrack,libssl1.0.0 1.0.0
  simutrans,libssl1.0.0 1.0.0
  sflphone-daemon,libssl1.0.0 1.0.0
  sendmail-bin,libssl1.0.0 1.0.0
  scrypt,libssl1.0.0 1.0.0
  scim-mozc,libssl1.0.0 1.0.0
  sbnc,libssl1.0.0 1.0.0
  samdump2,libssl1.0.0 1.0.0
  s3270,libssl1.0.0 1.0.0
  rsyncrypto,libssl1.0.0 1.0.0
  rhash,libssl1.0.0 1.0.0
  rdd,libssl1.0.0 1.0.0
  ratproxy,libssl1.0.0 1.0.0
  radsecproxy,libssl1.0.0 1.0.0
  qwbfsmanager,libssl1.0.0 1.0.0
  qutecom,libssl1.0.0 1.0.0
  qterm,libssl1.0.0 1.0.0
  qesteidutil,libssl1.0.0 1.0.0
  qdigidoc,libssl1.0.0 1.0.0
  qbittorrent-nox,libssl1.0.0 1.0.0
  qbittorrent,libssl1.0.0 1.0.0
  python-ncrypt,libssl1.0.0 1.0.0
  python-libtorrent-dbg,libssl1.0.0 1.0.0
  python-libtorrent,libssl1.0.0 1.0.0
  pyrit,libssl1.0.0 1.0.0
  pypy,libssl1.0.0 1.0.0
  pure-ftpd-postgresql,libssl1.0.0 1.0.0
  pure-ftpd-mysql,libssl1.0.0 1.0.0
  pure-ftpd-ldap,libssl1.0.0 1.0.0
  pure-ftpd,libssl1.0.0 1.0.0
  prosody,libssl1.0.0 1.0.0
  proftpd-basic,libssl1.0.0 1.0.0
  prayer-accountd,libssl1.0.0 1.0.0
  prayer,libssl1.0.0 1.0.0
  pr3287,libssl1.0.0 1.0.0
  pound,libssl1.0.0 1.0.0
  postler,libssl1.0.0 1.0.0
  postgresql-contrib-8.4,libssl1.0.0 1.0.0
  postgresql-client-8.4,libssl1.0.0 1.0.0
  postgresql-8.4,libssl1.0.0 1.0.0
  polygraph,libssl1.0.0 1.0.0
  pkcs11-dump,libssl1.0.0 1.0.0
  pinot,libssl1.0.0 1.0.0
  pidgin-openfetion,libssl1.0.0 1.0.0
  pidentd,libssl1.0.0 1.0.0
  picolisp,libssl1.0.0 1.0.0
  php5-fpm,libssl1.0.0 1.0.0
  perdition,libssl1.0.0 1.0.0
  pennmush-mysql,libssl1.0.0 1.0.0
  pennmush,libssl1.0.0 1.0.0
  pavuk,libssl1.0.0 1.0.0
  pathfinderd,libssl1.0.0 1.0.0
  pathfinder-utils,libssl1.0.0 1.0.0
  partimage-server,libssl1.0.0 1.0.0
  partimage,libssl1.0.0 1.0.0
  p3scan,libssl1.0.0 1.0.0
  owl,libssl1.0.0 1.0.0
  osptoolkit,libssl1.0.0 1.0.0
  ophcrack-cli,libssl1.0.0 1.0.0
  ophcrack,libssl1.0.0 1.0.0
  openwsman,libssl1.0.0 1.0.0
  openvswitch-switch,libssl1.0.0 1.0.0
  openvswitch-controller,libssl1.0.0 1.0.0
  openvswitch-common,libssl1.0.0 1.0.0
  openvswitch-brcompat,libssl1.0.0 1.0.0
  openvas-client,libssl1.0.0 1.0.0
  opensc,libssl1.0.0 1.0.0
  openntpd,libssl1.0.0 1.0.0
  opennebula,libssl1.0.0 1.0.0
  openhpi-plugin-ipmidirect,libssl1.0.0 1.0.0
  opendkim,libssl1.0.0 1.0.0
  openconnect,libssl1.0.0 1.0.0
  oftc-hybrid-respond,libssl1.0.0 1.0.0
  oftc-hybrid,libssl1.0.0 1.0.0
  odbc-postgresql,libssl1.0.0 1.0.0
  ocsigen,libssl1.0.0 1.0.0
  ntop,libssl1.0.0 1.0.0
  nsd3,libssl1.0.0 1.0.0
  nordugrid-arc-plugins-needed,libssl1.0.0 1.0.0
  nordugrid-arc-gridftpd,libssl1.0.0 1.0.0
  nordugrid-arc-client,libssl1.0.0 1.0.0
  nordugrid-arc-arex,libssl1.0.0 1.0.0
  nodejs,libssl1.0.0 1.0.1
  ngorca,libssl1.0.0 1.0.0
  nginx-naxsi,libssl1.0.0 1.0.0
  nginx-light,libssl1.0.0 1.0.0
  nginx-full,libssl1.0.0 1.0.0
  nginx-extras,libssl1.0.0 1.0.0
  network-manager-openconnect-gnome,libssl1.0.0 1.0.0
  netsurf-gtk,libssl1.0.0 1.0.0
  navit,libssl1.0.0 1.0.0
  nagircbot,libssl1.0.0 1.0.0
  nagios-nrpe-plugin,libssl1.0.0 1.0.0
  myproxy,libssl1.0.0 1.0.0
  mumble-server,libssl1.0.0 1.0.0
  mumble-11x,libssl1.0.0 1.0.0
  mumble,libssl1.0.0 1.0.0
  mozc-server,libssl1.0.0 1.0.0
  monit,libssl1.0.0 1.0.0
  mktorrent,libssl1.0.0 1.0.0
  mixmaster,libssl1.0.0 1.0.0
  mini-httpd,libssl1.0.0 1.0.0
  medusa,libssl1.0.0 1.0.0
  maptool,libssl1.0.0 1.0.0
  mailfilter,libssl1.0.0 1.0.0
  mailavenger,libssl1.0.0 1.0.0
  mail-notification,libssl1.0.0 1.0.0
  linuxdcpp,libssl1.0.0 1.0.0
  links2,libssl1.0.0 1.0.0
  links,libssl1.0.0 1.0.0
  lighttpd,libssl1.0.0 1.0.0
  licq,libssl1.0.0 1.0.0
  libzorpll3.9-1-memtrace,libssl1.0.0 1.0.0
  libzorpll3.9-1,libssl1.0.0 1.0.0
  libzorp3.9-0,libssl1.0.0 1.0.0
  libxr1,libssl1.0.0 1.0.0
  libxmltooling5,libssl1.0.0 1.0.0
  libxmlsec1-openssl,libssl1.0.0 1.0.0
  libxml-security-c16,libssl1.0.0 1.0.0
  libwthttp29,libssl1.0.0 1.0.0
  libwebauth5,libssl1.0.0 1.0.0
  libvomsapi1,libssl1.0.0 1.0.0
  libunbound2,libssl1.0.0 1.0.0
  libtqsllib1,libssl1.0.0 1.0.0
  libtorrent14,libssl1.0.0 1.0.0
  libtorrent-rasterbar6,libssl1.0.0 1.0.0
  libtntnet9,libssl1.0.0 1.0.0
  libtcnative-1,libssl1.0.0 1.0.0
  libtao-orbsvcs-2.0.1,libssl1.0.0 1.0.0
  libsylph1,libssl1.0.0 1.0.0
  libstrongswan,libssl1.0.0 1.0.0
  libssl-ocaml,libssl1.0.0 1.0.0
  libspice-server1,libssl1.0.0 1.0.0
  libspice-client-glib-2.0-1,libssl1.0.0 1.0.0
  libsofia-sip-ua0,libssl1.0.0 1.0.0
  libshairport1,libssl1.0.0 1.0.0
  libsasl2-modules-otp,libssl1.0.0 1.0.0
  librhash0,libssl1.0.0 1.0.0
  librampart0,libssl1.0.0 1.0.0
  libpt2.4.5,libssl1.0.0 1.0.0
  libpt2.10.2,libssl1.0.0 1.0.0
  libpt-1.10.10,libssl1.0.0 1.0.0
  libpoconetssl9-dbg,libssl1.0.0 1.0.0
  libpoconetssl9,libssl1.0.0 1.0.0
  libpococrypto9-dbg,libssl1.0.0 1.0.0
  libpococrypto9,libssl1.0.0 1.0.0
  libpion-net-plugins,libssl1.0.0 1.0.0
  libpion-net-dev,libssl1.0.0 1.0.0
  libpion-net-4.0,libssl1.0.0 1.0.0
  libpantomime1.2,libssl1.0.0 1.0.0
  libpam-rsa,libssl1.0.0 1.0.0
  libpam-pkcs11,libssl1.0.0 1.0.0
  libpam-barada,libssl1.0.0 1.0.0
  libosptk3,libssl1.0.0 1.0.0
  libopkele3,libssl1.0.0 1.0.0
  libopenh323-1.18.0-develop,libssl1.0.0 1.0.0
  libopenh323-1.18.0,libssl1.0.0 1.0.0
  libopendkim6,libssl1.0.0 1.0.0
  libopenconnect1,libssl1.0.0 1.0.0
  libopal3.10.2,libssl1.0.0 1.0.0
  libomniorb4-1,libssl1.0.0 1.0.0
  libofetion1,libssl1.0.0 1.0.0
  libnet-tclink-perl,libssl1.0.0 1.0.0
  libnanohttp1,libssl1.0.0 1.0.0
  libmyproxy5,libssl1.0.0 1.0.0
  liblua5.1-sec1,libssl1.0.0 1.0.0
  libldns1,libssl1.0.0 1.0.0
  liblcgdm1,libssl1.0.0 1.0.0
  liblasso3,libssl1.0.0 1.0.0
  libkvilib4,libssl1.0.0 1.0.0
  libitalc,libssl1.0.0 1.0.0
  libicessl34,libssl1.0.0 1.0.0
  libicepatch2-34,libssl1.0.0 1.0.0
  libhttrack2,libssl1.0.0
  libhttrack-dev,libssl1.0.0
  libh323-1.21.0,libssl1.0.0 1.0.0
  libgsoap1,libssl1.0.0 1.0.0
  libgridsite1.7,libssl1.0.0 1.0.0
  libglobus-openssl-module0,libssl1.0.0 1.0.0
  libglobus-gssapi-gsi4,libssl1.0.0 1.0.0
  libglobus-gsi-sysconfig1,libssl1.0.0 1.0.0
  libglobus-gsi-proxy-ssl1,libssl1.0.0 1.0.0
  libglobus-gsi-proxy-core0,libssl1.0.0 1.0.0
  libglobus-gsi-openssl-error0,libssl1.0.0 1.0.0
  libglobus-gsi-credential1,libssl1.0.0 1.0.0
  libglobus-gsi-cert-utils0,libssl1.0.0 1.0.0
  libglobus-gsi-callback0,libssl1.0.0 1.0.0
  libglobus-gridftp-server0,libssl1.0.0 1.0.0
  libglobus-gass-copy2,libssl1.0.0 1.0.0
  libglobus-gass-cache5,libssl1.0.0 1.0.0
  libglobus-ftp-client2,libssl1.0.0 1.0.0
  libgfarm1,libssl1.0.0 1.0.0
  libgdcm2.0,libssl1.0.0 1.0.0
  libgcgi0,libssl1.0.0 1.0.0
  libfaifa0,libssl1.0.0 1.0.0
  libengine-pkcs11-openssl,libssl1.0.0 1.0.0
  libeiskaltdcpp2.2,libssl1.0.0 1.0.0
  libduo3,libssl1.0.0 1.0.0
  libdkim1d,libssl1.0.0 1.0.0
  libdigidocpp0,libssl1.0.0 1.0.0
  libdigidoc2,libssl1.0.0 1.0.0
  libdigidoc-dev,libssl1.0.0 1.0.0
  libdc5,libssl1.0.0 1.0.0
  libcyrus-imap-perl24,libssl1.0.0 1.0.0
  libcrypt-ssleay-perl,libssl1.0.0 1.0.0
  libcrypt-smime-perl,libssl1.0.0 1.0.0
  libcrypt-openssl-x509-perl,libssl1.0.0 1.0.0
  libcrypt-openssl-dsa-perl,libssl1.0.0 1.0.0
  libcouchdb-glib-1.0-2,libssl1.0.0 1.0.0
  libcherokee-mod-libssl,libssl1.0.0 1.0.0
  libc-client2007e,libssl1.0.0 1.0.0
  libbotan-1.8.13,libssl1.0.0 1.0.0
  libbotan-1.10-0,libssl1.0.0 1.0.0
  libbobcat2,libssl1.0.0 1.0.0
  libbeidlibopensc2,libssl1.0.0 1.0.0
  libbeidlib3,libssl1.0.0 1.0.0
  libbeid2,libssl1.0.0 1.0.0
  libaxis2c0,libssl1.0.0 1.0.0
  libarccommon1,libssl1.0.0 1.0.0
  libapache2-mod-qos,libssl1.0.0 1.0.0
  libapache2-mod-php5filter,libssl1.0.0 1.0.0
  libapache2-mod-authn-webid,libssl1.0.0 1.0.0
  libapache2-mod-auth-cas,libssl1.0.0 1.0.0
  libafflib0,libssl1.0.0 1.0.0
  libace-ssl-6.0.1,libssl1.0.0 1.0.0
  libace-inet-ssl-6.0.1,libssl1.0.0 1.0.0
  ldnsutils,libssl1.0.0 1.0.0
  l2tp-ipsec-vpn,libssl1.0.0 1.0.0
  kvirc-modules,libssl1.0.0 1.0.0
  kvirc,libssl1.0.0 1.0.0
  kumofs,libssl1.0.0 1.0.0
  krb5-pkinit,libssl1.0.0 1.0.0
  kontrolpack,libssl1.0.0 1.0.0
  kolabadmin,libssl1.0.0 1.0.0
  kolab-libcyrus-imap-perl,libssl1.0.0 1.0.0
  kolab-cyrus-pop3d,libssl1.0.0 1.0.0
  kolab-cyrus-imapd,libssl1.0.0 1.0.0
  kolab-cyrus-common,libssl1.0.0 1.0.0
  kolab-cyrus-clients,libssl1.0.0 1.0.0
  kftpgrabber,libssl1.0.0 1.0.0
  kannel-sqlbox,libssl1.0.0 1.0.0
  kannel-extras,libssl1.0.0 1.0.0
  kannel,libssl1.0.0 1.0.0
  jabberd2,libssl1.0.0 1.0.0
  italc-client,libssl1.0.0 1.0.0
  isync,libssl1.0.0 1.0.0
  istgt,libssl1.0.0 1.0.0
  isc-dhcp-server-ldap,libssl1.0.0 1.0.0
  isakmpd,libssl1.0.0 1.0.0
  ipmitool,libssl1.0.0 1.0.0
  inn2,libssl1.0.0 1.0.0
  imapproxy,libssl1.0.0 1.0.0
  imapfilter,libssl1.0.0 1.0.0
  ike-scan,libssl1.0.0 1.0.0
  ike-qtgui,libssl1.0.0 1.0.0
  ike,libssl1.0.0 1.0.0
  idecrypt,libssl1.0.0 1.0.0
  ice34-services,libssl1.0.0 1.0.0
  hydra,libssl1.0.0 1.0.0
  httping,libssl1.0.0 1.0.0
  httperf,libssl1.0.0 1.0.0
  httest,libssl1.0.0 1.0.0
  hostapd,libssl1.0.0 1.0.0
  hfsprogs,libssl1.0.0 1.0.0
  heirloom-mailx,libssl1.0.0 1.0.0
  gvpe,libssl1.0.0 1.0.0
  gstreamer0.10-plugins-bad,libssl1.0.0 1.0.0
  grisbi,libssl1.0.0 1.0.0
  gridengine-exec,libssl1.0.0 1.0.0
  gogoc,libssl1.0.0 1.0.0
  gnupg-pkcs11-scd,libssl1.0.0 1.0.0
  gnubiff,libssl1.0.0 1.0.0
  globus-proxy-utils,libssl1.0.0 1.0.0
  globus-gram-job-manager,libssl1.0.0 1.0.0
  globus-gatekeeper,libssl1.0.0 1.0.0
  globus-gass-copy-progs,libssl1.0.0 1.0.0
  ginkgocadx,libssl1.0.0 1.0.0
  gfsd,libssl1.0.0 1.0.0
  gatling,libssl1.0.0 1.0.0
  g2ipmsg,libssl1.0.0 1.0.0
  ftpd-ssl,libssl1.0.0 1.0.0
  ftp-ssl,libssl1.0.0 1.0.0
  fqterm,libssl1.0.0 1.0.0
  fossil,libssl1.0.0 1.0.0
  flush,libssl1.0.0 1.0.0
  fdm,libssl1.0.0 1.0.0
  ewf-tools,libssl1.0.0 1.0.0
  eurephia,libssl1.0.0 1.0.0
  ettercap-text-only,libssl1.0.0 1.0.0
  ettercap-graphical,libssl1.0.0 1.0.0
  epic5,libssl1.0.0 1.0.0
  epic4,libssl1.0.0 1.0.0
  encfs,libssl1.0.0 1.0.0
  ekg2-core,libssl1.0.0 1.0.0
  ekg-gtk,libssl1.0.0 1.0.0
  ekg,libssl1.0.0 1.0.0
  ejabberd,libssl1.0.0 1.0.0
  eggdrop,libssl1.0.0 1.0.0
  dsniff,libssl1.0.0 1.0.0
  dmg2img,libssl1.0.0 1.0.0
  dma,libssl1.0.0 1.0.0
  dk-filter,libssl1.0.0 1.0.0
  dillo,libssl1.0.0 1.0.0
  dicomscope,libssl1.0.0 1.0.0
  dcmtk,libssl1.0.0 1.0.0
  dcap-tunnel-ssl,libssl1.0.0 1.0.0
  cyrus-replication-2.4,libssl1.0.0 1.0.0
  cyrus-pop3d-2.4,libssl1.0.0 1.0.0
  cyrus-nntpd-2.4,libssl1.0.0 1.0.0
  cyrus-murder-2.4,libssl1.0.0 1.0.0
  cyrus-imapd-2.4,libssl1.0.0 1.0.0
  cyrus-common-2.4,libssl1.0.0 1.0.0
  cyrus-clients-2.4,libssl1.0.0 1.0.0
  crtmpserver-libs,libssl1.0.0 1.0.0
  crtmpserver-apps,libssl1.0.0 1.0.0
  courier-ssl,libssl1.0.0 1.0.0
  cone,libssl1.0.0 1.0.0
  citadel-webcit,libssl1.0.0 1.0.0
  citadel-server,libssl1.0.0 1.0.0
  citadel-client,libssl1.0.0 1.0.0
  cfengine3,libssl1.0.0 1.0.0
  cfengine2,libssl1.0.0 1.0.0
  certmonger,libssl1.0.0 1.0.0
  c3270,libssl1.0.0 1.0.0
  burp,libssl1.0.0 1.0.0
  btpd,libssl1.0.0 1.0.0
  bozohttpd,libssl1.0.0 1.0.0
  boxbackup-server,libssl1.0.0 1.0.0
  boxbackup-client,libssl1.0.0 1.0.0
  boinc-server-maker,libssl1.0.0 1.0.0
  boinc-client,libssl1.0.0 1.0.0
  bitcoind,libssl1.0.0 1.0.0
  bip,libssl1.0.0 1.0.0
  beid-tools,libssl1.0.0 1.0.0
  batv-filter,libssl1.0.0 1.0.0
  barnowl,libssl1.0.0 1.0.0
  balsa,libssl1.0.0 1.0.0
  ayttm,libssl1.0.0 1.0.0
  asterisk-modules,libssl1.0.0 1.0.0
  asterisk,libssl1.0.0 1.0.0
  apf-server,libssl1.0.0 1.0.0
  apf-client,libssl1.0.0 1.0.0
  anon-proxy,libssl1.0.0 1.0.0
  amanda-common,libssl1.0.0 1.0.0
  alpine,libssl1.0.0 1.0.0
  afflib-tools,libssl1.0.0 1.0.0
  xchat-gnome,libssl1.0.0 1.0.0
  wpasupplicant,libssl1.0.0 1.0.0
  wget,libssl1.0.0 1.0.0
  w3m,libssl1.0.0 1.0.0
  vsftpd,libssl1.0.0 1.0.0
  virtuoso-opensource-6.1-common,libssl1.0.0 1.0.0
  virtuoso-opensource-6.1-bin,libssl1.0.0 1.0.0
  trousers,libssl1.0.0 1.0.0
  transmission-qt,libssl1.0.0 1.0.0
  transmission-gtk,libssl1.0.0 1.0.0
  transmission-daemon,libssl1.0.0 1.0.0
  transmission-cli,libssl1.0.0 1.0.0
  tcpdump,libssl1.0.0 1.0.0
  spamc,libssl1.0.0 1.0.0
  snmp,libssl1.0.0 1.0.0
  siege,libssl1.0.0 1.0.0
  sasl2-bin,libssl1.0.0 1.0.0
  rdesktop,libssl1.0.0 1.0.0
  racoon,libssl1.0.0 1.0.0
  python3.2-minimal,libssl1.0.0 1.0.0
  python3.2-dbg,libssl1.0.0 1.0.0
  python2.7-minimal,libssl1.0.0 1.0.0
  python2.7-dbg,libssl1.0.0 1.0.0
  python-openssl-dbg,libssl1.0.0 1.0.0
  python-openssl,libssl1.0.0 1.0.0
  python-m2crypto,libssl1.0.0 1.0.0
  pulseaudio-module-raop,libssl1.0.0 1.0.0
  postgresql-contrib-9.1,libssl1.0.0 1.0.0
  postgresql-client-9.1,libssl1.0.0 1.0.0
  postgresql-9.1,libssl1.0.0 1.0.0
  postfix,libssl1.0.0 1.0.0
  php5-cli,libssl1.0.0 1.0.0
  php5-cgi,libssl1.0.0 1.0.0
  pacemaker,libssl1.0.0 1.0.0
  openvpn,libssl1.0.0 1.0.0
  openssl,libssl1.0.0 1.0.1
  openssh-server,libssl1.0.0 1.0.0
  openssh-client,libssl1.0.0 1.0.0
  nmap,libssl1.0.0 1.0.0
  nagios-plugins-basic,libssl1.0.0 1.0.0
  nagios-nrpe-server,libssl1.0.0 1.0.0
  likewise-open,libssl1.0.0 1.0.0
  libwvstreams4.6-extras,libssl1.0.0 1.0.0
  libvirtodbc0,libssl1.0.0 1.0.0
  libtspi1,libssl1.0.0 1.0.0
  libssl1.0.0-dbg,libssl1.0.0 1.0.1-4ubuntu3
  libssl-dev,libssl1.0.0 1.0.1-4ubuntu3
  libssh-4,libssl1.0.0 1.0.0
  libsnmp15,libssl1.0.0 1.0.0
  libserf1,libssl1.0.0 1.0.0
  libsasl2-modules-gssapi-mit,libssl1.0.0 1.0.0
  libsasl2-modules,libssl1.0.0 1.0.0
  libruby1.9.1,libssl1.0.0 1.0.0
  libruby1.8,libssl1.0.0 1.0.0
  libreoffice-core,libssl1.0.0 1.0.0
  libqca2-plugin-ossl,libssl1.0.0 1.0.0
  libpython3.2,libssl1.0.0 1.0.0
  libpython2.7,libssl1.0.0 1.0.0
  libpq5,libssl1.0.0 1.0.0
  libpkcs11-helper1,libssl1.0.0 1.0.0
  libpam-p11,libssl1.0.0 1.0.0
  libpam-mount,libssl1.0.0 1.0.0
  libp11-2,libssl1.0.0 1.0.0
  libopenhpi2,libssl1.0.0 1.0.0
  libopencryptoki0,libssl1.0.0 1.0.0
  libnet-ssleay-perl,libssl1.0.0 1.0.0
  libneon27,libssl1.0.0 1.0.0
  libmsn0.3,libssl1.0.0 1.0.0
  libfreerdp1,libssl1.0.0 1.0.0
  libevent-openssl-2.0-5,libssl1.0.0 1.0.0
  libesmtp6,libssl1.0.0 1.0.0
  libdns81,libssl1.0.0 1.0.0
  libcurl3,libssl1.0.0 1.0.0
  libcrypt-openssl-rsa-perl,libssl1.0.0 1.0.0
  libcrypt-openssl-random-perl,libssl1.0.0 1.0.0
  libcrypt-openssl-bignum-perl,libssl1.0.0 1.0.0
  libcib1,libssl1.0.0 1.0.0
  libapache2-mod-php5,libssl1.0.0 1.0.0
  keepalived,libssl1.0.0 1.0.0
  irssi,libssl1.0.0 1.0.0
  iputils-ping,libssl1.0.0 1.0.0
  htmldoc,libssl1.0.0 1.0.0
  freeradius-utils,libssl1.0.0 1.0.0
  freeradius,libssl1.0.0 1.0.0
  fetchmail,libssl1.0.0 1.0.0
  erlang-ssl,libssl1.0.0 1.0.0
  erlang-crypto,libssl1.0.0 1.0.0
  dovecot-core,libssl1.0.0 1.0.0
  crda,libssl1.0.0 1.0.0
  bacula-common,libssl1.0.0 1.0.0
  apache2.2-bin,libssl1.0.0 1.0.0
  apache2-utils,libssl1.0.0 1.0.0
Dependencies: 
1.0.1-4ubuntu5.10 - libc6 (2 2.14) zlib1g (2 1:1.1.4) debconf (18 0.5) debconf-2.0 (0 (null)) multiarch-support (0 (null)) openssh-client (3 1:5.9p1-4) openssh-client:i386 (3 1:5.9p1-4) openssh-server (3 1:5.9p1-4) openssh-server:i386 (3 1:5.9p1-4) libssl1.0.0:i386 (3 1.0.1-4ubuntu5.10) libssl1.0.0:i386 (6 1.0.1-4ubuntu5.10) 
1.0.1-4ubuntu3 - libc6 (2 2.14) zlib1g (2 1:1.1.4) debconf (18 0.5) debconf-2.0 (0 (null)) multiarch-support (0 (null)) openssh-client (3 1:5.9p1-4) openssh-client:i386 (3 1:5.9p1-4) openssh-server (3 1:5.9p1-4) openssh-server:i386 (3 1:5.9p1-4) libssl1.0.0:i386 (3 1.0.1-4ubuntu3) libssl1.0.0:i386 (6 1.0.1-4ubuntu3) 
Provides: 
1.0.1-4ubuntu5.10 - 
1.0.1-4ubuntu3 - 
Reverse Provides:
```

When I typed this line: 

apt-cache showpkg libssl1.0.0:i386

I got this result:

```
libmyth-0.25-0:i386,libssl1.0.0:i386 1.0.0
  conserver-server:i386,libssl1.0.0:i386 1.0.0
  conserver-client:i386,libssl1.0.0:i386 1.0.0
  ckermit:i386,libssl1.0.0:i386 1.0.0
  znc:i386,libssl1.0.0:i386 1.0.0
  zfs-fuse:i386,libssl1.0.0:i386 1.0.0
  yate-core:i386,libssl1.0.0:i386 1.0.0
  yapet:i386,libssl1.0.0:i386 1.0.0
  xymon:i386,libssl1.0.0:i386 1.0.0
  xrdp:i386,libssl1.0.0:i386 1.0.0
  xorp:i386,libssl1.0.0:i386 1.0.0
  xmms2-plugin-airplay:i386,libssl1.0.0:i386 1.0.0
  xmail:i386,libssl1.0.0:i386 1.0.0
  xchat:i386,libssl1.0.0:i386 1.0.0
  xca:i386,libssl1.0.0:i386 1.0.0
  xbmc-bin:i386,libssl1.0.0:i386 1.0.0
  x3270:i386,libssl1.0.0:i386 1.0.0
  x11vnc:i386,libssl1.0.0:i386 1.0.0
  wine1.4-i386:i386,libssl1.0.0:i386
  webauth-utils:i386,libssl1.0.0:i386 1.0.0
  vtun:i386,libssl1.0.0:i386 1.0.0
  voms-server:i386,libssl1.0.0:i386 1.0.0
  voms-mysql-plugin:i386,libssl1.0.0:i386 1.0.0
  voms-clients:i386,libssl1.0.0:i386 1.0.0
  virtualbox:i386,libssl1.0.0:i386 1.0.0
  vde2-cryptcab:i386,libssl1.0.0:i386 1.0.0
  unworkable:i386,libssl1.0.0:i386 1.0.0
  unbound-anchor:i386,libssl1.0.0:i386 1.0.0
  unbound:i386,libssl1.0.0:i386 1.0.0
  unar:i386,libssl1.0.0:i386 1.0.0
  transgui:i386,libssl1.0.0:i386
  trafficserver:i386,libssl1.0.0:i386 1.0.0
  tpm-tools:i386,libssl1.0.0:i386 1.0.0
  tor:i386,libssl1.0.0:i386 1.0.0
  tkrat:i386,libssl1.0.0:i386 1.0.0
  tinc:i386,libssl1.0.0:i386 1.0.0
  telnetd-ssl:i386,libssl1.0.0:i386 1.0.0
  telnet-ssl:i386,libssl1.0.0:i386 1.0.0
  tcl-trf:i386,libssl1.0.0:i386 1.0.0
  tcl-tls:i386,libssl1.0.0:i386 1.0.0
  tboot:i386,libssl1.0.0:i386 1.0.0
  syslog-ng-mod-sql:i386,libssl1.0.0:i386 1.0.0
  syslog-ng-core:i386,libssl1.0.0:i386 1.0.0
  sylpheed:i386,libssl1.0.0:i386 1.0.0
  suck:i386,libssl1.0.0:i386 1.0.0
  stunnel4:i386,libssl1.0.0:i386 1.0.0
  stud:i386,libssl1.0.0:i386 1.0.0
  stone:i386,libssl1.0.0:i386 1.0.0
  ssvnc:i386,libssl1.0.0:i386 1.0.0
  sslsniff:i386,libssl1.0.0:i386 1.0.0
  sslscan:i386,libssl1.0.0:i386 1.0.0
  spice-client:i386,libssl1.0.0:i386 1.0.0
  sofia-sip-bin:i386,libssl1.0.0:i386 1.0.0
  socat:i386,libssl1.0.0:i386 1.0.0
  slurm-llnl-basic-plugins:i386,libssl1.0.0:i386 1.0.0
  skipfish:i386,libssl1.0.0:i386 1.0.0
  sipcrack:i386,libssl1.0.0:i386 1.0.0
  simutrans:i386,libssl1.0.0:i386 1.0.0
  sflphone-daemon:i386,libssl1.0.0:i386 1.0.0
  sendmail-bin:i386,libssl1.0.0:i386 1.0.0
  scrypt:i386,libssl1.0.0:i386 1.0.0
  scim-mozc:i386,libssl1.0.0:i386 1.0.0
  sbnc:i386,libssl1.0.0:i386 1.0.0
  samdump2:i386,libssl1.0.0:i386 1.0.0
  s3270:i386,libssl1.0.0:i386 1.0.0
  rsyncrypto:i386,libssl1.0.0:i386 1.0.0
  rhash:i386,libssl1.0.0:i386 1.0.0
  rdd:i386,libssl1.0.0:i386 1.0.0
  ratproxy:i386,libssl1.0.0:i386 1.0.0
  radsecproxy:i386,libssl1.0.0:i386 1.0.0
  qwbfsmanager:i386,libssl1.0.0:i386 1.0.0
  qutecom:i386,libssl1.0.0:i386 1.0.0
  qterm:i386,libssl1.0.0:i386 1.0.0
  qesteidutil:i386,libssl1.0.0:i386 1.0.0
  qdigidoc:i386,libssl1.0.0:i386 1.0.0
  qbittorrent-nox:i386,libssl1.0.0:i386 1.0.0
  qbittorrent:i386,libssl1.0.0:i386 1.0.0
  python-ncrypt:i386,libssl1.0.0:i386 1.0.0
  python-libtorrent-dbg:i386,libssl1.0.0:i386 1.0.0
  python-libtorrent:i386,libssl1.0.0:i386 1.0.0
  pyrit:i386,libssl1.0.0:i386 1.0.0
  pypy:i386,libssl1.0.0:i386 1.0.0
  pure-ftpd-postgresql:i386,libssl1.0.0:i386 1.0.0
  pure-ftpd-mysql:i386,libssl1.0.0:i386 1.0.0
  pure-ftpd-ldap:i386,libssl1.0.0:i386 1.0.0
  pure-ftpd:i386,libssl1.0.0:i386 1.0.0
  prosody:i386,libssl1.0.0:i386 1.0.0
  proftpd-basic:i386,libssl1.0.0:i386 1.0.0
  prayer-accountd:i386,libssl1.0.0:i386 1.0.0
  prayer:i386,libssl1.0.0:i386 1.0.0
  pr3287:i386,libssl1.0.0:i386 1.0.0
  pound:i386,libssl1.0.0:i386 1.0.0
  postler:i386,libssl1.0.0:i386 1.0.0
  postgresql-contrib-8.4:i386,libssl1.0.0:i386 1.0.0
  postgresql-client-8.4:i386,libssl1.0.0:i386 1.0.0
  postgresql-8.4:i386,libssl1.0.0:i386 1.0.0
  polygraph:i386,libssl1.0.0:i386 1.0.0
  pkcs11-dump:i386,libssl1.0.0:i386 1.0.0
  pinot:i386,libssl1.0.0:i386 1.0.0
  pidgin-openfetion:i386,libssl1.0.0:i386 1.0.0
  pidentd:i386,libssl1.0.0:i386 1.0.0
  picolisp:i386,libssl1.0.0:i386 1.0.0
  php5-fpm:i386,libssl1.0.0:i386 1.0.0
  perdition:i386,libssl1.0.0:i386 1.0.0
  pennmush-mysql:i386,libssl1.0.0:i386 1.0.0
  pennmush:i386,libssl1.0.0:i386 1.0.0
  pavuk:i386,libssl1.0.0:i386 1.0.0
  pathfinderd:i386,libssl1.0.0:i386 1.0.0
  pathfinder-utils:i386,libssl1.0.0:i386 1.0.0
  partimage-server:i386,libssl1.0.0:i386 1.0.0
  partimage:i386,libssl1.0.0:i386 1.0.0
  p3scan:i386,libssl1.0.0:i386 1.0.0
  owl:i386,libssl1.0.0:i386 1.0.0
  osptoolkit:i386,libssl1.0.0:i386 1.0.0
  ophcrack-cli:i386,libssl1.0.0:i386 1.0.0
  ophcrack:i386,libssl1.0.0:i386 1.0.0
  openwsman:i386,libssl1.0.0:i386 1.0.0
  openvswitch-switch:i386,libssl1.0.0:i386 1.0.0
  openvswitch-controller:i386,libssl1.0.0:i386 1.0.0
  openvswitch-common:i386,libssl1.0.0:i386 1.0.0
  openvswitch-brcompat:i386,libssl1.0.0:i386 1.0.0
  openvas-client:i386,libssl1.0.0:i386 1.0.0
  opensc:i386,libssl1.0.0:i386 1.0.0
  openntpd:i386,libssl1.0.0:i386 1.0.0
  opennebula:i386,libssl1.0.0:i386 1.0.0
  openhpi-plugin-ipmidirect:i386,libssl1.0.0:i386 1.0.0
  opendkim:i386,libssl1.0.0:i386 1.0.0
  openconnect:i386,libssl1.0.0:i386 1.0.0
  oftc-hybrid-respond:i386,libssl1.0.0:i386 1.0.0
  oftc-hybrid:i386,libssl1.0.0:i386 1.0.0
  odbc-postgresql:i386,libssl1.0.0:i386 1.0.0
  ocsigen:i386,libssl1.0.0:i386 1.0.0
  ntop:i386,libssl1.0.0:i386 1.0.0
  nsd3:i386,libssl1.0.0:i386 1.0.0
  nordugrid-arc-plugins-needed:i386,libssl1.0.0:i386 1.0.0
  nordugrid-arc-gridftpd:i386,libssl1.0.0:i386 1.0.0
  nordugrid-arc-client:i386,libssl1.0.0:i386 1.0.0
  nordugrid-arc-arex:i386,libssl1.0.0:i386 1.0.0
  nodejs:i386,libssl1.0.0:i386 1.0.1
  ngorca:i386,libssl1.0.0:i386 1.0.0
  nginx-naxsi:i386,libssl1.0.0:i386 1.0.0
  nginx-light:i386,libssl1.0.0:i386 1.0.0
  nginx-full:i386,libssl1.0.0:i386 1.0.0
  nginx-extras:i386,libssl1.0.0:i386 1.0.0
  network-manager-openconnect-gnome:i386,libssl1.0.0:i386 1.0.0
  netsurf-gtk:i386,libssl1.0.0:i386 1.0.0
  navit:i386,libssl1.0.0:i386 1.0.0
  nagircbot:i386,libssl1.0.0:i386 1.0.0
  nagios-nrpe-plugin:i386,libssl1.0.0:i386 1.0.0
  myproxy:i386,libssl1.0.0:i386 1.0.0
  mumble-server:i386,libssl1.0.0:i386 1.0.0
  mumble-11x:i386,libssl1.0.0:i386 1.0.0
  mumble:i386,libssl1.0.0:i386 1.0.0
  mozc-server:i386,libssl1.0.0:i386 1.0.0
  monit:i386,libssl1.0.0:i386 1.0.0
  mktorrent:i386,libssl1.0.0:i386 1.0.0
  mixmaster:i386,libssl1.0.0:i386 1.0.0
  mit-scheme:i386,libssl1.0.0:i386 1.0.0
  mini-httpd:i386,libssl1.0.0:i386 1.0.0
  medusa:i386,libssl1.0.0:i386 1.0.0
  maptool:i386,libssl1.0.0:i386 1.0.0
  mailfilter:i386,libssl1.0.0:i386 1.0.0
  mailavenger:i386,libssl1.0.0:i386 1.0.0
  mail-notification:i386,libssl1.0.0:i386 1.0.0
  linuxdcpp:i386,libssl1.0.0:i386 1.0.0
  links2:i386,libssl1.0.0:i386 1.0.0
  links:i386,libssl1.0.0:i386 1.0.0
  lighttpd:i386,libssl1.0.0:i386 1.0.0
  licq:i386,libssl1.0.0:i386 1.0.0
  libzorpll3.9-1-memtrace:i386,libssl1.0.0:i386 1.0.0
  libzorpll3.9-1:i386,libssl1.0.0:i386 1.0.0
  libzorp3.9-0:i386,libssl1.0.0:i386 1.0.0
  libxr1:i386,libssl1.0.0:i386 1.0.0
  libxmltooling5:i386,libssl1.0.0:i386 1.0.0
  libxmlsec1-openssl:i386,libssl1.0.0:i386 1.0.0
  libxml-security-c16:i386,libssl1.0.0:i386 1.0.0
  libwthttp29:i386,libssl1.0.0:i386 1.0.0
  libwebauth5:i386,libssl1.0.0:i386 1.0.0
  libvomsapi1:i386,libssl1.0.0:i386 1.0.0
  libunbound2:i386,libssl1.0.0:i386 1.0.0
  libtqsllib1:i386,libssl1.0.0:i386 1.0.0
  libtorrent14:i386,libssl1.0.0:i386 1.0.0
  libtorrent-rasterbar6:i386,libssl1.0.0:i386 1.0.0
  libtntnet9:i386,libssl1.0.0:i386 1.0.0
  libtcnative-1:i386,libssl1.0.0:i386 1.0.0
  libtao-orbsvcs-2.0.1:i386,libssl1.0.0:i386 1.0.0
  libsylph1:i386,libssl1.0.0:i386 1.0.0
  libstrongswan:i386,libssl1.0.0:i386 1.0.0
  libssl-ocaml:i386,libssl1.0.0:i386 1.0.0
  libspice-server1:i386,libssl1.0.0:i386 1.0.0
  libspice-client-glib-2.0-1:i386,libssl1.0.0:i386 1.0.0
  libsofia-sip-ua0:i386,libssl1.0.0:i386 1.0.0
  libshairport1:i386,libssl1.0.0:i386 1.0.0
  libsasl2-modules-otp:i386,libssl1.0.0:i386 1.0.0
  librhash0:i386,libssl1.0.0:i386 1.0.0
  librampart0:i386,libssl1.0.0:i386 1.0.0
  libpt2.4.5:i386,libssl1.0.0:i386 1.0.0
  libpt2.10.2:i386,libssl1.0.0:i386 1.0.0
  libpt-1.10.10:i386,libssl1.0.0:i386 1.0.0
  libpoconetssl9-dbg:i386,libssl1.0.0:i386 1.0.0
  libpoconetssl9:i386,libssl1.0.0:i386 1.0.0
  libpococrypto9-dbg:i386,libssl1.0.0:i386 1.0.0
  libpococrypto9:i386,libssl1.0.0:i386 1.0.0
  libpion-net-plugins:i386,libssl1.0.0:i386 1.0.0
  libpion-net-dev:i386,libssl1.0.0:i386 1.0.0
  libpion-net-4.0:i386,libssl1.0.0:i386 1.0.0
  libpantomime1.2:i386,libssl1.0.0:i386 1.0.0
  libpam-rsa:i386,libssl1.0.0:i386 1.0.0
  libpam-pkcs11:i386,libssl1.0.0:i386 1.0.0
  libpam-barada:i386,libssl1.0.0:i386 1.0.0
  libosptk3:i386,libssl1.0.0:i386 1.0.0
  libopkele3:i386,libssl1.0.0:i386 1.0.0
  libopenh323-1.18.0-develop:i386,libssl1.0.0:i386 1.0.0
  libopenh323-1.18.0:i386,libssl1.0.0:i386 1.0.0
  libopendkim6:i386,libssl1.0.0:i386 1.0.0
  libopenconnect1:i386,libssl1.0.0:i386 1.0.0
  libopal3.10.2:i386,libssl1.0.0:i386 1.0.0
  libomniorb4-1:i386,libssl1.0.0:i386 1.0.0
  libofetion1:i386,libssl1.0.0:i386 1.0.0
  libnet-tclink-perl:i386,libssl1.0.0:i386 1.0.0
  libnanohttp1:i386,libssl1.0.0:i386 1.0.0
  libmyproxy5:i386,libssl1.0.0:i386 1.0.0
  liblua5.1-sec1:i386,libssl1.0.0:i386 1.0.0
  libldns1:i386,libssl1.0.0:i386 1.0.0
  liblcgdm1:i386,libssl1.0.0:i386 1.0.0
  liblasso3:i386,libssl1.0.0:i386 1.0.0
  libkvilib4:i386,libssl1.0.0:i386 1.0.0
  libitalc:i386,libssl1.0.0:i386 1.0.0
  libicessl34:i386,libssl1.0.0:i386 1.0.0
  libicepatch2-34:i386,libssl1.0.0:i386 1.0.0
  libhttrack2:i386,libssl1.0.0:i386
  libhttrack-dev:i386,libssl1.0.0:i386
  libh323-1.21.0:i386,libssl1.0.0:i386 1.0.0
  libgsoap1:i386,libssl1.0.0:i386 1.0.0
  libgridsite1.7:i386,libssl1.0.0:i386 1.0.0
  libglobus-openssl-module0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gssapi-gsi4:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-sysconfig1:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-proxy-ssl1:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-proxy-core0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-openssl-error0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-credential1:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-cert-utils0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gsi-callback0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gridftp-server0:i386,libssl1.0.0:i386 1.0.0
  libglobus-gass-copy2:i386,libssl1.0.0:i386 1.0.0
  libglobus-gass-cache5:i386,libssl1.0.0:i386 1.0.0
  libglobus-ftp-client2:i386,libssl1.0.0:i386 1.0.0
  libgfarm1:i386,libssl1.0.0:i386 1.0.0
  libgdcm2.0:i386,libssl1.0.0:i386 1.0.0
  libgcgi0:i386,libssl1.0.0:i386 1.0.0
  libfaifa0:i386,libssl1.0.0:i386 1.0.0
  libengine-pkcs11-openssl:i386,libssl1.0.0:i386 1.0.0
  libeiskaltdcpp2.2:i386,libssl1.0.0:i386 1.0.0
  libduo3:i386,libssl1.0.0:i386 1.0.0
  libdkim1d:i386,libssl1.0.0:i386 1.0.0
  libdigidocpp0:i386,libssl1.0.0:i386 1.0.0
  libdigidoc2:i386,libssl1.0.0:i386 1.0.0
  libdigidoc-dev:i386,libssl1.0.0:i386 1.0.0
  libdc5:i386,libssl1.0.0:i386 1.0.0
  libcyrus-imap-perl24:i386,libssl1.0.0:i386 1.0.0
  libcrypt-ssleay-perl:i386,libssl1.0.0:i386 1.0.0
  libcrypt-smime-perl:i386,libssl1.0.0:i386 1.0.0
  libcrypt-openssl-x509-perl:i386,libssl1.0.0:i386 1.0.0
  libcrypt-openssl-dsa-perl:i386,libssl1.0.0:i386 1.0.0
  libcouchdb-glib-1.0-2:i386,libssl1.0.0:i386 1.0.0
  libcherokee-mod-libssl:i386,libssl1.0.0:i386 1.0.0
  libc-client2007e:i386,libssl1.0.0:i386 1.0.0
  libbotan-1.8.13:i386,libssl1.0.0:i386 1.0.0
  libbotan-1.10-0:i386,libssl1.0.0:i386 1.0.0
  libbobcat2:i386,libssl1.0.0:i386 1.0.0
  libbeidlibopensc2:i386,libssl1.0.0:i386 1.0.0
  libbeidlib3:i386,libssl1.0.0:i386 1.0.0
  libbeid2:i386,libssl1.0.0:i386 1.0.0
  libaxis2c0:i386,libssl1.0.0:i386 1.0.0
  libarccommon1:i386,libssl1.0.0:i386 1.0.0
  libapache2-mod-qos:i386,libssl1.0.0:i386 1.0.0
  libapache2-mod-php5filter:i386,libssl1.0.0:i386 1.0.0
  libapache2-mod-authn-webid:i386,libssl1.0.0:i386 1.0.0
  libapache2-mod-auth-cas:i386,libssl1.0.0:i386 1.0.0
  libafflib0:i386,libssl1.0.0:i386 1.0.0
  libace-ssl-6.0.1:i386,libssl1.0.0:i386 1.0.0
  libace-inet-ssl-6.0.1:i386,libssl1.0.0:i386 1.0.0
  ldnsutils:i386,libssl1.0.0:i386 1.0.0
  l2tp-ipsec-vpn:i386,libssl1.0.0:i386 1.0.0
  kvirc-modules:i386,libssl1.0.0:i386 1.0.0
  kvirc:i386,libssl1.0.0:i386 1.0.0
  kumofs:i386,libssl1.0.0:i386 1.0.0
  krb5-pkinit:i386,libssl1.0.0:i386 1.0.0
  kontrolpack:i386,libssl1.0.0:i386 1.0.0
  kolabadmin:i386,libssl1.0.0:i386 1.0.0
  kolab-libcyrus-imap-perl:i386,libssl1.0.0:i386 1.0.0
  kolab-cyrus-pop3d:i386,libssl1.0.0:i386 1.0.0
  kolab-cyrus-imapd:i386,libssl1.0.0:i386 1.0.0
  kolab-cyrus-common:i386,libssl1.0.0:i386 1.0.0
  kolab-cyrus-clients:i386,libssl1.0.0:i386 1.0.0
  kftpgrabber:i386,libssl1.0.0:i386 1.0.0
  kannel-sqlbox:i386,libssl1.0.0:i386 1.0.0
  kannel-extras:i386,libssl1.0.0:i386 1.0.0
  kannel:i386,libssl1.0.0:i386 1.0.0
  jabberd2:i386,libssl1.0.0:i386 1.0.0
  italc-client:i386,libssl1.0.0:i386 1.0.0
  isync:i386,libssl1.0.0:i386 1.0.0
  istgt:i386,libssl1.0.0:i386 1.0.0
  isc-dhcp-server-ldap:i386,libssl1.0.0:i386 1.0.0
  isakmpd:i386,libssl1.0.0:i386 1.0.0
  ipmitool:i386,libssl1.0.0:i386 1.0.0
  inn2-lfs:i386,libssl1.0.0:i386 1.0.0
  inn2:i386,libssl1.0.0:i386 1.0.0
  imapproxy:i386,libssl1.0.0:i386 1.0.0
  imapfilter:i386,libssl1.0.0:i386 1.0.0
  ike-scan:i386,libssl1.0.0:i386 1.0.0
  ike-qtgui:i386,libssl1.0.0:i386 1.0.0
  ike:i386,libssl1.0.0:i386 1.0.0
  idecrypt:i386,libssl1.0.0:i386 1.0.0
  ice34-services:i386,libssl1.0.0:i386 1.0.0
  ia32-libs-multiarch:i386,libssl1.0.0:i386
  hydra:i386,libssl1.0.0:i386 1.0.0
  httping:i386,libssl1.0.0:i386 1.0.0
  httperf:i386,libssl1.0.0:i386 1.0.0
  httest:i386,libssl1.0.0:i386 1.0.0
  hostapd:i386,libssl1.0.0:i386 1.0.0
  hfsprogs:i386,libssl1.0.0:i386 1.0.0
  heirloom-mailx:i386,libssl1.0.0:i386 1.0.0
  gvpe:i386,libssl1.0.0:i386 1.0.0
  gstreamer0.10-plugins-bad:i386,libssl1.0.0:i386 1.0.0
  grisbi:i386,libssl1.0.0:i386 1.0.0
  gridengine-exec:i386,libssl1.0.0:i386 1.0.0
  gogoc:i386,libssl1.0.0:i386 1.0.0
  gnupg-pkcs11-scd:i386,libssl1.0.0:i386 1.0.0
  gnubiff:i386,libssl1.0.0:i386 1.0.0
  globus-proxy-utils:i386,libssl1.0.0:i386 1.0.0
  globus-gram-job-manager:i386,libssl1.0.0:i386 1.0.0
  globus-gatekeeper:i386,libssl1.0.0:i386 1.0.0
  globus-gass-copy-progs:i386,libssl1.0.0:i386 1.0.0
  ginkgocadx:i386,libssl1.0.0:i386 1.0.0
  gfsd:i386,libssl1.0.0:i386 1.0.0
  gatling:i386,libssl1.0.0:i386 1.0.0
  g2ipmsg:i386,libssl1.0.0:i386 1.0.0
  ftpd-ssl:i386,libssl1.0.0:i386 1.0.0
  ftp-ssl:i386,libssl1.0.0:i386 1.0.0
  fqterm:i386,libssl1.0.0:i386 1.0.0
  fossil:i386,libssl1.0.0:i386 1.0.0
  flush:i386,libssl1.0.0:i386 1.0.0
  fdm:i386,libssl1.0.0:i386 1.0.0
  ewf-tools:i386,libssl1.0.0:i386 1.0.0
  eurephia:i386,libssl1.0.0:i386 1.0.0
  ettercap-text-only:i386,libssl1.0.0:i386 1.0.0
  ettercap-graphical:i386,libssl1.0.0:i386 1.0.0
  epic5:i386,libssl1.0.0:i386 1.0.0
  epic4:i386,libssl1.0.0:i386 1.0.0
  encfs:i386,libssl1.0.0:i386 1.0.0
  ekg2-core:i386,libssl1.0.0:i386 1.0.0
  ekg-gtk:i386,libssl1.0.0:i386 1.0.0
  ekg:i386,libssl1.0.0:i386 1.0.0
  ejabberd:i386,libssl1.0.0:i386 1.0.0
  eggdrop:i386,libssl1.0.0:i386 1.0.0
  dsniff:i386,libssl1.0.0:i386 1.0.0
  dmg2img:i386,libssl1.0.0:i386 1.0.0
  dma:i386,libssl1.0.0:i386 1.0.0
  dk-filter:i386,libssl1.0.0:i386 1.0.0
  dillo:i386,libssl1.0.0:i386 1.0.0
  dicomscope:i386,libssl1.0.0:i386 1.0.0
  dcmtk:i386,libssl1.0.0:i386 1.0.0
  dcap-tunnel-ssl:i386,libssl1.0.0:i386 1.0.0
  cyrus-replication-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-pop3d-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-nntpd-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-murder-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-imapd-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-common-2.4:i386,libssl1.0.0:i386 1.0.0
  cyrus-clients-2.4:i386,libssl1.0.0:i386 1.0.0
  crtmpserver-libs:i386,libssl1.0.0:i386 1.0.0
  crtmpserver-apps:i386,libssl1.0.0:i386 1.0.0
  courier-ssl:i386,libssl1.0.0:i386 1.0.0
  cone:i386,libssl1.0.0:i386 1.0.0
  citadel-webcit:i386,libssl1.0.0:i386 1.0.0
  citadel-server:i386,libssl1.0.0:i386 1.0.0
  citadel-client:i386,libssl1.0.0:i386 1.0.0
  cfengine3:i386,libssl1.0.0:i386 1.0.0
  cfengine2:i386,libssl1.0.0:i386 1.0.0
  certmonger:i386,libssl1.0.0:i386 1.0.0
  c3270:i386,libssl1.0.0:i386 1.0.0
  burp:i386,libssl1.0.0:i386 1.0.0
  btpd:i386,libssl1.0.0:i386 1.0.0
  bozohttpd:i386,libssl1.0.0:i386 1.0.0
  boxbackup-server:i386,libssl1.0.0:i386 1.0.0
  boxbackup-client:i386,libssl1.0.0:i386 1.0.0
  boinc-server-maker:i386,libssl1.0.0:i386 1.0.0
  boinc-client:i386,libssl1.0.0:i386 1.0.0
  bitcoind:i386,libssl1.0.0:i386 1.0.0
  bip:i386,libssl1.0.0:i386 1.0.0
  beid-tools:i386,libssl1.0.0:i386 1.0.0
  batv-filter:i386,libssl1.0.0:i386 1.0.0
  barnowl:i386,libssl1.0.0:i386 1.0.0
  balsa:i386,libssl1.0.0:i386 1.0.0
  ayttm:i386,libssl1.0.0:i386 1.0.0
  asterisk-modules:i386,libssl1.0.0:i386 1.0.0
  asterisk:i386,libssl1.0.0:i386 1.0.0
  apf-server:i386,libssl1.0.0:i386 1.0.0
  apf-client:i386,libssl1.0.0:i386 1.0.0
  anon-proxy:i386,libssl1.0.0:i386 1.0.0
  amanda-common:i386,libssl1.0.0:i386 1.0.0
  alpine:i386,libssl1.0.0:i386 1.0.0
  afflib-tools:i386,libssl1.0.0:i386 1.0.0
  xchat-gnome:i386,libssl1.0.0:i386 1.0.0
  wpasupplicant:i386,libssl1.0.0:i386 1.0.0
  wget:i386,libssl1.0.0:i386 1.0.0
  w3m:i386,libssl1.0.0:i386 1.0.0
  vsftpd:i386,libssl1.0.0:i386 1.0.0
  virtuoso-opensource-6.1-common:i386,libssl1.0.0:i386 1.0.0
  virtuoso-opensource-6.1-bin:i386,libssl1.0.0:i386 1.0.0
  trousers:i386,libssl1.0.0:i386 1.0.0
  transmission-qt:i386,libssl1.0.0:i386 1.0.0
  transmission-gtk:i386,libssl1.0.0:i386 1.0.0
  transmission-daemon:i386,libssl1.0.0:i386 1.0.0
  transmission-cli:i386,libssl1.0.0:i386 1.0.0
  tcpdump:i386,libssl1.0.0:i386 1.0.0
  spamc:i386,libssl1.0.0:i386 1.0.0
  snmp:i386,libssl1.0.0:i386 1.0.0
  siege:i386,libssl1.0.0:i386 1.0.0
  sasl2-bin:i386,libssl1.0.0:i386 1.0.0
  rdesktop:i386,libssl1.0.0:i386 1.0.0
  racoon:i386,libssl1.0.0:i386 1.0.0
  python3.2-minimal:i386,libssl1.0.0:i386 1.0.0
  python3.2-dbg:i386,libssl1.0.0:i386 1.0.0
  python2.7-minimal:i386,libssl1.0.0:i386 1.0.0
  python2.7-dbg:i386,libssl1.0.0:i386 1.0.0
  python-openssl-dbg:i386,libssl1.0.0:i386 1.0.0
  python-openssl:i386,libssl1.0.0:i386 1.0.0
  python-m2crypto:i386,libssl1.0.0:i386 1.0.0
  pulseaudio-module-raop:i386,libssl1.0.0:i386 1.0.0
  postgresql-contrib-9.1:i386,libssl1.0.0:i386 1.0.0
  postgresql-client-9.1:i386,libssl1.0.0:i386 1.0.0
  postgresql-9.1:i386,libssl1.0.0:i386 1.0.0
  postfix:i386,libssl1.0.0:i386 1.0.0
  php5-cli:i386,libssl1.0.0:i386 1.0.0
  php5-cgi:i386,libssl1.0.0:i386 1.0.0
  pacemaker:i386,libssl1.0.0:i386 1.0.0
  openvpn:i386,libssl1.0.0:i386 1.0.0
  openssl:i386,libssl1.0.0:i386 1.0.1
  openssh-server:i386,libssl1.0.0:i386 1.0.0
  openssh-client:i386,libssl1.0.0:i386 1.0.0
  nmap:i386,libssl1.0.0:i386 1.0.0
  nagios-plugins-basic:i386,libssl1.0.0:i386 1.0.0
  nagios-nrpe-server:i386,libssl1.0.0:i386 1.0.0
  likewise-open:i386,libssl1.0.0:i386 1.0.0
  libwvstreams4.6-extras:i386,libssl1.0.0:i386 1.0.0
  libvirtodbc0:i386,libssl1.0.0:i386 1.0.0
  libtspi1:i386,libssl1.0.0:i386 1.0.0
  libssl1.0.0-dbg:i386,libssl1.0.0:i386 1.0.1-4ubuntu3
  libssl1.0.0,libssl1.0.0:i386 1.0.1-4ubuntu3
  libssl1.0.0,libssl1.0.0:i386 1.0.1-4ubuntu3
  libssl-dev:i386,libssl1.0.0:i386 1.0.1-4ubuntu3
  libssh-4:i386,libssl1.0.0:i386 1.0.0
  libsnmp15:i386,libssl1.0.0:i386 1.0.0
  libserf1:i386,libssl1.0.0:i386 1.0.0
  libsasl2-modules-gssapi-mit:i386,libssl1.0.0:i386 1.0.0
  libsasl2-modules:i386,libssl1.0.0:i386 1.0.0
  libruby1.9.1:i386,libssl1.0.0:i386 1.0.0
  libruby1.8:i386,libssl1.0.0:i386 1.0.0
  libreoffice-core:i386,libssl1.0.0:i386 1.0.0
  libqca2-plugin-ossl:i386,libssl1.0.0:i386 1.0.0
  libpython3.2:i386,libssl1.0.0:i386 1.0.0
  libpython2.7:i386,libssl1.0.0:i386 1.0.0
  libpq5:i386,libssl1.0.0:i386 1.0.0
  libpkcs11-helper1:i386,libssl1.0.0:i386 1.0.0
  libpam-p11:i386,libssl1.0.0:i386 1.0.0
  libpam-mount:i386,libssl1.0.0:i386 1.0.0
  libp11-2:i386,libssl1.0.0:i386 1.0.0
  libopenhpi2:i386,libssl1.0.0:i386 1.0.0
  libopencryptoki0:i386,libssl1.0.0:i386 1.0.0
  libnet-ssleay-perl:i386,libssl1.0.0:i386 1.0.0
  libneon27:i386,libssl1.0.0:i386 1.0.0
  libmsn0.3:i386,libssl1.0.0:i386 1.0.0
  libfreerdp1:i386,libssl1.0.0:i386 1.0.0
  libevent-openssl-2.0-5:i386,libssl1.0.0:i386 1.0.0
  libesmtp6:i386,libssl1.0.0:i386 1.0.0
  libdns81:i386,libssl1.0.0:i386 1.0.0
  libcurl3:i386,libssl1.0.0:i386 1.0.0
  libcrypt-openssl-rsa-perl:i386,libssl1.0.0:i386 1.0.0
  libcrypt-openssl-random-perl:i386,libssl1.0.0:i386 1.0.0
  libcrypt-openssl-bignum-perl:i386,libssl1.0.0:i386 1.0.0
  libcib1:i386,libssl1.0.0:i386 1.0.0
  libapache2-mod-php5:i386,libssl1.0.0:i386 1.0.0
  keepalived:i386,libssl1.0.0:i386 1.0.0
  irssi:i386,libssl1.0.0:i386 1.0.0
  iputils-ping:i386,libssl1.0.0:i386 1.0.0
  htmldoc:i386,libssl1.0.0:i386 1.0.0
  freeradius-utils:i386,libssl1.0.0:i386 1.0.0
  freeradius:i386,libssl1.0.0:i386 1.0.0
  fetchmail:i386,libssl1.0.0:i386 1.0.0
  erlang-ssl:i386,libssl1.0.0:i386 1.0.0
  erlang-crypto:i386,libssl1.0.0:i386 1.0.0
  dovecot-core:i386,libssl1.0.0:i386 1.0.0
  crda:i386,libssl1.0.0:i386 1.0.0
  bacula-common:i386,libssl1.0.0:i386 1.0.0
  apache2.2-bin:i386,libssl1.0.0:i386 1.0.0
  apache2-utils:i386,libssl1.0.0:i386 1.0.0
Dependencies: 
1.0.1-4ubuntu5.10 - libc6:i386 (2 2.7) zlib1g:i386 (2 1:1.1.4) debconf:i386 (18 0.5) debconf-2.0:i386 (0 (null)) multiarch-support:i386 (0 (null)) openssh-client (3 1:5.9p1-4) openssh-client:i386 (3 1:5.9p1-4) openssh-server (3 1:5.9p1-4) openssh-server:i386 (3 1:5.9p1-4) libssl1.0.0 (3 1.0.1-4ubuntu5.10) libssl1.0.0 (6 1.0.1-4ubuntu5.10) 
1.0.1-4ubuntu5.9 - libc6:i386 (2 2.7) zlib1g:i386 (2 1:1.1.4) debconf:i386 (18 0.5) debconf-2.0:i386 (0 (null)) multiarch-support:i386 (0 (null)) openssh-client (3 1:5.9p1-4) openssh-client:i386 (3 1:5.9p1-4) openssh-server (3 1:5.9p1-4) openssh-server:i386 (3 1:5.9p1-4) libssl1.0.0 (3 1.0.1-4ubuntu5.9) libssl1.0.0 (6 1.0.1-4ubuntu5.9) 
1.0.1-4ubuntu3 - libc6:i386 (2 2.7) zlib1g:i386 (2 1:1.1.4) debconf:i386 (18 0.5) debconf-2.0:i386 (0 (null)) multiarch-support:i386 (0 (null)) openssh-client (3 1:5.9p1-4) openssh-client:i386 (3 1:5.9p1-4) openssh-server (3 1:5.9p1-4) openssh-server:i386 (3 1:5.9p1-4) libssl1.0.0 (3 1.0.1-4ubuntu3) libssl1.0.0 (6 1.0.1-4ubuntu3) 
Provides: 
1.0.1-4ubuntu5.10 - 
1.0.1-4ubuntu5.9 - 
1.0.1-4ubuntu3 - 
Reverse Provides: 


```

---

### Post by philinux on 2013-08-14
Try running this.

sudo dpkg --configure -a

---

### Post by candra2 on 2013-08-14
here is what I got...


```
:~$ sudo dpkg --configure -a
[sudo] password for: 
dpkg: error processing libssl1.0.0 (--configure):
 libssl1.0.0:amd64 1.0.1-4ubuntu5.10 cannot be configured because libssl1.0.0:i386 is in a different version (1.0.1-4ubuntu5.9)
dpkg: error processing libssl1.0.0:i386 (--configure):
 libssl1.0.0:i386 1.0.1-4ubuntu5.9 cannot be configured because libssl1.0.0:amd64 is in a different version (1.0.1-4ubuntu5.10)
Errors were encountered while processing:
 libssl1.0.0
 libssl1.0.0:i386

```

---

### Post by ian-weisser on 2013-08-14
Looks like at some point you tried to install a Myth or Mythbuntu or a Mythbuntu PPA. Seems like it dragged in multiarch support.

We have almost enough information. But a little more yet.
Please post the results of
```
cat /etc/apt/sources.list
ls -l /etc/apt/sources.list.d/
```

Next, try (and post the results of)
```
sudo apt-get remove --simulate libssl1.0.0:i386
```
The --simulate flag means it may generate a lot of (potential) error messages...but will not actually *do* anything.

---

### Post by candra2 on 2013-08-14
Here is part 1:
```

~$ cat /etc/apt/sources.list
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

Here is part 2:

```
$ ls -l /etc/apt/sources.list.d/
total 0
```

Here is part 3:

```
~$ sudo apt-get remove --simulate libssl1.0.0:i386
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libsasl2-modules:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

thanks for your ongoing help :-)

---

### Post by ian-weisser on 2013-08-14
> **candra2 said:**
> Here is part 1:```
...
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```


Here is an example of a third-party (non-Ubuntu) repository. 
When troubleshooting package conflicts, disable these.
To disable it, edit the file to add a # (a comment symbol) to the front of the offending line.
You can also add comments to remind yourself why you disabled it.

> **candra2 said:**
> ```
$ ls -l /etc/apt/sources.list.d/
total 0
```
Good! Only one third-party repository, and no PPAs. Makes troubleshooting much easier.


> **candra2 said:**
> 
```
~$ sudo apt-get remove --simulate libssl1.0.0:i386
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
[COLOR=#ff0000] libsasl2-modules:i386[/COLOR] : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

See how libsasl2-modules:i386 depends on libssl1.0.0:i386?
Next, we need to see what depends on libsasl2-modules:i386.
```
sudo apt-get remove --simulate libsasl2-modules:i386
```
We'll follow this tree of dependencies to the top. That will tell us what you added that caused the problem. Removing (or reinstalling) is an easy way to fix the problem.

---

### Post by candra2 on 2013-08-14
> See how libsasl2-modules:i386 depends on libssl1.0.0:i386?
Next, we need to see what depends on libsasl2-modules:i386.


here is the code:

```
~$ sudo apt-get remove --simulate libsasl2-modules:i386
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is to be installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

About part 1 in the previous message you wrote:

> Here is an example of a third-party (non-Ubuntu) repository. 
When troubleshooting package conflicts, disable these.
To disable it, edit the file to add a # (a comment symbol) to the front of the offending line.
You can also add comments to remind yourself why you disabled it.

I am in process of doing this and will report back...

thanks!!

---

### Post by candra2 on 2013-08-14
> Here is an example of a third-party (non-Ubuntu) repository. 
When troubleshooting package conflicts, disable these.
To disable it, edit the file to add a # (a comment symbol) to the front of the offending line.
You can also add comments to remind yourself why you disabled it.

Can you tell me how to open the file listing the repositiories so I can put the # at the front of the offending line...

standing by...

---

### Post by philinux on 2013-08-15
> **candra2 said:**
> Can you tell me how to open the file listing the repositiories so I can put the # at the front of the offending line...

standing by...

```
gksu gedit /etc/apt/sources.list
```

---

### Post by candra2 on 2013-08-15
Thank you - OK - done

I have placed a # before the below line and saved the file in gedit


```
deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main


```

Awaitng any further instructions...

---

### Post by philinux on 2013-08-15
I have both of those files installed on my system which is also 64 bit but I'm running Saucy so versions are higher.

Make sure you back up any data you need before proceeding with this.

Then try this.

I would try removing the i386 package. Then we can try reinstalling it after but check this commands output is not going to do anything drastic. Lets do a dry run with this.

```
sudo dpkg --dry-run --remove libssl1.0.0:i386
```

[edit] when I run the above on my system it comes back with this:-
```
dpkg: dependency problems prevent removal of libssl1.0.0:i386:
 skype-bin depends on libssl1.0.0.

dpkg: error processing libssl1.0.0:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libssl1.0.0:i386
```

Looks like skype and it's dependencies are the source.

---

### Post by candra2 on 2013-08-15
Thanks -0 pardon the delay - had to be out today - now here...
```

~$ sudo dpkg --dry-run --remove libssl1.0.0:i386
[sudo] password for d: 
dpkg: dependency problems prevent removal of libssl1.0.0:i386:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0).
dpkg: error processing libssl1.0.0:i386 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libssl1.0.0:i386
```

standing by...

---

### Post by candra2 on 2013-08-15
Also know this - I do not need Skype - if taht would help things at all...

---

### Post by philinux on 2013-08-15
Unless anyone else has a better idea I would try this. Assuming you done the data backups.

sudo apt-get install -f --force-yes

---

### Post by candra2 on 2013-08-15
Ok - I will be sure to back it up - it sounds like you are also putting out a call for suggestions - so I may wait a bit to see if someone else has input. 

Thank you for your guidance...

---

### Post by bapoumba on 2013-08-15
After you modified your sources.list, did you run **sudo apt-get update** and **sudo apt-get dist-upgrade **?
Just to make sure, please post again your sources.list, thanks.

---

### Post by philinux on 2013-08-15
> **bapoumba said:**
> After you modified your sources.list, did you run **sudo apt-get update** and **sudo apt-get dist-upgrade **?
Just to make sure, please post again your sources.list, thanks.

Deffo worth a shot.

---

### Post by bapoumba on 2013-08-15
> **philinux said:**
> Deffo worth a shot.
Well, yeah, last resort is to either place the packages on hold, the package manager will probably stop complaining but the issue wont be fully solved, or attack at the dpkg level, which has risks :)

---

### Post by philinux on 2013-08-15
> **bapoumba said:**
> Well, yeah, last resort is to either place the packages on hold, the package manager will probably stop complaining but the issue wont be fully solved, or attack at the dpkg level, which has risks :)

Yep hence the request to make sure backups ok. Can u do a --force-yes with a dry run. Never done that.8-)

(Edit) I assume that a dry run would work ok too.

---

### Post by candra2 on 2013-08-15
> After you modified your sources.list, did you run **sudo apt-get update** and **sudo apt-get dist-upgrade **?
Just to make sure, please post again your sources.list, thanks.

Here it is - I think this is what you wanted to see - I just ran it again...
```

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/

#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
#deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu precise partner
# deb-src http://archive.canonical.com/ubuntu precise partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main

#deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
```

---

### Post by bapoumba on 2013-08-15
OK thanks, now the outputs to sudo apt-get update and sudo apt-get dist-upgrade please.
It is quite late here, I'll wait a little, but not too much. If I'm not around, others will pick it up and I'll be back tomorrow :)

---

### Post by candra2 on 2013-08-15
here is the first one...
```

~$  sudo apt-get update
[sudo] password for d: 
Hit http://us.archive.ubuntu.com precise Release.gpg                                                                                                         
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                                       
Hit http://us.archive.ubuntu.com precise-backports Release.gpg             
Get:2 http://extras.ubuntu.com precise Release.gpg [72 B]
Hit http://us.archive.ubuntu.com precise Release
Get:3 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Get:4 http://security.ubuntu.com precise-security Release.gpg [198 B]                               
Hit http://extras.ubuntu.com precise Release                                                        
Get:5 http://security.ubuntu.com precise-security Release [49.6 kB]             
Hit http://extras.ubuntu.com precise/main Sources                                       
Hit http://us.archive.ubuntu.com precise-backports Release                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                
Hit http://extras.ubuntu.com precise/main i386 Packages                        
Ign http://extras.ubuntu.com precise/main TranslationIndex                     
Hit http://us.archive.ubuntu.com precise/main Sources                          
Hit http://us.archive.ubuntu.com precise/restricted Sources                    
Hit http://us.archive.ubuntu.com precise/universe Sources                      
Hit http://us.archive.ubuntu.com precise/multiverse Sources                    
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Get:6 http://security.ubuntu.com precise-security/main Sources [85.0 kB]
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex          
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex          
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex            
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [412 kB]      
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                                                                                                                                                                            
Get:9 http://security.ubuntu.com precise-security/universe Sources [28.0 kB]                                                                                                                                                                                                              
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                                                                                                                                                               
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                                  
Get:10 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                                                                                                                                                                                                          
Get:11 http://us.archive.ubuntu.com precise-updates/universe Sources [93.9 kB]                                                                                                                                                                                                            
Get:12 http://security.ubuntu.com precise-security/multiverse Sources [1,383 B]                                                                                                                                                                                                           
Get:13 http://security.ubuntu.com precise-security/main amd64 Packages [305 kB]                                                                                                                                                                                                           
Get:14 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                                                                                                                                                                                                          
Get:15 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [672 kB]                                                                                                                                                                                                          
Get:16 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]                                                                                                                                                                                                    
Get:17 http://security.ubuntu.com precise-security/universe amd64 Packages [80.8 kB]                                                                                                                                                                                                      
Get:18 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]                                                                                                                                                                                                    
Get:19 http://security.ubuntu.com precise-security/main i386 Packages [320 kB]                                                                                                                                                                                                            
Get:20 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]                                                                                                                                                                                                   
Get:21 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [211 kB]                                                                                                                                                                                                      
Get:22 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                                                                                                                                                                                                     
Get:23 http://security.ubuntu.com precise-security/universe i386 Packages [83.7 kB]                                                                                                                                                                                                       
Get:24 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]                                                                                                                                                                                                     
Get:25 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]                                                                                                                                                                                                           
Get:26 http://security.ubuntu.com precise-security/multiverse TranslationIndex [71 B]                                                                                                                                                                                                     
Get:27 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]                                                                                                                                                                                                   
Get:28 http://us.archive.ubuntu.com precise-updates/main i386 Packages [692 kB]                                                                                                                                                                                                           
Get:29 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]                                                                                                                                                                                                     
Get:30 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]                                                                                                                                                                                                       
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                                                                                                                                       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                                                                                                                                                 
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                                                                                                                                                 
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                                                                                                                                                   
Get:31 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]                                                                                                                                                                                                    
Get:32 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [215 kB]                                                                                                                                                                                                       
Get:33 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]                                                                                                                                                                                                    
Get:34 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                                                                                                                                                       
Get:35 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                                                                                                                                                                 
Get:36 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                                                                                                                                                                 
Get:37 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                                                                                                                                                                   
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                                                                                                                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                                                                                                                                                                                                                       
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                                                                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                                                                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                                                                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                                                                                                                                                        
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                                                                                                                                                        
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                                                                                                                                                          
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                                                                                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                                                                                                                                                                                                
Fetched 3,387 kB in 51s (66.3 kB/s)                                                                                                                                                                                                                                                       
Reading package lists... Done

```

second one is coming right away...stay tuned....

---

### Post by candra2 on 2013-08-15
here is the second...

```
~$ sudo apt-get dist-upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is installed
E: Unmet dependencies. Try using -f.

```

thank you, thank you - standing by...

---

### Post by bapoumba on 2013-08-15
> **candra2 said:**
> here is the first one...
<snip>
second one is coming right away...stay tuned....

Looks ok, no error.

---

### Post by candra2 on 2013-08-15
just so you saw it - my second got posted a millisecond before your first reply...

---

### Post by bapoumba on 2013-08-15
> **candra2 said:**
> here is the second...

```
~$ sudo apt-get dist-upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is installed
E: Unmet dependencies. Try using -f.

```

thank you, thank you - standing by...
OK now that the correct sources.list has been read, please try **sudo apt-get -f install**. Not sure it will downgrade the libs..

---

### Post by candra2 on 2013-08-15
here it is...

```
~$ sudo apt-get -f install
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb thunderbird-locale-en-us libqt4-designer:i386 calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386 libgettextpo0:i386
  thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be upgraded:
  libssl1.0.0:i386
1 upgraded, 0 newly installed, 0 to remove and 112 not upgraded.
2 not fully installed or removed.
Need to get 0 B/1,008 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
E: Internal Error, No file name for libssl1.0.0

```

---

### Post by bapoumba on 2013-08-15
y,
you'll run the autoremove after.

---

### Post by candra2 on 2013-08-15
sorry, I am not understanding...

---

### Post by bapoumba on 2013-08-15
Sorry, did not read all the way down.
Please try sudo apt-get install libssl1.0.0

---

### Post by candra2 on 2013-08-15
here it is...

```
~$ sudo apt-get install libssl1.0.0 
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libssl1.0.0 is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is to be installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by bapoumba on 2013-08-15
apt-cache show libssl1.0.0
Which version is currently installed ?

---

### Post by candra2 on 2013-08-15
I am not sure...

---

### Post by bapoumba on 2013-08-15
> **candra2 said:**
> I am not sure...

just run the above command and post the output. It will be in there.

---

### Post by candra2 on 2013-08-15
here it is...

```
    apt-cache show libssl1.0.0
Package: libssl1.0.0
Priority: required
Section: libs
Installed-Size: 2921
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu5.10
Depends: libc6 (>= 2.14), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Pre-Depends: multiarch-support
Breaks: openssh-client (<< 1:5.9p1-4), openssh-server (<< 1:5.9p1-4)
Filename: pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu5.10_amd64.deb
Size: 1048422
MD5sum: 4cb449213437fe44c23491ba3523f02d
SHA1: 4f1e4ede4376d2c7294050c2b7c33ca54626e219
SHA256: 9f8b0df37301fae9d70f9c9e8df73c7177bf3e27c7ef0995b26f7671e8a9c15c
Description-en: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.
 .
 It is part of the OpenSSL implementation of SSL.
Multi-Arch: same
Description-md5: 2e9416e72fb31714d9b26021a3ee7e85
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal

Package: libssl1.0.0
Priority: required
Section: libs
Installed-Size: 2835
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian OpenSSL Team <pkg-openssl-devel@lists.alioth.debian.org>
Architecture: amd64
Source: openssl
Version: 1.0.1-4ubuntu3
Depends: libc6 (>= 2.14), zlib1g (>= 1:1.1.4), debconf (>= 0.5) | debconf-2.0
Pre-Depends: multiarch-support
Breaks: openssh-client (<< 1:5.9p1-4), openssh-server (<< 1:5.9p1-4)
Filename: pool/main/o/openssl/libssl1.0.0_1.0.1-4ubuntu3_amd64.deb
Size: 1010968
MD5sum: 9de8b4fcd6476fd259eb9609998fec2b
SHA1: 9941d8ab68aab61589009e58ea3bc1241bfa7233
SHA256: 64e407da8ed6bf82aa829e52329e7f27bd4417742595b5c2c7c4e1d228ff08ba
Description-en: SSL shared libraries
 libssl and libcrypto shared libraries needed by programs like
 apache-ssl, telnet-ssl and openssh.
 .
 It is part of the OpenSSL implementation of SSL.
Multi-Arch: same
Description-md5: 2e9416e72fb31714d9b26021a3ee7e85
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 5y
Task: minimal

```

---

### Post by bapoumba on 2013-08-15
OK you have 1.0.1-4ubuntu5.10 installed which is the correct version for precise : [http://packages.ubuntu.com/search?keywords=libssl1.0.0&searchon=names&suite=precise&section=all](http://packages.ubuntu.com/search?keywords=libssl1.0.0&searchon=names&suite=precise&section=all)

Let me go back to your previous error messages, some libs may have to be downgraded manually, I have to think a bit.

---

### Post by candra2 on 2013-08-15
sure thing - standing by - I understand it is very late for you - I can function as is and if we continue after your rest that is certainly fine...as is best for you...

---

### Post by bapoumba on 2013-08-15
Before getting into too harsh commands, please try:
```
sudo apt-get clean
sudo apt-get autoremove
```
You should get the same error message at the end, but it will do some cleaning.

Then run
```
sudo dpkg --configure -a
```
And see what it says.

---

### Post by candra2 on 2013-08-15
```
~$ sudo apt-get clean
:~$ 

```

the above did not seem to do anything - i tried it twice...
here is the next one
```

~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is installed
E: Unmet dependencies. Try using -f.

```
here is the third one...
```
~$ sudo dpkg --configure -a
dpkg: error processing libssl1.0.0 (--configure):
 libssl1.0.0:amd64 1.0.1-4ubuntu5.10 cannot be configured because libssl1.0.0:i386 is in a different version (1.0.1-4ubuntu5.9)
dpkg: error processing libssl1.0.0:i386 (--configure):
 libssl1.0.0:i386 1.0.1-4ubuntu5.9 cannot be configured because libssl1.0.0:amd64 is in a different version (1.0.1-4ubuntu5.10)
Errors were encountered while processing:
 libssl1.0.0
 libssl1.0.0:i386

```

---

### Post by bapoumba on 2013-08-15
```
sudo apt-get install libssl --reinstall
```

---

### Post by candra2 on 2013-08-15
```
~$ sudo apt-get install libssl --reinstall
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libssl is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'libssl' has no installation candidate

```

---

### Post by bapoumba on 2013-08-15
Sorry, sudo apt-get install libssl1.0.0 --reinstall

---

### Post by candra2 on 2013-08-15
```
~$ sudo apt-get install libssl1.0.0 --reinstall 
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libssl1.0.0 : Breaks: libssl1.0.0:i386 (!= 1.0.1-4ubuntu5.10) but 1.0.1-4ubuntu5.9 is to be installed
 libssl1.0.0:i386 : Breaks: libssl1.0.0 (!= 1.0.1-4ubuntu5.9) but 1.0.1-4ubuntu5.10 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by bapoumba on 2013-08-15
OK, all the "soft" fixes I know have been applied. 
```
sudo dpkg --purge --force-depends libssl1.0.0:i386
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by candra2 on 2013-08-15
do i have to be "careful" before proceeding further: Should I close programs and get everything backed up??

If you are only going to do surgery on the corrup file that is fine, or is the whole operating system at stake??

can I proceed as is or should I take maximum precautions...

thank you

---

### Post by bapoumba on 2013-08-15
Well, having backups is always a good idea :)

From earlier posts (the problem with skype for ex and looking around) I suppose you have a mix install of packages for 32 and 64 bit arch. What is the output to ```
uname -a
``` I bet you have 64-bit arch and installed some 32-bit packages (skype). The i386 lib is the one for 32-bit, so this is the one we are trying to get rid of, so that your normal libssl1.0.0 can be at the normal state for the package manager.

---

### Post by candra2 on 2013-08-15
```

~$ uname -a
Linux d-Parallels-Ubuntu 3.2.0-48-generic #74-Ubuntu SMP Thu Jun 6 19:43:26 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by bapoumba on 2013-08-15
Yes, you have a 64-bit arch. 
Either you try to remove the i386 lib, or there is here a process that worked to keep both :
[https://answers.launchpad.net/ubuntu/+source/software-center/+question/222801](https://answers.launchpad.net/ubuntu/+source/software-center/+question/222801) but did not work for some other user. I'm not that familiar with the process described there.

---

### Post by candra2 on 2013-08-15
Thank you so much...

As noted earlier in this thread - I do not need Skype - it can be deleted entirely. 

I just want to do whatever is easiest and safest to get the Update Manager working again. 

So we can delete both versions or remove te i386 lib if that is easier. 

Thoughts??

---

### Post by bapoumba on 2013-08-15
Well, at 2 in the morning, I say it is late.
Your system is not in danger for now :)
The package manager is upset and wont work until this is solved. If it was my own system, I'd remove the i386 lib. Now I will get some sleep.

You may not be able to remove skype if not all its dependencies are satisfied. That may just add some more complexity.

The package manager follows a tree of dependecies in a distribution, A depends on B which depends on C etc. All should be coherent at all times. When coherence is lost, the package manager cannot always solve the dependencies, and wont work normally until they are all met. Hopefully removing the i386 lib from your system will clear that dependency problem.

They are harsher commands with dpkg that can be tried if the one I proposed fails.

---

### Post by candra2 on 2013-08-15
Thank you so much - wishing you a peaceful rest..

Yes, I will aim to remove the i386 lib

I will go back in this thread and look for your instructions on how to remove teh i386 lib.

---

### Post by candra2 on 2013-08-16
Is this how I remove the i386 lib??
```

sudo dpkg --purge --force-depends libssl1.0.0:i386
sudo dpkg --configure -a
sudo apt-get -f install
```

---

### Post by ian-weisser on 2013-08-16
> **candra2 said:**
> Is this how I remove the i386 lib??
```

sudo dpkg --purge --force-depends libssl1.0.0:i386
sudo dpkg --configure -a
sudo apt-get -f install
```

The first line, yes. Certainly post the output of that session here. The warnings will be helpful.
The second line should not be necessary. Removed packages don't need to be configured.
The third line should be used carefully...it may not do what you expect, and it depends upon the warnings from the purge.

---

### Post by candra2 on 2013-08-16
here is the code from that first line
```

sudo dpkg --purge --force-depends libssl1.0.0:i386
[sudo] password for d: 
dpkg: libssl1.0.0:i386: dependency problems, but removing anyway as you requested:
 libsasl2-modules:i386 depends on libssl1.0.0 (>= 1.0.0).
(Reading database ... 666817 files and directories currently installed.)
Removing libssl1.0.0:i386 ...
Purging configuration files for libssl1.0.0:i386 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by bapoumba on 2013-08-16
Ok good, you removed the i386 lib that was causing the circular dependency hell :)
[https://en.wikipedia.org/wiki/Dependency_hell](https://en.wikipedia.org/wiki/Dependency_hell)

Please run to make sure things are ok or not.
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by philinux on 2013-08-16
Woohoo this is looking promising at last. :D

---

### Post by bapoumba on 2013-08-16
> **philinux said:**
> Woohoo this is looking promising at last. :D
Hehe, I still had one last resort command but not sure it would have worked in that case ;)

---

### Post by philinux on 2013-08-16
And it's taken 4 months to get this far lol.:D

---

### Post by candra2 on 2013-08-16
here is the first one:

 ```
sudo apt-get update
[sudo] password for d: 
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg              
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]
Get:4 http://extras.ubuntu.com precise Release.gpg [72 B]                    
Hit http://us.archive.ubuntu.com precise Release                             
Get:5 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://extras.ubuntu.com precise Release                                                                    
Hit http://extras.ubuntu.com precise/main Sources                                         
Hit http://us.archive.ubuntu.com precise-backports Release
Get:6 http://security.ubuntu.com precise-security/main Sources [85.0 kB]
Hit http://extras.ubuntu.com precise/main amd64 Packages                                               
Hit http://extras.ubuntu.com precise/main i386 Packages                       
Hit http://us.archive.ubuntu.com precise/main Sources                         
Hit http://us.archive.ubuntu.com precise/restricted Sources                   
Hit http://us.archive.ubuntu.com precise/universe Sources                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                    
Hit http://us.archive.ubuntu.com precise/multiverse Sources                   
Hit http://us.archive.ubuntu.com precise/main amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise/main i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise/universe i386 Packages                
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages              
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                 
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex           
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex           
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex             
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [412 kB]       
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                      
Get:9 http://security.ubuntu.com precise-security/universe Sources [28.0 kB]                        
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,383 B]                                                                                                                                                                                                           
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [305 kB]                                                                                                                                                                                                           
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                                                                                                                                                                               
Get:12 http://us.archive.ubuntu.com precise-updates/restricted Sources [5,467 B]                                                                                                                                                                                                          
Get:13 http://us.archive.ubuntu.com precise-updates/universe Sources [93.9 kB]                                                                                                                                                                                                            
Ign http://extras.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                                  
Get:14 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]                                                                                                                                                                                                    
Get:15 http://security.ubuntu.com precise-security/universe amd64 Packages [80.8 kB]                                                                                                                                                                                                      
Get:16 http://us.archive.ubuntu.com precise-updates/multiverse Sources [6,582 B]                                                                                                                                                                                                          
Get:17 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [672 kB]                                                                                                                                                                                                          
Get:18 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,186 B]                                                                                                                                                                                                    
Get:19 http://security.ubuntu.com precise-security/main i386 Packages [320 kB]                                                                                                                                                                                                            
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                                                                                                                                                                                                     
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [83.7 kB]                                                                                                                                                                                                       
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,371 B]                                                                                                                                                                                                     
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                                                                                                                                                                                                     
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                                                                                                                                                                                               
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                                                                                                                                                                                               
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                                                                                                                                                                                                 
Hit http://security.ubuntu.com precise-security/main Translation-en                                                                                                                                                                                                                       
Hit http://security.ubuntu.com precise-security/multiverse Translation-en                                                                                                                                                                                                                 
Get:23 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [10.1 kB]                                                                                                                                                                                                   
Hit http://security.ubuntu.com precise-security/restricted Translation-en                                                                                                                                                                                                                 
Hit http://security.ubuntu.com precise-security/universe Translation-en                                                                                                                                                                                                                   
Get:24 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [211 kB]                                                                                                                                                                                                      
Get:25 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [13.6 kB]                                                                                                                                                                                                   
Get:26 http://us.archive.ubuntu.com precise-updates/main i386 Packages [692 kB]                                                                                                                                                                                                           
Get:27 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [10.0 kB]                                                                                                                                                                                                    
Get:28 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [215 kB]                                                                                                                                                                                                       
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [13.8 kB]                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex                                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-backports/main Sources                                                                                                                                                                                                                           
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/universe Sources                                                                                                                                                                                                                       
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages                                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages                                                                                                                                                                                                                     
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages                                                                                                                                                                                                                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages                                                                                                                                                                                                               
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex                                                                                                                                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex                                                                                                                                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex                                                                                                                                                                                                            
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise/main Translation-en                                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en                                                                                                                                                                                                                        
Hit http://us.archive.ubuntu.com precise/restricted Translation-en                                                                                                                                                                                                                        
Hit http://us.archive.ubuntu.com precise/universe Translation-en                                                                                                                                                                                                                          
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en                                                                                                                                                                                                                      
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                                                                                                                                                                                                                
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                                                                                                                                                                                                                  
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                                                                                                                                                                                                    
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                                                                                                                                                                                                              
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                                                                                                                                                                                                                
Fetched 3,375 kB in 48s (68.9 kB/s)                                                                                                                                                                                                                                                       
Reading package lists... Done
```

here is the second...
```

$ sudo apt-get dist-upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libsasl2-modules:i386 : Depends: libssl1.0.0:i386 (>= 1.0.0) but it is not installed
E: Unmet dependencies. Try using -f.

```

---

### Post by philinux on 2013-08-16
It looks like you need to remove that 386 package as well.

libsasl2-modules:i386

---

### Post by candra2 on 2013-08-16
```
~$ libsasl2-modules:i386 
libsasl2-modules:i386: command not found
```

---

### Post by bapoumba on 2013-08-16
Well, libssl1.0.0:i386 is not in the precise repos, so you need to remove it. Please try with the same command you used previously : **sudo dpkg --purge --force-depends libssl1.0.0:i386**. Let's hope there are not too many of these libs in the same situation ..

---

### Post by bapoumba on 2013-08-16
> **bapoumba said:**
> Well, libssl1.0.0:i386 is not in the precise repos, so you need to remove it. Please try with the same command you used previously : **sudo dpkg --purge --force-depends libssl1.0.0:i386**. Let's hope there are not too many of these libs in the same situation ..

Sorry I miscopypasted
**sudo dpkg --purge --force-depends libsasl2-modules:i386**
Thanks philinux :)

---

### Post by candra2 on 2013-08-16
```
~$ sudo dpkg --purge --force-depends libssl1.0.0:i386
[sudo] password for d: 
dpkg: warning: there's no installed package matching libssl1.0.0:i386

```

---

### Post by bapoumba on 2013-08-16
Sorry, please see my previous post, just above yours ..

---

### Post by candra2 on 2013-08-16
here it is with the correct code:

```
sudo dpkg --purge --force-depends libsasl2-modules:i386
(Reading database ... 666801 files and directories currently installed.)
Removing libsasl2-modules:i386 ...
```

---

### Post by bapoumba on 2013-08-16
Is that the whole output ? I was kind of expecting something similar as you got in post #69.

If it did complete the same way, please run again ```
sudo apt-get dist-upgrade
``` to see if they are some more of these libs.

---

### Post by candra2 on 2013-08-16
I ran the above command and the output is going on - in the lower right it is showing a countdown that is hovering around 30min to 50min till completion...is that right??

---

### Post by philinux on 2013-08-16
If this goes on... it might be worth purging skype if that is the source of the problem.

What is the output of.

apt-cache policy skype

---

### Post by candra2 on 2013-08-16
As stated a few times earlier, I am completely ready to purge Skype - I do not need it...

The current output is still going on and it looks like ti will go on for some time - shall I run the above command simultaneously in a separate tab??

---

### Post by philinux on 2013-08-16
Yeah separate tab it only confirms if skype installed and the version. Handy command to remember.

---

### Post by candra2 on 2013-08-16
here it is...

> ~$ apt-cache policy skype 
skype:i386:
  Installed: 2.2.0.35-1
  Candidate: 2.2.0.35-1
  Version table:
 *** 2.2.0.35-1 0
        100 /var/lib/dpkg/status

---

### Post by candra2 on 2013-08-16
my connection got cut while doing that long download - here is the code - will restart it...

```
 sudo apt-get dist-upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-51 linux-headers-3.2.0-51-generic linux-image-3.2.0-51-generic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bind9-host dnsutils evince evince-common evolution-data-server evolution-data-server-common firefox firefox-globalmenu firefox-locale-en firefox-locale-zh-hans flashplugin-installer gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gudev-1.0 gnupg gpgv grub-common grub-pc grub-pc-bin grub2-common gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter jockey-common jockey-gtk libapt-inst1.4 libapt-pkg4.12 libbind9-80 libcamel-1.2-29
  libcroco3 libcroco3:i386 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdns81 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libevince3-3 libgcrypt11 libgcrypt11:i386 libgudev-1.0-0 libgwibber-gtk2 libgwibber2 libisc83 libisccc80 libisccfg82 liblcms2-2 liblightdm-gobject-1-0 liblwres80 libmysqlclient18
  libmysqlclient18:i386 libraptor2-0 libruby1.8 libudev0 libunity-core-5.0-5 libxml2 libxml2:i386 libxml2-utils lightdm linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev lsb-base lsb-release mysql-client-core-5.5 mysql-common
  mysql-server-core-5.5 openssl python-apport python-libxml2 python-problem-report remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc ruby1.8 thunderbird thunderbird-globalmenu thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us
  thunderbird-locale-zh-cn thunderbird-locale-zh-hans udev unity unity-common unity-lens-files unity-services whoopsie xul-ext-ubufox
112 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 157 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-pkg4.12 amd64 0.8.16~exp12ubuntu10.12 [936 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gpgv amd64 1.4.11-3ubuntu2.3 [185 kB]                                                                                                                                                                                     
Get:3 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gnupg amd64 1.4.11-3ubuntu2.3 [807 kB]                                                                                                                                                                                    
Get:4 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt amd64 0.8.16~exp12ubuntu10.12 [1,105 kB]                                                                                                                                                                              
Get:5 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libapt-inst1.4 amd64 0.8.16~exp12ubuntu10.12 [102 kB]                                                                                                                                                                     
Get:6 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm2 amd64 2.4.43-0ubuntu0.0.2 [26.2 kB]                                                                                                                                                                               
Get:7 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm2 i386 2.4.43-0ubuntu0.0.2 [27.6 kB]                                                                                                                                                                                
Get:8 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-intel1 i386 2.4.43-0ubuntu0.0.2 [64.9 kB]                                                                                                                                                                          
Get:9 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-intel1 amd64 2.4.43-0ubuntu0.0.2 [64.4 kB]                                                                                                                                                                         
Get:10 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau1a i386 2.4.43-0ubuntu0.0.2 [14.2 kB]                                                                                                                                                                      
Get:11 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-nouveau1a amd64 2.4.43-0ubuntu0.0.2 [14.0 kB]                                                                                                                                                                     
Get:12 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-radeon1 i386 2.4.43-0ubuntu0.0.2 [24.7 kB]                                                                                                                                                                        
Get:13 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdrm-radeon1 amd64 2.4.43-0ubuntu0.0.2 [24.1 kB]                                                                                                                                                                       
Get:14 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libudev0 amd64 175-0ubuntu9.4 [28.6 kB]                                                                                                                                                                                  
Get:15 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11 i386 1.5.0-3ubuntu0.2 [281 kB]                                                                                                                                                                               
Get:16 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgcrypt11 amd64 1.5.0-3ubuntu0.2 [280 kB]                                                                                                                                                                              
Get:17 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxml2 i386 2.7.8.dfsg-5.1ubuntu4.6 [662 kB]                                                                                                                                                                            
Get:18 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.6 [673 kB]                                                                                                                                                                           
Get:19 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcroco3 i386 0.6.5-1ubuntu0.1 [100 kB]                                                                                                                                                                                 
Get:20 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcroco3 amd64 0.6.5-1ubuntu0.1 [99.8 kB]                                                                                                                                                                               
Get:21 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-dbusmenu-gtk-0.4 amd64 0.6.2-0ubuntu0.2 [3,290 B]                                                                                                                                                                 
Get:22 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdbusmenu-gtk4 amd64 0.6.2-0ubuntu0.2 [31.2 kB]                                                                                                                                                                        
Get:23 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-dbusmenu-glib-0.4 amd64 0.6.2-0ubuntu0.2 [7,140 B]                                                                                                                                                                
Get:24 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdbusmenu-glib4 amd64 0.6.2-0ubuntu0.2 [47.9 kB]                                                                                                                                                                       
Get:25 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdbusmenu-gtk3-4 amd64 0.6.2-0ubuntu0.2 [31.3 kB]                                                                                                                                                                      
Get:26 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgudev-1.0-0 amd64 1:175-0ubuntu9.4 [14.5 kB]                                                                                                                                                                          
Get:27 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main liblcms2-2 amd64 2.2+git20110628-2ubuntu3.1 [143 kB]                                                                                                                                                                     
Get:28 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-common all 5.5.32-0ubuntu0.12.04.1 [13.3 kB]                                                                                                                                                                       
Get:29 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmysqlclient18 i386 5.5.32-0ubuntu0.12.04.1 [924 kB]                                                                                                                                                                   
Get:30 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libmysqlclient18 amd64 5.5.32-0ubuntu0.12.04.1 [944 kB]                                                                                                                                                                  
Get:31 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main lightdm amd64 1.2.3-0ubuntu2.3 [100 kB]                                                                                                                                                                                  
Get:32 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-3.2.0-51-generic amd64 3.2.0-51.77 [38.5 MB]                                                                                                                                                                 
Get:33 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main whoopsie amd64 0.1.33 [24.6 kB]                                                                                                                                                                                          
Get:34 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-base all 4.0-0ubuntu20.3 [10.5 kB]                                                                                                                                                                                   
Get:35 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-utils amd64 0.8.16~exp12ubuntu10.12 [192 kB]                                                                                                                                                                         
Get:36 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main lsb-release all 4.0-0ubuntu20.3 [11.0 kB]                                                                                                                                                                                
Get:37 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main udev amd64 175-0ubuntu9.4 [314 kB]                                                                                                                                                                                       
Get:38 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apt-transport-https amd64 0.8.16~exp12ubuntu10.12 [16.3 kB]                                                                                                                                                              
Get:39 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main bind9-host amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [55.3 kB]                                                                                                                                                                    
Get:40 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main dnsutils amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [148 kB]                                                                                                                                                                       
Get:41 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libisc83 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [161 kB]                                                                                                                                                                       
Get:42 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libdns81 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [704 kB]                                                                                                                                                                       
Get:43 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libisccc80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [17.6 kB]                                                                                                                                                                    
Get:44 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libisccfg82 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [43.4 kB]                                                                                                                                                                   
Get:45 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main liblwres80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [37.9 kB]                                                                                                                                                                    
Get:46 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libbind9-80 amd64 1:9.8.1.dfsg.P1-4ubuntu0.7 [24.3 kB]                                                                                                                                                                   
Get:47 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main openssl amd64 1.0.1-4ubuntu5.10 [524 kB]                                                                                                                                                                                 
Get:48 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-problem-report all 2.0.1-0ubuntu17.4 [9,342 B]                                                                                                                                                                    
Get:49 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu17.4 [81.1 kB]                                                                                                                                                                            
Get:50 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apport all 2.0.1-0ubuntu17.4 [147 kB]                                                                                                                                                                                    
Get:51 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu17.4 [9,200 B]                                                                                                                                                                               
Get:52 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main evince amd64 3.4.0-0ubuntu1.7 [206 kB]                                                                                                                                                                                   
Get:53 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libevince3-3 amd64 3.4.0-0ubuntu1.7 [357 kB]                                                                                                                                                                             
Get:54 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main evince-common all 3.4.0-0ubuntu1.7 [476 kB]                                                                                                                                                                              
Get:55 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libedataserver-1.2-15 amd64 3.2.3-0ubuntu7.1 [189 kB]                                                                                                                                                                    
Get:56 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main evolution-data-server amd64 3.2.3-0ubuntu7.1 [529 kB]                                                                                                                                                                    
Get:57 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libcamel-1.2-29 amd64 3.2.3-0ubuntu7.1 [449 kB]                                                                                                                                                                          
Get:58 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libebackend-1.2-1 amd64 3.2.3-0ubuntu7.1 [17.5 kB]                                                                                                                                                                       
Get:59 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libebook-1.2-12 amd64 3.2.3-0ubuntu7.1 [110 kB]                                                                                                                                                                          
Get:60 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libebook-1.2-12 amd64 3.2.3-0ubuntu7.1 [110 kB]                                                                                                                                                                          
Get:61 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libecal-1.2-10 amd64 3.2.3-0ubuntu7.1 [149 kB]                                                                                                                                                                           
Get:62 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libedata-book-1.2-11 amd64 3.2.3-0ubuntu7.1 [75.0 kB]                                                                                                                                                                    
Get:63 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libedata-cal-1.2-13 amd64 3.2.3-0ubuntu7.1 [94.3 kB]                                                                                                                                                                     
Get:64 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main evolution-data-server-common all 3.2.3-0ubuntu7.1 [89.5 kB]                                                                                                                                                              
Get:65 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox amd64 23.0+build2-0ubuntu0.12.04.1 [27.7 MB]                                                                                                                                                                     
Get:66 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-globalmenu amd64 23.0+build2-0ubuntu0.12.04.1 [18.3 kB]                                                                                                                                                          
Get:67 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-en amd64 23.0+build2-0ubuntu0.12.04.1 [572 kB]                                                                                                                                                            
Get:68 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main firefox-locale-zh-hans amd64 23.0+build2-0ubuntu0.12.04.1 [341 kB]                                                                                                                                                       
Get:69 http://us.archive.ubuntu.com/ubuntu/ precise-updates/multiverse flashplugin-installer amd64 11.2.202.297ubuntu0.12.04.1 [6,944 B]                                                                                                                                                  
Get:70 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gir1.2-gudev-1.0 amd64 175-0ubuntu9.4 [3,982 B]                                                                                                                                                                          
Get:71 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc amd64 1.99-21ubuntu3.10 [140 kB]                                                                                                                                                                                 
Get:72 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-pc-bin amd64 1.99-21ubuntu3.10 [868 kB]                                                                                                                                                                             
Get:73 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub2-common amd64 1.99-21ubuntu3.10 [94.2 kB]                                                                                                                                                                           
Get:74 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main grub-common amd64 1.99-21ubuntu3.10 [2,067 kB]                                                                                                                                                                           
Get:75 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gwibber amd64 3.4.2-0ubuntu2.3 [159 kB]                                                                                                                                                                                  
Get:76 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gwibber-service all 3.4.2-0ubuntu2.3 [39.3 kB]                                                                                                                                                                           
Get:77 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgwibber2 amd64 3.4.2-0ubuntu2.3 [71.1 kB]                                                                                                                                                                             
Get:78 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libgwibber-gtk2 amd64 3.4.2-0ubuntu2.3 [64.0 kB]                                                                                                                                                                         
Get:79 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gwibber-service-facebook all 3.4.2-0ubuntu2.3 [7,754 B]                                                                                                                                                                  
Get:80 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gwibber-service-identica all 3.4.2-0ubuntu2.3 [7,752 B]                                                                                                                                                                  
Get:81 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main gwibber-service-twitter all 3.4.2-0ubuntu2.3 [8,962 B]                                                                                                                                                                   
Get:82 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-gtk all 0.9.7-0ubuntu7.9 [9,116 B]                                                                                                                                                                                
Get:83 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main jockey-common all 0.9.7-0ubuntu7.9 [129 kB]                                                                                                                                                                              
Get:84 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libedataserverui-3.0-1 amd64 3.2.3-0ubuntu7.1 [109 kB]                                                                                                                                                                   
Get:85 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main liblightdm-gobject-1-0 amd64 1.2.3-0ubuntu2.3 [31.2 kB]                                                                                                                                                                  
Get:86 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libraptor2-0 amd64 2.0.6-1ubuntu0.1 [177 kB]                                                                                                                                                                             
Get:87 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main ruby1.8 amd64 1.8.7.352-2ubuntu1.3 [33.9 kB]                                                                                                                                                                             
Get:88 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libruby1.8 amd64 1.8.7.352-2ubuntu1.3 [1,797 kB]                                                                                                                                                                         
Get:89 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity amd64 5.20.0-0ubuntu2 [1,289 kB]                                                                                                                                                                                   
Get:90 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-common all 5.20.0-0ubuntu2 [150 kB]                                                                                                                                                                                
Get:91 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libunity-core-5.0-5 amd64 5.20.0-0ubuntu2 [235 kB]                                                                                                                                                                       
Get:92 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-services amd64 5.20.0-0ubuntu2 [35.2 kB]                                                                                                                                                                           
Get:93 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libxml2-utils amd64 2.7.8.dfsg-5.1ubuntu4.6 [39.8 kB]                                                                                                                                                                    
Get:94 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-firmware all 1.79.6 [23.2 MB]                                                                                                                                                                                      
61% [94 linux-firmware 8,643 kB/23.2 MB 37%]                                                                                                                                                                                                                           58.0 kB/s 17min 26s^Get:95 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-generic amd64 3.2.0.51.61 [1,720 B]                                                                                                                                                                                
Get:96 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-image-generic amd64 3.2.0.51.61 [2,340 B]                                                                                                                                                                          
Get:97 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-51 all 3.2.0-51.77 [11.7 MB]                                                                                                                                                                         
Get:98 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-3.2.0-51-generic amd64 3.2.0-51.77 [977 kB]                                                                                                                                                                
Get:99 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-headers-generic amd64 3.2.0.51.61 [2,338 B]                                                                                                                                                                        
Get:100 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main linux-libc-dev amd64 3.2.0-51.77 [859 kB]                                                                                                                                                                               
Get:101 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-client-core-5.5 amd64 5.5.32-0ubuntu0.12.04.1 [1,921 kB]                                                                                                                                                          
Get:102 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main mysql-server-core-5.5 amd64 5.5.32-0ubuntu0.12.04.1 [6,071 kB]                                                                                                                                                          
Get:103 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main python-libxml2 amd64 2.7.8.dfsg-5.1ubuntu4.6 [187 kB]                                                                                                                                                                   
Get:104 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main remmina-plugin-rdp amd64 1.0.0-1ubuntu6.3 [31.9 kB]                                                                                                                                                                     
Get:105 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main remmina-plugin-vnc amd64 1.0.0-1ubuntu6.3 [21.2 kB]                                                                                                                                                                     
Get:106 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main remmina amd64 1.0.0-1ubuntu6.3 [131 kB]                                                                                                                                                                                 
Get:107 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main remmina-common all 1.0.0-1ubuntu6.3 [47.7 kB]                                                                                                                                                                           
Get:108 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-locale-zh-hans amd64 1:17.0.8+build1-0ubuntu0.12.04.1 [385 kB]                                                                                                                                              
Get:109 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-globalmenu amd64 17.0.8+build1-0ubuntu0.12.04.1 [49.7 kB]                                                                                                                                                   
Get:110 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird-locale-en amd64 1:17.0.8+build1-0ubuntu0.12.04.1 [340 kB]                                                                                                                                                   
Get:111 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird amd64 17.0.8+build1-0ubuntu0.12.04.1 [23.3 MB]                                                                                                                                                              
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main thunderbird amd64 17.0.8+build1-0ubuntu0.12.04.1                                                                                                                                                                            
  Connection failed [IP: 91.189.91.13 80]
Err http://us.archive.ubuntu.com/ubuntu/ precise-updates/main unity-lens-files amd64 5.10.0-0ubuntu1.1
  Unable to connect to us.archive.ubuntu.com:http: [IP: 2001:67c:1562::14 80]
85% [Connecting to security.ubuntu.com]                                                                                                                                                                                                                                                   
85% [Connecting to security.ubuntu.com]
```

---

### Post by candra2 on 2013-08-16
here is the rest of that code

> sudo apt-get dist-upgrade
[sudo] password for d: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following NEW packages will be installed:
  linux-headers-3.2.0-51 linux-headers-3.2.0-51-generic linux-image-3.2.0-51-generic
The following packages will be upgraded:
  apport apport-gtk apt apt-transport-https apt-utils bind9-host dnsutils evince evince-common evolution-data-server evolution-data-server-common firefox firefox-globalmenu firefox-locale-en firefox-locale-zh-hans flashplugin-installer gir1.2-dbusmenu-glib-0.4
  gir1.2-dbusmenu-gtk-0.4 gir1.2-gudev-1.0 gnupg gpgv grub-common grub-pc grub-pc-bin grub2-common gwibber gwibber-service gwibber-service-facebook gwibber-service-identica gwibber-service-twitter jockey-common jockey-gtk libapt-inst1.4 libapt-pkg4.12 libbind9-80 libcamel-1.2-29
  libcroco3 libcroco3:i386 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdns81 libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau1a libdrm-nouveau1a:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386 libebackend-1.2-1 libebook-1.2-12 libecal-1.2-10
  libedata-book-1.2-11 libedata-cal-1.2-13 libedataserver-1.2-15 libedataserverui-3.0-1 libevince3-3 libgcrypt11 libgcrypt11:i386 libgudev-1.0-0 libgwibber-gtk2 libgwibber2 libisc83 libisccc80 libisccfg82 liblcms2-2 liblightdm-gobject-1-0 liblwres80 libmysqlclient18
  libmysqlclient18:i386 libraptor2-0 libruby1.8 libudev0 libunity-core-5.0-5 libxml2 libxml2:i386 libxml2-utils lightdm linux-firmware linux-generic linux-headers-generic linux-image-generic linux-libc-dev lsb-base lsb-release mysql-client-core-5.5 mysql-common
  mysql-server-core-5.5 openssl python-apport python-libxml2 python-problem-report remmina remmina-common remmina-plugin-rdp remmina-plugin-vnc ruby1.8 thunderbird thunderbird-globalmenu thunderbird-locale-en thunderbird-locale-en-gb thunderbird-locale-en-us
  thunderbird-locale-zh-cn thunderbird-locale-zh-hans udev unity unity-common unity-lens-files unity-services whoopsie xul-ext-ubufox
112 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 23.4 MB/157 MB of archives.
After this operation, 220 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird amd64 17.0.8+build1-0ubuntu0.12.04.1 [23.3 MB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-locale-en-gb all 1:17.0.8+build1-0ubuntu0.12.04.1 [11.6 kB]                                                                                                                                                   
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-locale-en-us all 1:17.0.8+build1-0ubuntu0.12.04.1 [11.6 kB]                                                                                                                                                   
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main thunderbird-locale-zh-cn all 1:17.0.8+build1-0ubuntu0.12.04.1 [11.6 kB]                                                                                                                                                   
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main unity-lens-files amd64 5.10.0-0ubuntu1.1 [51.4 kB]                                                                                                                                                                        
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates/main xul-ext-ubufox all 2.7-0ubuntu0.12.04.1 [56.8 kB]                                                                                                                                                                         
Fetched 9,887 kB in 3min 37s (45.5 kB/s)                                                                                                                                                                                                                                                  
E: Internal Error, No file name for libssl1.0.0


---

### Post by philinux on 2013-08-17
If it got interrupted then use.

```
sudo dpkg --configure -a
```

---

### Post by candra2 on 2013-08-17
here is what I got

```
~$ sudo dpkg --configure -a
[sudo] password for d: 
Setting up libssl1.0.0 (1.0.1-4ubuntu5.10) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
```

---

### Post by bapoumba on 2013-08-19
Hello,
I was away for the WE. Looks that last dpkg command ran fine. Please try, again, **sudo apt-get update** and **sudo apt-get dist-upgrade ** to see how your dependency tree is doing. did you finally remove skype ?

---

### Post by candra2 on 2013-08-19
here is the first one:

```
:~$ sudo apt-get update
[sudo] password for d: 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg                       
Hit http://us.archive.ubuntu.com precise-updates Release.gpg               
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://security.ubuntu.com precise-security Release
Hit http://us.archive.ubuntu.com precise Release                      
Hit http://us.archive.ubuntu.com precise-updates Release              
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]             
Hit http://us.archive.ubuntu.com precise-backports Release
Hit http://security.ubuntu.com precise-security/main Sources                                
Hit http://extras.ubuntu.com precise Release                         
Hit http://us.archive.ubuntu.com precise/main Sources                 
Hit http://security.ubuntu.com precise-security/restricted Sources
Hit http://security.ubuntu.com precise-security/universe Sources     
Hit http://security.ubuntu.com precise-security/multiverse Sources   
Hit http://security.ubuntu.com precise-security/main amd64 Packages  
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages   
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/restricted Sources          
Hit http://us.archive.ubuntu.com precise/universe Sources            
Hit http://us.archive.ubuntu.com precise/multiverse Sources          
Hit http://us.archive.ubuntu.com precise/main amd64 Packages         
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages   
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages     
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages   
Hit http://us.archive.ubuntu.com precise/main i386 Packages          
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages    
Hit http://us.archive.ubuntu.com precise/universe i386 Packages      
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages    
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex 
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex 
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex   
Hit http://us.archive.ubuntu.com precise-updates/main Sources        
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources  
Hit http://us.archive.ubuntu.com precise-updates/universe Sources    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://extras.ubuntu.com precise/main amd64 Packages             
Hit http://extras.ubuntu.com precise/main i386 Packages              
Ign http://extras.ubuntu.com precise/main TranslationIndex           
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources
Hit http://us.archive.ubuntu.com precise-backports/restricted Sources
Hit http://us.archive.ubuntu.com precise-backports/universe Sources
Hit http://us.archive.ubuntu.com precise-backports/multiverse Sources
Hit http://us.archive.ubuntu.com precise-backports/main amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-backports/main i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-backports/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main Translation-en
Hit http://us.archive.ubuntu.com precise/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise/restricted Translation-en
Hit http://us.archive.ubuntu.com precise/universe Translation-en
Hit http://us.archive.ubuntu.com precise-updates/main Translation-en
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Fetched 72 B in 3s (23 B/s)
Reading package lists... Done
```

the second one is in process, but taking a while - will post it when done. 

As for removing skype, I do not know whethter it is fully removed or not...

---

### Post by candra2 on 2013-08-19
here is the second one - it was a long process and it does not seem to show the beginning portion and initial command line anymore...is there are limit how much it can store in one tab????

if you need me to run it again let me know...

```
Preparing to replace libdrm2 2.4.43-0ubuntu0.0.1 (using .../libdrm2_2.4.43-0ubuntu0.0.2_amd64.deb) ...
De-configuring libdrm2:i386 ...
Unpacking replacement libdrm2 ...
Preparing to replace libdrm2:i386 2.4.43-0ubuntu0.0.1 (using .../libdrm2_2.4.43-0ubuntu0.0.2_i386.deb) ...
Unpacking replacement libdrm2:i386 ...
Setting up libdrm2 (2.4.43-0ubuntu0.0.2) ...
Setting up libdrm2:i386 (2.4.43-0ubuntu0.0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libdrm-intel1:i386 2.4.43-0ubuntu0.0.1 (using .../libdrm-intel1_2.4.43-0ubuntu0.0.2_i386.deb) ...
De-configuring libdrm-intel1 ...
Unpacking replacement libdrm-intel1:i386 ...
Preparing to replace libdrm-intel1 2.4.43-0ubuntu0.0.1 (using .../libdrm-intel1_2.4.43-0ubuntu0.0.2_amd64.deb) ...
Unpacking replacement libdrm-intel1 ...
Setting up libdrm-intel1:i386 (2.4.43-0ubuntu0.0.2) ...
Setting up libdrm-intel1 (2.4.43-0ubuntu0.0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libdrm-nouveau1a:i386 2.4.43-0ubuntu0.0.1 (using .../libdrm-nouveau1a_2.4.43-0ubuntu0.0.2_i386.deb) ...
De-configuring libdrm-nouveau1a ...
Unpacking replacement libdrm-nouveau1a:i386 ...
Preparing to replace libdrm-nouveau1a 2.4.43-0ubuntu0.0.1 (using .../libdrm-nouveau1a_2.4.43-0ubuntu0.0.2_amd64.deb) ...
Unpacking replacement libdrm-nouveau1a ...
Setting up libdrm-nouveau1a:i386 (2.4.43-0ubuntu0.0.2) ...
Setting up libdrm-nouveau1a (2.4.43-0ubuntu0.0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libdrm-radeon1:i386 2.4.43-0ubuntu0.0.1 (using .../libdrm-radeon1_2.4.43-0ubuntu0.0.2_i386.deb) ...
De-configuring libdrm-radeon1 ...
Unpacking replacement libdrm-radeon1:i386 ...
Preparing to replace libdrm-radeon1 2.4.43-0ubuntu0.0.1 (using .../libdrm-radeon1_2.4.43-0ubuntu0.0.2_amd64.deb) ...
Unpacking replacement libdrm-radeon1 ...
Setting up libdrm-radeon1:i386 (2.4.43-0ubuntu0.0.2) ...
Setting up libdrm-radeon1 (2.4.43-0ubuntu0.0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libudev0 175-0ubuntu9.3 (using .../libudev0_175-0ubuntu9.4_amd64.deb) ...
Unpacking replacement libudev0 ...
Preparing to replace libgcrypt11:i386 1.5.0-3ubuntu0.1 (using .../libgcrypt11_1.5.0-3ubuntu0.2_i386.deb) ...
De-configuring libgcrypt11 ...
Unpacking replacement libgcrypt11:i386 ...
Preparing to replace libgcrypt11 1.5.0-3ubuntu0.1 (using .../libgcrypt11_1.5.0-3ubuntu0.2_amd64.deb) ...
Unpacking replacement libgcrypt11 ...
Setting up libgcrypt11:i386 (1.5.0-3ubuntu0.2) ...
Setting up libgcrypt11 (1.5.0-3ubuntu0.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libxml2:i386 2.7.8.dfsg-5.1ubuntu4.4 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.6_i386.deb) ...
De-configuring libxml2 ...
Unpacking replacement libxml2:i386 ...
Preparing to replace libxml2 2.7.8.dfsg-5.1ubuntu4.4 (using .../libxml2_2.7.8.dfsg-5.1ubuntu4.6_amd64.deb) ...
Unpacking replacement libxml2 ...
Setting up libxml2:i386 (2.7.8.dfsg-5.1ubuntu4.6) ...
Setting up libxml2 (2.7.8.dfsg-5.1ubuntu4.6) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace libcroco3:i386 0.6.5-1 (using .../libcroco3_0.6.5-1ubuntu0.1_i386.deb) ...
De-configuring libcroco3 ...
Unpacking replacement libcroco3:i386 ...
Preparing to replace libcroco3 0.6.5-1 (using .../libcroco3_0.6.5-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libcroco3 ...
Setting up libcroco3:i386 (0.6.5-1ubuntu0.1) ...
Setting up libcroco3 (0.6.5-1ubuntu0.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace gir1.2-dbusmenu-gtk-0.4 0.6.2-0ubuntu0.1 (using .../gir1.2-dbusmenu-gtk-0.4_0.6.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement gir1.2-dbusmenu-gtk-0.4 ...
Preparing to replace libdbusmenu-gtk4 0.6.2-0ubuntu0.1 (using .../libdbusmenu-gtk4_0.6.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libdbusmenu-gtk4 ...
Preparing to replace gir1.2-dbusmenu-glib-0.4 0.6.2-0ubuntu0.1 (using .../gir1.2-dbusmenu-glib-0.4_0.6.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement gir1.2-dbusmenu-glib-0.4 ...
Preparing to replace libdbusmenu-glib4 0.6.2-0ubuntu0.1 (using .../libdbusmenu-glib4_0.6.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libdbusmenu-glib4 ...
Preparing to replace libdbusmenu-gtk3-4 0.6.2-0ubuntu0.1 (using .../libdbusmenu-gtk3-4_0.6.2-0ubuntu0.2_amd64.deb) ...
Unpacking replacement libdbusmenu-gtk3-4 ...
Preparing to replace libgudev-1.0-0 1:175-0ubuntu9.3 (using .../libgudev-1.0-0_1%3a175-0ubuntu9.4_amd64.deb) ...
Unpacking replacement libgudev-1.0-0 ...
Preparing to replace liblcms2-2 2.2+git20110628-2ubuntu3 (using .../liblcms2-2_2.2+git20110628-2ubuntu3.1_amd64.deb) ...
Unpacking replacement liblcms2-2 ...
Preparing to replace mysql-common 5.5.31-0ubuntu0.12.04.2 (using .../mysql-common_5.5.32-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement mysql-common ...
Preparing to replace libmysqlclient18:i386 5.5.31-0ubuntu0.12.04.2 (using .../libmysqlclient18_5.5.32-0ubuntu0.12.04.1_i386.deb) ...
De-configuring libmysqlclient18 ...
Unpacking replacement libmysqlclient18:i386 ...
Preparing to replace libmysqlclient18 5.5.31-0ubuntu0.12.04.2 (using .../libmysqlclient18_5.5.32-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement libmysqlclient18 ...
Setting up mysql-common (5.5.32-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18:i386 (5.5.32-0ubuntu0.12.04.1) ...
Setting up libmysqlclient18 (5.5.32-0ubuntu0.12.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
(Reading database ... 666784 files and directories currently installed.)
Preparing to replace lightdm 1.2.3-0ubuntu2.2 (using .../lightdm_1.2.3-0ubuntu2.3_amd64.deb) ...
Unpacking replacement lightdm ...
Selecting previously unselected package linux-image-3.2.0-51-generic.
Unpacking linux-image-3.2.0-51-generic (from .../linux-image-3.2.0-51-generic_3.2.0-51.77_amd64.deb) ...
Done.
Preparing to replace whoopsie 0.1.32 (using .../whoopsie_0.1.33_amd64.deb) ...
whoopsie stop/waiting
Unpacking replacement whoopsie ...
Preparing to replace lsb-base 4.0-0ubuntu20.2 (using .../lsb-base_4.0-0ubuntu20.3_all.deb) ...
Unpacking replacement lsb-base ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up lsb-base (4.0-0ubuntu20.3) ...
(Reading database ... 670922 files and directories currently installed.)
Preparing to replace apt-utils 0.8.16~exp12ubuntu10.10 (using .../apt-utils_0.8.16~exp12ubuntu10.12_amd64.deb) ...
Unpacking replacement apt-utils ...
Preparing to replace lsb-release 4.0-0ubuntu20.2 (using .../lsb-release_4.0-0ubuntu20.3_all.deb) ...
Unpacking replacement lsb-release ...
Preparing to replace udev 175-0ubuntu9.3 (using .../udev_175-0ubuntu9.4_amd64.deb) ...
Adding 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace apt-transport-https 0.8.16~exp12ubuntu10.10 (using .../apt-transport-https_0.8.16~exp12ubuntu10.12_amd64.deb) ...
Unpacking replacement apt-transport-https ...
Preparing to replace bind9-host 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../bind9-host_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement bind9-host ...
Preparing to replace dnsutils 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../dnsutils_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement dnsutils ...
Preparing to replace libisc83 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../libisc83_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement libisc83 ...
Preparing to replace libdns81 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../libdns81_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement libdns81 ...
Preparing to replace libisccc80 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../libisccc80_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement libisccc80 ...
Preparing to replace libisccfg82 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../libisccfg82_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement libisccfg82 ...
Preparing to replace liblwres80 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../liblwres80_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement liblwres80 ...
Preparing to replace libbind9-80 1:9.8.1.dfsg.P1-4ubuntu0.6 (using .../libbind9-80_1%3a9.8.1.dfsg.P1-4ubuntu0.7_amd64.deb) ...
Unpacking replacement libbind9-80 ...
Preparing to replace openssl 1.0.1-4ubuntu5.9 (using .../openssl_1.0.1-4ubuntu5.10_amd64.deb) ...
Unpacking replacement openssl ...
Preparing to replace python-problem-report 2.0.1-0ubuntu17.3 (using .../python-problem-report_2.0.1-0ubuntu17.4_all.deb) ...
Unpacking replacement python-problem-report ...
Preparing to replace python-apport 2.0.1-0ubuntu17.3 (using .../python-apport_2.0.1-0ubuntu17.4_all.deb) ...
Unpacking replacement python-apport ...
Preparing to replace apport 2.0.1-0ubuntu17.3 (using .../apport_2.0.1-0ubuntu17.4_all.deb) ...
apport stop/waiting
Unpacking replacement apport ...
Preparing to replace apport-gtk 2.0.1-0ubuntu17.3 (using .../apport-gtk_2.0.1-0ubuntu17.4_all.deb) ...
Unpacking replacement apport-gtk ...
Preparing to replace evince 3.4.0-0ubuntu1.6 (using .../evince_3.4.0-0ubuntu1.7_amd64.deb) ...
Unpacking replacement evince ...
Preparing to replace libevince3-3 3.4.0-0ubuntu1.6 (using .../libevince3-3_3.4.0-0ubuntu1.7_amd64.deb) ...
Unpacking replacement libevince3-3 ...
Preparing to replace evince-common 3.4.0-0ubuntu1.6 (using .../evince-common_3.4.0-0ubuntu1.7_all.deb) ...
Unpacking replacement evince-common ...
Preparing to replace libedataserver-1.2-15 3.2.3-0ubuntu7 (using .../libedataserver-1.2-15_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libedataserver-1.2-15 ...
Preparing to replace evolution-data-server 3.2.3-0ubuntu7 (using .../evolution-data-server_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement evolution-data-server ...
Preparing to replace libcamel-1.2-29 3.2.3-0ubuntu7 (using .../libcamel-1.2-29_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libcamel-1.2-29 ...
Preparing to replace libebackend-1.2-1 3.2.3-0ubuntu7 (using .../libebackend-1.2-1_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libebackend-1.2-1 ...
Preparing to replace libebook-1.2-12 3.2.3-0ubuntu7 (using .../libebook-1.2-12_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libebook-1.2-12 ...
Preparing to replace libecal-1.2-10 3.2.3-0ubuntu7 (using .../libecal-1.2-10_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libecal-1.2-10 ...
Preparing to replace libedata-book-1.2-11 3.2.3-0ubuntu7 (using .../libedata-book-1.2-11_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libedata-book-1.2-11 ...
Preparing to replace libedata-cal-1.2-13 3.2.3-0ubuntu7 (using .../libedata-cal-1.2-13_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libedata-cal-1.2-13 ...
Preparing to replace evolution-data-server-common 3.2.3-0ubuntu7 (using .../evolution-data-server-common_3.2.3-0ubuntu7.1_all.deb) ...
Unpacking replacement evolution-data-server-common ...
Preparing to replace firefox 22.0+build2-0ubuntu0.12.04.2 (using .../firefox_23.0+build2-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox ...
Preparing to replace firefox-globalmenu 22.0+build2-0ubuntu0.12.04.2 (using .../firefox-globalmenu_23.0+build2-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-globalmenu ...
Preparing to replace firefox-locale-en 22.0+build2-0ubuntu0.12.04.2 (using .../firefox-locale-en_23.0+build2-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-en ...
Preparing to replace firefox-locale-zh-hans 22.0+build2-0ubuntu0.12.04.2 (using .../firefox-locale-zh-hans_23.0+build2-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement firefox-locale-zh-hans ...
Preparing to replace flashplugin-installer 11.2.202.291ubuntu0.12.04.1 (using .../flashplugin-installer_11.2.202.297ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement flashplugin-installer ...
Preparing to replace gir1.2-gudev-1.0 175-0ubuntu9.3 (using .../gir1.2-gudev-1.0_175-0ubuntu9.4_amd64.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Preparing to replace grub-pc 1.99-21ubuntu3.9 (using .../grub-pc_1.99-21ubuntu3.10_amd64.deb) ...
Unpacking replacement grub-pc ...
Preparing to replace grub-pc-bin 1.99-21ubuntu3.9 (using .../grub-pc-bin_1.99-21ubuntu3.10_amd64.deb) ...
Unpacking replacement grub-pc-bin ...
Preparing to replace grub2-common 1.99-21ubuntu3.9 (using .../grub2-common_1.99-21ubuntu3.10_amd64.deb) ...
Unpacking replacement grub2-common ...
Preparing to replace grub-common 1.99-21ubuntu3.9 (using .../grub-common_1.99-21ubuntu3.10_amd64.deb) ...
Unpacking replacement grub-common ...
Preparing to replace gwibber 3.4.2-0ubuntu2.2 (using .../gwibber_3.4.2-0ubuntu2.3_amd64.deb) ...
Unpacking replacement gwibber ...
Preparing to replace gwibber-service 3.4.2-0ubuntu2.2 (using .../gwibber-service_3.4.2-0ubuntu2.3_all.deb) ...
Unpacking replacement gwibber-service ...
Preparing to replace libgwibber2 3.4.2-0ubuntu2.2 (using .../libgwibber2_3.4.2-0ubuntu2.3_amd64.deb) ...
Unpacking replacement libgwibber2 ...
Preparing to replace libgwibber-gtk2 3.4.2-0ubuntu2.2 (using .../libgwibber-gtk2_3.4.2-0ubuntu2.3_amd64.deb) ...
Unpacking replacement libgwibber-gtk2 ...
Preparing to replace gwibber-service-facebook 3.4.2-0ubuntu2.2 (using .../gwibber-service-facebook_3.4.2-0ubuntu2.3_all.deb) ...
Unpacking replacement gwibber-service-facebook ...
Preparing to replace gwibber-service-identica 3.4.2-0ubuntu2.2 (using .../gwibber-service-identica_3.4.2-0ubuntu2.3_all.deb) ...
Unpacking replacement gwibber-service-identica ...
Preparing to replace gwibber-service-twitter 3.4.2-0ubuntu2.2 (using .../gwibber-service-twitter_3.4.2-0ubuntu2.3_all.deb) ...
Unpacking replacement gwibber-service-twitter ...
Preparing to replace jockey-gtk 0.9.7-0ubuntu7.7 (using .../jockey-gtk_0.9.7-0ubuntu7.9_all.deb) ...
Unpacking replacement jockey-gtk ...
Preparing to replace jockey-common 0.9.7-0ubuntu7.7 (using .../jockey-common_0.9.7-0ubuntu7.9_all.deb) ...
Unpacking replacement jockey-common ...
Preparing to replace libedataserverui-3.0-1 3.2.3-0ubuntu7 (using .../libedataserverui-3.0-1_3.2.3-0ubuntu7.1_amd64.deb) ...
Unpacking replacement libedataserverui-3.0-1 ...
Preparing to replace liblightdm-gobject-1-0 1.2.3-0ubuntu2.2 (using .../liblightdm-gobject-1-0_1.2.3-0ubuntu2.3_amd64.deb) ...
Unpacking replacement liblightdm-gobject-1-0 ...
Preparing to replace libraptor2-0 2.0.6-1 (using .../libraptor2-0_2.0.6-1ubuntu0.1_amd64.deb) ...
Unpacking replacement libraptor2-0 ...
Preparing to replace ruby1.8 1.8.7.352-2ubuntu1.2 (using .../ruby1.8_1.8.7.352-2ubuntu1.3_amd64.deb) ...
Unpacking replacement ruby1.8 ...
Preparing to replace libruby1.8 1.8.7.352-2ubuntu1.2 (using .../libruby1.8_1.8.7.352-2ubuntu1.3_amd64.deb) ...
Unpacking replacement libruby1.8 ...
Preparing to replace unity 5.18.0-0ubuntu2 (using .../unity_5.20.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity ...
Preparing to replace unity-common 5.18.0-0ubuntu2 (using .../unity-common_5.20.0-0ubuntu2_all.deb) ...
Unpacking replacement unity-common ...
Preparing to replace libunity-core-5.0-5 5.18.0-0ubuntu2 (using .../libunity-core-5.0-5_5.20.0-0ubuntu2_amd64.deb) ...
Unpacking replacement libunity-core-5.0-5 ...
Preparing to replace unity-services 5.18.0-0ubuntu2 (using .../unity-services_5.20.0-0ubuntu2_amd64.deb) ...
Unpacking replacement unity-services ...
Preparing to replace libxml2-utils 2.7.8.dfsg-5.1ubuntu4.4 (using .../libxml2-utils_2.7.8.dfsg-5.1ubuntu4.6_amd64.deb) ...
Unpacking replacement libxml2-utils ...
Preparing to replace linux-firmware 1.79.4 (using .../linux-firmware_1.79.6_all.deb) ...
Unpacking replacement linux-firmware ...
Preparing to replace linux-generic 3.2.0.48.58 (using .../linux-generic_3.2.0.51.61_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 3.2.0.48.58 (using .../linux-image-generic_3.2.0.51.61_amd64.deb) ...
Unpacking replacement linux-image-generic ...
Selecting previously unselected package linux-headers-3.2.0-51.
Unpacking linux-headers-3.2.0-51 (from .../linux-headers-3.2.0-51_3.2.0-51.77_all.deb) ...
Selecting previously unselected package linux-headers-3.2.0-51-generic.
Unpacking linux-headers-3.2.0-51-generic (from .../linux-headers-3.2.0-51-generic_3.2.0-51.77_amd64.deb) ...
Preparing to replace linux-headers-generic 3.2.0.48.58 (using .../linux-headers-generic_3.2.0.51.61_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
Preparing to replace linux-libc-dev 3.2.0-48.74 (using .../linux-libc-dev_3.2.0-51.77_amd64.deb) ...
Unpacking replacement linux-libc-dev ...
Preparing to replace mysql-client-core-5.5 5.5.31-0ubuntu0.12.04.2 (using .../mysql-client-core-5.5_5.5.32-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement mysql-client-core-5.5 ...
Preparing to replace mysql-server-core-5.5 5.5.31-0ubuntu0.12.04.2 (using .../mysql-server-core-5.5_5.5.32-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement mysql-server-core-5.5 ...
Preparing to replace python-libxml2 2.7.8.dfsg-5.1ubuntu4.4 (using .../python-libxml2_2.7.8.dfsg-5.1ubuntu4.6_amd64.deb) ...
Unpacking replacement python-libxml2 ...
Preparing to replace remmina-plugin-rdp 1.0.0-1ubuntu6.1 (using .../remmina-plugin-rdp_1.0.0-1ubuntu6.3_amd64.deb) ...
Unpacking replacement remmina-plugin-rdp ...
Preparing to replace remmina-plugin-vnc 1.0.0-1ubuntu6.1 (using .../remmina-plugin-vnc_1.0.0-1ubuntu6.3_amd64.deb) ...
Unpacking replacement remmina-plugin-vnc ...
Preparing to replace remmina 1.0.0-1ubuntu6.1 (using .../remmina_1.0.0-1ubuntu6.3_amd64.deb) ...
Unpacking replacement remmina ...
Preparing to replace remmina-common 1.0.0-1ubuntu6.1 (using .../remmina-common_1.0.0-1ubuntu6.3_all.deb) ...
Unpacking replacement remmina-common ...
Preparing to replace thunderbird-locale-zh-hans 1:17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-zh-hans_1%3a17.0.8+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-zh-hans ...
Preparing to replace thunderbird-globalmenu 17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-globalmenu_17.0.8+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-globalmenu ...
Preparing to replace thunderbird-locale-en 1:17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en_1%3a17.0.8+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird-locale-en ...
Preparing to replace thunderbird 17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird_17.0.8+build1-0ubuntu0.12.04.1_amd64.deb) ...
Unpacking replacement thunderbird ...
Preparing to replace thunderbird-locale-en-gb 1:17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-gb_1%3a17.0.8+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-gb ...
Preparing to replace thunderbird-locale-en-us 1:17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-en-us_1%3a17.0.8+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-en-us ...
Preparing to replace thunderbird-locale-zh-cn 1:17.0.7+build1-0ubuntu0.12.04.1 (using .../thunderbird-locale-zh-cn_1%3a17.0.8+build1-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement thunderbird-locale-zh-cn ...
Preparing to replace unity-lens-files 5.10.0-0ubuntu1 (using .../unity-lens-files_5.10.0-0ubuntu1.1_amd64.deb) ...
Unpacking replacement unity-lens-files ...
Preparing to replace xul-ext-ubufox 2.6-0ubuntu0.12.04.1 (using .../xul-ext-ubufox_2.7-0ubuntu0.12.04.1_all.deb) ...
Unpacking replacement xul-ext-ubufox ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for shared-mime-info ...
Unknown media type in type 'all/all'
Unknown media type in type 'all/allfiles'
Unknown media type in type 'uri/mms'
Unknown media type in type 'uri/mmst'
Unknown media type in type 'uri/mmsu'
Unknown media type in type 'uri/pnm'
Unknown media type in type 'uri/rtspt'
Unknown media type in type 'uri/rtspu'
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for libglib2.0-0 ...
Processing triggers for libglib2.0-0:i386 ...
Processing triggers for gconf2 ...
Processing triggers for update-notifier-common ...
flashplugin-installer: downloading http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_11.2.202.297.orig.tar.gz
Installing from local file /tmp/tmpkBp8Cu.gz
Flash Plugin installed.
Processing triggers for install-info ...
Setting up libapt-inst1.4 (0.8.16~exp12ubuntu10.12) ...
Setting up libudev0 (175-0ubuntu9.4) ...
Setting up libdbusmenu-glib4 (0.6.2-0ubuntu0.2) ...
Setting up libdbusmenu-gtk4 (0.6.2-0ubuntu0.2) ...
Setting up gir1.2-dbusmenu-glib-0.4 (0.6.2-0ubuntu0.2) ...
Setting up gir1.2-dbusmenu-gtk-0.4 (0.6.2-0ubuntu0.2) ...
Setting up libdbusmenu-gtk3-4 (0.6.2-0ubuntu0.2) ...
Setting up libgudev-1.0-0 (1:175-0ubuntu9.4) ...
Setting up liblcms2-2 (2.2+git20110628-2ubuntu3.1) ...
Setting up lightdm (1.2.3-0ubuntu2.3) ...
Setting up linux-image-3.2.0-51-generic (3.2.0-51.77) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
update-initramfs: Generating /boot/initrd.img-3.2.0-51-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up whoopsie (0.1.33) ...
whoopsie start/running, process 7092
Setting up apt-utils (0.8.16~exp12ubuntu10.12) ...
Setting up lsb-release (4.0-0ubuntu20.3) ...
Setting up udev (175-0ubuntu9.4) ...
udev stop/waiting
udev start/running, process 7144
Removing 'diversion of /sbin/udevadm to /sbin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up apt-transport-https (0.8.16~exp12ubuntu10.12) ...
Setting up libisc83 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up libdns81 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up libisccc80 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up libisccfg82 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up libbind9-80 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up liblwres80 (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up bind9-host (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up dnsutils (1:9.8.1.dfsg.P1-4ubuntu0.7) ...
Setting up openssl (1.0.1-4ubuntu5.10) ...
Setting up python-problem-report (2.0.1-0ubuntu17.4) ...
Setting up python-apport (2.0.1-0ubuntu17.4) ...
Setting up apport (2.0.1-0ubuntu17.4) ...
Installing new version of config file /etc/init/apport.conf ...
apport start/running
Setting up apport-gtk (2.0.1-0ubuntu17.4) ...
Setting up libevince3-3 (3.4.0-0ubuntu1.7) ...
Setting up evince-common (3.4.0-0ubuntu1.7) ...
Setting up evince (3.4.0-0ubuntu1.7) ...
Setting up libedataserver-1.2-15 (3.2.3-0ubuntu7.1) ...
Setting up libcamel-1.2-29 (3.2.3-0ubuntu7.1) ...
Setting up libebackend-1.2-1 (3.2.3-0ubuntu7.1) ...
Setting up libebook-1.2-12 (3.2.3-0ubuntu7.1) ...
Setting up libecal-1.2-10 (3.2.3-0ubuntu7.1) ...
Setting up libedata-book-1.2-11 (3.2.3-0ubuntu7.1) ...
Setting up libedata-cal-1.2-13 (3.2.3-0ubuntu7.1) ...
Setting up evolution-data-server-common (3.2.3-0ubuntu7.1) ...
Setting up evolution-data-server (3.2.3-0ubuntu7.1) ...
Setting up firefox (23.0+build2-0ubuntu0.12.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (23.0+build2-0ubuntu0.12.04.1) ...
Setting up firefox-locale-en (23.0+build2-0ubuntu0.12.04.1) ...
Setting up firefox-locale-zh-hans (23.0+build2-0ubuntu0.12.04.1) ...
Setting up flashplugin-installer (11.2.202.297ubuntu0.12.04.1) ...
Setting up gir1.2-gudev-1.0 (175-0ubuntu9.4) ...
Setting up grub-common (1.99-21ubuntu3.10) ...
Setting up grub2-common (1.99-21ubuntu3.10) ...
Setting up grub-pc-bin (1.99-21ubuntu3.10) ...
Setting up grub-pc (1.99-21ubuntu3.10) ...
Installation finished. No error reported.
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.2.0-51-generic
Found initrd image: /boot/initrd.img-3.2.0-51-generic
Found linux image: /boot/vmlinuz-3.2.0-48-generic
Found initrd image: /boot/initrd.img-3.2.0-48-generic
Found linux image: /boot/vmlinuz-3.2.0-45-generic
Found initrd image: /boot/initrd.img-3.2.0-45-generic
Found linux image: /boot/vmlinuz-3.2.0-44-generic
Found initrd image: /boot/initrd.img-3.2.0-44-generic
Found linux image: /boot/vmlinuz-3.2.0-43-generic
Found initrd image: /boot/initrd.img-3.2.0-43-generic
Found linux image: /boot/vmlinuz-3.2.0-41-generic
Found initrd image: /boot/initrd.img-3.2.0-41-generic
Found linux image: /boot/vmlinuz-3.2.0-40-generic
Found initrd image: /boot/initrd.img-3.2.0-40-generic
Found linux image: /boot/vmlinuz-3.2.0-39-generic
Found initrd image: /boot/initrd.img-3.2.0-39-generic
Found linux image: /boot/vmlinuz-3.2.0-38-generic
Found initrd image: /boot/initrd.img-3.2.0-38-generic
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found linux image: /boot/vmlinuz-3.2.0-36-generic
Found initrd image: /boot/initrd.img-3.2.0-36-generic
Found linux image: /boot/vmlinuz-3.2.0-35-generic
Found initrd image: /boot/initrd.img-3.2.0-35-generic
Found linux image: /boot/vmlinuz-3.2.0-34-generic
Found initrd image: /boot/initrd.img-3.2.0-34-generic
Found linux image: /boot/vmlinuz-3.2.0-31-generic
Found initrd image: /boot/initrd.img-3.2.0-31-generic
Found linux image: /boot/vmlinuz-3.2.0-30-generic
Found initrd image: /boot/initrd.img-3.2.0-30-generic
Found linux image: /boot/vmlinuz-3.2.0-29-generic
Found initrd image: /boot/initrd.img-3.2.0-29-generic
Found linux image: /boot/vmlinuz-3.2.0-27-generic
Found initrd image: /boot/initrd.img-3.2.0-27-generic
Found linux image: /boot/vmlinuz-3.2.0-26-generic
Found initrd image: /boot/initrd.img-3.2.0-26-generic
Found linux image: /boot/vmlinuz-3.2.0-25-generic
Found initrd image: /boot/initrd.img-3.2.0-25-generic
Found linux image: /boot/vmlinuz-3.2.0-24-generic
Found initrd image: /boot/initrd.img-3.2.0-24-generic
Found linux image: /boot/vmlinuz-3.2.0-23-generic
Found initrd image: /boot/initrd.img-3.2.0-23-generic
Found memtest86+ image: /boot/memtest86+.bin
done
Setting up gwibber-service (3.4.2-0ubuntu2.3) ...
Setting up libgwibber2 (3.4.2-0ubuntu2.3) ...
Setting up libgwibber-gtk2 (3.4.2-0ubuntu2.3) ...
Setting up gwibber (3.4.2-0ubuntu2.3) ...
Setting up gwibber-service-facebook (3.4.2-0ubuntu2.3) ...
Setting up gwibber-service-identica (3.4.2-0ubuntu2.3) ...
Setting up gwibber-service-twitter (3.4.2-0ubuntu2.3) ...
Setting up jockey-common (0.9.7-0ubuntu7.9) ...
Setting up jockey-gtk (0.9.7-0ubuntu7.9) ...
Setting up libedataserverui-3.0-1 (3.2.3-0ubuntu7.1) ...
Setting up liblightdm-gobject-1-0 (1.2.3-0ubuntu2.3) ...
Setting up libraptor2-0 (2.0.6-1ubuntu0.1) ...
Setting up libruby1.8 (1.8.7.352-2ubuntu1.3) ...
Setting up ruby1.8 (1.8.7.352-2ubuntu1.3) ...
Setting up unity-services (5.20.0-0ubuntu2) ...
Setting up libunity-core-5.0-5 (5.20.0-0ubuntu2) ...
Setting up unity-common (5.20.0-0ubuntu2) ...
Setting up unity (5.20.0-0ubuntu2) ...
Setting up libxml2-utils (2.7.8.dfsg-5.1ubuntu4.6) ...
Setting up linux-firmware (1.79.6) ...
Setting up linux-image-generic (3.2.0.51.61) ...
Setting up linux-headers-3.2.0-51 (3.2.0-51.77) ...
Setting up linux-headers-3.2.0-51-generic (3.2.0-51.77) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.2.0-51-generic /boot/vmlinuz-3.2.0-51-generic
Setting up linux-headers-generic (3.2.0.51.61) ...
Setting up linux-generic (3.2.0.51.61) ...
Setting up linux-libc-dev (3.2.0-51.77) ...
Setting up mysql-client-core-5.5 (5.5.32-0ubuntu0.12.04.1) ...
Setting up mysql-server-core-5.5 (5.5.32-0ubuntu0.12.04.1) ...
Setting up python-libxml2 (2.7.8.dfsg-5.1ubuntu4.6) ...
Setting up remmina-common (1.0.0-1ubuntu6.3) ...
Setting up remmina (1.0.0-1ubuntu6.3) ...
Setting up remmina-plugin-rdp (1.0.0-1ubuntu6.3) ...
Setting up remmina-plugin-vnc (1.0.0-1ubuntu6.3) ...
Setting up thunderbird (17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-zh-hans (1:17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-globalmenu (17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en (1:17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-gb (1:17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-en-us (1:17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up thunderbird-locale-zh-cn (1:17.0.8+build1-0ubuntu0.12.04.1) ...
Setting up unity-lens-files (5.10.0-0ubuntu1.1) ...
Setting up xul-ext-ubufox (2.7-0ubuntu0.12.04.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.2.0-51-generic
:~$ 

```

---

### Post by philinux on 2013-08-19
Looks fine. All sorted no errors.

Although you have a lot of old kernels there. Bit of housekeeping needed maybe.

You can remove the old ones via synaptic.

---

### Post by candra2 on 2013-08-19
So does that mean we are done - shall I try and run the update manager??

I will run Synpatic as well...

---

### Post by candra2 on 2013-08-19
oh - I see it did all the updates via the last terminal command - that was what that was all about!!

So then it really is mission accomplished!!

Thanks so much!!

Or is there a part of the puzzle I am missing?

---

### Post by ian-weisser on 2013-08-19
Since you can successfully update now, the problem is fixed.
Congratulations.

If you wish to reinstall Skype, you can now. Remember to uninstall it if the problem recurs.

---

### Post by candra2 on 2013-08-19
Thanks so much - you all did a wonderful job - I am very grateful for your efforts and time. 

As for Skype...nah : -)

---

### Post by philinux on 2013-08-19
Only thing to do now is mark the thread solved from the thread tools pull down menu. ;)

---

### Post by candra2 on 2013-08-19
When I go to thread tools it only show me three options - not five. When five optinos are displayed then one is **mark as solved**, but that option is not on my thread tools menu - why I do not know. 

Can you please mark the thread as solved or inform me what / how I can get that option in my thread tools drop down menu.

thanks

---

### Post by ubentobox on 2013-08-19
I had actually ran into this issue with 12.04 before.  While I am at work I cannot give you the direct path, I believe the /etc/environments had an errant '$' in the paths to install.  I had not touched the file and it was a fresh install from the website, but once I removed this I was able to update my machine for the first time since I had installed it.  Just something to look out for.

---

### Post by bapoumba on 2013-08-19
Wow :)
I've marked your thread as solved.

In the future, make sure to be careful when installing 3rd party packages, in particular during a release upgrade.

---

### Post by candra2 on 2013-08-19
Thanks for marking my thread as solved...

I shall certainly be careful about 3rd party installs in the future; in my several years (6 or more) of running Ubuntu I never encountered such problems with installs. I will certainly be wary from now forward. 

Thanks again for your help and solutions!!

---

### Post by bapoumba on 2013-08-20
You are welcome candra2. Please do not get me wrong. 3rd party apps and software are ok. One problem is when they install packages that have version numbers higher than the ones from the standard distribution. Then uninstalling has to be done 1- from the package manager itself AND 2- with the third party repo still active in the sources.list. If the 3rd party devs do their jobs correctly, uninstalling should be transparent and then you can remove the repo from the sources.list.

Any other combination of circumstances, including unfortunate internet problem to anything else, can result in a dependency nightmare : some packages are installed, others depend on them, but the version numbers do not match for your release. Clearing out the situation is always a one on one solution. Some general rules can apply, dpkg is a very powerful tool in that situation, but misused it can lead to a completely unusable system. This is why we did go very slowly, small step by small step, trying to identify where the problems were and clearing them out one by one from soft to harsher commands.
apt-get dist-upgrade is also very handy. It checks the dependencies within the distribution and can handle a certain level of conflict.

Thanks everyone, and candra2, thanks for your patience :)

---


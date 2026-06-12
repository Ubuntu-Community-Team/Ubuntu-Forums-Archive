---
title: "cant remove broken packages in Synaptic"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by ro12 on 2013-06-14
I did an update from 12.04 to 12.10 and 11 packages are broken.I cant repair or remove them. When I run update in Terminal I get this message.
"dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar':
 mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)"
Any ideas much appreciated .

---

### Post by fantab on 2013-06-14
Post the complete output of:

sudo apt-get update

so we know what packages are broken.

---

### Post by newb85 on 2013-06-15
And put it in code tags, while you're at it, so it's easier to read.  Like this:

```
[noparse][CODE]Output of apt-get update here...
```[/noparse][/code]

---

### Post by ro12 on 2013-06-16
Hello, the out put I get is  [Reading package lists... Error!E: Could not open file /var/lib/dpkg/status - open (2: No such file or directory)
E: The package lists or status file could not be parsed or opened.]

---

### Post by newb85 on 2013-06-16
That's strange.  What are the results of
```
ls -l /var/lib/dpkg
```

---

### Post by ro12 on 2013-06-16
out put of:     [COLOR=#000000][FONT=Ubuntu Mono]ls -l /var/lib/dpkg  is
[/FONT][/COLOR]total 12224
drwxr-xr-x 2 root root    4096 May 22 14:05 alternatives
-rw-r--r-- 1 root root 2960053 May 31 16:46 available-bad
-rw-r--r-- 1 root root 2960053 May 31 16:49 available.bak
-rw-r--r-- 1 root root       0 May 31 17:01 available-old
-rw-r--r-- 1 root root       8 Apr 29  2010 cmethopt
-rw-r--r-- 1 root root    1446 Apr  2 15:59 diversions
-rw-r--r-- 1 root root    1492 Apr  2 15:53 diversions-old
-rw-r--r-- 1 root root       1 Aug 14  2011 format
drwxr-xr-x 2 root root  552960 May 21 17:43 info
-rw-r----- 1 root root       0 Jun 15 21:01 lock
drwxr-xr-x 2 root root    4096 Apr 15  2010 parts
-rw-r--r-- 1 root root     228 Jan 25  2012 statoverride
-rw-r--r-- 1 root root     185 Jan 25  2012 statoverride-old
-rw-r--r-- 1 root root 2994637 May 31 16:48 status-bad
-rw-r--r-- 1 root root 2994637 May 21 17:43 status-old
drwxr-xr-x 2 root root    4096 May 21 17:42 triggers
drwxr-xr-x 2 root root    4096 May 21 17:43 updates

---

### Post by ro12 on 2013-06-16
Somehow I removed the packages, but now I cant install or upgrade my system.

---

### Post by fantab on 2013-06-16
Post the complete output of:

sudo apt-get update

so that we know what is happening and going wrong.

---

### Post by newb85 on 2013-06-17
There appears to be a problem with your /var/lib/dpkg/status and /var/lib/dpkg/available files.  Let's focus on the status file first, since that's what's kicking out the error message at the moment.  I've never dealt with problems in these files, so if anyone else has a better idea for diagnosing the problem, please jump in.

Please give the output of
```
cat /var/lib/dpkg/status-bad | grep Status
```

Also, put terminal commands and terminal outputs in code tags.  I know it might seem cumbersome to type them in manually or use the Adv. Reply instead of the Quick Reply, but really, it's easier to read (case in point: post #6) and harder to make a mistake copying and pasting, and that's why it's part of the Code of Conduct.

---

### Post by matt_symes on 2013-06-17
Hi

For the initial problem, read these bug reports

[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015567](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015567)
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015616](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/1015616)

I would diff the two status and available files to see what the changes are (the .bad and .old files) and, depending on the differences, either try to fix the .bad files or roll back to the .old files.

I will not be about though, for the rest of the day.

Kind regards

---

### Post by ro12 on 2013-06-17
output of get update is ```


Hit http://archive.canonical.com raring Release.gpg
Hit http://security.ubuntu.com raring-security Release.gpg           
Hit http://ca.archive.ubuntu.com raring Release.gpg                  
Get:1 http://ca.archive.ubuntu.com raring-updates Release.gpg [933 B]
Hit http://extras.ubuntu.com raring Release.gpg                                
Hit http://archive.canonical.com raring Release                      
Hit http://security.ubuntu.com raring-security Release                         
Hit http://ca.archive.ubuntu.com raring Release                                
Hit http://extras.ubuntu.com raring Release                                    
Hit http://archive.canonical.com raring/partner amd64 Packages                 
Hit http://security.ubuntu.com raring-security/main Sources          
Get:2 http://ca.archive.ubuntu.com raring-updates Release [40.8 kB]  
Hit http://extras.ubuntu.com raring/main amd64 Packages                        
Ign http://archive.canonical.com raring/partner TranslationIndex               
Hit http://security.ubuntu.com raring-security/restricted Sources              
Hit http://security.ubuntu.com raring-security/universe Sources                
Hit http://security.ubuntu.com raring-security/multiverse Sources              
Hit http://security.ubuntu.com raring-security/main amd64 Packages             
Hit http://security.ubuntu.com raring-security/restricted amd64 Packages       
Hit http://security.ubuntu.com raring-security/universe amd64 Packages         
Hit http://security.ubuntu.com raring-security/multiverse amd64 Packages       
Hit http://security.ubuntu.com raring-security/main TranslationIndex           
Hit http://security.ubuntu.com raring-security/multiverse TranslationIndex     
Hit http://security.ubuntu.com raring-security/restricted TranslationIndex     
Ign http://extras.ubuntu.com raring/main TranslationIndex                      
Hit http://security.ubuntu.com raring-security/universe TranslationIndex       
Hit http://security.ubuntu.com raring-security/main Translation-en             
Hit http://security.ubuntu.com raring-security/multiverse Translation-en       
Hit http://ca.archive.ubuntu.com raring/main Sources                           
Hit http://ca.archive.ubuntu.com raring/restricted Sources                     
Hit http://ca.archive.ubuntu.com raring/universe Sources                       
Hit http://ca.archive.ubuntu.com raring/multiverse Sources                     
Hit http://ca.archive.ubuntu.com raring/main amd64 Packages                    
Hit http://ca.archive.ubuntu.com raring/restricted amd64 Packages              
Hit http://ca.archive.ubuntu.com raring/universe amd64 Packages                
Hit http://ca.archive.ubuntu.com raring/multiverse amd64 Packages              
Hit http://ca.archive.ubuntu.com raring/main TranslationIndex                  
Hit http://ca.archive.ubuntu.com raring/multiverse TranslationIndex            
Hit http://security.ubuntu.com raring-security/restricted Translation-en       
Hit http://ca.archive.ubuntu.com raring/restricted TranslationIndex            
Hit http://ca.archive.ubuntu.com raring/universe TranslationIndex              
Get:3 http://ca.archive.ubuntu.com raring-updates/main Sources [35.7 kB]       
Hit http://security.ubuntu.com raring-security/universe Translation-en         
Get:4 http://ca.archive.ubuntu.com raring-updates/restricted Sources [14 B]    
Get:5 http://ca.archive.ubuntu.com raring-updates/universe Sources [48.7 kB]
Get:6 http://ca.archive.ubuntu.com raring-updates/multiverse Sources [690 B]   
Get:7 http://ca.archive.ubuntu.com raring-updates/main amd64 Packages [92.9 kB]
Ign http://archive.canonical.com raring/partner Translation-en_CA              
Get:8 http://ca.archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]
Get:9 http://ca.archive.ubuntu.com raring-updates/universe amd64 Packages [91.5 kB]
Ign http://archive.canonical.com raring/partner Translation-en                 
Ign http://extras.ubuntu.com raring/main Translation-en_CA                     
Get:10 http://ca.archive.ubuntu.com raring-updates/multiverse amd64 Packages [1,143 B]
Hit http://ca.archive.ubuntu.com raring-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com raring-updates/multiverse TranslationIndex
Hit http://ca.archive.ubuntu.com raring-updates/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com raring-updates/universe TranslationIndex
Hit http://ca.archive.ubuntu.com raring/main Translation-en_CA
Hit http://ca.archive.ubuntu.com raring/main Translation-en
Hit http://ca.archive.ubuntu.com raring/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring/restricted Translation-en
Ign http://extras.ubuntu.com raring/main Translation-en                
Hit http://ca.archive.ubuntu.com raring/universe Translation-en_CA     
Hit http://ca.archive.ubuntu.com raring/universe Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/main Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/universe Translation-en
Fetched 312 kB in 2s (113 kB/s)
Reading package lists... Done
robin@robin-laptop:~$ 


         
```

---

### Post by ro12 on 2013-06-17
sorry I double posted

---

### Post by ro12 on 2013-06-17
output of :  [COLOR=#000000][FONT=Ubuntu Mono]cat /var/lib/dpkg/status-bad | grep Status is```

[/FONT][/COLOR]Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok unpacked
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
 Twitter, Identi.ca, StatusNet, FriendFeed, Qaiku, Flickr, and Digg.
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: deinstall ok config-files
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
Status: install ok installed
robin@robin-laptop:~$ 

```

---

### Post by newb85 on 2013-06-17
I don't see anything in those two outputs that looks out of place.  Why don't you take matt_symes' suggestion and diff the two status and available files.  That might throw some new light on the problem.

```
diff -c8 /var/lib/dpkg/status-old /var/lib/dpkg/status-bad
```
and
```
diff -c8 /var/lib/dpkg/available-old /var/lib/dpkg/available-bad
```

---

### Post by ro12 on 2013-06-18
When I [COLOR=#000000]tried ```

[/COLOR][COLOR=#000000]
diff -c8 /var/lib/dpkg/status-old /var/lib/dpkg/status-bad
diff -c8 /var/lib/dpkg/available-old /var/lib/dpkg/available-bad[/COLOR]
[COLOR=#000000]this is what I got[CODE] [/COLOR]+  This library provides a method of binding JavaScript objects to QObjects, so+  you can script your applications. It also provides an interface for running
+  embedded Javascript.
+  .
+  This package is part of the KDE Development Platform libraries module.
+ Homepage: http://www.kde.org/
+ Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
+ 
+ Package: libkrb5-3
+ Multi-Arch: same
+ Priority: standard
+ Section: libs
+ Installed-Size: 959
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: krb5
+ Version: 1.10+dfsg~beta1-2ubuntu0.3
+ Replaces: libkrb53 (<< 1.6.dfsg.4~beta1-7)
+ Depends: libc6 (>= 2.14), libcomerr2 (>= 1.34), libk5crypto3 (>= 1.9+dfsg~beta1), libkeyutils1, libkrb5support0 (= 1.10+dfsg~beta1-2ubuntu0.3)
+ Pre-Depends: multiarch-support
+ Recommends: krb5-locales
+ Suggests: krb5-doc, krb5-user
+ Breaks: libkrb53 (<< 1.6.dfsg.4~beta1-9), libsmbclient (<= 2:3.6.1-2), sssd (<= 1.2.1-4.3)
+ Filename: pool/main/k/krb5/libkrb5-3_1.8.1+dfsg-2_amd64.deb
+ Size: 354728
+ MD5sum: b24f86b90ca48816c6453be466216492
+ Description: MIT Kerberos runtime libraries
+  Kerberos is a system for authenticating users and services on a network.
+  Kerberos is a trusted third-party service.  That means that there is a
+  third party (the Kerberos server) that is trusted by all the entities on
+  the network (users and services, usually called "principals").
+  .
+  This is the MIT reference implementation of Kerberos V5.
+  .
+  This package contains the runtime library for the main Kerberos v5 API
+  used by applications and Kerberos clients.
+ Homepage: http://web.mit.edu/kerberos/
+ Original-Maintainer: Sam Hartman <hartmans@debian.org>
+ 
+ Package: libkrb5-3
+ Multi-Arch: same
+ Priority: standard
+ Section: libs
+ Installed-Size: 957
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: i386
+ Source: krb5
+ Version: 1.10+dfsg~beta1-2ubuntu0.3
+ Replaces: libkrb53 (<< 1.6.dfsg.4~beta1-7)
+ Depends: libc6 (>= 2.9), libcomerr2 (>= 1.34), libk5crypto3 (>= 1.9+dfsg~beta1), libkeyutils1, libkrb5support0 (= 1.10+dfsg~beta1-2ubuntu0.3)
+ Pre-Depends: multiarch-support
+ Recommends: krb5-locales
+ Suggests: krb5-doc, krb5-user
+ Breaks: libkrb53 (<< 1.6.dfsg.4~beta1-9), libsmbclient (<= 2:3.6.1-2), sssd (<= 1.2.1-4.3)
+ Size: 365618
+ Description: MIT Kerberos runtime libraries
+  Kerberos is a system for authenticating users and services on a network.
+  Kerberos is a trusted third-party service.  That means that there is a
+  third party (the Kerberos server) that is trusted by all the entities on
+  the network (users and services, usually called "principals").
+  .
+  This is the MIT reference implementation of Kerberos V5.
+  .
+  This package contains the runtime library for the main Kerberos v5 API
+  used by applications and Kerberos clients.
+ Homepage: http://web.mit.edu/kerberos/
+ Original-Maintainer: Sam Hartman <hartmans@debian.org>
+ 
+ Package: libgnome-media0
+ Priority: optional
+ Section: libs
+ Installed-Size: 160
+ Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
+ Architecture: amd64
+ Source: gnome-media
+ Version: 2.32.0-0ubuntu7
+ Replaces: gnome-media (<< 2.12.0-4)
+ Depends: gnome-media-common (>= 2.32), gnome-media-common (<< 2.33), libatk1.0-0 (>= 1.12.4), libc6 (>= 2.2.5), libcairo2 (>= 1.2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1), libgconf2-4 (>= 2.31.1), libgdk-pixbuf2.0-0 (>= 2.22.0), libgladeui-1-11 (>= 3.7.2), libglib2.0-0 (>= 2.18.2), libgstreamer0.10-0 (>= 0.10.23), libgtk2.0-0 (>= 2.18), libpango1.0-0 (>= 1.14.0), libxml2 (>= 2.6.27)
+ Size: 45078
+ Description: runtime libraries for the GNOME media utilities
+  This package contains media-related libraries used by the GNOME
+  suite:
+   * libgnome-media-profiles, which manages a store of media profiles
+     for software using GStreamer to encode audio data.
+ Homepage: http://live.gnome.org/GnomeMedia
+ Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>
+ 
+ Package: libmono-system-drawing4.0-cil
+ Priority: optional
+ Section: cli-mono
+ Installed-Size: 512
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: all
+ Source: mono
+ Version: 2.10.8.1-1ubuntu2.2
+ Depends: libc6 (>= 2.15) | libc6.1 (>= 2.15) | libc0.1 (>= 2.15), libgdiplus (>= 2.6.7), libmono-corlib4.0-cil (>= 2.10.1), libmono-system4.0-cil (>= 2.10.7), libx11-6
+ Suggests: libcups2 (>= 1.3.8)
+ Size: 167580
+ Description: Mono System.Drawing library (for CLI 4.0)
+  Mono is a platform for running and developing applications based on the
+  ECMA/ISO Standards. Mono is an open source effort led by Novell.
+  Mono provides a complete CLR (Common Language Runtime) including compiler and
+  runtime, which can produce and execute CIL (Common Intermediate Language)
+  bytecode (aka assemblies), and a class library.
+  .
+  This package contains the Mono System.Drawing library for CLI 4.0.
+ Homepage: http://www.mono-project.com/
+ Original-Maintainer: Debian Mono Group <pkg-mono-group@lists.alioth.debian.org>
+ 
+ Package: lsof
+ Priority: standard
+ Section: utils
+ Installed-Size: 452
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Version: 4.81.dfsg.1-1build1
+ Replaces: lsof-2.0.35, lsof-2.0.36, lsof-2.0.38, lsof-2.2 (<< 4.73)
+ Depends: libc6 (>= 2.11)
+ Conflicts: suidmanager (<< 0.50)
+ Size: 284326
+ Description: List open files
+  Lsof is a Unix-specific diagnostic tool.  Its name stands
+  for LiSt Open Files, and it does just that.  It lists
+  information about any files that are open, by processes
+  currently running on the system.
+ Original-Maintainer: Norbert Tretkowski <nobse@debian.org>
+ 
+ Package: qapt-batch
+ Priority: optional
+ Section: kde
+ Installed-Size: 120
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: qapt
+ Version: 1.3.1-0ubuntu2
+ Depends: kde-runtime, libc6 (>= 2.14), libkdecore5 (>= 4:4.3.4), libkdeui5 (>= 4:4.3.4), libqt4-dbus (>= 4:4.6.1), libqtcore4 (>= 4:4.7.0~beta1), libqtgui4 (>= 4:4.5.3), libstdc++6 (>= 4.1.1), libqapt-runtime
+ Size: 23324
+ Description: Batch package manager for KDE
+  QApt Batch is a simple GUI for doing batch package management operations.
+  It can install and remove packages, as well as update the package cache via a
+  command line interface. It also has an attach function invokable via the
+  command line. QApt Batch is a drop-in replacement for the "install-package"
+  batch package management tool.
+ Homepage: https://projects.kde.org/projects/extragear/sysadmin/libqapt/
+ Original-Maintainer: Jonathan Thomas <echidnaman@kubuntu.org>
+ 
+ Package: python-pysqlite2
+ Priority: optional
+ Section: python
+ Installed-Size: 149
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Version: 2.6.3-2build1
+ Replaces: python2.3-pysqlite2, python2.4-pysqlite2
+ Provides: python2.7-pysqlite2
+ Depends: libc6 (>= 2.4), libsqlite3-0 (>= 3.5.9), python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8)
+ Suggests: python-pysqlite2-doc, python-pysqlite2-dbg
+ Conflicts: python2.3-pysqlite2, python2.4-pysqlite2
+ Size: 36602
+ Description: Python interface to SQLite 3
+  pysqlite is a DB-API 2.0-compliant database interface for SQLite.
+  .
+  This package is built against SQLite 3. For an interface to SQLite 2,
+  see the package python-sqlite. An alternative Python SQLite 3 module
+  is packaged as python-apsw.
+  .
+  SQLite is a relational database management system contained in a
+  relatively small C library. It is a public domain project created
+  by D. Richard Hipp. Unlike the usual client-server paradigm, the
+  SQLite engine is not a standalone process with which the program
+  communicates, but is linked in and thus becomes an integral part
+  of the program. The library implements most of SQL-92 standard,
+  including transactions, triggers and most of complex queries.
+  .
+  pysqlite makes this powerful embedded SQL engine available to
+  Python programmers. It stays compatible with the Python database
+  API specification 2.0 as much as possible, but also exposes most
+  of SQLite's native API, so that it is for example possible to
+  create user-defined SQL functions and aggregates in Python.
+  .
+  If you need a relational database for your applications, or even
+  small tools or helper scripts, pysqlite is often a good fit. It's
+  easy to use, easy to deploy, and does not depend on any other
+  Python libraries or platform libraries, except SQLite. SQLite
+  itself is ported to most platforms you'd ever care about.
+  .
+  It's often a good alternative to MySQL, the Microsoft JET engine
+  or the MSDE, without having any of their license and deployment
+  issues.
+ Original-Maintainer: Joel Rosdahl <joel@debian.org>
+ 
+ Package: pulseaudio-module-bluetooth
+ Priority: extra
+ Section: sound
+ Installed-Size: 303
+ Maintainer: Ubuntu Core Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: pulseaudio
+ Version: 1:1.1-0ubuntu15.2
+ Depends: libbluetooth3 (>= 4.91), libc6 (>= 2.15), libdbus-1-3 (>= 1.0.2), libpulse0 (>= 1:1.1-0ubuntu15.2), pulseaudio
+ Conflicts: pulseaudio (<< 0.9.14-2)
+ Size: 82374
+ Description: Bluetooth module for PulseAudio sound server
+  PulseAudio, previously known as Polypaudio, is a sound server for POSIX and
+  WIN32 systems. It is a drop in replacement for the ESD sound server with
+  much better latency, mixing/re-sampling quality and overall architecture.
+  .
+  This module enables PulseAudio to work with bluetooth devices, like headset
+  or audio gateway.
+  .
+  The module is called module-bluetooth
+ Homepage: http://www.pulseaudio.org
+ Original-Maintainer: Pulseaudio maintenance team <pkg-pulseaudio-devel@lists.alioth.debian.org>
+ 
+ Package: liblockfile1
+ Multi-Arch: same
+ Priority: standard
+ Section: libs
+ Installed-Size: 56
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: liblockfile
+ Version: 1.09-3
+ Depends: libc6 (>= 2.4), liblockfile-bin (>= 1.09-3)
+ Pre-Depends: multiarch-support
+ Filename: pool/main/libl/liblockfile/liblockfile1_1.08-3ubuntu1_amd64.deb
+ Size: 9102
+ MD5sum: f31025a869f68f0a54ec12bf015d13ab
+ Description: NFS-safe locking library
+  Liblockfile is a shared library with NFS-safe locking functions.
+ Original-Maintainer: Miquel van Smoorenburg <miquels@cistron.nl>
+ 
+ Package: libxau6
+ Multi-Arch: same
+ Priority: optional
+ Section: libs
+ Installed-Size: 54
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: libxau
+ Version: 1:1.0.6-4
+ Depends: libc6 (>= 2.4)
+ Pre-Depends: multiarch-support
+ Size: 8392
+ Description: X11 authorisation library
+  This package provides the main interface to the X11 authorisation handling,
+  which controls authorisation for X connections, both client-side and
+  server-side.
+  .
+  More information about X.Org can be found at:
+  <URL:http://www.X.org>
+  .
+  This module can be found at
+  git://anongit.freedesktop.org/git/xorg/lib/libXau
+ Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
+ 
+ Package: libxau6
+ Multi-Arch: same
+ Priority: optional
+ Section: libs
+ Installed-Size: 53
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: i386
+ Source: libxau
+ Version: 1:1.0.6-4
+ Depends: libc6 (>= 2.4)
+ Pre-Depends: multiarch-support
+ Size: 8344
+ Description: X11 authorisation library
+  This package provides the main interface to the X11 authorisation handling,
+  which controls authorisation for X connections, both client-side and
+  server-side.
+  .
+  More information about X.Org can be found at:
+  <URL:http://www.X.org>
+  .
+  This module can be found at
+  git://anongit.freedesktop.org/git/xorg/lib/libXau
+ Original-Maintainer: Debian X Strike Force <debian-x@lists.debian.org>
+ 
+ Package: liblaunchpad-integration1
+ Priority: optional
+ Section: libs
+ Installed-Size: 51
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Source: launchpad-integration
+ Version: 0.1.56.1
+ Replaces: liblaunchpad-integration0
+ Depends: libc6 (>= 2.2.5), libglib2.0-0 (>= 2.12.0), libgtk2.0-0 (>= 2.8.2), liblaunchpad-integration-common
+ Recommends: launchpad-integration
+ Size: 8826
+ Description: library for launchpad integration
+  The launchpad-integration tools provide an easy way to set menu items,
+  for an application using GtkUIManager, pointing to the launchpad pages
+  about a package. Users can get information about the used application here,
+  translate it, ...
+   .
+  This package contains the shared library for GTK+ 2.0.
+ Original-Maintainer: Sebastien Bacher <seb128@debian.org>
+ 
+ Package: gconf-defaults-service
+ Multi-Arch: foreign
+ Priority: optional
+ Section: libs
+ Installed-Size: 445
+ Maintainer: Ubuntu Desktop Team <ubuntu-desktop@lists.ubuntu.com>
+ Architecture: amd64
+ Source: gconf
+ Version: 3.2.5-0ubuntu2
+ Replaces: gconf2-common (<< 2.24.0-3)
+ Depends: gconf-service, libc6 (>= 2.2.5), libdbus-1-3 (>= 1.0.2), libdbus-glib-1-2 (>= 0.88), libgconf-2-4 (>= 2.31.1), libglib2.0-0 (>= 2.25.9), libpolkit-gobject-1-0 (>= 0.94), dbus-x11, gconf2-common (= 3.2.5-0ubuntu2)
+ Breaks: gconf-editor (<< 2.28)
+ Conflicts: gconf2-common (<< 2.24.0-3), libgconf2-4 (<< 2.24.0-3)
+ Size: 14664
+ Description: GNOME configuration database system (system defaults service)
+  GConf is a configuration database system for storing application
+  preferences. It supports default or mandatory settings set by the
+  administrator, and changes to the database are instantly applied to all
+  running applications. It is written for the GNOME desktop but doesn't
+  require it.
+  .
+  This package contains the PolicyKit service that allows users to edit the
+  system-wide defaults from a user session.
+ Homepage: http://projects.gnome.org/gconf/
+ Original-Maintainer: Josselin Mouette <joss@debian.org>
+ 
+ Package: wwwconfig-common
+ Priority: optional
+ Section: web
+ Installed-Size: 216
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: all
+ Version: 0.2.2
+ Suggests: mysql-client, postgresql-client, apache2
+ Size: 18004
+ Description: Debian web auto configuration
+  A package to provide common setup scripts for some
+  packages that need apache, php and a database.
+ Original-Maintainer: Ola Lundqvist <opal@debian.org>
+ 
+ Package: kde-runtime
+ Priority: optional
+ Section: kde
+ Installed-Size: 10075
+ Maintainer: Kubuntu Developers <kubuntu-devel@lists.ubuntu.com>
+ Architecture: amd64
+ Version: 4:4.8.5-0ubuntu0.1
+ Replaces: kdebase-runtime (<< 4:4.6.80), kdebase-runtime-bin-kde4, kdebase-runtime-data (<< 4:4.4.80), kdebase-workspace-bin (<< 4:4.6), kdebluetooth (<< 1.0~beta7-1), kdelibs5 (<< 4:4.4.80), kdelibs5-plugins (<< 4:4.5), nepomukcontroller, plasma-netbook (<< 4:4.5.95), plasma-scriptengine-declarative, plasma-scriptengine-javascript (<< 4:4.6.80)
+ Depends: libasound2 (>= 1.0.23), libattica0.3 (>= 0.3.0), libc6 (>= 2.15), libcanberra0 (>= 0.2), libexiv2-11, libgcc1 (>= 1:4.1.1), libjpeg8 (>= 8c), libkcmutils4 (>= 4:4.8.1), libkdeclarative5 (>= 4:4.7.0), libkdecore5 (>= 4:4.8.1), libkdesu5 (>= 4:4.8.1), libkdeui5 (>= 4:4.8.1), libkdewebkit5 (>= 4:4.8.1), libkdnssd4 (>= 4:4.8.1), libkemoticons4 (>= 4:4.8.1), libkfile4 (>= 4:4.8.1), libkhtml5 (>= 4:4.8.1), libkidletime4 (>= 4:4.8.1), libkio5 (>= 4:4.8.1), libkmediaplayer4 (>= 4:4.8.1), libknewstuff3-4 (>= 4:4.8.1), libknotifyconfig4 (>= 4:4.8.1), libkparts4 (>= 4:4.8.1), libkpty4 (>= 4:4.8.1), libnepomuk4 (>= 4:4.8.1), libnepomukdatamanagement4 (>= 4:4.8.1), libnepomukquery4a (>= 4:4.8.1), libnepomuksync4 (>= 4:4.8.1), libntrack-qt4-1 (>= 005), libopenexr6 (>= 1.6.1), libphonon4 (>= 4:4.7.0really4.5.0), libplasma3 (>= 4:4.8.1), libpulse-mainloop-glib0 (>= 1:0.99.1), libpulse0 (>= 1:0.99.1), libqt4-dbus (>= 4:4.6.1), libqt4-declarative (>= 4:4.7.0~rc1), libqt4-network (>= 4:4.5.3), libqt4-script (>= 4:4.6.1), libqt4-svg (>= 4:4.5.3), libqt4-xml (>= 4:4.5.3), libqtcore4 (>= 4:4.8.0), libqtgui4 (>= 4:4.8.0), libqtwebkit4 (>= 2.2~2011week36), libsmbclient (>= 2:3.2.0), libsolid4 (>= 4:4.8.1), libsoprano4 (>= 2.6.51), libssh-4 (>= 0.3.91), libstdc++6 (>= 4.6), libstreamanalyzer0 (>= 0.7.7), libstreams0 (>= 0.7.7), libx11-6, libxcursor1 (>> 1.1.2), phonon, perl, kde-runtime-data (>= 4:4.8.5-0ubuntu0.1), kdelibs5-plugins (>= 4:4.8.1), oxygen-icon-theme (>= 4:4.6), shared-desktop-ontologies, plasma-scriptengine-javascript (= 4:4.8.5-0ubuntu0.1)
+ Recommends: udisks, upower, virtuoso-minimal, kubuntu-debug-installer, icoutils, libcanberra-pulse | libcanberra-gstreamer
+ Suggests: djvulibre-bin, finger
+ Breaks: kdebase-runtime (<< 4:4.6.80), kdebase-runtime-bin-kde4, kdebase-runtime-data (<< 4:4.4.80), kdebase-workspace-bin (<< 4:4.6), kdebluetooth (<< 1.0~beta7-1), kdelibs5 (<< 4:4.4.80), kdelibs5-plugins (<< 4:4.5), nepomukcontroller, plasma-netbook (<< 4:4.5.95), plasma-scriptengine-declarative, plasma-scriptengine-javascript (<< 4:4.6.80)
+ Conflicts: kdelibs4-dev
+ Size: 2076360
+ Description: runtime components from the official KDE release
+  KDE is produced by an international technology team that creates free and open
+  source software for desktop and portable computing. Among KDE's products are a
+  modern desktop system for Linux and UNIX platforms, comprehensive office
+  productivity and groupware suites and hundreds of software titles in many
+  categories including Internet and web applications, multimedia, entertainment,
+  educational, graphics and software development.
+  .
+  This package contains programs and data needed at runtime by KDE applications.
+ Homepage: http://www.kde.org/
+ Original-Maintainer: Debian Qt/KDE Maintainers <debian-qt-kde@lists.debian.org>
+ 
+ Package: libio-string-perl
+ Priority: optional
+ Section: perl
+ Installed-Size: 72
+ Maintainer: Ubuntu Core Developers <ubuntu-devel@lists.ubuntu.com>
+ Architecture: all
+ Version: 1.08-2
+ Depends: perl (>= 5.6.0-16)
+ Filename: pool/main/libi/libio-string-perl/libio-string-perl_1.08-2_all.deb
+ Size: 12022
+ MD5sum: 3637a4ce8783d519141c6c96313145b8
+ Description: Emulate IO::File interface for in-core strings
+  The IO::String module provide the IO::File interface for in-core
+  strings.  An IO::String object can be attached to a string, and
+  will make it possible to use the normal file operations for reading or
+  writing data, as well as seeking to various locations of the string.
+  The main reason you might want to do this, is if you have some other
+  library module that only provide an interface to file handles, and you
+  want to keep all the stuff in memory.
+  .
+  The IO::String module provide an interface compatible with
+  IO::File as distributed with IO-1.20, but the following methods
+  are not available; new_from_fd, fdopen, format_write,
+  format_page_number, format_lines_per_page, format_lines_left,
+  format_name, format_top_name.
+ Original-Maintainer: Debian Perl Group <pkg-perl-maintainers@lists.alioth.debian.org>
+ 
+ Package: python-cherrypy3
+ Priority: optional
+ Section: python
+ Installed-Size: 21478
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: all
+ Source: cherrypy3
+ Version: 3.2.2-2
+ Provides: python2.7-cherrypy3
+ Depends: python2.7, python (>= 2.7.1-0ubuntu2), python (<< 2.8)
+ Conflicts: python-cherrypy, python2.3-cherrypy, python2.4-cherrypy
+ Size: 2353368
+ Description: Python web development framework - version 3
+  CherryPy is a pythonic, object-oriented web development framework. It
+  provides the foundation over which complex web-based applications can
+  be written, with little or no knowledge of the underlying
+  protocols. CherryPy allows developers to build web applications in
+  much the same way they would build any other object-oriented Python
+  program. This usually results in smaller source code developed in
+  less time.
+  .
+  CherryPy is up-to-date with the latest developments on using Python
+  for web development: it features a bundled WSGI server, and is able
+  to integrate with other dispatching mechanisms, such as
+  Routes. CherryPy can be run as a standalone application, since it
+  provides its own HTTP server; setting it up behind another HTTP
+  server, such as Apache, or even with mod_python are also options.
+  .
+  This version is backwards incompatible with the 2.2 version in some
+  ways. See http://www.cherrypy.org/wiki/UpgradeTo30.
+ Original-Maintainer: Gustavo Noronha Silva <kov@debian.org>
+ Homepage: http://www.cherrypy.org/
+ 
+ Package: gnome-power-manager
+ Priority: optional
+ Section: gnome
+ Installed-Size: 1580
+ Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
+ Architecture: amd64
+ Version: 3.4.0-0ubuntu1.1
+ Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libglib2.0-0 (>= 2.31.18), libgtk-3-0 (>= 3.3.8), libpango1.0-0 (>= 1.18.0), libupower-glib1 (>= 0.9.1), dconf-gsettings-backend | gsettings-backend, notification-daemon, dbus-x11, consolekit, upower, gnome-settings-daemon (>= 3.2)
+ Suggests: policykit-1
+ Breaks: gnome-session (<< 2.28)
+ Size: 407498
+ Description: power management tool for the GNOME desktop
+  GNOME Power Manager is a session daemon for the GNOME desktop
+  that takes care of system or desktop events related to power, and
+  triggers actions accordingly. Its philosophy is to completely hide
+  these complex tasks and only show some settings important to the user.
+  .
+  GNOME power manager displays and manages battery status, power plug
+  events, display brightness, CPU, graphics card and hard disk drive
+  power saving, and can trigger suspend-to-RAM, hibernate or shutdown
+  events, all integrated to other components of the GNOME desktop.
+ Homepage: http://www.gnome.org/projects/gnome-power-manager/
+ Original-Maintainer: Debian GNOME Maintainers <pkg-gnome-maintainers@lists.alioth.debian.org>

```
[COLOR=#000000]

[/COLOR]

---

### Post by HiImTye on 2013-06-18
open ```
/var/log/apt/term.log
``` and paste that here. **after that**, do```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status; sudo apt-get update; sudo apt-get dist-upgrade -y
```
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]

---

### Post by ro12 on 2013-06-19
When I tried [COLOR=#000000]Code:[/COLOR]
/var/log/apt/term.logI got ```
[COLOR=#222222][FONT=Verdana]bash: /var/log/apt/term.log: Permission denied[/FONT][/COLOR]

Then I tried [CODE][COLOR=#000000][FONT=Ubuntu Mono]sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status; sudo apt-get update; sudo apt-get dist-upgrade -y
```

I got```
[/FONT][/COLOR]Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                       
Hit http://dl.google.com stable/main amd64 Packages                           
Ign http://dl.google.com stable/main TranslationIndex                         
Hit http://archive.canonical.com raring Release.gpg                           
Hit http://ca.archive.ubuntu.com raring Release.gpg                           
Get:1 http://ca.archive.ubuntu.com raring-updates Release.gpg [933 B]         
Get:2 http://security.ubuntu.com raring-security Release.gpg [933 B]          
Hit http://extras.ubuntu.com raring Release.gpg                               
Hit http://archive.canonical.com raring Release                               
Hit http://ca.archive.ubuntu.com raring Release                               
Get:3 http://security.ubuntu.com raring-security Release [40.8 kB]            
Hit http://extras.ubuntu.com raring Release                                   
Ign http://dl.google.com stable/main Translation-en_CA                        
Hit http://archive.canonical.com raring/partner amd64 Packages                
Get:4 http://ca.archive.ubuntu.com raring-updates Release [40.8 kB]           
Ign http://dl.google.com stable/main Translation-en                           
Hit http://extras.ubuntu.com raring/main amd64 Packages                       
Ign http://archive.canonical.com raring/partner TranslationIndex              
Ign http://extras.ubuntu.com raring/main TranslationIndex                     
Get:5 http://security.ubuntu.com raring-security/main Sources [24.7 kB]       
Hit http://ca.archive.ubuntu.com raring/main Sources                          
Hit http://ca.archive.ubuntu.com raring/restricted Sources                    
Hit http://ca.archive.ubuntu.com raring/universe Sources                      
Hit http://ca.archive.ubuntu.com raring/multiverse Sources                    
Hit http://ca.archive.ubuntu.com raring/main amd64 Packages                   
Hit http://ca.archive.ubuntu.com raring/restricted amd64 Packages             
Hit http://ca.archive.ubuntu.com raring/universe amd64 Packages               
Hit http://ca.archive.ubuntu.com raring/multiverse amd64 Packages             
Hit http://ca.archive.ubuntu.com raring/main TranslationIndex                 
Hit http://ca.archive.ubuntu.com raring/multiverse TranslationIndex           
Hit http://ca.archive.ubuntu.com raring/restricted TranslationIndex           
Hit http://ca.archive.ubuntu.com raring/universe TranslationIndex             
Get:6 http://ca.archive.ubuntu.com raring-updates/main Sources [37.6 kB]      
Get:7 http://security.ubuntu.com raring-security/restricted Sources [14 B]    
Get:8 http://security.ubuntu.com raring-security/universe Sources [4,802 B]   
Get:9 http://security.ubuntu.com raring-security/multiverse Sources [690 B]   
Get:10 http://security.ubuntu.com raring-security/main amd64 Packages [68.2 kB]
Get:11 http://ca.archive.ubuntu.com raring-updates/restricted Sources [14 B]  
Get:12 http://ca.archive.ubuntu.com raring-updates/universe Sources [49.8 kB] 
Get:13 http://security.ubuntu.com raring-security/restricted amd64 Packages [14 B]
Get:14 http://security.ubuntu.com raring-security/universe amd64 Packages [18.5 kB]
Get:15 http://ca.archive.ubuntu.com raring-updates/multiverse Sources [690 B] 
Get:16 http://ca.archive.ubuntu.com raring-updates/main amd64 Packages [98.6 kB]
Get:17 http://security.ubuntu.com raring-security/multiverse amd64 Packages [1,143 B]
Hit http://security.ubuntu.com raring-security/main TranslationIndex          
Hit http://security.ubuntu.com raring-security/multiverse TranslationIndex    
Hit http://security.ubuntu.com raring-security/restricted TranslationIndex    
Hit http://security.ubuntu.com raring-security/universe TranslationIndex      
Hit http://security.ubuntu.com raring-security/main Translation-en            
Ign http://archive.canonical.com raring/partner Translation-en_CA             
Hit http://security.ubuntu.com raring-security/multiverse Translation-en      
Hit http://security.ubuntu.com raring-security/restricted Translation-en      
Get:18 http://ca.archive.ubuntu.com raring-updates/restricted amd64 Packages [14 B]
Get:19 http://ca.archive.ubuntu.com raring-updates/universe amd64 Packages [93.9 kB]
Ign http://archive.canonical.com raring/partner Translation-en                
Hit http://security.ubuntu.com raring-security/universe Translation-en        
Ign http://extras.ubuntu.com raring/main Translation-en_CA                    
Get:20 http://ca.archive.ubuntu.com raring-updates/multiverse amd64 Packages [1,143 B]
Hit http://ca.archive.ubuntu.com raring-updates/main TranslationIndex         
Hit http://ca.archive.ubuntu.com raring-updates/multiverse TranslationIndex   
Hit http://ca.archive.ubuntu.com raring-updates/restricted TranslationIndex
Hit http://ca.archive.ubuntu.com raring-updates/universe TranslationIndex
Hit http://ca.archive.ubuntu.com raring/main Translation-en_CA          
Hit http://ca.archive.ubuntu.com raring/main Translation-en             
Hit http://ca.archive.ubuntu.com raring/multiverse Translation-en       
Hit http://ca.archive.ubuntu.com raring/restricted Translation-en       
Ign http://extras.ubuntu.com raring/main Translation-en                 
Hit http://ca.archive.ubuntu.com raring/universe Translation-en_CA      
Hit http://ca.archive.ubuntu.com raring/universe Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/main Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/multiverse Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/restricted Translation-en
Hit http://ca.archive.ubuntu.com raring-updates/universe Translation-en
Fetched 483 kB in 2s (169 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 acroread : Depends: acroread-bin but it is not installable
 glib-networking : Depends: glib-networking-services (>= 2.32.1-1ubuntu2) but it is not installed
                   Depends: glib-networking-services (< 2.32.1-1ubuntu2.1~) but it is not installed
 gvfs : Depends: gvfs-daemons (>= 1.12.1-0ubuntu1.1) but it is not installed
        Depends: gvfs-daemons (< 1.12.1-0ubuntu1.1.1~) but it is not installed
 gvfs-backends : Depends: gvfs-daemons (= 1.12.1-0ubuntu1.1) but it is not installed
 libpoppler28 : Depends: libfontconfig1 (>= 2.9.0) but 2.8.0-3ubuntu9.1 is installed
 libsane : Depends: libsane-common (= 1.0.22-7ubuntu1) but it is not installed
 nspluginwrapper : Depends: nspluginviewer (= 1.4.4-0ubuntu4) but it is not installable
 skype : Depends: skype-bin but it is not installable
 texlive-base : Depends: texlive-doc-base (>= 2012.20120516) but 2009-2 is installed
                Depends: texlive-common (>= 2012.20120516) but 2009-15 is installed
                Depends: tex-common (>= 3) but 2.10 is installed
 texlive-binaries : Depends: libfontconfig1 (>= 2.9.0) but 2.8.0-3ubuntu9.1 is installed
                    Depends: texlive-common (>= 2011) but 2009-15 is installed
                    Depends: tex-common (>= 3) but 2.10 is installed
                    Recommends: ruby
 wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1) but it is not installable
E: Unmet dependencies. Try using -f.

```
Now I have the red warning icon showing Error: Brokencount>0 again. If I run apt-get I get this list of commands[CODE]apt 0.8.16~exp12ubuntu10.10 for amd64 compiled on Mar 13 2013 21:23:55
Usage: apt-get [options] command
       apt-get [options] install|remove pkg1 [pkg2 ...]
       apt-get [options] source pkg1 [pkg2 ...]


apt-get is a simple command line interface for downloading and
installing packages. The most frequently used commands are update
and install.


Commands:
   update - Retrieve new lists of packages
   upgrade - Perform an upgrade
   install - Install new packages (pkg is libc6 not libc6.deb)
   remove - Remove packages
   autoremove - Remove automatically all unused packages
   purge - Remove packages and config files
   source - Download source archives
   build-dep - Configure build-dependencies for source packages
   dist-upgrade - Distribution upgrade, see apt-get(8)
   dselect-upgrade - Follow dselect selections
   clean - Erase downloaded archive files
   autoclean - Erase old downloaded archive files
   check - Verify that there are no broken dependencies
   changelog - Download and display the changelog for the given package
   download - Download the binary package into the current directory


Options:
  -h  This help text.
  -q  Loggable output - no progress indicator
  -qq No output except for errors
  -d  Download only - do NOT install or unpack archives
  -s  No-act. Perform ordering simulation
  -y  Assume Yes to all queries and do not prompt
  -f  Attempt to correct a system with broken dependencies in place
  -m  Attempt to continue if archives are unlocatable
  -u  Show a list of upgraded packages as well
  -b  Build the source package after fetching it
  -V  Show verbose version numbers
  -c=? Read this configuration file
  -o=? Set an arbitrary configuration option, eg -o dir::cache=/tmp
See the apt-get(8), sources.list(5) and apt.conf(5) manual
pages for more information and options.
                       This APT has Super Cow Powers.
How can I type or use these commands?
Thank your for your help

---

### Post by fantab on 2013-06-20
> 
The following packages have unmet dependencies:  acroread : Depends: acroread-bin but it is not installable  glib-networking : Depends: glib-networking-services (>= 2.32.1-1ubuntu2) but it is not installed                    Depends: glib-networking-services (< 2.32.1-1ubuntu2.1~) but it is not installed  gvfs : Depends: gvfs-daemons (>= 1.12.1-0ubuntu1.1) but it is not installed         Depends: gvfs-daemons (< 1.12.1-0ubuntu1.1.1~) but it is not installed  gvfs-backends : Depends: gvfs-daemons (= 1.12.1-0ubuntu1.1) but it is not installed  libpoppler28 : Depends: libfontconfig1 (>= 2.9.0) but 2.8.0-3ubuntu9.1 is installed  libsane : Depends: libsane-common (= 1.0.22-7ubuntu1) but it is not installed  nspluginwrapper : Depends: nspluginviewer (= 1.4.4-0ubuntu4) but it is not installable  skype : Depends: skype-bin but it is not installable  texlive-base : Depends: texlive-doc-base (>= 2012.20120516) but 2009-2 is installed                 Depends: texlive-common (>= 2012.20120516) but 2009-15 is installed                 Depends: tex-common (>= 3) but 2.10 is installed  texlive-binaries : Depends: libfontconfig1 (>= 2.9.0) but 2.8.0-3ubuntu9.1 is installed                     Depends: texlive-common (>= 2011) but 2009-15 is installed                     Depends: tex-common (>= 3) but 2.10 is installed                     Recommends: ruby  wine1.4 : Depends: wine1.4-i386 (= 1.4-0ubuntu4.1) but it is not installable E: Unmet dependencies. Try using -f.
 
How did you install 'acroread' and 'skype'? You should install them from Ubuntu Repostitories, for which you have to enable 'PARTNER' Repository in Software Sources, using either **Synaptic** or **Software Center**.
The problem you have is related 32bit dependencies.

**Enable 'PARTNER' Repository**, if you haven't already and run 'sudo apt-get update, nevermind the errors.
Remove all the packages that apt-get reports as having 'Unmet Dependencies' (note down all the packages that you'll remove so you can instal them later) like this:

```
sudo dpkg --purge acroread glib-networking gvfs gvfs-backends libpoppler28 libsane nspluginwrapper skype texlive-base texlive-binaries wine1.4
sudo apt-get remove --purge acroread glib-networking gvfs gvfs-backends libpoppler28 libsane nspluginwrapper skype texlive-base texlive-binaries wine1.4
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get update
sudo apt-get -f install
sudo apt-get dist-upgrade
```
If there are any errors then post the output, if not:

```
sudo apt-get install acroread glib-networking gvfs gvfs-backends libpoppler28 libsane nspluginwrapper skype texlive-base texlive-binaries wine1.4
```

---

### Post by HiImTye on 2013-06-20
[CENTER][COLOR=#333333][FONT=Roboto][/FONT][/COLOR][/CENTER]
you just need to open the log file in a text editor (such as gedit)
you are getting dependency errors, make sure that your repositories are all enabled
[https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu#Adding_Repositories_in_Ubuntu)

---

### Post by ro12 on 2013-06-21
I can't find where to open partner repositories in Synaptic and when I try to open Software Sources I get a package repair window that cant repair whats wrong.
When I try to repair Broken Package in Synaptic i get this:
```
Extracting templates from packages: 100%Preconfiguring packages ...
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar':
 mixed non-coinstallable and coinstallable package instances present
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install.  Trying to recover:
dpkg: error: parsing file '/var/lib/dpkg/status' near line 27728 package 'rar':
 mixed non-coinstallable and coinstallable package instances present



```

---

### Post by fantab on 2013-06-22
In Synaptic you can enable/add repositories under Settings-> Repositories-> Other Software

---

### Post by ro12 on 2013-06-22
If I click Settings->>Repositories->  I don't get any options for other software

---


---
title: "Cannot Run Update Manager"
date: 2014-07-01
forum: New to Ubuntu
---

### Post by candra2 on 2014-07-01
Greetings, 

Am using Ubuntu 12.0.4 and cannot run my update manager. 

Here is error message I am getting when I try to run Update Manager:

```
Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

The following packages have unmet dependencies:

libjpeg-turbo8: Depends: libc6 (>= 2.14) but 2.15-0ubuntu10.5 is installed
libjpeg-turbo8:i386: Depends: libc6 (>= 2.7) but 2.15-0ubuntu10.5 is installed
```

I then followed the instruction above and exctuted the following as root: 

**apt-get install -f**

And here is the output:

```
:~$ sudo su
[sudo] password for c: 
root@c-Parallels-Ubuntu:/home/c# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb
  thunderbird-locale-en-us linux-headers-3.2.0-51 libqt4-designer:i386
  calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn
  libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386
  libgettextpo0:i386 thunderbird-globalmenu linux-headers-3.2.0-51-generic
  thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en
  libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjpeg-turbo8
The following packages will be upgraded:
  libjpeg-turbo8
1 upgraded, 0 newly installed, 0 to remove and 397 not upgraded.
2 not fully installed or removed.
Need to get 111 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main libjpeg-turbo8 amd64 1.1.90+svn733-0ubuntu4.3 [111 kB]
Fetched 111 kB in 0s (312 kB/s)    
dpkg: error processing libjpeg-turbo8 (--configure):
 libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 cannot be configured because libjpeg-turbo8:i386 is in a different version (1.1.90+svn733-0ubuntu4.3)
No apport report written because MaxReports is reached already
                                                              dpkg: error processing libjpeg-turbo8:i386 (--configure):
 libjpeg-turbo8:i386 1.1.90+svn733-0ubuntu4.3 cannot be configured because libjpeg-turbo8:amd64 is in a different version (1.1.90+svn733-0ubuntu4.1)
Errors were encountered while processing:
 libjpeg-turbo8
 libjpeg-turbo8:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Note: This is problem I had in the past - here is ther [thread]("http://ubuntuforums.org/showthread.php?t=2131760&p=12762386#post12762386") - but as I am not very experience I did not feel comfortable addressing this issue on my own.

Thanks for your help

candra

---

### Post by newb85 on 2014-07-01
Let's start with the initial suggestion.  What is the output of 
```
ls /etc/apt/sources.list.d
```

---

### Post by candra2 on 2014-07-01
here is the output

```
c# ls /etc/apt/sources.list.d
recoll-backports-recoll-1_15-on-precise.list
```

---

### Post by Bashing-om on 2014-07-01
candra2; -> newb85; Hey ,

I notice the difference in the versions of the currently installed library. - libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 -.

This is the correct version:
> 
Package libjpeg-turbo8

precise-updates (libs): IJG JPEG compliant runtime library. 
1.1.90+svn733-0ubuntu4.3: amd64 i386

Whereas; on your system:
> 

Fetched 111 kB in 0s (312 kB/s)    
dpkg: error processing libjpeg-turbo8 (--configure):
 libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 cannot be configured because libjpeg-turbo8:i386 is in a different version (1.1.90+svn733-0ubuntu4.3)
No apport report written because MaxReports is reached already
                                                              dpkg: error processing libjpeg-turbo8:i386 (--configure):
 libjpeg-turbo8:i386 1.1.90+svn733-0ubuntu4.3 cannot be configured because libjpeg-turbo8:amd64 is in a different version (1.1.90+svn733-0ubuntu4.1)
Errors were encountered while processing:
 libjpeg-turbo8
 libjpeg-turbo8:i386


Maybe we can remove the package and then (re-)install  and pick up the current version ?

[INDENT][INDENT]worth a shot
[/INDENT][/INDENT]

---

### Post by candra2 on 2014-07-01
Greetings Bashing-Om,

Kindly understand that I am not well-versed in this arena.

I need more specific, step-by-step instructions. 

Thank you for your help and support...

candra

---

### Post by Bashing-om on 2014-07-01
candra2; Hey,

We are all at some point in learning. Believe me I am no exception.

But to make the package manager happy, try this:
```

sudo apt-get remove libjpeg-turbo8

```

May have to also explicitly declare it as :i386.. we shall see.

When removed, see what the package manager thinks:
```

sudo apt-get -f install

```

And if that returns positive:
```

sudo apt-get install libjpeg-turbo8

``` depending on what the package manager relates.

[INDENT][INDENT]maybe yes 
[/INDENT][/INDENT]

---

### Post by candra2 on 2014-07-01
I did the first two steps and this is what came back:

```
c# sudo apt-get remove libjpeg-turbo8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8 : Depends: libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
root@c-Ubuntu:/home/c# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb
  thunderbird-locale-en-us linux-headers-3.2.0-51 libqt4-designer:i386
  calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn
  libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386
  libgettextpo0:i386 thunderbird-globalmenu linux-headers-3.2.0-51-generic
  thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en
  libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjpeg-turbo8
The following packages will be upgraded:
  libjpeg-turbo8
1 upgraded, 0 newly installed, 0 to remove and 397 not upgraded.
2 not fully installed or removed.
Need to get 0 B/111 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libjpeg-turbo8 (--configure):
 libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 cannot be configured because libjpeg-turbo8:i386 is in a different version (1.1.90+svn733-0ubuntu4.3)
No apport report written because MaxReports is reached already
                                                              dpkg: error processing libjpeg-turbo8:i386 (--configure):
 libjpeg-turbo8:i386 1.1.90+svn733-0ubuntu4.3 cannot be configured because libjpeg-turbo8:amd64 is in a different version (1.1.90+svn733-0ubuntu4.1)
Errors were encountered while processing:
 libjpeg-turbo8
 libjpeg-turbo8:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

I did not do step three because it did not seem like the second outcome was positive....

---

### Post by Bashing-om on 2014-07-02
candra2; Welp;

Let's see about:
```

sudo apt-get remove libjpeg-turbo8:i386

```

And now get an idea of what all depends on that 32 bit library:
```

sudo apt-get -f install

```

Depending on that output, is what we do next.

[INDENT][INDENT]If at 1st you do not succeed
[INDENT][INDENT][INDENT]try something else
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by candra2 on 2014-07-02
here is the first output

```
# sudo apt-get remove libjpeg-turbo8:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8:i386 : Depends: libjpeg-turbo8:i386 (>= 1.1.90+svn722-1ubuntu6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

and the second...

```
c# sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-locale-zh-cn libunistring0:i386 thunderbird-locale-en-gb thunderbird-locale-en-us linux-headers-3.2.0-51 libqt4-designer:i386 calligra-l10n-engb libgomp1:i386 libqt4-opengl:i386 calligra-l10n-zhcn libmp3lame0:i386 libcroco3:i386 libqt4-svg:i386 libvorbisenc2:i386
  libgettextpo0:i386 thunderbird-globalmenu linux-headers-3.2.0-51-generic thunderbird-locale-zh-hans libvorbis0a:i386 thunderbird-locale-en libogg0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libjpeg-turbo8
The following packages will be upgraded:
  libjpeg-turbo8
1 upgraded, 0 newly installed, 0 to remove and 397 not upgraded.
2 not fully installed or removed.
Need to get 0 B/111 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: error processing libjpeg-turbo8 (--configure):
 libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 cannot be configured because libjpeg-turbo8:i386 is in a different version (1.1.90+svn733-0ubuntu4.3)
No apport report written because MaxReports is reached already
                                                              dpkg: error processing libjpeg-turbo8:i386 (--configure):
 libjpeg-turbo8:i386 1.1.90+svn733-0ubuntu4.3 cannot be configured because libjpeg-turbo8:amd64 is in a different version (1.1.90+svn733-0ubuntu4.1)
Errors were encountered while processing:
 libjpeg-turbo8
 libjpeg-turbo8:i386
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by plucky on 2014-07-02
Try using dpkg ```
sudo dpkg -r libjpeg-turbo8
``` and see if that works.

Good Luck

---

### Post by candra2 on 2014-07-02
hi Plucky

here is the output

```
# sudo dpkg -r libjpeg-turbo8
dpkg: dependency problems prevent removal of libjpeg-turbo8:
 libjpeg8 depends on libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6).
dpkg: error processing libjpeg-turbo8 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libjpeg-turbo8

```

---

### Post by plucky on 2014-07-02
> dpkg: dependency problems prevent removal of libjpeg-turbo8:
 libjpeg8 depends on libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6).

Try removing libjpeg8 first ```
sudo dpkg -r libjpeg8
```

---

### Post by candra2 on 2014-07-02
hi plucky

first I did this

```
# sudo dpkg -r libjpeg8
dpkg: dependency problems prevent removal of libjpeg8:
 kde-runtime depends on libjpeg8 (>= 8c).
 libcupsimage2 depends on libjpeg8 (>= 8c).
 libreoffice-core depends on libjpeg8 (>= 8c).
 libpoppler19 depends on libjpeg8 (>= 8c).
 libdjvulibre21 depends on libjpeg8 (>= 8c).
 gstreamer0.10-plugins-good depends on libjpeg8 (>= 8c).
 libmjpegtools-1.9 depends on libjpeg8 (>= 8c).
 python-imaging depends on libjpeg8 (>= 8c).
 libgphoto2-2 depends on libjpeg8 (>= 8c).
 vino depends on libjpeg8 (>= 8c).
 openjdk-6-jre depends on libjpeg8 (>= 8c).
 libv4lconvert0 depends on libjpeg8 (>= 8c).
 openjdk-6-jre-headless depends on libjpeg8.
 libjasper1 depends on libjpeg8 (>= 8c).
 libkhtml5 depends on libjpeg8 (>= 8c).
 libmng1 depends on libjpeg8 (>= 8c).
 compiz-plugins-main depends on libjpeg8 (>= 8c).
 libvncserver0 depends on libjpeg8 (>= 8c).
 libgs9 depends on libjpeg8 (>= 8c).
 libtiff4 depends on libjpeg8 (>= 8c).
 simple-scan depends on libjpeg8 (>= 8c).
 libwmf0.2-7 depends on libjpeg8 (>= 8c).
 libzbar0 depends on libjpeg8 (>= 8c).
 tracker-extract depends on libjpeg8 (>= 8c).
 libcupsfilters1 depends on libjpeg8 (>= 8c).
 jpegoptim depends on libjpeg8 (>= 8c).
 libwebkitgtk-3.0-0 depends on libjpeg8 (>= 8c).
 libquicktime2 depends on libjpeg8 (>= 8c); however:
  Package libjpeg8 is to be removed.
 libgdk-pixbuf2.0-0 depends on libjpeg8 (>= 8c).
 printer-driver-hpcups depends on libjpeg8 (>= 8c).
 libqtgui4 depends on libjpeg8 (>= 8c).
 printer-driver-hpijs depends on libjpeg8 (>= 8c).
 libgd2-xpm depends on libjpeg8 (>= 8c).
 eog depends on libjpeg8 (>= 8c).
 libwxgtk2.8-0 depends on libjpeg8 (>= 8c).
 printer-driver-pxljr depends on libjpeg8 (>= 8c).
 libsane depends on libjpeg8 (>= 8c).
dpkg: error processing libjpeg8 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libjpeg8
```

and then redid this:

```
c# sudo dpkg -r libjpeg-turbo8
dpkg: dependency problems prevent removal of libjpeg-turbo8:
 libjpeg8 depends on libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6).
dpkg: error processing libjpeg-turbo8 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libjpeg-turbo8

```

---

### Post by plucky on 2014-07-02
> dpkg: error processing libjpeg-turbo8 (--configure):
 libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1 cannot be configured because libjpeg-turbo8:i386 is in a different version (1.1.90+svn733-0ubuntu4.3)

I am not sure why you have a lower version of  **libjpeg-turbo8:amd64 1.1.90+svn733-0ubuntu4.1** than that of the installed version **1.1.90+svn733-0ubuntu4.3**

Try running ```
 sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
``` to see if it corrects the discrepancy and downloads the latest version.

Do you have **Synaptic Package Manager** installed?

---

### Post by candra2 on 2014-07-02
here is the output and yes I have **Synaptic Package Manager **installed...

(by the way, had this problem in the past and I put a link to that issue in the first post of this thread - maybe that will give further insight, not sure if you saw it or not...)

```
# sudo apt-get clean
c# sudo apt-get update && sudo apt-get upgrade
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                     
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                                                                                                         
Hit http://us.archive.ubuntu.com precise Release                                                                                           
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                       
Hit http://us.archive.ubuntu.com precise-backports Release                                                                                             
Get:3 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                                  
Hit http://extras.ubuntu.com precise Release.gpg                                                                        
Hit http://us.archive.ubuntu.com precise/main Sources                                                                
Get:4 http://security.ubuntu.com precise-security Release [49.6 kB]                         
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
Hit http://extras.ubuntu.com precise Release                                                         
Hit http://ppa.launchpad.net precise Release.gpg                                                     
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages                                     
Hit http://us.archive.ubuntu.com precise/main TranslationIndex                                        
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex                                  
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex                                  
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex                                    
Get:5 http://us.archive.ubuntu.com precise-updates/main Sources [474 kB]                              
Hit http://ppa.launchpad.net precise Release                                                                  
Hit http://extras.ubuntu.com precise/main Sources                                                             
Hit http://ppa.launchpad.net precise/main Sources                            
Get:6 http://security.ubuntu.com precise-security/main Sources [106 kB]      
Hit http://extras.ubuntu.com precise/main amd64 Packages                                                    
Hit http://extras.ubuntu.com precise/main i386 Packages                                                     
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                  
Get:7 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]                             
Get:8 http://us.archive.ubuntu.com precise-updates/universe Sources [108 kB]                                                         
Hit http://ppa.launchpad.net precise/main amd64 Packages                                                                             
Hit http://ppa.launchpad.net precise/main i386 Packages                                                                            
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                         
Get:9 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,890 B]                                                    
Get:10 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [814 kB]                                                    
Get:11 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                                                     
Get:12 http://security.ubuntu.com precise-security/universe Sources [30.7 kB]                                                         
Get:13 http://security.ubuntu.com precise-security/multiverse Sources [1,795 B]                                                       
Get:14 http://security.ubuntu.com precise-security/main amd64 Packages [407 kB]                                 
Get:15 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]                                               
Get:16 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [244 kB]                                                 
Get:17 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]                                               
Get:18 http://us.archive.ubuntu.com precise-updates/main i386 Packages [846 kB]                                                           
Get:19 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]                                                    
Get:20 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [250 kB]                                                      
Ign http://extras.ubuntu.com precise/main Translation-en_US                                                                            
Get:21 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]                                                 
Get:22 http://us.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                     
Get:23 http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                      
Get:24 http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                      
Get:25 http://us.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                      
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
Ign http://extras.ubuntu.com precise/main Translation-en                                                                          
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en                                                        
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en                             
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en                               
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en                                 
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en                           
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en                           
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en                             
Ign http://ppa.launchpad.net precise/main Translation-en_US                                            
Ign http://ppa.launchpad.net precise/main Translation-en                         
Get:26 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]
Get:27 http://security.ubuntu.com precise-security/universe amd64 Packages [93.9 kB]
Get:28 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,434 B]
Get:29 http://security.ubuntu.com precise-security/main i386 Packages [433 kB]
Get:30 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]
Get:31 http://security.ubuntu.com precise-security/universe i386 Packages [99.1 kB]
Get:32 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,647 B]
Get:33 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]
Get:34 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:35 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:36 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Fetched 4,109 kB in 3s (1,227 kB/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.1) but 1.1.90+svn733-0ubuntu4.3 is installed
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4.3) but 1.1.90+svn733-0ubuntu4.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by plucky on 2014-07-02
I am running 12.04.4 X86_64 and my version of libjpeg-turbo8 is 1.1.90+svn733-0ubuntu4.3

Open Synaptic Package Manager and search for libjpeg-turbo8 and in the window that opens,see what versions you have available.

If it is installed from a PPA,it is worth removing the PPA and running the commands ```
sudo apt-get clean
sudo apt-get update && sudo apt-get upgrade
``` again.

If not from a PPA,it might be worth changing the Download server to "Main" to see if it corrects the problem.

Remember to change it back to your normal server afterwards so you get the fastest download.

Good Luck

---

### Post by candra2 on 2014-07-02
this is what comes up in Synaptic Package Manager when I do the search...

see attachment

---

### Post by plucky on 2014-07-02
Right click on libjpeg-turbo8 and go to **Properties** and the open the "Versions" tab.

---

### Post by candra2 on 2014-07-02
See attached

---

### Post by newb85 on 2014-07-03
Scanning through, I don't think you've tried this, yet:
```
sudo apt-get install --reinstall libjpeg-turbo8
```

---

### Post by candra2 on 2014-07-03
here is the outcome...

```
sudo apt-get install --reinstall libjpeg-turbo8
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by bapoumba on 2014-07-03
The lock message is because you are trying to run apt-get while synaptic of Software Updater is open. Only one package manager can run at a time. So close anything related to package management before running apt-get.

Now, it would be useful to see the current repositories you are using :
```
cat -n /etc/apt/sources.list
ls -l /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by candra2 on 2014-07-03
thanks bapoumba, & here is that outcome:

```
cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    20    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    22    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    
    42    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://security.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main
    60    
    61    # deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main
c# ls -l /etc/apt/sources.list.d
total 4
-rw-r--r-- 1 root root 166 Oct 15  2013 recoll-backports-recoll-1_15-on-precise.list
c# tail -v -n +1 /etc/apt/sources.list.d/*

```

---

### Post by bapoumba on 2014-07-04
Here is the current precise version : [http://packages.ubuntu.com/precise/libjpeg-turbo8](http://packages.ubuntu.com/precise/libjpeg-turbo8)

Please post the outputs to :
```
apt-cache policy libjpeg-turbo8
cat /etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list
```

---

### Post by candra2 on 2014-07-04
here is that outcome:

```
apt-cache policy libjpeg-turbo8
libjpeg-turbo8:
  Installed: 1.1.90+svn733-0ubuntu4.1
  Candidate: 1.1.90+svn733-0ubuntu4.3
  Version table:
     1.1.90+svn733-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 1.1.90+svn733-0ubuntu4.1 0
        100 /var/lib/dpkg/status
     1.1.90+svn733-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
root@c# cat /etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list
deb http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu precise main
deb-src http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu precise main

```

---

### Post by bapoumba on 2014-07-04
So libjpeg-turbo8 did not come from this ppa. Trying to see where it's coming from. What did you install from this ppa ?

---

### Post by candra2 on 2014-07-04
Thank you bapoumba for your support - please excuse me but I really have not idea what I installed from that ppa...

What I can offer is that my update manager broke once before and a link to that thread is embedded in my very first post of that thread. Perhaps that will give greater clues as to what the problem may be.

thanks, 
candra

---

### Post by bapoumba on 2014-07-04
OK, so you might as well remove it. Are you using any other ppa ? You did not paste the las command output of the 3 ones I gave you.
```
ls -a /etc/apt/sources.list.d/
```

The normal procedure should be using ppa-purge to completely remove a ppa and revert the packages that came from it to their regular ubuntu version. I suppose you do not have ppa-purge installed, have you (it is in the universe repositories) ?

If you do have ppa-purge installed, please run : 
```
sudo ppa-purge ppa:recoll-backports/recoll-1.15-on
sudo apt-get update
sudo apt-get upgrade
```

If you do not have ppa-purge installed, please run :
```
sudo mv /etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list ~/Desktop
```
This will move the ppa file to your Desktop, you can remove it later on.
```
sudo apt-get update
sudo apt-get upgrade
```
I think it will work because the file causing problems is at a lower version than the regular one. But I may be wrong :)

---

### Post by candra2 on 2014-07-04
Thanks - bapoumba - here is what has occurred - kindly let me know if I missed anything...

OK here is the first of your three earlier requests:

```
$ cat -n /etc/apt/sources.list
     1    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/main/binary-i386/
     2    
     3    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ dists/precise/restricted/binary-i386/
     4    # deb cdrom:[Ubuntu 12.04 LTS _Precise Pangolin_ - Release amd64 (20120423)]/ precise main restricted
     5    
     6    # See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
     7    # newer versions of the distribution.
     8    deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
     9    deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted
    10    
    11    ## Major bug fix updates produced after the final release of the
    12    ## distribution.
    13    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    14    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
    15    
    16    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
    17    ## team. Also, please note that software in universe WILL NOT receive any
    18    ## review or updates from the Ubuntu security team.
    19    deb http://us.archive.ubuntu.com/ubuntu/ precise universe
    20    deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
    21    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    22    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
    23    
    24    ## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
    25    ## team, and may not be under a free licence. Please satisfy yourself as to 
    26    ## your rights to use the software. Also, please note that software in 
    27    ## multiverse WILL NOT receive any review or updates from the Ubuntu
    28    ## security team.
    29    deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    30    deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
    31    deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    32    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
    33    
    34    ## N.B. software from this repository may not have been tested as
    35    ## extensively as that contained in the main release, although it includes
    36    ## newer versions of some applications which may provide useful features.
    37    ## Also, please note that software in backports WILL NOT receive any review
    38    ## or updates from the Ubuntu security team.
    39    deb http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    40    deb-src http://us.archive.ubuntu.com/ubuntu/ precise-backports main restricted universe multiverse
    41    
    42    deb http://security.ubuntu.com/ubuntu precise-security main restricted
    43    deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
    44    deb http://security.ubuntu.com/ubuntu precise-security universe
    45    deb-src http://security.ubuntu.com/ubuntu precise-security universe
    46    deb http://security.ubuntu.com/ubuntu precise-security multiverse
    47    deb-src http://security.ubuntu.com/ubuntu precise-security multiverse
    48    
    49    ## Uncomment the following two lines to add software from Canonical's
    50    ## 'partner' repository.
    51    ## This software is not part of Ubuntu, but is offered by Canonical and the
    52    ## respective vendors as a service to Ubuntu users.
    53    # deb http://archive.canonical.com/ubuntu precise partner
    54    # deb-src http://archive.canonical.com/ubuntu precise partner
    55    
    56    ## This software is not part of Ubuntu, but is offered by third-party
    57    ## developers who want to ship their latest software.
    58    deb http://extras.ubuntu.com/ubuntu precise main
    59    deb-src http://extras.ubuntu.com/ubuntu precise main
    60    
    61    # deb http://downloads.sourceforge.net/project/ubuntuzilla/mozilla/apt all main

```

here is the second:

```

:~$ ls -l /etc/apt/sources.list.d
total 0
```

here is the third:

```
:~$ tail -v -n +1 /etc/apt/sources.list.d/*
tail: cannot open `/etc/apt/sources.list.d/*' for reading: No such file or directory

```

then I did this...

```

~$ ls -a /etc/apt/sources.list.d/
.  ..


```

and tried to install ppa purge

```

$ sudo mv /etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list ~/Desktop
[sudo] password for c: 
mv: cannot stat `/etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list': No such file or directory

```

---

### Post by bapoumba on 2014-07-04
Well, you removed the ppa.
What is the output to 
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by candra2 on 2014-07-04
here is the first outcome

```
$ sudo apt-get update
[sudo] password for c: 
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release.gpg       
Get:1 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://us.archive.ubuntu.com precise-backports Release.gpg                         
Hit http://security.ubuntu.com precise-security Release    
Hit http://us.archive.ubuntu.com precise Release           
Get:2 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://us.archive.ubuntu.com precise-backports Release                                  
Hit http://security.ubuntu.com precise-security/main Sources                                       
Hit http://us.archive.ubuntu.com precise/main Sources                                          
Get:3 http://extras.ubuntu.com precise Release.gpg [72 B]                                    
Hit http://security.ubuntu.com precise-security/restricted Sources                           
Hit http://security.ubuntu.com precise-security/universe Sources      
Hit http://security.ubuntu.com precise-security/multiverse Sources    
Hit http://security.ubuntu.com precise-security/main amd64 Packages   
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise/restricted Sources           
Hit http://us.archive.ubuntu.com precise/universe Sources             
Hit http://us.archive.ubuntu.com precise/multiverse Sources           
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages    
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://us.archive.ubuntu.com precise/main amd64 Packages          
Hit http://us.archive.ubuntu.com precise/restricted amd64 Packages    
Hit http://us.archive.ubuntu.com precise/universe amd64 Packages      
Hit http://us.archive.ubuntu.com precise/multiverse amd64 Packages    
Hit http://us.archive.ubuntu.com precise/main i386 Packages           
Hit http://us.archive.ubuntu.com precise/restricted i386 Packages     
Hit http://us.archive.ubuntu.com precise/universe i386 Packages       
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages     
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex 
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise/main TranslationIndex        
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Get:4 http://us.archive.ubuntu.com precise-updates/main Sources [473 kB]
Hit http://extras.ubuntu.com precise Release    
Hit http://security.ubuntu.com precise-security/main Translation-en            
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://security.ubuntu.com precise-security/universe Translation-en
Hit http://extras.ubuntu.com precise/main Sources      
Hit http://extras.ubuntu.com precise/main amd64 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Get:5 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]
Get:6 http://us.archive.ubuntu.com precise-updates/universe Sources [108 kB]
Get:7 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,890 B]
Get:8 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [814 kB]
Get:9 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:10 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [244 kB]
Ign http://extras.ubuntu.com precise/main Translation-en_US                     
Ign http://extras.ubuntu.com precise/main Translation-en                        
Get:11 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:12 http://us.archive.ubuntu.com precise-updates/main i386 Packages [846 kB]
Get:13 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:14 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [250 kB]
Get:15 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
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
Fetched 2,859 kB in 3s (746 kB/s)
Reading package lists... Done
```

here is the second...

```
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.1) but 1.1.90+svn733-0ubuntu4.3 is installed
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4.3) but 1.1.90+svn733-0ubuntu4.1 is installed
E: Unmet dependencies. Try using -f.

```

---

### Post by bapoumba on 2014-07-07
> **candra2 said:**
> here is that outcome:

```
apt-cache policy libjpeg-turbo8
libjpeg-turbo8:
  Installed: 1.1.90+svn733-0ubuntu4.1
  Candidate: 1.1.90+svn733-0ubuntu4.3
  Version table:
     1.1.90+svn733-0ubuntu4.3 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu/ precise-security/main amd64 Packages
 *** 1.1.90+svn733-0ubuntu4.1 0
        100 /var/lib/dpkg/status
     1.1.90+svn733-0ubuntu4 0
        500 http://us.archive.ubuntu.com/ubuntu/ precise/main amd64 Packages
root@c# cat /etc/apt/sources.list.d/recoll-backports-recoll-1_15-on-precise.list
deb http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu precise main
deb-src http://ppa.launchpad.net/recoll-backports/recoll-1.15-on/ubuntu precise main

```

Going back to this previous output : have you been pinning version 1.1.90+svn733-0ubuntu4.1 0 ? Apt sees version 1.1.90+svn733-0ubuntu4.3 0 which is the current precise one, it has a higher priority so it should install it, but for some reason it does not.
Other explanation : you have another package that installed it as a dependency. Do you remember what you installed that required libjpeg-turbo8 at a lower version from the official repos ?

---

### Post by candra2 on 2014-07-07
As far as I know, I have not been doing anything out of the ordinary like pinning and I am not sure of any install that would have required "libjpeg-turbo8 at a lower version from the official repos."

I just let Update Manager run its updates accordingly - I do not do any other installs.

Last year around this time you fixed this type problem - are the two incidents related? 

Wish I could be more helpful in my replies.

respectfully, 
candra

---

### Post by newb85 on 2014-07-07
You can get a much more definitive answer to what you've installed that depends on the package by running

```
 apt-cache showpkg --installed libjpeg-turbo8 
```

---

### Post by candra2 on 2014-07-07
thanks - here is that output:

```
$  apt-cache showpkg --installed libjpeg-turbo8
Package: libjpeg-turbo8
Versions: 
1.1.90+svn733-0ubuntu4.3 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages) (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: e73784921dcb74ecc93efca2d0dbf06a
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: e73784921dcb74ecc93efca2d0dbf06a

1.1.90+svn733-0ubuntu4.1 (/var/lib/dpkg/status)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: e73784921dcb74ecc93efca2d0dbf06a
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: e73784921dcb74ecc93efca2d0dbf06a

1.1.90+svn733-0ubuntu4 (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages)
 Description Language: 
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages
                  MD5: e73784921dcb74ecc93efca2d0dbf06a
 Description Language: en
                 File: /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en
                  MD5: e73784921dcb74ecc93efca2d0dbf06a


Reverse Depends: 
  libturbojpeg:i386,libjpeg-turbo8 1.1.90+svn722-1ubuntu6
  libjpeg-turbo8:i386,libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3
  libjpeg-turbo8:i386,libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3
  libturbojpeg,libjpeg-turbo8 1.1.90+svn722-1ubuntu6
  libjpeg-turbo8-dev,libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3
  libjpeg-turbo8-dbg,libjpeg-turbo8 1.1.90+svn733-0ubuntu4.3
  libturbojpeg:i386,libjpeg-turbo8 1.1.90+svn722-1ubuntu6
  libjpeg-turbo8:i386,libjpeg-turbo8 1.1.90+svn733-0ubuntu4
  libjpeg-turbo8:i386,libjpeg-turbo8 1.1.90+svn733-0ubuntu4
  libturbojpeg,libjpeg-turbo8 1.1.90+svn722-1ubuntu6
  libjpeg8,libjpeg-turbo8 1.1.90+svn722-1ubuntu6
  libjpeg-turbo8-dev,libjpeg-turbo8 1.1.90+svn733-0ubuntu4
  libjpeg-turbo8-dbg,libjpeg-turbo8 1.1.90+svn733-0ubuntu4
Dependencies: 
1.1.90+svn733-0ubuntu4.3 - libc6 (2 2.14) multiarch-support (0 (null)) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg-turbo8:i386 (3 1.1.90+svn733-0ubuntu4.3) libjpeg-turbo8:i386 (6 1.1.90+svn733-0ubuntu4.3) 
1.1.90+svn733-0ubuntu4.1 - libc6 (2 2.14) multiarch-support (0 (null)) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg-turbo8:i386 (3 1.1.90+svn733-0ubuntu4.1) libjpeg-turbo8:i386 (6 1.1.90+svn733-0ubuntu4.1) 
1.1.90+svn733-0ubuntu4 - libc6 (2 2.7) multiarch-support (0 (null)) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg8 (3 8c-2ubuntu5) libjpeg8:i386 (3 8c-2ubuntu5) libjpeg-turbo8:i386 (3 1.1.90+svn733-0ubuntu4) libjpeg-turbo8:i386 (6 1.1.90+svn733-0ubuntu4) 
Provides: 
1.1.90+svn733-0ubuntu4.3 - 
1.1.90+svn733-0ubuntu4.1 - 
1.1.90+svn733-0ubuntu4 - 
Reverse Provides: 
```

---

### Post by bapoumba on 2014-07-07
From your previous thread, you has problems with :i386 libs on a 64-bits architecture. Are you still running on a 64-bit Ubuntu release ?

If so, I'd try :
```
sudo apt-get purge libturbojpeg:i386
```
If that fails
```
sudo dpkg --purge --force-depends libturbojpeg:i386
```
and see if there are any errors to the following commands after removing the :i386 lib :
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by candra2 on 2014-07-07
yes, I am running a 64-bit Ubuntu release...

here is the first output

```
$ sudo apt-get purge libturbojpeg:i386
[sudo] password for c: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libturbojpeg:i386 is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.1) but 1.1.90+svn733-0ubuntu4.3 is to be installed
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4.3) but 1.1.90+svn733-0ubuntu4.1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

here is the second output

```
$ sudo dpkg --purge --force-depends libturbojpeg:i386
dpkg: warning: there's no installed package matching libturbojpeg:i386

```

and here is the third one...

```
$ sudo dpkg --purge --force-depends libturbojpeg:i386
dpkg: warning: there's no installed package matching libturbojpeg:i386
krpa@krpa-Parallels-Ubuntu:~$ sudo apt-get update
Hit http://us.archive.ubuntu.com precise Release.gpg
Hit http://us.archive.ubuntu.com precise-updates Release.gpg
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://us.archive.ubuntu.com precise Release                           
Hit http://us.archive.ubuntu.com precise-updates Release                   
Hit http://us.archive.ubuntu.com precise-backports Release                                                              
Hit http://security.ubuntu.com precise-security Release                                                                 
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
Get:1 http://extras.ubuntu.com precise Release.gpg [72 B]            
Hit http://us.archive.ubuntu.com precise/universe i386 Packages      
Hit http://us.archive.ubuntu.com precise/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise/main TranslationIndex
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex
Hit http://security.ubuntu.com precise-security/main Sources
Hit http://us.archive.ubuntu.com precise-updates/main Sources
Hit http://us.archive.ubuntu.com precise-updates/restricted Sources
Hit http://us.archive.ubuntu.com precise-updates/universe Sources    
Hit http://us.archive.ubuntu.com precise-updates/multiverse Sources  
Hit http://us.archive.ubuntu.com precise-updates/main amd64 Packages 
Hit http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages
Hit http://us.archive.ubuntu.com precise-updates/main i386 Packages  
Hit http://us.archive.ubuntu.com precise-updates/restricted i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/universe i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages
Hit http://us.archive.ubuntu.com precise-updates/main TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/restricted TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-backports/main Sources      
Hit http://extras.ubuntu.com precise Release                         
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
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
Hit http://us.archive.ubuntu.com precise-updates/multiverse Translation-en
Hit http://extras.ubuntu.com precise/main Sources                    
Hit http://us.archive.ubuntu.com precise-updates/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-updates/universe Translation-en
Hit http://us.archive.ubuntu.com precise-backports/main Translation-en
Hit http://us.archive.ubuntu.com precise-backports/multiverse Translation-en
Hit http://us.archive.ubuntu.com precise-backports/restricted Translation-en
Hit http://us.archive.ubuntu.com precise-backports/universe Translation-en
Hit http://security.ubuntu.com precise-security/main Translation-en  
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://extras.ubuntu.com precise/main amd64 Packages
Hit http://extras.ubuntu.com precise/main i386 Packages
Ign http://extras.ubuntu.com precise/main TranslationIndex
Hit http://security.ubuntu.com precise-security/universe Translation-en
Ign http://extras.ubuntu.com precise/main Translation-en_US
Ign http://extras.ubuntu.com precise/main Translation-en
Fetched 72 B in 1s (37 B/s)
Reading package lists... Done

```

and here is the 4th output:

```
~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libjpeg-turbo8 : Breaks: libjpeg-turbo8:i386 (!= 1.1.90+svn733-0ubuntu4.1) but 1.1.90+svn733-0ubuntu4.3 is installed
 libjpeg-turbo8:i386 : Breaks: libjpeg-turbo8 (!= 1.1.90+svn733-0ubuntu4.3) but 1.1.90+svn733-0ubuntu4.1 is installed
E: Unmet dependencies. Try using -f.
```

---

### Post by bapoumba on 2014-07-08
Please try 
```
sudo apt-get purge libjpeg-turbo8
```
or 
```
sudo dpkg --purge --force-depends libjpeg-turbo8
```
if the first one does not work. No idea if it would break some apps up.

---

### Post by candra2 on 2014-07-08
> if the first one does not work. No idea if it would break some apps up.

Before moving ahead let me clarify. You gave me two commands. Is it the first command that might adversely affect my apps or the second. 

If the first command is deemed safe I will try it right away. 

Kindly let me know - thanks!

---

### Post by bapoumba on 2014-07-09
Well, what I mean is that libjpeg-turbo8 may be needed by other applications and these might not be working after you remove it. Most important is to end up with a working dependency tree, an app can always be reinstalled. If the dependency tree is clean, reinstalling should bring in the correct versions.

---

### Post by candra2 on 2014-07-09
here is the first outcome:

```
 sudo apt-get purge libjpeg-turbo8
[sudo] password for c: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8 : Depends: libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

here is the second outcome:


```
:~$ sudo dpkg --purge --force-depends libjpeg-turbo8
dpkg: libjpeg-turbo8: dependency problems, but removing anyway as you requested:
 libjpeg8 depends on libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6).
(Reading database ... 866856 files and directories currently installed.)
Removing libjpeg-turbo8 ...
Purging configuration files for libjpeg-turbo8 ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

```

---

### Post by candra2 on 2014-07-09
In follow-up I seem to have lost all my desktop wallpaper - just superficial presentation.

All programs and info are fine...

Will inform of any other things I notice.

(note: please be sure to see above outcomes in previous reply...)

Addendum: Also my image viewer (for opening an viewing photos) have been disabled. I suppose first update manager will have to be repaired before this can be re-loaded.

---

### Post by bapoumba on 2014-07-10
Please ```
run sudo apt-get update
sudo apt-get upgrade
```
And please reinstall your desktop metapackage
```
sudo apt-get install --reintall ubuntu-desktop
```
if you are running ubuntu with unity, use kubuntu-desktop, xubuntu-desktop or lubuntu-desktop depending on the flavor you are running.

---

### Post by candra2 on 2014-07-10
here it first output

```
$ run sudo apt-get update
No command 'run' found, did you mean:
 Command 'zrun' from package 'moreutils' (universe)
 Command 'runq' from package 'exim4-daemon-heavy' (main)
 Command 'runq' from package 'exim4-daemon-light' (main)
 Command 'runq' from package 'sendmail-bin' (universe)
 Command 'grun' from package 'grun' (universe)
 Command 'qrun' from package 'torque-client' (universe)
 Command 'qrun' from package 'torque-client-x11' (universe)
 Command 'lrun' from package 'lustre-utils' (universe)
 Command 'rn' from package 'trn' (multiverse)
 Command 'rn' from package 'trn4' (multiverse)
 Command 'rup' from package 'rstat-client' (universe)
 Command 'srun' from package 'slurm-llnl' (universe)
run: command not found

```

here is the second:

```
 sudo apt-get upgrade
[sudo] password for c: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 libjpeg8 : Depends: libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6) but it is not installed
E: Unmet dependencies. Try using -f.
```

here is the third

```
~$ sudo apt-get install --reintall ubuntu-desktop
E: Command line option --reintall is not understood


```

---

### Post by oldos2er on 2014-07-10
You can leave out "run" from the first command, should be ```
sudo apt-get update
``` The second command has a typo, try ```

sudo apt-get install --reinstall ubuntu-desktop
```

---

### Post by candra2 on 2014-07-10
thanks Ann...

here is that first output

```
$ sudo apt-get update
[sudo] password for c: 
Hit http://us.archive.ubuntu.com precise Release.gpg
Get:1 http://security.ubuntu.com precise-security Release.gpg [198 B]
Get:2 http://us.archive.ubuntu.com precise-updates Release.gpg [198 B]                 
Hit http://us.archive.ubuntu.com precise-backports Release.gpg
Get:3 http://security.ubuntu.com precise-security Release [49.6 kB]
Hit http://us.archive.ubuntu.com precise Release                                                     
Get:4 http://us.archive.ubuntu.com precise-updates Release [49.6 kB]                                                              
Hit http://us.archive.ubuntu.com precise-backports Release                                                                                  
Hit http://us.archive.ubuntu.com precise/main Sources                                                                                       
Get:5 http://extras.ubuntu.com precise Release.gpg [72 B]
Get:6 http://security.ubuntu.com precise-security/main Sources [106 kB]
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
Hit http://us.archive.ubuntu.com precise/multiverse TranslationIndex          
Hit http://us.archive.ubuntu.com precise/restricted TranslationIndex          
Hit http://us.archive.ubuntu.com precise/universe TranslationIndex            
Get:7 http://us.archive.ubuntu.com precise-updates/main Sources [473 kB]      
Hit http://extras.ubuntu.com precise Release                                           
Get:8 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]                      
Get:9 http://security.ubuntu.com precise-security/universe Sources [30.7 kB]                                 
Get:10 http://security.ubuntu.com precise-security/multiverse Sources [1,795 B]                              
Get:11 http://security.ubuntu.com precise-security/main amd64 Packages [407 kB]                              
Hit http://extras.ubuntu.com precise/main Sources                                                              
Hit http://extras.ubuntu.com precise/main amd64 Packages                                
Hit http://extras.ubuntu.com precise/main i386 Packages                                
Ign http://extras.ubuntu.com precise/main TranslationIndex                             
Get:12 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B] 
Get:13 http://security.ubuntu.com precise-security/universe amd64 Packages [93.8 kB]                        
Get:14 http://us.archive.ubuntu.com precise-updates/restricted Sources [8,056 B]                              
Get:15 http://us.archive.ubuntu.com precise-updates/universe Sources [108 kB]                                       
Get:16 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,442 B]                            
Get:17 http://security.ubuntu.com precise-security/main i386 Packages [433 kB]                                    
Get:18 http://us.archive.ubuntu.com precise-updates/multiverse Sources [8,905 B]                                 
Get:19 http://us.archive.ubuntu.com precise-updates/main amd64 Packages [814 kB]                                 
Get:20 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]                             
Get:21 http://security.ubuntu.com precise-security/universe i386 Packages [99.1 kB]                              
Get:22 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,650 B]                            
Hit http://security.ubuntu.com precise-security/main TranslationIndex                                            
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex                                      
Hit http://security.ubuntu.com precise-security/universe TranslationIndex                                        
Hit http://security.ubuntu.com precise-security/main Translation-en                                              
Hit http://security.ubuntu.com precise-security/multiverse Translation-en      
Hit http://security.ubuntu.com precise-security/restricted Translation-en      
Hit http://security.ubuntu.com precise-security/universe Translation-en        
Get:23 http://us.archive.ubuntu.com precise-updates/restricted amd64 Packages [13.7 kB]
Get:24 http://us.archive.ubuntu.com precise-updates/universe amd64 Packages [244 kB]
Get:25 http://us.archive.ubuntu.com precise-updates/multiverse amd64 Packages [15.3 kB]
Get:26 http://us.archive.ubuntu.com precise-updates/main i386 Packages [846 kB]    
Ign http://extras.ubuntu.com precise/main Translation-en_US                        
Ign http://extras.ubuntu.com precise/main Translation-en                         
Get:27 http://us.archive.ubuntu.com precise-updates/restricted i386 Packages [13.7 kB]
Get:28 http://us.archive.ubuntu.com precise-updates/universe i386 Packages [250 kB]
Get:29 http://us.archive.ubuntu.com precise-updates/multiverse i386 Packages [15.5 kB]
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
Fetched 4,096 kB in 2s (1,395 kB/s)               
Reading package lists... Done

```

here is the second:

```
sudo apt-get install --reinstall ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 libjpeg8 : Depends: libjpeg-turbo8 (>= 1.1.90+svn722-1ubuntu6) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

---

### Post by bapoumba on 2014-07-10
Sorry for the typos and thanks oldos2er for pointing them out :)

Not sure how this is going to come out, as these libs are dependencies of many other applications.
```
sudo dpkg --purge --force-depends libjpeg8
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
```
If the last command fails again, please run the following and see if it would go through this time :
```
sudo apt-get -f install
```

---

### Post by candra2 on 2014-07-10
> Not sure how this is going to come out, as these libs are dependencies of many other applications.

Already, I am finding more and more of my apps are not working (image viewer, simple scan, libre office etc) - I am not sure I am ready to go in deeper, unless you feel that this is all going towards fixing the initial single problem of fixing the update manager and will in course resolve all my apps that I have suddenly lost...

Thank you for your understanding.

I suppose at this point I have to move forward - things certainly cannot remain as is - I was just not thinking things would go this direction as I need this computer to run my daily office etc.

---

### Post by bapoumba on 2014-07-10
Apps can be reinstalled as soon as ubuntu-desktop can be.
Not knowing which package you installed (and from where you installed it) that got these libs to conflicting versions, it is going to be trials and errors to get the dependency tree coherent again. If we could root the cause of these discrepancies, at least we could force remove that and build/reinstall from the ubuntu repositories again.
For info, you can run :
```
apt-cache rdepends libjpeg8
```
This will tell you all the packages libjpeg8 is a dependency of. May be that would ring a bell ?

ppa and third party repos are great to get packages that are not in the ubuntu repositories. Dependency problems is sometimes the price to pay.

---

### Post by candra2 on 2014-07-10
> ppa and third party repos are great to get packages that are not in the  ubuntu repositories. Dependency problems is sometimes the price to pay.

As far as I know I never do this - only I do suggested updates via the Update Manager...

---

### Post by candra2 on 2014-07-10
here is that output - it looks like a lot of apps:

```
$ apt-cache rdepends libjpeg8
libjpeg8
Reverse Depends:
  libcupsimage2
  libreoffice-core
  openjdk-6-jre
  openjdk-6-jre-headless
  libtiff4
  simple-scan
  libcupsfilters1
  printer-driver-hpcups
  printer-driver-hpijs
  emacs23-lucid
  vino
  libreoffice-filter-binfilter
  libreoffice-core
  libqtgui4
  libkhtml5
  libcupsimage2
  emacs23
  supertuxkart
  amsn
  0ad
  printer-driver-hpijs
  printer-driver-hpcups
  libjpeg-turbo8:i386
  libjpeg-turbo8:i386
  wine1.4-amd64
  python-mapscript
  php5-mapscript
  photoprint
  paraview
  openjdk-7-jre-headless
  openjdk-7-jre
  mplayer2
  mapserver-bin
  libmapscript-ruby1.9.1
  libmapscript-ruby1.8
  libmapscript-perl
  liblcms2-utils
  libinventor0
  gnash-common
  emacs23-lucid
  cgi-mapserver
  vino
  simple-scan
  python-imaging-dbg
  python-imaging
  printer-driver-hpijs
  printer-driver-hpcups
  openjdk-6-jre-headless
  openjdk-6-jre
  okular
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libv4lconvert0
  libtiff4
  libreoffice-filter-binfilter
  libreoffice-core
  libqtgui4
  libpoppler19
  libmagickcore4
  libkhtml5
  libjpeg-turbo8
  libjpeg-turbo8
  libjpeg-turbo-progs
  libgs9
  libgphoto2-2
  libgdk-pixbuf2.0-0
  libdjvulibre21
  libcupsimage2
  libcupsfilters1
  krita
  krfb
  kde-workspace-bin
  kde-runtime
  gwenview
  gstreamer0.10-plugins-good
  gimp
  eog
  emacs23
  compiz-plugins-main
  libjpeg8:i386
  libjpeg8:i386
  libjpeg-turbo8:i386
  libjpeg-turbo8:i386
  vice
  transcode
  lugaru
  amoeba
  alien-arena
  zoneminder
  ziproxy
  zgv
  zapping
  yorick-z
  yafaray
  xtightvncviewer
  xtel
  xsystem35
  xscreensaver-screensaver-webcollage
  xsane
  xracer
  xmoto
  xloadimage
  xli
  xjig
  xineliboutput-sxfe
  xineliboutput-fbfe
  xfig
  xemacs21-nomule
  xemacs21-mule-canna-wnn
  xemacs21-mule
  xbmc-bin
  xawtv-plugins
  xawtv
  wings3d
  wine1.4-amd64
  whitedune
  weston
  webp
  webcam
  vncsnapshot
  vgrabbj
  vdr-dbg
  vdr
  uvccapture
  ufraw-batch
  ufraw
  tuxpuck
  tumbler
  ttv
  tracker-extract
  tightvncserver
  therion-viewer
  testdisk
  swi-prolog-x
  sunclock
  streamer
  steghide
  ssvnc
  spice-client
  spamprobe
  slim
  simgear2.4.0
  shoes
  sfftobmp
  sdop
  scorched3d
  scantv
  scantailor
  robot-player
  rlvm
  rawtherapee
  r-base-core
  qlandkartegt
  python-pygame
  python-mapscript
  python-exactimage
  pslib1
  pike7.8-image
  pia
  php5-mapscript
  php5-exactimage
  photoprint
  perl-tk
  performous
  pekwm
  paraview
  openuniverse
  openjdk-7-jre-headless
  openjdk-7-jre
  open-font-design-toolkit
  onscripter
  neverputt
  neverball
  netsurf-gtk
  netgen
  mupdf-tools
  mupdf
  mtpaint
  mrxvt
  mplayer2
  mplayer-gui
  mplayer
  mjpegtools
  minidlna
  metapixel
  mencoder
  megaglest
  mapserver-bin
  mandelbulber
  links2
  lightspark-common
  libzbar0
  libxineliboutput-sxfe
  libxineliboutput-fbfe
  libxcomp3
  libwxgtk2.8-dbg
  libwxgtk2.8-0
  libwxgtk2.6-0
  libwraster3
  libvxl1.14
  libvtk5.8
  libvips15
  libtk-img
  libthunar-vfs-1-2
  libterralib
  libspice-server1
  libspice-client-glib-2.0-1
  libsimage20
  libsilly
  libsfml-graphics1.6
  libsdl-image1.2
  librasterlite1
  libquicktime2
  libprima-perl
  libpodofo0.9.0
  libplayerjpeg3.0
  libphash0
  libpano13-2
  libossim1
  libopenslide0
  libopenscenegraph80
  libopenraw1
  libopencv-highgui2.3
  libomxil-components
  libnvtt2
  libmrpt-dbg
  libmrpt-base0.9
  libmjpegtools-1.9
  libmgl5
  libmatchbox1
  libmapscript-ruby1.9.1
  libmapscript-ruby1.8
  libmapscript-perl
  libmapnik2-2.0
  libleptonica
  liblcms2-utils
  liblcms-utils
  libiulib0
  libitalc
  libirrlicht1.7a
  libinventor0
  libimager-perl
  libhdf4-0-alt
  libhdf4-0
  libgxps2
  libgxps-utils
  libgraphicsmagick3
  libgpac1
  libgnustep-gui0.20
  libgdal1-1.7.0
  libfreeimage3
  libfox-1.6-0
  libforms2
  libfltk-images1.3
  libffmpegthumbnailer4
  libexactimage-perl
  libevas1
  libeet1
  libdirectfb-extra
  libdevil1c2
  libclaw-graphic1
  libclanapp-1.0
  libavifile-0.7c2
  libafterimage0
  libabiword-2.9
  knews
  kipi-plugins
  kdc2tiff
  k3d
  jpegpixi
  jpegoptim
  jpegjudge
  jpeginfo
  jp2a
  jigzo
  italc-client
  ioquake3
  imview
  imaptool
  imagevis3d
  hugin-tools
  hp2xx
  gthumb
  grace
  gpicview
  gphoto2
  gnash-common
  gmsh
  gmic
  gmerlin-plugins-base
  gimp-ufraw
  gimp-gap
  gargoyle-free
  flphoto
  flam3
  fim
  fbtv
  fbi
  exrtools
  exiftran
  exactimage
  enfuse
  enblend
  emacs23-lucid
  edisplay
  dvgrab
  dvdstyler
  driftnet
  directvnc
  dillo
  digikam
  dcraw
  dcmtk
  darnwdl
  darktable
  darkroom
  darkplaces-server
  darkplaces
  ctwm
  chimera2
  cgi-mapserver
  celestia-gnome
  celestia-glut
  blender
  abiword
  aaphoto
  0ad
  xplanet
  vino
  simple-scan
  scribus
  python-imaging-dbg
  python-imaging
  printer-driver-pxljr
  printer-driver-hpijs
  printer-driver-hpcups
  openjdk-6-jre-headless
  openjdk-6-jre
  okular
  netpbm
  libwmf0.2-7
  libwebkitgtk-3.0-0
  libwebkitgtk-1.0-0
  libvncserver0
  libvigraimpex3
  libv4lconvert0
  libtiff4
  libsane
  libreoffice-filter-binfilter
  libreoffice-core
  libqtgui4
  libqt3-mt
  libpoppler19
  libmng1
  libmagickcore4
  libkhtml5
  libjpeg8-dev
  libjpeg8-dbg
  libjpeg-turbo8
  libjpeg-turbo8
  libjpeg-turbo-progs
  libjasper1
  libimlib2
  libgs9
  libgphoto2-2
  libgegl-0.0-0
  libgdk-pixbuf2.0-0
  libgdiplus
  libgd2-xpm
  libgd2-noxpm
  libfontforge1
  libfltk1.1
  libdjvulibre21
  libcupsimage2
  libcupsfilters1
  krita
  krfb
  kde-workspace-bin
  kde-runtime
  gwenview
  gstreamer0.10-plugins-good
  gimp
  eog
  emacs23
  compiz-plugins-main

```

---

### Post by bapoumba on 2014-07-10
> **candra2 said:**
> As far as I know I never do this - only I do suggested updates via the Update Manager...
[http://ubuntuforums.org/showthread.php?t=2232392&p=13065246#post13065246](http://ubuntuforums.org/showthread.php?t=2232392&p=13065246#post13065246) < you did have one ppa enabled.
And yes, these libs are dependencies of a lot of other packages.

---

### Post by candra2 on 2014-07-10
Ok - so is this still my next move???

```
sudo dpkg --purge --force-depends libjpeg8
sudo apt-get update
sudo apt-get install --reinstall ubuntu-desktop
```

What I really cannot afford to lose are my Text Edit (Gedit) and my Thunderbird email application

---

### Post by bapoumba on 2014-07-10
Other than back up all your important files, all the ones you cannot afford to loose, yes, that is what I would do. Do you have a cd or usb drive you can boot from in case you need to reinstall ?

---

### Post by candra2 on 2014-07-10
I will get my back-ups in place....

---

### Post by newb85 on 2014-07-11
Even if it does uninstall gedit or thunderbird, the --reinstall ubuntu-desktop line will put them back.  The config files with your preferences and emails reside in your ./home folder, and should be unaffected.

All the same, backups are a good idea.

---

### Post by candra2 on 2014-07-13
Ok thanks for your note - prior I was sitting in limbo...

Do you think the reinstall of the desktop will fix all the things that got affected i.e. Office Libre, Image / Document Viewer, etc etc

---

### Post by bapoumba on 2014-07-14
Well, once the package manager gets to work again, yes, reinstalling ubuntu-desktop will get you all the default apps back. If you have been installing other apps such as gimp, you may have to reinstall them individually.

You know, I rarely recommend to reinstall ubuntu, but in your case, that is what I would do. Do you have a separate /home ? You may want to back that up in addition to your own work files.

---

### Post by candra2 on 2014-07-14
Right  - I see - I am thinking to re-install and move up to 14.04...and yes in that case I will be sure to backup my entire home folder.

That said, just out of curiosity, is there anyway to reverse course and get everything back to the way it was where my "only" problem was a broken update manager.

---

### Post by bapoumba on 2014-07-14
You current problem is a non-functional package manager. A package manager's job is to ensure all packages are at the correct versions for a distribution given the repositories it knows (standard ubuntu + third parties). Most packages are tied one to another via dependencies. This is how Open Source works. Why write code again or reinvent the wheel when someone else has already done the work and given their code to the community ? So package A will depend on B and C, that in turn depends on D etc.. in the dependency tree.

Dependencies, recommendations and conflicts are in packages descriptions. The package manager reads that. You managed in some way to install packages versions that made the package manager unhappy. When such conflict is about to happen, the package manager asks if you are sure, because in the end you are the one to know. You need to confirm such changes. Most of the time it happens using third party repos or ppas. Do not read me wrong, these extra repos have some use, but need to be handled properly.

It is not easy to untangle the situation not knowing which original move created the conflict and thus how it can be undone. In your case, reversing the course would mean remove and reinstall that original package and its dependencies without the third party repos. What we currently see is one end of the rope. Your original install may be far at the other end. We can only work with current errors. With a little luck, force removing a package with dpkg (that does not care about dependencies, it just does what you instruct it to) quickly leads to resolve the equation. Sometimes not if there are several dependency hoops between the error message and the origin of the conflict.

In addition, a package manager can only install/reinstall (current version) or upgrade (next up-to-date version or ppa), but not downgrade. A "downgrade" would be very difficult to achieve considering some packages and libs are 1- essential and 2- central to the system.

Should you reinstall, please take the time to install ppa-purge once you get a working system. May save you much trouble in the future :)

---

### Post by candra2 on 2014-07-14
Many thanks for your help and support!!

Will keep you posted....

---

### Post by bapoumba on 2014-07-14
All my best brainwaves :)

---


---
title: "E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2013-08-22
forum: New to Ubuntu
---

### Post by Sky001 on 2013-08-22
Hello everyone, 

I've encountered this problem when running the code below. I've included the output from terminal. ```
sudo apt-get update && sudo apt-get upgrade
``` Before that, I was trying to remove WINE. I had installed in order to try a few games but nothing worked.   

```

$ sudo apt-get update && sudo apt-get upgrade
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                                                                                   
Hit http://us.archive.ubuntu.com raring Release.gpg                                                                                       
Get:1 http://security.ubuntu.com raring-security Release.gpg [933 B]                                                                      
Get:2 http://us.archive.ubuntu.com raring-updates Release.gpg [933 B]                                                                     
Hit http://deb.playonlinux.com precise Release.gpg                                                                                        
Hit http://archive.canonical.com raring Release.gpg                                                                                       
Get:3 http://security.ubuntu.com raring-security Release [40.8 kB]                                                                        
Hit http://us.archive.ubuntu.com raring-backports Release.gpg                                                                             
Hit http://ppa.launchpad.net raring Release.gpg                                                                                           
Hit http://dl.google.com stable/main i386 Packages                                                                                        
Hit http://extras.ubuntu.com raring Release.gpg                                                                                           
Hit http://us.archive.ubuntu.com raring Release                                                                                           
Hit http://download.opensuse.org ./ Release.gpg                                                                                           
Hit http://deb.playonlinux.com precise Release                                                                                            
Hit http://archive.canonical.com raring Release.gpg                                                                                       
Hit http://ppa.launchpad.net raring Release                                                                                               
Hit http://extras.ubuntu.com raring Release                                                                                               
Get:4 http://us.archive.ubuntu.com raring-updates Release [40.8 kB]                                                                      
Ign http://dl.google.com stable/main Translation-en_US                                                                                    
Ign http://dl.google.com stable/main Translation-en                                                                                       
Hit http://archive.canonical.com raring Release                                                                                           
Get:5 http://security.ubuntu.com raring-security/main Sources [37.1 kB]                                                                   
Hit http://deb.playonlinux.com precise/main i386 Packages                                                                                 
Hit http://ppa.launchpad.net raring/main Sources                                                                                          
Hit http://extras.ubuntu.com raring/main Sources                                                                                          
Hit https://download.01.org Ubuntu Release.gpg                                                                                            
Hit http://us.archive.ubuntu.com raring-backports Release                                                                                 
Hit http://archive.canonical.com raring Release                                                                                           
Hit https://download.01.org Ubuntu Release                                                                                                
Get:6 http://security.ubuntu.com raring-security/restricted Sources [14 B]                                                                
Hit http://download.opensuse.org ./ Release                                                                                               
Hit http://us.archive.ubuntu.com raring/main Sources                                                                                      
Hit http://ppa.launchpad.net raring/main i386 Packages                                                                                    
Hit http://extras.ubuntu.com raring/main i386 Packages                                                                                    
Get:7 http://security.ubuntu.com raring-security/universe Sources [8,832 B]                                                               
Hit http://us.archive.ubuntu.com raring/restricted Sources                                                                                
Hit http://archive.canonical.com raring/partner Sources                                                                                   
Hit https://download.01.org Ubuntu/13.04 i386 Packages                                                                                    
Get:8 http://security.ubuntu.com raring-security/multiverse Sources [2,264 B]                                                             
Hit http://us.archive.ubuntu.com raring/universe Sources                                                                                  
Hit http://archive.canonical.com raring/partner i386 Packages                                                                             
Get:9 http://security.ubuntu.com raring-security/main i386 Packages [96.2 kB]                                                           
Hit http://us.archive.ubuntu.com raring/multiverse Sources                                                                                
Hit http://download.opensuse.org ./ Packages                                                                                              
Hit http://us.archive.ubuntu.com raring/main i386 Packages                                                                                
Hit http://us.archive.ubuntu.com raring/restricted i386 Packages                                                                          
Hit http://us.archive.ubuntu.com raring/universe i386 Packages                                                                            
Hit http://us.archive.ubuntu.com raring/multiverse i386 Packages                                                                          
Hit http://archive.canonical.com raring/partner Sources                                                                                   
Get:10 http://security.ubuntu.com raring-security/restricted i386 Packages [14 B]                                                         
Hit http://us.archive.ubuntu.com raring/main Translation-en                                                                               
Get:11 http://security.ubuntu.com raring-security/universe i386 Packages [33.9 kB]                                                        
Hit http://archive.canonical.com raring/partner i386 Packages                                                                             
Hit http://download.opensuse.org  Release.gpg                                                                                             
Get:12 http://security.ubuntu.com raring-security/multiverse i386 Packages [3,871 B]                                                      
Hit http://us.archive.ubuntu.com raring/multiverse Translation-en                                                                         
Hit http://security.ubuntu.com raring-security/main Translation-en                                                                        
Hit http://us.archive.ubuntu.com raring/restricted Translation-en                                                                       
Ign http://ppa.launchpad.net raring/main Translation-en_US                                                                              
Hit http://security.ubuntu.com raring-security/multiverse Translation-en                                          
Hit http://us.archive.ubuntu.com raring/universe Translation-en                                                                           
Ign http://deb.playonlinux.com precise/main Translation-en_US                                                                             
Ign http://ppa.launchpad.net raring/main Translation-en                                                                                   
Ign http://extras.ubuntu.com raring/main Translation-en_US                                                                              
Hit http://security.ubuntu.com raring-security/restricted Translation-en                                          
Get:13 http://us.archive.ubuntu.com raring-updates/main Sources [62.0 kB]                                         
Ign http://extras.ubuntu.com raring/main Translation-en                                                                                   
Ign http://deb.playonlinux.com precise/main Translation-en                                                                                
Hit http://security.ubuntu.com raring-security/universe Translation-en                                                      
Get:14 http://us.archive.ubuntu.com raring-updates/restricted Sources [14 B]                                       
Get:15 http://us.archive.ubuntu.com raring-updates/universe Sources [70.9 kB]                                      
Get:16 http://us.archive.ubuntu.com raring-updates/multiverse Sources [2,264 B]                                    
Get:17 http://us.archive.ubuntu.com raring-updates/main i386 Packages [157 kB]                          
Hit http://download.opensuse.org  Release                                                        
Ign http://security.ubuntu.com raring-security/main Translation-en_US                                                       
Ign http://security.ubuntu.com raring-security/multiverse Translation-en_US                           
Ign http://download.opensuse.org ./ Translation-en_US                                                 
Ign http://security.ubuntu.com raring-security/restricted Translation-en_US                           
Ign http://download.opensuse.org ./ Translation-en                                                                                        
Ign http://security.ubuntu.com raring-security/universe Translation-en_US                                                                 
Get:18 http://us.archive.ubuntu.com raring-updates/restricted i386 Packages [14 B]                                                        
Get:19 http://us.archive.ubuntu.com raring-updates/universe i386 Packages [138 kB]                                                        
Ign http://archive.canonical.com raring/partner Translation-en_US                                                                         
Ign http://archive.canonical.com raring/partner Translation-en                                                                            
Get:20 http://us.archive.ubuntu.com raring-updates/multiverse i386 Packages [3,871 B]                                                     
Ign http://archive.canonical.com raring/partner Translation-en_US                                                                         
Ign http://archive.canonical.com raring/partner Translation-en                                                                            
Hit http://us.archive.ubuntu.com raring-updates/main Translation-en                                                                       
Hit http://us.archive.ubuntu.com raring-updates/multiverse Translation-en                                                                 
Hit http://us.archive.ubuntu.com raring-updates/restricted Translation-en                                                                 
Hit http://download.opensuse.org  Packages                                                                                                
Hit http://us.archive.ubuntu.com raring-updates/universe Translation-en                                                                   
Hit http://us.archive.ubuntu.com raring-backports/main Sources                                                                            
Hit http://us.archive.ubuntu.com raring-backports/restricted Sources                                                                      
Hit http://us.archive.ubuntu.com raring-backports/universe Sources                                                                        
Hit http://us.archive.ubuntu.com raring-backports/multiverse Sources                                                                      
Hit http://us.archive.ubuntu.com raring-backports/main i386 Packages                                                                      
Hit http://us.archive.ubuntu.com raring-backports/restricted i386 Packages                                                                
Hit http://us.archive.ubuntu.com raring-backports/universe i386 Packages                                                                  
Hit http://us.archive.ubuntu.com raring-backports/multiverse i386 Packages                                                                
Hit http://us.archive.ubuntu.com raring-backports/main Translation-en                                                                     
Hit http://us.archive.ubuntu.com raring-backports/multiverse Translation-en                                                               
Hit http://us.archive.ubuntu.com raring-backports/restricted Translation-en                                                               
Ign https://download.01.org Ubuntu/13.04 Translation-en_US                                                                                
Hit http://us.archive.ubuntu.com raring-backports/universe Translation-en                                                                 
Ign https://download.01.org Ubuntu/13.04 Translation-en                                                                                   
Ign http://us.archive.ubuntu.com raring/main Translation-en_US                                                                            
Ign http://us.archive.ubuntu.com raring/multiverse Translation-en_US                                                                      
Ign http://us.archive.ubuntu.com raring/restricted Translation-en_US                                                                      
Ign http://us.archive.ubuntu.com raring/universe Translation-en_US                                                                        
Ign http://us.archive.ubuntu.com raring-updates/main Translation-en_US                                                                    
Ign http://us.archive.ubuntu.com raring-updates/multiverse Translation-en_US                                                              
Ign http://us.archive.ubuntu.com raring-updates/restricted Translation-en_US                                                              
Ign http://us.archive.ubuntu.com raring-updates/universe Translation-en_US                                                                
Ign http://us.archive.ubuntu.com raring-backports/main Translation-en_US                                                                  
Ign http://us.archive.ubuntu.com raring-backports/multiverse Translation-en_US                                                            
Ign http://us.archive.ubuntu.com raring-backports/restricted Translation-en_US                                                            
Ign http://download.opensuse.org  Translation-en_US                                                                                       
Ign http://us.archive.ubuntu.com raring-backports/universe Translation-en_US                                                              
Ign http://download.opensuse.org  Translation-en                                                                                          
Fetched 700 kB in 11s (58.7 kB/s)                                                                                                         
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  intel-linux-graphics-installer libopenscenegraph80
The following packages will be upgraded:
  activity-log-manager-common activity-log-manager-control-center apport apport-gtk bamfdaemon command-not-found command-not-found-data
  gir1.2-dbusmenu-glib-0.4 gir1.2-dbusmenu-gtk-0.4 gnome-control-center-unity gnome-screenshot google-chrome-stable libbamf3-1
  libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4 libdvdnav4 libplymouth2 libunity-2d-private0 libunity-core-6.0-5 libwhoopsie0
  lsb-base lsb-release passwd plymouth plymouth-label plymouth-theme-ubuntu-logo plymouth-theme-ubuntu-text python-apport
  python-problem-report python3-apport python3-commandnotfound python3-problem-report unity unity-2d unity-2d-common unity-2d-panel
  unity-2d-shell unity-2d-spread unity-common unity-lens-applications unity-services whoopsie
43 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
Need to get 0 B/47.4 MB of archives.
After this operation, 3,360 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
dpkg: parse error, in file '/var/lib/dpkg/status' near line 4794 package 'wine1.6-i386':
 `Depends' field, invalid package name `wine1.6:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

If anyone can help: I'd really appreciate it.
Thanks1.

---

### Post by deadflowr on 2013-08-23
Open up gedit and then select Open, then select file system, then select var, then lib, the dpkg, then status.
Now go to the menu listing "Search", then go to "Go to Line".
Type in line 4794.
Now copy that line and post it.

It seems from the error message that there is a character problem in that line, so posting the iine will help confirm it.

---

### Post by Sky001 on 2013-08-24
> **deadflowr said:**
> Open up gedit and then select Open, then select file system, then select var, then lib, the dpkg, then status.
Now go to the menu listing "Search", then go to "Go to Line".
Type in line 4794.
Now copy that line and post it.

It seems from the error message that there is a character problem in that line, so posting the iine will help confirm it.

I did as you asked. There were two files with the name status. status and status-old.
From status:
```
/etc/sane.d/artec_eplus48u.conf 3672fe16e6b14a124ad74acd47941be9
```

From status-old:
```
/etc/sane.d/artec_eplus48u.conf 3672fe16e6b14a124ad74acd47941be9
```

The lines appear the same to me.

---

### Post by deadflowr on 2013-08-24
No matter. It was worth a shot to see the problem but alas I became stumped by it.

Look at this from Ask Ubuntu on how to try to fix this error problem
[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

Basically, though, it calls for you to move an old backup copy into the existing files place.

---

### Post by Bashing-om on 2013-08-24
Sky001; Hi !

This to me indicates there are still some remnants of "wine" left on the system"
> 
dpkg: parse error, in file '/var/lib/dpkg/status' near line 4794 package 'wine1.6-i386':
 `Depends' field, invalid package name `wine1.6:any': character `:' not allowed (only letters, digits and characters `-+._')


What means have you employed to this time to remove "Wine" ?

[INDENT][INDENT]this could now be a long row to hoe
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-25
to remove wine, I used sudo apt-get remove wine && sudo apt-get purge wine.

---

### Post by ibjsb4 on 2013-08-25
> **Sky001 said:**
> to remove wine, I used sudo apt-get remove wine && sudo apt-get purge wine.

That would of removed the meta-package from the repositories.  This wine 1.6 sounds like ppa install, is it?

[http://ubuntuforums.org/showthread.php?t=1949373&p=11805378#post11805378](http://ubuntuforums.org/showthread.php?t=1949373&p=11805378#post11805378)

You may need to first remove that [ppa using terminal.]("http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remove+ppa+in+terminal&sa=Search&cof=FORID:9")

---

### Post by Bashing-om on 2013-08-25
Sky001; Hi ! ..

I bet if you look into the directory "/etc/apt/sources.list.d"
```

ls -la /etc/apt/sources.list.d

```
There is yet a "get" for "'wine1.6-i386"
Please post that output. Looking at that you perhaps installed "Wine" via the Wine PPA .. and the better way to remove said Wine if via "ppa-purge' procedure.

At this time I also look at the probability of manually intervening to correct the "in file '/var/lib/dpkg/status' near line 4794" issue.

[INDENT][INDENT]where solutions exist, there are no problems
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-25
Here you go. 
```

$ ls -la /etc/apt/sources.list.d
total 44
drwxr-xr-x 2 root root 4096 Aug  5 17:17 .
drwxr-xr-x 6 root root 4096 Aug  5 17:27 ..
-rw-r--r-- 1 root root  176 Aug  5 11:52 google-chrome.list
-rw-r--r-- 1 root root  211 Jul 21 21:13 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root  176 Aug  5 11:52 google-chrome.list.save
-rw-r--r-- 1 root root   87 Aug  5 11:52 intellinuxgraphics.list
-rw-r--r-- 1 root root   87 Aug  5 11:52 intellinuxgraphics.list.save
-rw-r--r-- 1 root root   45 Jul  3 15:35 playonlinux.list
-rw-r--r-- 1 root root  132 Aug  5 11:52 ubuntu-wine-ppa-raring.list
-rw-r--r-- 1 root root  134 Aug  5 11:52 ubuntu-wine-ppa-raring.list.save
-rw-r--r-- 1 root root   88 Aug  5 17:17 vegastrike-data.list
```

Edit: I've tried to install the ppa-purge and the same error came about. See below
```

~$ ppa-purge
The program 'ppa-purge' is currently not installed. You can install it by typing:
sudo apt-get install ppa-purge
saipal@saipal-HP-Compaq-tc4400-EN357UT-ABA:~$ sudo apt-get install ppa-purge
[sudo] password for saipal: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-exe-thumbnailer libcapi20-3 libnss-winbind libosmesa6 libpam-winbind linux-headers-3.8.0-26 linux-headers-3.8.0-26-generic
  linux-image-3.8.0-26-generic linux-image-extra-3.8.0-26-generic p7zip ttf-droid ttf-liberation ttf-umefont ttf-unfonts-core winbind
  wine-gecko1.4 wine-gecko2.21 wine-mono0.0.8 wine1.5 wine1.6 wine1.6-i386 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude aptitude-common libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget3 ppa-purge
0 upgraded, 4 newly installed, 0 to remove and 45 not upgraded.
Need to get 2,480 kB of archives.
After this operation, 10.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main aptitude-common all 0.6.8.1-2ubuntu2 [669 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/main libcwidget3 i386 0.5.16-3.4ubuntu1 [381 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring/main aptitude i386 0.6.8.1-2ubuntu2 [1,423 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring/universe ppa-purge all 0.2.8+bzr57 [5,704 B]
Fetched 2,480 kB in 3s (813 kB/s)
dpkg: parse error, in file '/var/lib/dpkg/status' near line 4794 package 'wine1.6-i386':
 `Depends' field, invalid package name `wine1.6:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Bashing-om on 2013-08-25
Sky001; Well, well
do:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine-ppa-raring
ls -la /etc/apt/sources.list.d

```
and let us see then where you stand.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-25
> **deadflowr said:**
> No matter. It was worth a shot to see the problem but alas I became stumped by it.

Look at this from Ask Ubuntu on how to try to fix this error problem
[http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file](http://askubuntu.com/questions/4834/how-do-i-rebuild-a-corrupt-dpkg-status-file)

Basically, though, it calls for you to move an old backup copy into the existing files place.

I tried following the instructions in the link.

At the first stage:
```

sudo apt-get install pcregrep
pcregrep -nM '\n\s*\n[^P]+' /var/lib/dpkg/status
```

My terminal result:
```

sudo apt-get install pcregrep
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-exe-thumbnailer libcapi20-3 libnss-winbind libosmesa6 libpam-winbind linux-headers-3.8.0-26 linux-headers-3.8.0-26-generic
  linux-image-3.8.0-26-generic linux-image-extra-3.8.0-26-generic p7zip ttf-droid ttf-liberation ttf-umefont ttf-unfonts-core winbind
  wine-gecko1.4 wine-gecko2.21 wine-mono0.0.8 wine1.5 wine1.6 wine1.6-i386 winetricks
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  pcregrep
0 upgraded, 1 newly installed, 0 to remove and 45 not upgraded.
Need to get 0 B/26.2 kB of archives.
After this operation, 74.8 kB of additional disk space will be used.
dpkg: parse error, in file '/var/lib/dpkg/status' near line 4794 package 'wine1.6-i386':
 `Depends' field, invalid package name `wine1.6:any': character `:' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
```

---

### Post by Sky001 on 2013-08-25
> **Bashing-om said:**
> Sky001; Well, well
do:
```

sudo apt-get install ppa-purge
sudo ppa-purge ppa:ubuntu-wine-ppa-raring
ls -la /etc/apt/sources.list.d

```
and let us see then where you stand.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


I ran the code you gave me 3 times. Why did it abort?

```

 sudo apt-get install ppa-purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  gnome-exe-thumbnailer libcapi20-3 libnss-winbind libosmesa6 libpam-winbind linux-headers-3.8.0-26 linux-headers-3.8.0-26-generic
  linux-image-3.8.0-26-generic linux-image-extra-3.8.0-26-generic p7zip ttf-droid ttf-liberation ttf-umefont ttf-unfonts-core winbind
  wine-gecko1.4 wine-gecko2.21 wine-mono0.0.8 wine1.5 wine1.6 wine1.6-i386 winetricks
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  aptitude aptitude-common libcwidget3
Suggested packages:
  aptitude-doc-en aptitude-doc tasksel debtags libcwidget-dev
The following NEW packages will be installed:
  aptitude aptitude-common libcwidget3 ppa-purge
0 upgraded, 4 newly installed, 0 to remove and 45 not upgraded.
Need to get 0 B/2,480 kB of archives.
After this operation, 10.1 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Abort.
```

---

### Post by Bashing-om on 2013-08-25
Sky001; ...

I am far from knowing all about this wonderful operating system .. I will surmise that there no longer exist the index files for ppa-purge to install.

Let's see what we can find on the system yet in respect to "wine" prior to editing the index file.
```

sudo find / -name "wine*"

```

This command searches your whole system for any instance of a "Wine" system file. Will take a bit of time to look through all the files .. be patient.

If any returns, post them .. so we can see what should/might be done to remove them.

[INDENT][INDENT]longest journey begins with a 1st step
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-25
The list is rather long. 

```

~$ sudo find / -name "wine*"
[sudo] password for saipal: 
/etc/xdg/menus/applications-merged/wine.menu
/home/saipal/.wine/drive_c/users/saipal/Application Data/wine_gecko
/home/saipal/.wine/drive_c/windows/system32/winecfg.exe
/home/saipal/.wine/drive_c/windows/system32/winealsa.drv
/home/saipal/.wine/drive_c/windows/system32/wined3d.dll
/home/saipal/.wine/drive_c/windows/system32/winegstreamer.dll
/home/saipal/.wine/drive_c/windows/system32/wineboot.exe
/home/saipal/.wine/drive_c/windows/system32/winepath.exe
/home/saipal/.wine/drive_c/windows/system32/winex11.drv
/home/saipal/.wine/drive_c/windows/system32/wineps16.drv
/home/saipal/.wine/drive_c/windows/system32/winemsibuilder.exe
/home/saipal/.wine/drive_c/windows/system32/winedevice.exe
/home/saipal/.wine/drive_c/windows/system32/wineoss.drv
/home/saipal/.wine/drive_c/windows/system32/winebrowser.exe
/home/saipal/.wine/drive_c/windows/system32/winemenubuilder.exe
/home/saipal/.wine/drive_c/windows/system32/winepulse.drv
/home/saipal/.wine/drive_c/windows/system32/winemine.exe
/home/saipal/.wine/drive_c/windows/system32/winejoystick.drv
/home/saipal/.wine/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/saipal/.wine/drive_c/windows/system32/gecko/2.21/wine_gecko
/home/saipal/.wine/drive_c/windows/system32/wineconsole.exe
/home/saipal/.wine/drive_c/windows/system32/winemp3.acm
/home/saipal/.wine/drive_c/windows/system32/winemapi.dll
/home/saipal/.wine/drive_c/windows/system32/winefile.exe
/home/saipal/.wine/drive_c/windows/system32/wineps.drv
/home/saipal/.wine/drive_c/windows/system32/winevdm.exe
/home/saipal/.wine/drive_c/windows/system32/winedbg.exe
/home/saipal/.PlayOnLinux/wineprefix
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winecfg.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winealsa.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wined3d.dll
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winegstreamer.dll
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wineboot.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winepath.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winex11.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wineps16.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winemsibuilder.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winedevice.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wineoss.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winebrowser.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winemenubuilder.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winemine.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winejoystick.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wineconsole.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winemp3.acm
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winemapi.dll
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winefile.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/wineps.drv
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winevdm.exe
/home/saipal/.PlayOnLinux/wineprefix/DivineDiviniy/drive_c/windows/system32/winedbg.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winecfg.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winealsa.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wined3d.dll
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winegstreamer.dll
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wineboot.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winepath.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winex11.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wineps16.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winemsibuilder.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winedevice.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wineoss.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winebrowser.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winemenubuilder.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winemine.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winejoystick.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/gecko/1.4/wine_gecko
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wineconsole.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winemp3.acm
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winemapi.dll
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winefile.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/wineps.drv
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winevdm.exe
/home/saipal/.PlayOnLinux/wineprefix/Mystical_Land/drive_c/windows/system32/winedbg.exe
/home/saipal/.PlayOnLinux/wine
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winemine
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winefile
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wineconsole
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winecpp
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winebuild
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wine
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winemaker
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wineg++
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wineserver
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winedbg
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winecfg
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winedump
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winepath
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/winegcc
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wine-preloader
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/bin/wineboot
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winemapi.dll.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winefile.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winemine.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/wined3d.dll.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winedevice.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winecfg.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winealsa.drv
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/wined3d.dll
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/wineboot.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winepath.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winex11.drv
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winemsibuilder.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winedevice.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winebrowser.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winemenubuilder.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winemine.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winejoystick.drv
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/wineconsole.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winemp3.acm
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winemapi.dll
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winefile.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/wineps16.drv16
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/wineps.drv
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winevdm.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/fakedlls/winedbg.exe
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/wineconsole.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winedbg.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winebrowser.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winepath.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winevdm.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/wineps.drv.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winemsibuilder.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winex11.drv.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winemenubuilder.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winejoystick.drv.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winealsa.drv.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/wineps16.drv16.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winecfg.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/wineboot.exe.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/lib/wine/winemp3.acm.so
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/wine
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/wine/wine.inf
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/applications/wine.desktop
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/pl.UTF-8/man1/wine.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/wineboot.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winemaker.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/wine.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winedbg.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/wineconsole.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winegcc.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winedump.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/wineserver.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/wineg++.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winecfg.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winemine.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winecpp.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winepath.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winebuild.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/man1/winefile.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/de.UTF-8/man1/winemaker.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/de.UTF-8/man1/wine.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/de.UTF-8/man1/wineserver.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/fr.UTF-8/man1/winemaker.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/fr.UTF-8/man1/wine.1
/home/saipal/.PlayOnLinux/wine/linux-x86/1.4/share/man/fr.UTF-8/man1/wineserver.1
/home/saipal/.PlayOnLinux/wine/gecko/wine_gecko-1.4-x86.msi
/home/saipal/.PlayOnLinux/plugins/Wine Look/scripts/wine_colors_from_gnome.py
/home/saipal/.PlayOnLinux/plugins/Capture/software/usr/bin/wine-pthread
/home/saipal/.PlayOnLinux/plugins/Capture/software/usr/bin64/wine-pthread
/home/saipal/.config/menus/applications-merged/wine-Programs-Drakensang Online-Uninstall.menu
/home/saipal/.config/menus/applications-merged/wine-Programs-Drakensang Online-Drakensang Online.menu
/home/saipal/.config/menus/applications-merged/wine-Programs-AeriaGames-Ignite.menu
/home/saipal/.cache/winetricks
/home/saipal/.local/share/desktop-directories/wine-wine.directory
/home/saipal/.local/share/desktop-directories/wine-Programs-Joymax-Silkroad.directory
/home/saipal/.local/share/desktop-directories/wine-Programs.directory
/home/saipal/.local/share/desktop-directories/wine-Programs-Drakensang Online.directory
/home/saipal/.local/share/desktop-directories/wine-Programs-Joymax.directory
/home/saipal/.local/share/desktop-directories/wine-Programs-Torchlight 2.directory
/home/saipal/.local/share/desktop-directories/wine-Programs-AeriaGames.directory
/home/saipal/.local/share/applications/wine-extension-hlp.desktop
/home/saipal/.local/share/applications/wine-extension-jfif.desktop
/home/saipal/.local/share/applications/wine-extension-txt.desktop
/home/saipal/.local/share/applications/wine-extension-png.desktop
/home/saipal/.local/share/applications/wine-extension-htm.desktop
/home/saipal/.local/share/applications/wine-extension-wri.desktop
/home/saipal/.local/share/applications/wine-extension-jpe.desktop
/home/saipal/.local/share/applications/wine
/home/saipal/.local/share/applications/wine-extension-gif.desktop
/home/saipal/.local/share/applications/wine-extension-ini.desktop
/home/saipal/.local/share/applications/wine-extension-chm.desktop
/home/saipal/.local/share/applications/wine-extension-msp.desktop
/home/saipal/.local/share/applications/wine-extension-rtf.desktop
/home/saipal/.local/share/applications/wine-extension-url.desktop
/home/saipal/.local/share/applications/wine-extension-vbs.desktop
/home/saipal/.local/share/applications/wine-extension-xml.desktop
/var/lib/binfmts/wine
/var/lib/dpkg/info/wine1.6-i386.postrm
/var/lib/dpkg/info/winetricks.list
/var/lib/dpkg/info/wine1.6-i386.postinst
/var/lib/dpkg/info/wine1.6.conffiles
/var/lib/dpkg/info/wine-gecko1.4:i386.md5sums
/var/lib/dpkg/info/wine-mono0.0.8.md5sums
/var/lib/dpkg/info/wine1.4.postrm
/var/lib/dpkg/info/wine1.6.config
/var/lib/dpkg/info/wine1.4-i386.list
/var/lib/dpkg/info/wine1.6.postinst
/var/lib/dpkg/info/wine1.6.preinst
/var/lib/dpkg/info/wine-mono0.0.8.list
/var/lib/dpkg/info/winetricks.md5sums
/var/lib/dpkg/info/wine1.6-i386.list
/var/lib/dpkg/info/wine1.6.list
/var/lib/dpkg/info/wine-gecko2.21:i386.md5sums
/var/lib/dpkg/info/wine1.6-i386.md5sums
/var/lib/dpkg/info/wine-gecko1.4:i386.list
/var/lib/dpkg/info/wine1.6-i386.shlibs
/var/lib/dpkg/info/wine-gecko2.21:i386.list
/var/lib/dpkg/info/wine1.6.postrm
/var/lib/dpkg/info/wine1.6.md5sums
/var/lib/dpkg/info/wine1.4.list
/var/lib/dpkg/info/wine1.5.md5sums
/var/lib/dpkg/info/wine1.4-i386.postrm
/var/lib/dpkg/info/wine1.5.list
/var/lib/dpkg/info/wine1.6.prerm
/var/cache/apt/archives/wine1.6-i386_1.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/wine-gecko2.21_2.21-0ubuntu1~ppa1~precise1_i386.deb
/var/cache/apt/archives/wine-mono0.0.8_0.0.8-0ubuntu1~ppa1_all.deb
/var/cache/apt/archives/wine1.5_1.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/wine1.6_1.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/wine_1.6-0ubuntu1~ppa1_i386.deb
/var/cache/apt/archives/winetricks_0.0+20130707~precise1~ppa1_i386.deb
/usr/bin/wine-preloader
/usr/bin/winefile
/usr/bin/wineboot
/usr/bin/winedump
/usr/bin/wineconsole
/usr/bin/wine
/usr/bin/winegcc
/usr/bin/winemaker
/usr/bin/winedbg
/usr/bin/winemine
/usr/bin/winetricks
/usr/bin/winecpp
/usr/bin/winepath
/usr/bin/wine-auto
/usr/bin/winecfg
/usr/bin/wineg++
/usr/bin/wineserver
/usr/bin/winebuild
/usr/share/wine
/usr/share/wine/wine.inf
/usr/share/wine/mono/wine-mono-0.0.8.msi
/usr/share/wine/gecko/wine_gecko-1.4-x86.msi
/usr/share/wine/gecko/wine_gecko-2.21-x86.msi
/usr/share/wine/wineserver-restart-required.update-notifier
/usr/share/bash-completion/completions/wine
/usr/share/desktop-directories/wine-Programs.directory
/usr/share/desktop-directories/wine-Programs-Accessories.directory
/usr/share/desktop-directories/wine-wine.directory
/usr/share/man/man1/winedbg.1.gz
/usr/share/man/man1/winepath.1.gz
/usr/share/man/man1/winefile.1.gz
/usr/share/man/man1/wineconsole.1.gz
/usr/share/man/man1/winecfg.1.gz
/usr/share/man/man1/winecpp.1.gz
/usr/share/man/man1/wine.1.gz
/usr/share/man/man1/wineserver.1.gz
/usr/share/man/man1/winemaker.1.gz
/usr/share/man/man1/wineboot.1.gz
/usr/share/man/man1/winemine.1.gz
/usr/share/man/man1/winegcc.1.gz
/usr/share/man/man1/winedump.1.gz
/usr/share/man/man1/wineg++.1.gz
/usr/share/man/man1/winebuild.1.gz
/usr/share/man/de.UTF-8/man1/wine.1.gz
/usr/share/man/de.UTF-8/man1/wineserver.1.gz
/usr/share/man/de.UTF-8/man1/winemaker.1.gz
/usr/share/man/fr.UTF-8/man1/wine.1.gz
/usr/share/man/fr.UTF-8/man1/wineserver.1.gz
/usr/share/man/fr.UTF-8/man1/winemaker.1.gz
/usr/share/man/pl.UTF-8/man1/wine.1.gz
/usr/share/playonlinux/etc/onglet/wine.png
/usr/share/playonlinux/etc/setups/wineserver
/usr/share/playonlinux/etc/install/wine-packages.png
/usr/share/playonlinux/etc/install/wine-warning.png
/usr/share/playonlinux/etc/install/wine.png
/usr/share/playonlinux/resources/images/menu/wineserver.png
/usr/share/playonlinux/resources/images/menu/winecfg.png
/usr/share/playonlinux/resources/images/menu/wine.png
/usr/share/playonlinux/resources/images/setups/wineserver
/usr/share/playonlinux/resources/images/install/wine-packages.png
/usr/share/playonlinux/resources/images/install/wine-warning.png
/usr/share/playonlinux/resources/images/install/wine.png
/usr/share/playonlinux/resources/images/configure/wineboot.png
/usr/share/playonlinux/resources/images/configure/winecfg.png
/usr/share/playonlinux/resources/images/configure/wine-uninstaller.png
/usr/share/playonlinux/resources/images/configure/wine-winecfg.png
/usr/share/playonlinux/bash/winebash
/usr/share/playonlinux/python/wine_versions.py
/usr/share/playonlinux/python/lib/wine.py
/usr/share/playonlinux/lib/wine.lib
/usr/share/applications/wine-winecfg.desktop
/usr/share/applications/wine-winetricks.desktop
/usr/share/applications/wine-browsedrive.desktop
/usr/share/applications/wine-notepad.desktop
/usr/share/applications/wine-uninstaller.desktop
/usr/share/applications/wine.desktop
/usr/share/binfmts/wine
/usr/share/doc/wine1.5
/usr/share/doc/texlive-doc/latex/newlfm/wine.pdf
/usr/share/doc/texlive-doc/latex/newlfm/wine.eps.gz
/usr/share/doc/wine-mono0.0.8
/usr/share/doc/texlive-latex-extra-doc/latex/newlfm/wine.pdf
/usr/share/doc/texlive-latex-extra-doc/latex/newlfm/wine.eps.gz
/usr/share/doc/wine1.6
/usr/share/doc/wine1.6-i386
/usr/share/doc/wine-gecko1.4
/usr/share/doc/winetricks
/usr/share/doc/wine-gecko2.21
/usr/share/app-install/desktop/wine1.4:wine.desktop
/usr/share/app-install/desktop/winefish:winefish.desktop
/usr/share/app-install/icons/wine.svg
/usr/share/icons/hicolor/scalable/apps/wine-winecfg.svg
/usr/share/icons/hicolor/scalable/apps/wine.svg
/usr/share/icons/hicolor/scalable/apps/wine-winetricks.svg
/usr/share/icons/hicolor/scalable/apps/wine-uninstaller.svg
/usr/share/icons/hicolor/48x48/apps/wine.png
/usr/share/icons/hicolor/48x48/apps/wine-uninstaller.png
/usr/share/icons/hicolor/48x48/apps/wine-notepad.png
/usr/share/icons/hicolor/48x48/apps/wine-winecfg.png
/usr/share/icons/hicolor/22x22/apps/wine.png
/usr/share/icons/hicolor/22x22/apps/wine-uninstaller.png
/usr/share/icons/hicolor/22x22/apps/wine-notepad.png
/usr/share/icons/hicolor/22x22/apps/wine-winecfg.png
/usr/share/icons/hicolor/24x24/apps/wine.png
/usr/share/icons/hicolor/24x24/apps/wine-uninstaller.png
/usr/share/icons/hicolor/24x24/apps/wine-notepad.png
/usr/share/icons/hicolor/24x24/apps/wine-winecfg.png
/usr/share/icons/hicolor/32x32/apps/wine.png
/usr/share/icons/hicolor/32x32/apps/wine-uninstaller.png
/usr/share/icons/hicolor/32x32/apps/wine-notepad.png
/usr/share/icons/hicolor/32x32/apps/wine-winecfg.png
/usr/share/icons/hicolor/16x16/apps/wine.png
/usr/share/icons/hicolor/16x16/apps/wine-uninstaller.png
/usr/share/icons/hicolor/16x16/apps/wine-notepad.png
/usr/share/icons/hicolor/16x16/apps/wine-winecfg.png
/usr/share/lintian/overrides/wine1.6
/usr/lib/i386-linux-gnu/wine
/usr/lib/i386-linux-gnu/wine/winemsibuilder.exe.so
/usr/lib/i386-linux-gnu/wine/winebrowser.exe.so
/usr/lib/i386-linux-gnu/wine/winex11.drv.so
/usr/lib/i386-linux-gnu/wine/wineoss.drv.so
/usr/lib/i386-linux-gnu/wine/winemapi.dll.so
/usr/lib/i386-linux-gnu/wine/wineps16.drv16.so
/usr/lib/i386-linux-gnu/wine/winefile.exe.so
/usr/lib/i386-linux-gnu/wine/winevdm.exe.so
/usr/lib/i386-linux-gnu/wine/wineps.drv.so
/usr/lib/i386-linux-gnu/wine/winemine.exe.so
/usr/lib/i386-linux-gnu/wine/winepulse.drv.so
/usr/lib/i386-linux-gnu/wine/wined3d.dll.so
/usr/lib/i386-linux-gnu/wine/winecfg.exe.so
/usr/lib/i386-linux-gnu/wine/winedbg.exe.so
/usr/lib/i386-linux-gnu/wine/winejoystick.drv.so
/usr/lib/i386-linux-gnu/wine/winedevice.exe.so
/usr/lib/i386-linux-gnu/wine/wineconsole.exe.so
/usr/lib/i386-linux-gnu/wine/winemenubuilder.exe.so
/usr/lib/i386-linux-gnu/wine/wineboot.exe.so
/usr/lib/i386-linux-gnu/wine/winepath.exe.so
/usr/lib/i386-linux-gnu/wine/winealsa.drv.so
/usr/lib/i386-linux-gnu/wine/winemp3.acm.so
/usr/lib/i386-linux-gnu/wine/winegstreamer.dll.so
/usr/lib/i386-linux-gnu/wine/fakedlls/winemp3.acm
/usr/lib/i386-linux-gnu/wine/fakedlls/winedevice.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winepulse.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winefile.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wined3d.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/winejoystick.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/wineps16.drv16
/usr/lib/i386-linux-gnu/wine/fakedlls/winemsibuilder.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineconsole.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winemapi.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/wineoss.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winebrowser.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winex11.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winedbg.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineboot.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winealsa.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winecfg.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/wineps.drv
/usr/lib/i386-linux-gnu/wine/fakedlls/winegstreamer.dll
/usr/lib/i386-linux-gnu/wine/fakedlls/winemenubuilder.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winepath.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winevdm.exe
/usr/lib/i386-linux-gnu/wine/fakedlls/winemine.exe
/usr/lib/mime/packages/wine1.6
/proc/sys/fs/binfmt_misc/wine
```

And here I thought I had removed some of this wine.

---

### Post by Bashing-om on 2013-08-25
Sky001; Oh My !

Have you got your work cut out for you ..
Admonishment: should have done the homework first and known to use ppa-purge to remove any third party software ! -Ain't ubuntu - !
Upfront; I have no experience with either Wine or PlayonLinux .. That could be a serious disadvantage in this endeavor. I have no idea what files Wine and PlayonLinux may share.
The only recourse I am presently aware of is to manually remove all those "Wine" files and then clean up the index files. It might be a benefit to await others advise in this respect .. perhaps there exist a better option than manually removing these files and risking removing something required of the system - or breaking PlayonLinux.

OR .. might try and (re-)install Wine and if it does install properly ... then remove it via ppa-purge command ??? Which might prove to be the better course.

Others with the experience can advise better, no doubt. Might behoove us to await their advise.

I like the option to attempt to (re-)install Wine and then properly remove it .. let the system do the work for us ..iffy though that it will install with no problems at this stage. But, worth a shot ?  .. Have you attempted at all to (re-)install Wine ?

Is PlayonLinux presently functional ? What are we going to break !

[INDENT][INDENT]may be a tough row to hoe
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-25
I tried reinstalling wine using the terminal, using synaptic and using Ubuntu Software Center. The same error was returned. Linux is turning out much much harder to use than I wanted. Sometimes I feel as though I need a degree in computer science to make this machine work as I need it to. I'll probably end up purchasing a large hard drive, transferring all my data over and doing a full reinstall. 

Since I really don't understand what is wrong; I find it especially scary manually deleting all those files. I don't want to touch the power button and have this pc refuse to start. 

I suppose now I really (really) know I need to learn shell commands and perhaps go through several books on computer structure. What am I doing with my life?

---

### Post by Bashing-om on 2013-08-25
Sky001' Hey !

Let's put things in perspective.

There are many side benefits to learning to live with your operating system.

The current situation is not a 'buntu problem .. you chose to install 3rd party software that in it's self is outside of the umbrella of protection of the package management system. Now we can only try and fix it with the tools at our disposal. If you have not guessed it .. I have a great deal of respect and admiration for this operating system. With time and effort and a lot of frustration this situation is fixable.

What we have in your system is a failure to communicate. Dependency issues, in that files depend on other files to perform properly, - any one of those files missing and/or corrupt to either purge an application or install the application - prevent the completion of the task.

As it has proven difficult to (re-)install Wine .. let us look at what is entailed in manually completing the purging of wine.
From the command line; remove ALL those remaining files in a slow and tedious time consuming manner ... then
manually edit two index files to remove all those  "pointers" to "Wine"
then -> update all the packages on your system ...
and repeat until the system is error free.

And yes. it is a big deal.. on the bright side; you will learn a lot about your operating system and how to live with it ...This is a truly powerful operating system but that great power can only be unleashed from the command line ..Like any operating system there is a learning curve and if you are coming from windows it is indeed a steep learning curve .. requiring a different mindset.

If you choose to fix this install it is possible, though not at all probable. that it can be rendered "unbootable". There is that slight risk. We are removing application specific files and should not touch any system files in this operation. The worst I foresee happening is possibly breaking PlayonLinux.

You may rest assured that you are not the first to be in this situation. I will spend a bit of time looking about for what others have gone through in order to restore their system. There is no point in re-inventing the wheel .. others have been there and done that and related the circumstances .. see ain't ubuntu wonderful !  

Finally, If you are certain you are going to upgrade your hardware and do a clean install, there is little point in putting forth the effort that it may take to restore this install. Restoring will in any event be an experience and that in and of it's self makes it worth-the-while.

[INDENT][INDENT]it is all a work in progress
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-28
I know it's been a few days, but in the end I decided to stick with it. I manually removed all the listed files with the exception of this /proc/sys/fs/binfmt_misc/wine. when I try ```
 sudo rm wine 
``` I get ```
rm: cannot remove 'wine': Operation not permitted
```. 

I suppose the next steps would be first figuring out how to remove the above file then move on to edit the index files? Where can I find those index files?

---

### Post by Bashing-om on 2013-08-28
Sky001; Hello ,,,
I'll hang with you and help the best I am able.
As to any file in "/proc" I do not think one need worry about any file that is there.. as "/proc" is a virtual file system in ram ... and does not survive through a reboot ... maybe have to worry about what is placing a file in "/proc"...

To that end have you looked at all the Wine related files in the  "/var/lib/dpkg/info/" directory ... seen all the files that are being tracked by the operating system .. and manually removed all those ???
let's see what is left in  "/var/lib/dpkg/info/" to give us some direction on what else to remove.
```

ls -la  /var/lib/dpkg/info/wine*

```
and anything interesting here ?:
```

less /var/lib/dpkg/status | grep wine

```
[INDENT][INDENT]tough row to hoe, but it is doable
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-08-30
> **Bashing-om said:**
> Sky001; Hello ,,,
I'll hang with you and help the best I am able.
As to any file in "/proc" I do not think one need worry about any file that is there.. as "/proc" is a virtual file system in ram ... and does not survive through a reboot ... maybe have to worry about what is placing a file in "/proc"...

To that end have you looked at all the Wine related files in the  "/var/lib/dpkg/info/" directory ... seen all the files that are being tracked by the operating system .. and manually removed all those ???
let's see what is left in  "/var/lib/dpkg/info/" to give us some direction on what else to remove.
```

ls -la  /var/lib/dpkg/info/wine*

```
and anything interesting here ?:
```

less /var/lib/dpkg/status/ | grep wine

```[INDENT][INDENT]tough row to hoe, but it is doable
[/INDENT]
[/INDENT]


Thanks for sticking around, you've been so very helpful so far. I'll be by my computer for the most part today. Hopefully we can have this problem solved. 

The code ```
ls -la /var/lib/dpkg/info/wine*
``` returns ```
ls: cannot access /var/lib/dpkg/info/wine*: No such file or directory
```

The code ```
 less /var/lib/dpkg/status/ | grep wine
``` returns ```
 /var/lib/dpkg/status/: Not a directory
```

Status is a file. Were you looking for something specific?

---

### Post by Jonathan Precise on 2013-08-30
> **Bashing-om said:**
> I like the option to attempt to (re-)install Wine and then properly remove it .. let the system do the work for us ..iffy though that it will install with no problems at this stage. But, worth a shot ?  .. Have you attempted at all to (re-)install Wine ?

Is PlayonLinux presently functional ? What are we going to break !
[INDENT][INDENT]may be a tough row to hoe
[/INDENT]
[/INDENT]


I have used wine and PlayOnLinux before. What I know is that PlayOnLinux depends on wine (as it is a front-end). So downgrading (or removing) wine might break PlayOnLinux and associated games/apps.

Before downgrading/removing wine, be aware the consequences that might arise.

  --Just trying to reduce breaks!

---

### Post by Jonathan Precise on 2013-08-30
> **Sky001 said:**
> Thanks for sticking around, you've been so very helpful so far. I'll be by my computer for the most part today. Hopefully we can have this problem solved. 

The code ```
ls -la /var/lib/dpkg/info/wine*
``` returns ```
ls: cannot access /var/lib/dpkg/info/wine*: No such file or directory
```

The code ```
 less /var/lib/dpkg/status/ | grep wine
``` returns ```
 /var/lib/dpkg/status/: Not a directory
```

Status is a file. Were you looking for something specific?

Try:

```
sudo ls -la /var/lib/dpkg/info | grep wine
sudo cat /var./lib/dpkg/status | grep wine
```

--Hope it works!

---

### Post by Sky001 on 2013-08-30
The first line of code doesn't return anything. The second returns
```
cat: /var./lib/dpkg/status: No such file or directory
```

I could just open status using gedit and copy paste the contents of that large file or whatever it's called. It is massive.

---

### Post by Jonathan Precise on 2013-08-31
My bad! I misspelled it!!!

Try:

```
sudo cat /var/lib/dpkg/status | grep wine
```

---

### Post by Sky001 on 2013-09-01
I'm amazed at what I found. 
```

$ sudo cat /var/lib/dpkg/status | grep wine
[sudo] password for saipal: 
Package: wine1.6-i386
Source: wine1.6
Replaces: wine-i386, wine1.4-i386, wine1.5-i386
Provides: wine-i386, wine1.4-i386, wine1.5-i386
Depends: libasound2 (>= 1.0.23), libc6 (>= 2.11), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.12.0), libglu1-mesa | libglu1, libgphoto2-2 (>= 2.4.10.1), libgphoto2-port0 (>= 2.4.10.1), libgstreamer-plugins-base0.10-0 (>= 0.10.22), libgstreamer0.10-0 (>= 0.10.26), liblcms1 (>= 1.15-1), libldap-2.4-2 (>= 2.4.7), libmpg123-0 (>= 1.6.2), libopenal1 (>= 1:1.13), libpulse0 (>= 1:0.99.1), libsm6, libx11-6, libxext6, libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4), wine1.6:any (= 1.6-0ubuntu1~ppa1), libncurses5
Recommends: libasound2-plugins, libcapi20-3, libcups2, libdbus-1-3, libfontconfig1 | libfontconfig, libfreetype6, libgif4, libgnutls26, libjpeg8, libosmesa6, libpng12-0, libsane, libtiff4, libv4l-0, libxcomposite1, libxcursor1, libxi6, libxinerama1, libxrandr2, libxrender1, libxslt1.1, libxt6, libxxf86vm1, unixodbc, wine-gecko2.21, wine-mono0.0.8
Conflicts: wine-i386
Homepage: http://www.winehq.org/
Package: wine-gecko1.4
Replaces: wine-gecko, wine1.2-gecko, wine1.3-gecko
Provides: wine-gecko
Recommends: wine1.4-i386
Breaks: wine-gecko (<< 1.4), wine1.2-gecko, wine1.3-gecko
Homepage: http://www.winehq.org/
Package: wine1.5
Source: wine1.6
Depends: wine1.6
Homepage: http://www.winehq.org/
Package: wine1.4
Replaces: ttf-symbol-replacement, ttf-symbol-replacement-wine1.3, ttf-tahoma-replacement, wine, wine1.0, wine1.2, wine1.3
Provides: wine
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.11), libgettextpo0, wine1.4-i386 (= 1.4.1-0ubuntu5), binfmt-support (>= 1.1.2), procps
Recommends: cups-bsd, gnome-exe-thumbnailer | kde-runtime, ttf-droid, ttf-liberation, ttf-mscorefonts-installer, ttf-umefont, ttf-unfonts-core, ttf-wqy-microhei, winbind, winetricks, xdg-utils
Breaks: ttf-symbol-replacement, ttf-symbol-replacement-wine1.3, ttf-tahoma-replacement, wine (<< 1.2.1), wine1.2 (<< 1.4-0ubuntu1), wine1.3 (<< 1.4-0ubuntu1)
Conflicts: wine1.0
 /etc/xdg/menus/applications-merged/wine.menu d15dadc3527b2c6dca96023a5351aedc obsolete
Homepage: http://www.winehq.org/
Package: wine1.6
Replaces: wine, wine1.0, wine1.2, wine1.3, wine1.4, wine1.5
Provides: wine
Depends: debconf (>= 0.5) | debconf-2.0, libc6 (>= 2.11), libgettextpo0, wine1.6-i386 (= 1.6-0ubuntu1~ppa1), binfmt-support (>= 1.1.2), procps
Recommends: cups-bsd, gnome-exe-thumbnailer | kde-runtime, fonts-droid, fonts-liberation, ttf-mscorefonts-installer, fonts-horai-umefont, fonts-unfonts-core, ttf-wqy-microhei, winbind, winetricks, xdg-utils
Conflicts: wine1.0, wine1.2, wine1.3, wine1.4
 /etc/xdg/menus/applications-merged/wine.menu d15dadc3527b2c6dca96023a5351aedc
Homepage: http://www.winehq.org/
Description: This program is a front-end for wine.
 and several wine versions.
Package: wine-gecko2.21
Replaces: wine-gecko, wine1.2-gecko, wine1.3-gecko
Provides: wine-gecko
Recommends: wine1.5-i386
Breaks: wine-gecko (<< 1.4), wine1.2-gecko, wine1.3-gecko
Homepage: http://www.winehq.org/
Package: winetricks
Recommends: wine1.5 | wine1.4 | wine | cxoffice5 | cxgames5, unrar
Description: Microsoft Windows Compatibility Layer (winetricks)
Homepage: http://winetricks.org/
Package: wine-mono0.0.8
Provides: wine-mono
Recommends: wine1.5
Homepage: http://www.winehq.org/
Package: wine1.4-i386
Source: wine1.4
Replaces: wine (<< 1.2.1), wine1.2, wine1.3
Provides: wine-i386
Depends: libasound2 (>= 1.0.16), libc6 (>= 2.9), libgl1-mesa-glx | libgl1, libglib2.0-0 (>= 2.24.0), libglu1-mesa | libglu1, libgphoto2-2 (>= 2.4.10.1), libgphoto2-port0 (>= 2.4.10.1), libgstreamer-plugins-base0.10-0 (>= 0.10.22), libgstreamer0.10-0 (>= 0.10.26), liblcms1 (>= 1.15-1), libldap-2.4-2 (>= 2.4.7), libmpg123-0 (>= 1.13.7), libopenal1 (>= 1:1.13), libsm6, libx11-6, libxext6, libxml2 (>= 2.7.4), zlib1g (>= 1:1.1.4), wine1.4:any (= 1.4.1-0ubuntu5), libncurses5
Recommends: libasound2-plugins, libcapi20-3, libcups2, libdbus-1-3, libfontconfig1 | libfontconfig, libfreetype6, libgif4, libgnutls26, libjpeg8, libp11-kit-gnome-keyring, libpng12-0, libsane, libssl1.0.0, libtiff5, libv4l-0, libxcomposite1, libxcursor1, libxi6, libxinerama1, libxrandr2, libxrender1, libxslt1.1, libxt6, libxxf86vm1, unixodbc, wine-gecko1.4
Breaks: wine (<< 1.2.1), wine1.2 (<< 1.4-0ubuntu1), wine1.3 (<< 1.4-0ubuntu1)
Homepage: http://www.winehq.org/
```

---

### Post by Bashing-om on 2013-09-01
@ Jonathon; Thanks for taking up my slack.
Moving things along.

@ Sky001 as Jonathon advises, playonlinux is dependent on Wine:
> 
sysop@1304mini:~$ apt-cache search playonlinux
playonlinux - front-end for Wine
sysop@1304mini:~$

And we need to remove it from the system.
If you installed playonlinux within ubuntu's package management system, do in terminal:
```

sudo apt-get remove --purge playonlinux

```
else advise how you installed playonlinux.

If that goes well .. let's continue the cleanup of Wine's removal. We are going to, for the next step, hunt up any remaining Wine files, and remove any found:
```

sudo find / -name "wine1.6*"
sudo find / -name "wine1.5*"
sudo find / -name "wine1.4*"
sudo find / -name wine-i386
sudo find / -name "wine-gecko*"
sudo find / -name wine1.2-gecko
sudo find / -name wine1.3-gecko
sudo find / -name wine-mono

```
Next steps depend on completion of these removals, hopefully we are getting close to closure at that point.
If any uncertainties are encountered, by all means pause and inquire for confirmations.

[INDENT][INDENT]dirty way but it is a way
[/INDENT][/INDENT]

---

### Post by Sky001 on 2013-09-03
Thanks for the follow up. 

I installed play on linux using Ubuntu Software Center. As for removing PlayOnLinux. My computer refuses to install, upgrade, or remove any packages. I've tried installing several things these past weeks. From the Linux version of Java to suite programs like Open Office, to a new web browser. The same old error is returned. The terminal returns it, Synaptic does so as well. The Ubuntu Software Center just hangs, fails and gives an error message box. 

I'm running the seven listed code lines. I hope all goes well. They seem to take a little while to execute.

Edit: to append.
Terminal just got done running the seven lines of code. Nothing alarming was returned: In fact, nothing was returned. Was that what I should be looking for? What should I do next?

---

### Post by Bashing-om on 2013-09-03
Sky001; Yuk !

That does make it a bit more of a challenge... Chances are will have to repeat this hunt/manually remove files for "playonlinux" also .. sure hope not .. play it by ear and see what results when "Wine" is over and done with. When the "Wine" hunting/removing is completed will have to make a manual edit to the "/var/lib/dpkg/status" file .. before doing anything else. -> checking for dependencies no longer met and what not.

And yes that "find" command takes a while as it is searching through the whole file system on each invocation.

[INDENT][INDENT]try'n to hang with you
[/INDENT][/INDENT]

---


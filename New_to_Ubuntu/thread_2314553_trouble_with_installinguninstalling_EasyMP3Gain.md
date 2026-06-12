---
title: "trouble with installing/uninstalling EasyMP3Gain"
date: 2016-02-22
forum: New to Ubuntu
---

### Post by fotoflex on 2016-02-22
Yesterday I tried to install EasyMP3Gain via the Software Center.
I got a message about a broken package and was given the option to repair it.
I did this, but it was still not okay.
The program did work, however, and I modified the volume of several files.
When I turned the computer back on today I hoped that the problem had solved itself as is often the case after restarting.
But no, not this time.
I saw a round red traffic sign with a white bar on top of the screen, indicating something is wrong with the updates.
Apparently, updating is not possible because of a conflict with existing programs.
So I tried to remove EasyMP3Gain, but can't, because the package is broken and I was again given the option to repair it, which didn't work.
Neither can I install any new programs.
( I hoped re-installing EMP3G might do the trick )
And then I got the message that the Software Center had experienced an internal error.
Wits. end.
Anybody any suggestions? :confused:

---

### Post by oldos2er on 2016-02-22
What version of Ubuntu are you running? 

Try ```
sudo apt-get clean

sudo apt-get install -f
``` If there are errors please copy/paste the entire terminal output here.

---

### Post by goofprog on 2016-02-22
I had to dig deeper because the broken packages were still coming up because broken packages would not reinstall so I dig this up on the 'net
edit this file but it is dangerous to edit as a guess **/var/lib/dpkg/status**
Look for the package name and delete the whole entry and resave the file.

---

### Post by fotoflex on 2016-02-23
Sorry! 14.04 LTS.

This what was in the terminal:

```
fotoflex@fotoflex-Toshiba:~$ sudo apt-get clean
[sudo] password for fotoflex: 
fotoflex@fotoflex-Toshiba:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-nl libbit-vector-perl libcarp-clan-perl
  libdate-calc-perl libdate-calc-xs-perl libyaml-0-2 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-headers-3.13.0-48
  linux-headers-3.13.0-48-generic linux-headers-3.13.0-49
  linux-headers-3.13.0-49-generic linux-headers-3.13.0-51
  linux-headers-3.13.0-51-generic linux-headers-3.13.0-53
  linux-headers-3.13.0-53-generic linux-headers-3.13.0-54
  linux-headers-3.13.0-54-generic linux-headers-3.13.0-55
  linux-headers-3.13.0-55-generic linux-headers-3.13.0-57
  linux-headers-3.13.0-57-generic linux-headers-3.13.0-58
  linux-headers-3.13.0-58-generic linux-headers-3.13.0-61
  linux-headers-3.13.0-61-generic linux-headers-3.13.0-62
  linux-headers-3.13.0-62-generic linux-headers-3.13.0-63
  linux-headers-3.13.0-63-generic linux-headers-3.13.0-65
  linux-headers-3.13.0-65-generic linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-headers-3.13.0-67
  linux-headers-3.13.0-67-generic linux-headers-3.13.0-68
  linux-headers-3.13.0-68-generic linux-headers-3.13.0-70
  linux-headers-3.13.0-70-generic linux-headers-3.13.0-71
  linux-headers-3.13.0-71-generic linux-headers-3.13.0-73
  linux-headers-3.13.0-73-generic linux-headers-3.13.0-74
  linux-headers-3.13.0-74-generic linux-image-3.13.0-24-generic
  linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-51-generic linux-image-3.13.0-53-generic
  linux-image-3.13.0-54-generic linux-image-3.13.0-55-generic
  linux-image-3.13.0-57-generic linux-image-3.13.0-58-generic
  linux-image-3.13.0-61-generic linux-image-3.13.0-62-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-65-generic
  linux-image-3.13.0-66-generic linux-image-3.13.0-67-generic
  linux-image-3.13.0-68-generic linux-image-3.13.0-70-generic
  linux-image-3.13.0-71-generic linux-image-3.13.0-73-generic
  linux-image-3.13.0-74-generic linux-image-extra-3.13.0-24-generic
  linux-image-extra-3.13.0-48-generic linux-image-extra-3.13.0-49-generic
  linux-image-extra-3.13.0-51-generic linux-image-extra-3.13.0-53-generic
  linux-image-extra-3.13.0-54-generic linux-image-extra-3.13.0-55-generic
  linux-image-extra-3.13.0-57-generic linux-image-extra-3.13.0-58-generic
  linux-image-extra-3.13.0-61-generic linux-image-extra-3.13.0-62-generic
  linux-image-extra-3.13.0-63-generic linux-image-extra-3.13.0-65-generic
  linux-image-extra-3.13.0-66-generic linux-image-extra-3.13.0-67-generic
  linux-image-extra-3.13.0-68-generic linux-image-extra-3.13.0-70-generic
  linux-image-extra-3.13.0-71-generic linux-image-extra-3.13.0-73-generic
  linux-image-extra-3.13.0-74-generic python-appindicator
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  easymp3gain-data
The following NEW packages will be installed:
  easymp3gain-data
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 62,5 kB of archives.
After this operation, 236 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 [http://ubuntu-archive.mirror.nucleus.be/](http://ubuntu-archive.mirror.nucleus.be/) trusty/universe easymp3gain-data all 0.5.0+svn135-4 [62,5 kB]
Fetched 62,5 kB in 0s (192 kB/s)      
(Reading database ... 1018180 files and directories currently installed.)
Preparing to unpack .../easymp3gain-data_0.5.0+svn135-4_all.deb ...
Unpacking easymp3gain-data (0.5.0+svn135-4) ...
dpkg: error processing archive /var/cache/apt/archives/easymp3gain-data_0.5.0+svn135-4_all.deb (--unpack):
 trying to overwrite '/usr/share/icons/hicolor/48x48/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
Processing triggers for hicolor-icon-theme (0.13-1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/easymp3gain-data_0.5.0+svn135-4_all.deb
W: Duplicate sources.list entry [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_chrome_deb_dists_stable_main_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Thanks.

---

### Post by fotoflex on 2016-02-23
> **goofprog said:**
> I had to dig deeper because the broken packages were still coming up because broken packages would not reinstall so I dig this up on the 'net
edit this file but it is dangerous to edit as a guess **/var/lib/dpkg/status**
Look for the package name and delete the whole entry and resave the file.

Thank you.
But I have no idea of what I'm doing, so I'm not gonna try something 'dangerous'.
Should I do something wrong, I would not be able to fix it. :)

---

### Post by oldos2er on 2016-02-23
Wise not to do anything "dangerous." @goofprog, this is **New to Ubuntu** so it would be best not to recommend dangerous procedures or commands.

Let's try ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/easymp3gain-data_0.5.0+svn135-4_all.deb
``` Again please copy/paste all the terminal output here.

---

### Post by fotoflex on 2016-02-23
> **oldos2er said:**
> Wise not to do anything "dangerous." @goofprog, this is **New to Ubuntu** so it would be best not to recommend dangerous procedures or commands.

Let's try ```
sudo dpkg -i --force-overwrite /var/cache/apt/archives/easymp3gain-data_0.5.0+svn135-4_all.deb
``` Again please copy/paste all the terminal output here.

Thanks very much.
Wel, I tried that and after the restart and seariching for updates, two things happened; I got a message that updating was not possible and to check my internet connection, and secondly, a message that updates were available, the laptop is installing them now.
That is confusing.
Furthermore, in the program list, EasyMP3Gain is available twice.
Anyway, here is what was in the terminal:

```
fotoflex@fotoflex-Toshiba:~$ sudo dpkg -i --force-overwrite /var/cache/apt/archives/easymp3gain-data_0.5.0+svn135-4_all.deb
[sudo] password for fotoflex: 
(Reading database ... 1018180 files and directories currently installed.)
Preparing to unpack .../easymp3gain-data_0.5.0+svn135-4_all.deb ...
Unpacking easymp3gain-data (0.5.0+svn135-4) ...
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/48x48/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/22x22/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/16x16/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/128x128/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/192x192/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/32x32/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/64x64/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/icons/hicolor/24x24/apps/easymp3gain.png', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/easymp3gain/help/install.html', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/easymp3gain/help/index.html', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/easymp3gain/help/index.de.html', which is also in package easymp3gain-gtk2 0.5.0-2
dpkg: warning: overriding problem because --force enabled:
dpkg: warning: trying to overwrite '/usr/share/easymp3gain/help/install.de.html', which is also in package easymp3gain-gtk2 0.5.0-2
Setting up easymp3gain-data (0.5.0+svn135-4) ...
Processing triggers for hicolor-icon-theme (0.13-1) ...
```

---

### Post by mc4man on 2016-02-23
It appears you have an old version of easymp3gain-gtk. If you were to remove it, update your sources & re-install could be ok.
Otherwise post results of this
```
apt-cache policy easymp3gain*
```

---

### Post by fotoflex on 2016-02-23
> **mc4man said:**
> It appears you have an old version of easymp3gain-gtk. If you were to remove it, update your sources & re-install could be ok.
Otherwise post results of this
```
apt-cache policy easymp3gain*
```

It was indeed 0.5.0-1, which I installed from Ubuntu Software Center.
The new one, which I downloaded from Sourceforce, is 0.5.0 -2.
But I'm sorry to say that the new version doesn't even open.

Here's the terminal text:

fotoflex@fotoflex-Toshiba:~$ apt-cache policy easymp3gain*
easymp3gain-qt4:
  Installed: (none)
  Candidate: (none)
  Version table:
easymp3gain-gtk:
  Installed: (none)
  Candidate: 0.5.0+svn135-4
  Version table:
     0.5.0+svn135-4 0
        500 [http://ubuntu-archive.mirror.nucleus.be/](http://ubuntu-archive.mirror.nucleus.be/) trusty/universe i386 Packages
easymp3gain-dbg:
  Installed: (none)
  Candidate: 0.5.0+svn135-4
  Version table:
     0.5.0+svn135-4 0
        500 [http://ubuntu-archive.mirror.nucleus.be/](http://ubuntu-archive.mirror.nucleus.be/) trusty/universe i386 Packages
easymp3gain-gtk1:
  Installed: (none)
  Candidate: (none)
  Version table:
easymp3gain-gtk2:
  Installed: 0.5.0-2
  Candidate: 0.5.0-2
  Version table:
 *** 0.5.0-2 0
        100 /var/lib/dpkg/status
easymp3gain-qt:
  Installed: (none)
  Candidate: 0.5.0+svn135-4
  Version table:
     0.5.0+svn135-4 0
        500 [http://ubuntu-archive.mirror.nucleus.be/](http://ubuntu-archive.mirror.nucleus.be/) trusty/universe i386 Packages
easymp3gain-data:
  Installed: (none)
  Candidate: 0.5.0+svn135-4
  Version table:
     0.5.0+svn135-4 0
        500 [http://ubuntu-archive.mirror.nucleus.be/](http://ubuntu-archive.mirror.nucleus.be/) trusty/universe i386 Packages
easymp3gain-gtk-dbg:
  Installed: (none)
  Candidate: (none)
  Version table:

---

### Post by mc4man on 2016-02-24
Remove the sourceforge package, update your sources & then install easymp3gain-gtk
This should work - 
```
sudo apt-get purge easymp3gain-gtk2
```
```
sudo apt-get update && sudo apt-get install easymp3gain-gtk
```

---

### Post by fotoflex on 2016-02-24
> **mc4man said:**
> Remove the sourceforge package, update your sources & then install easymp3gain-gtk
This should work - 
```
sudo apt-get purge easymp3gain-gtk2
```
```
sudo apt-get update && sudo apt-get install easymp3gain-gtk
```

Thanks.
The first code is to remove the sourceforge package, or do I need to do that another way?

---

### Post by mc4man on 2016-02-24
> **fotoflex said:**
> Thanks.
The first code is to remove the sourceforge package, or do I need to do that another way?
Yes, 1st removes sf package.
Note that easymp3gain project is dead so what's on sf is not 'newer', last commits are from 2013.
What's available from Ubuntu repo's is just as 'new', main difference is it may actually work.

From changelog for 14.04 (will also be available for 16.04, then that'll be that..
> easymp3gain (0.5.0+svn135-5) unstable; urgency=medium

  * NOTE: This upload is done due to user-request who like
    easyMp3Gain. However, the software is dead upstream, and
    mp3gain is removed from Debian.
    So if nobody takes over maintenance upstream, this package will
    be removed from Debian soon.
  * Make vorbisgain the default CLI tool
  * Depend on lcl-utils, drop lazarus dependency (Closes: #741812)

---

### Post by fotoflex on 2016-02-25
Thanks.
Sorry to say that the program still doesn't appear as available for opening.
Here's the terminal text:

```
fotoflex@fotoflex-Toshiba:~$ sudo apt-get purge easymp3gain-gtk2
[sudo] password for fotoflex: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kde-l10n-engb kde-l10n-nl libbit-vector-perl libcarp-clan-perl
  libdate-calc-perl libdate-calc-xs-perl libyaml-0-2 linux-headers-3.13.0-24
  linux-headers-3.13.0-24-generic linux-headers-3.13.0-48
  linux-headers-3.13.0-48-generic linux-headers-3.13.0-49
  linux-headers-3.13.0-49-generic linux-headers-3.13.0-51
  linux-headers-3.13.0-51-generic linux-headers-3.13.0-53
  linux-headers-3.13.0-53-generic linux-headers-3.13.0-54
  linux-headers-3.13.0-54-generic linux-headers-3.13.0-55
  linux-headers-3.13.0-55-generic linux-headers-3.13.0-57
  linux-headers-3.13.0-57-generic linux-headers-3.13.0-58
  linux-headers-3.13.0-58-generic linux-headers-3.13.0-61
  linux-headers-3.13.0-61-generic linux-headers-3.13.0-62
  linux-headers-3.13.0-62-generic linux-headers-3.13.0-63
  linux-headers-3.13.0-63-generic linux-headers-3.13.0-65
  linux-headers-3.13.0-65-generic linux-headers-3.13.0-66
  linux-headers-3.13.0-66-generic linux-headers-3.13.0-67
  linux-headers-3.13.0-67-generic linux-headers-3.13.0-68
  linux-headers-3.13.0-68-generic linux-headers-3.13.0-70
  linux-headers-3.13.0-70-generic linux-headers-3.13.0-71
  linux-headers-3.13.0-71-generic linux-headers-3.13.0-73
  linux-headers-3.13.0-73-generic linux-headers-3.13.0-74
  linux-headers-3.13.0-74-generic linux-headers-3.13.0-76
  linux-headers-3.13.0-76-generic linux-image-3.13.0-24-generic
  linux-image-3.13.0-48-generic linux-image-3.13.0-49-generic
  linux-image-3.13.0-51-generic linux-image-3.13.0-53-generic
  linux-image-3.13.0-54-generic linux-image-3.13.0-55-generic
  linux-image-3.13.0-57-generic linux-image-3.13.0-58-generic
  linux-image-3.13.0-61-generic linux-image-3.13.0-62-generic
  linux-image-3.13.0-63-generic linux-image-3.13.0-65-generic
  linux-image-3.13.0-66-generic linux-image-3.13.0-67-generic
  linux-image-3.13.0-68-generic linux-image-3.13.0-70-generic
  linux-image-3.13.0-71-generic linux-image-3.13.0-73-generic
  linux-image-3.13.0-74-generic linux-image-3.13.0-76-generic
  linux-image-extra-3.13.0-24-generic linux-image-extra-3.13.0-48-generic
  linux-image-extra-3.13.0-49-generic linux-image-extra-3.13.0-51-generic
  linux-image-extra-3.13.0-53-generic linux-image-extra-3.13.0-54-generic
  linux-image-extra-3.13.0-55-generic linux-image-extra-3.13.0-57-generic
  linux-image-extra-3.13.0-58-generic linux-image-extra-3.13.0-61-generic
  linux-image-extra-3.13.0-62-generic linux-image-extra-3.13.0-63-generic
  linux-image-extra-3.13.0-65-generic linux-image-extra-3.13.0-66-generic
  linux-image-extra-3.13.0-67-generic linux-image-extra-3.13.0-68-generic
  linux-image-extra-3.13.0-70-generic linux-image-extra-3.13.0-71-generic
  linux-image-extra-3.13.0-73-generic linux-image-extra-3.13.0-74-generic
  linux-image-extra-3.13.0-76-generic python-appindicator
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  easymp3gain-gtk2*
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
After this operation, 3478 kB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 1048096 files and directories currently installed.)
Removing easymp3gain-gtk2 (0.5.0-2) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for hicolor-icon-theme (0.13-1) ...
fotoflex@fotoflex-Toshiba:~$ sudo apt-get update && sudo apt-get install easymp3gain-gtk
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty InRelease                   
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates InRelease           
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports InRelease         
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg                                
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security InRelease          
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat InRelease          
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Ign [http://mega.nz](http://mega.nz) ./ InRelease                                                
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages                       
Get:1 [http://mega.nz](http://mega.nz) ./ Release.gpg [189 B]                                    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Get:2 [http://mega.nz](http://mega.nz) ./ Release [967 B]                                        
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release.gpg                 
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main i386 Packages 
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Sources        
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Sources  
Get:3 [http://mega.nz](http://mega.nz) ./ Packages [1177 B]                                      
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Sources    
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Sources  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en_US                   
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main i386 Packages  
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en                      
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted i386 Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse i386 Packages
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Translation-en 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en_US
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://mega.nz](http://mega.nz) ./ Translation-en_US                                        
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Sources      
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Sources  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Translation-en
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Sources       
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Sources 
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages                         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Sources   
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Sources 
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main i386 Packages 
Ign [http://mega.nz](http://mega.nz) ./ Translation-en                                           
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse i386 Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Translation-en
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
  404  Not Found
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release                     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Sources                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Sources          
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Sources            
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Sources
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en         
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en_US  
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US                     
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Fetched 2333 B in 19s (121 B/s)                                                
W: Failed to fetch [http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.
```

---

### Post by mc4man on 2016-02-26
With a bad source list entry I guess the 2nd command didn't run so just do it alone now.
```
sudo apt-get install easymp3gain-gtk
```

---

### Post by fotoflex on 2016-02-26
> **mc4man said:**
> With a bad source list entry I guess the 2nd command didn't run so just do it alone now.
```
sudo apt-get install easymp3gain-gtk
```

Thanks again.
EasyMP3gain is back, which is the good news.
Bot now the sign has turned into an orange triangle.
That I have seen before and with help from the forum was able to remove it
So I ran apt get update, result posted below
I think Popcorn might be the problem since it doesn't exist anymore, but I can't remove it the same way I used last time.
Of course I'm not certain Popcorn is the problem, maybe you can spot some other cause?


 fotoflex@fotoflex-Toshiba:~$ sudo apt-get update[sudo] password for fotoflex: 
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty InRelease
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Get:1 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates InRelease [65,9 kB]
Ign [http://archive.canonical.com](http://archive.canonical.com) trusty InRelease                              
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty InRelease                                  
Ign [http://dl.google.com](http://dl.google.com) stable InRelease                                      
Ign [http://mega.nz](http://mega.nz) ./ InRelease                                                
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat InRelease          
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty InRelease                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release.gpg                            
Get:2 [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release.gpg [72 B]                       
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty InRelease                                  
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg                                    
Get:3 [http://mega.nz](http://mega.nz) ./ Release.gpg [189 B]                                    
Get:4 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports InRelease [65,9 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty Release                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty Release                                    
Hit [http://dl.google.com](http://dl.google.com) stable Release                                        
Get:5 [http://mega.nz](http://mega.nz) ./ Release [967 B]                                        
Get:6 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security InRelease [65,9 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty InRelease                                  
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release.gpg                                
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release.gpg                 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main i386 Packages 
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty Release                     
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Hit [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main i386 Packages                       
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty Release                                    
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release.gpg                                
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Get:7 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Sources [260 kB]
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner i386 Packages                  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages/DiffIndex               
Hit [http://archive.canonical.com](http://archive.canonical.com) trusty/partner Translation-en                 
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Sources                               
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main i386 Packages                         
Hit [http://dl.google.com](http://dl.google.com) stable/main i386 Packages                             
Get:8 [http://mega.nz](http://mega.nz) ./ Packages [1177 B]                                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty Release                                    
Get:9 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Sources [5352 B]
Get:10 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Sources [150 kB]
Get:11 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Sources [5547 B]
Get:12 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main i386 Packages [689 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en_US                   
Ign [http://deb.playonlinux.com](http://deb.playonlinux.com) trusty/main Translation-en                      
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main amd64 Packages                        
Get:13 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted i386 Packages [15,6 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en_US
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en_US                     
Get:14 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe i386 Packages [339 kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                         
Ign [http://download.mono-project.com](http://download.mono-project.com) wheezy-apache24-compat/main Translation-en
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) trusty/main Translation-en                        
Get:15 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse i386 Packages [13,4 kB]
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en                            
Hit [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main i386 Packages                         
Get:16 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/main Translation-en [359 kB]
Get:17 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/multiverse Translation-en [6947 B]
Get:18 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/restricted Translation-en [3699 B]
Get:19 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-updates/universe Translation-en [180 kB]
Get:20 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Sources [8661 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Ign [http://mega.nz](http://mega.nz) ./ Translation-en_US                                        
Get:21 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Sources [28 B]
Get:22 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Sources [33,2 kB]
Ign [http://mega.nz](http://mega.nz) ./ Translation-en                                           
Get:23 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Sources [1898 B]
Get:24 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main i386 Packages [9814 B]
Get:25 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted i386 Packages [28 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main i386 Packages                      
  404  Not Found
Get:26 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe i386 Packages [40,0 kB]
Get:27 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse i386 Packages [1552 B]
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/main Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-backports/universe Translation-en
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:28 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Sources [105 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:29 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Sources [4035 B]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en_US                     
Get:30 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Sources [33,0 kB]
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) trusty/main Translation-en                        
Get:31 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Sources [2767 B]
Get:32 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main i386 Packages [399 kB]
Get:33 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted i386 Packages [12,7 kB]
Get:34 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe i386 Packages [124 kB]
Get:35 [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse i386 Packages [5164 B]
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/main Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty-security/universe Translation-en
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en_US                 
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Sources            
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Sources      
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Sources            
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Sources          
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main i386 Packages          
Ign [http://linux.dropbox.com](http://linux.dropbox.com) trusty/main Translation-en                        
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted i386 Packages    
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe i386 Packages  
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse i386 Packages
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en     
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en
Hit [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/main Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/multiverse Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/restricted Translation-en_US
Ign [http://ubuntu-archive.mirror.nucleus.be](http://ubuntu-archive.mirror.nucleus.be) trusty/universe Translation-en_US  
Fetched 3008 kB in 15s (190 kB/s)                                              
W: Failed to fetch [http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu/dists/trusty/main/binary-i386/Packages](http://ppa.launchpad.net/webupd8team/popcorntime/ubuntu/dists/trusty/main/binary-i386/Packages)  404  Not Found


E: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by mc4man on 2016-02-28
Remove the webupd8 ppa for popcorntime as it (the ppa) no longer exists

---

### Post by fotoflex on 2016-02-28
> **mc4man said:**
> Remove the webupd8 ppa for popcorntime as it (the ppa) no longer exists

Oh yes!!
I removed that the way advised to me last time, then it was samrog ppa.
And I saw samrog had returned, so I removed that as well. (What is samrog and how does it come back?)
Anyway, the result was a clean update.

So, thanks again to all and especially mc4man

---


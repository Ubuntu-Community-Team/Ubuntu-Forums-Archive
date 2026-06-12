---
title: "[SOLVED] Add/Remove Program not Working"
date: 2008-07-28
forum: New to Ubuntu
---

### Post by mochiko on 2008-07-28
I need to install VLC again and so I opened up the Add remove program but a little window pops up and says this:

> Failed to check for installed and available applications

This is a major failure of your software management system. Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'.

I don't know how to correct the sources.list file but I know how to edit stuff, i just don't know how it's "supposed" to be. 

also what is kio-unmountsomethingsomething? is this related at all?

when i typed some stuff to get an update in the terminal, this is what i got:

```
chitra@chitra-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-pylibacl libwxbase2.6-0 libmysqlclient15off vcdimager libqt4-test
  libqt4-script libqt4-network libqt4-dbus videolan-doc libapr1 libiso9660-5
  kdeedu-data openvpn-blacklist libdvbpsi4 network-manager-pptp pptp-linux
  libxosd2 procmail libx264-57 libvlc0 libwxgtk2.6-0 network-manager-openvpn
  libqtcore4 pinentry-curses gtk2-engines-qtcurve libmatroska0 freepats
  libiptcdata0 liba52-0.7.4 ocrad localechooser-data libqt4-sql libwildmidi0
  libdvdnav4 vpnc libqt4-xml libdc1394-13 libqt4-assistant libcdaudio1
  network-manager-vpnc libxvidcore4 libsidplay1 zoo mpg123 libsoundtouch1c2
  libid3tag0 pmount libgmyth0 resolvconf libtar openvpn libqt4-sql-mysql
  libvcdinfo0 libebml0 mysql-common python-pyxattr libmpeg2-4 libmms0 libfaac0
  libfaad0
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 169423 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
chitra@chitra-laptop:~$ sudo apt-get remove

```

Not sure what's going on, or how to fix it..

---

### Post by eightmillion on 2008-07-28
Try this command.
> sudo apt-get -f install

---

### Post by mochiko on 2008-07-28
> **eightmillion said:**
> Try this command.

okie, here's what i get:

```
E: Sub-process /usr/bin/dpkg returned an error code (1)
chitra@chitra-laptop:~$ 
chitra@chitra-laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167984 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
chitra@chitra-laptop:~$ 

```

After i did that, this little notification came up saying some application crashed and it said this kiounmountwrapper thing failed to install or upgrade.

thanks for the fast reply though, hahah..

---

### Post by candtalan on 2008-07-28
> **mochiko said:**
> I need to install VLC again and so I opened up the Add remove program but a little window pops up and says this:

[big snip]

Not sure what's going on, or how to fix it..

You seem to be going along the right lines
however I note that the final command that you used was remove and not autoremove as suggested halfway down your quoted code list?

---

### Post by candtalan on 2008-07-28
it is possible that you have found a little bug......
It looks similar to

[Bug 250086] [NEW] Could not completly remove "kio-umountwrapper" package
murmeln
Sat, 19 Jul 2008 05:40:41 -0700

[http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg926472.html](http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg926472.html)

---

### Post by mochiko on 2008-07-28
> **candtalan said:**
> You seem to be going along the right lines
however I note that the final command that you used was remove and not autoremove as suggested halfway down your quoted code list?

i've also tried autoremove, here:
```

chitra@chitra-laptop:~$ sudo apt-get autoremove
[sudo] password for chitra: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kio-umountwrapper
0 upgraded, 0 newly installed, 1 to remove and 28 not upgraded.
1 not fully installed or removed.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 167984 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)
chitra@chitra-laptop:~$ 
```

A bug? Shioot. 
nooooooooooo... i don't even know what that means.. is it like a virus? 

blegh..

---

### Post by Sef on 2008-07-28
> A bug? Shioot.
nooooooooooo... i don't even know what that means.. is it like a virus? 

A bug is a flaw in the way the software was written.

---

### Post by ad_267 on 2008-07-28
Not sure if it would help but you could try "sudo apt-get purge kio-umountwrapper"

---

### Post by tinny on 2008-07-28
Please post the contents of /etc/apt/sources.list

```

gedit /etc/apt/sources.list

```

Also you could try to first clean the APT cache before fixing packages,

```

sudo apt-get clean
sudo apt-get update
sudo apt-get install -f

```

---

### Post by th3james on 2008-07-28
Have you tried fixing broken packages in synaptic? System -> Admin -> Synaptic, then Edit -> Fix Broken Packages. Usually helps when i get similar messages

---

### Post by mochiko on 2008-07-28
> **tinny said:**
> Please post the contents of /etc/apt/sources.list

```

[COLOR="Navy"]gedit /etc/apt/sources.list[/COLOR]

```

Right, I've got that here:

```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release Candidate amd64 (20080417)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main universe restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main universe restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main universe restricted multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu hardy partner
deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-proposed main universe restricted multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb-src http://ppa.launchpad.net/awn-testing/ubuntu hardy main
deb http://apt.wicd.net hardy extras

# Mactel PPA
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

# Remastersys
deb http://security.ubuntu.com/ubuntu/ hardy-security universe main multiverse restricted
deb http://www.remastersys.klikit-linux.com/repository remastersys/[CODE]
```[/CODE]

Also you could try to first clean the APT cache before fixing packages,

```

[COLOR="Navy"]sudo apt-get clean
sudo apt-get update
sudo apt-get install -f[/COLOR]

```

As for that, nothing seems to happen when i do sudo apt-get clean(but maybe that's supposed to happen).

When i do sudo apt-get update, there are no error messages but it says it fetched 3 B in 3 secs.. i dunno i get a weird feeling about it. 

```
chitra@chitra-laptop:~$ sudo apt-get update
Ign http://apt.wicd.net hardy Release.gpg                                      
Ign http://apt.wicd.net hardy/extras Translation-en_AU                         
Ign http://www.remastersys.klikit-linux.com remastersys/ Release.gpg           
Ign http://www.remastersys.klikit-linux.com remastersys/ Translation-en_AU     
Hit http://security.ubuntu.com hardy-security Release.gpg                      
Ign http://security.ubuntu.com hardy-security/main Translation-en_AU           
Get:1 http://apt.wicd.net hardy Release [29.1kB]                               
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://ppa.launchpad.net hardy/main Translation-en_AU                      
Ign http://ppa.launchpad.net hardy Release.gpg                                 
Ign http://www.remastersys.klikit-linux.com remastersys/ Release               
Hit http://apt.wicd.net hardy/extras Packages                                  
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_AU     
Ign http://security.ubuntu.com hardy-security/universe Translation-en_AU       
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_AU     
Hit http://security.ubuntu.com hardy-security Release                          
Hit http://archive.canonical.com hardy Release.gpg                             
Ign http://archive.canonical.com hardy/partner Translation-en_AU               
Hit http://us.archive.ubuntu.com hardy Release.gpg                             
Ign http://us.archive.ubuntu.com hardy/main Translation-en_AU                  
Ign http://ppa.launchpad.net hardy/main Translation-en_AU                      
Get:2 http://ppa.launchpad.net hardy Release [27.6kB]                          
Ign http://www.remastersys.klikit-linux.com remastersys/ Packages              
Hit http://security.ubuntu.com hardy-security/main Packages                    
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_AU              
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_AU            
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_AU            
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg                     
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_AU          
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_AU      
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_AU    
Hit http://archive.canonical.com hardy Release                                 
Get:3 http://ppa.launchpad.net hardy Release [27.6kB]                          
Hit http://www.remastersys.klikit-linux.com remastersys/ Packages    
Hit http://security.ubuntu.com hardy-security/restricted Packages    
Hit http://security.ubuntu.com hardy-security/main Sources           
Hit http://security.ubuntu.com hardy-security/universe Packages      
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_AU
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg         
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_AU
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_AU    
Hit http://archive.canonical.com hardy/partner Packages                        
Ign http://ppa.launchpad.net hardy/main Packages                               
Ign http://ppa.launchpad.net hardy/main Sources                                
Hit http://security.ubuntu.com hardy-security/universe Sources                 
Hit http://security.ubuntu.com hardy-security/multiverse Packages              
Hit http://security.ubuntu.com hardy-security/multiverse Sources               
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_AU  
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_AU
Hit http://us.archive.ubuntu.com hardy-proposed Release.gpg          
Ign http://us.archive.ubuntu.com hardy-proposed/main Translation-en_AU
Ign http://us.archive.ubuntu.com hardy-proposed/universe Translation-en_AU
Ign http://us.archive.ubuntu.com hardy-proposed/restricted Translation-en_AU
Ign http://us.archive.ubuntu.com hardy-proposed/multiverse Translation-en_AU
Hit http://archive.canonical.com hardy/partner Sources               
Ign http://ppa.launchpad.net hardy/main Packages                     
Ign http://ppa.launchpad.net hardy/main Sources
Hit http://us.archive.ubuntu.com hardy Release 
Hit http://us.archive.ubuntu.com hardy-updates Release              
Hit http://us.archive.ubuntu.com hardy-backports Release            
Hit http://ppa.launchpad.net hardy/main Packages                    
Hit http://us.archive.ubuntu.com hardy-proposed Release
Hit http://ppa.launchpad.net hardy/main Sources                     
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://ppa.launchpad.net hardy/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-proposed/main Packages
Hit http://us.archive.ubuntu.com hardy-proposed/universe Packages
Hit http://us.archive.ubuntu.com hardy-proposed/restricted Packages
Hit http://us.archive.ubuntu.com hardy-proposed/multiverse Packages
Fetched 3B in 3s (1B/s)  
Reading package lists... Done
chitra@chitra-laptop:~$ 

```

And that last one, with the -f, that is the one which gives me some error message about the kiounmountwrapper thing...

---

### Post by gjoellee on 2008-07-28
I HAD EXACTLY THE SAME PROBLEM BEFORE!

ok do this:
> sudo apt-get install kio-umountwrapperwhen it is installed you won't notice it is there...the same thing will happen again if you try to uninstall it anyway. (it is like that for me)
you may find one more package with problems install that one to (you wont notice it's there). if you have any problems now please post the output....

---

### Post by mochiko on 2008-07-28
hey gjoellee...

!!!!!IT WORKED =D !!!!!!!
thanks!!!
i can add apps now, weeeee..

---


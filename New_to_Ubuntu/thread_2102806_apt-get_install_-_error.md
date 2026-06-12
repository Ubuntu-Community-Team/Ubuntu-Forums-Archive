---
title: "apt-get install - error"
date: 2013-01-08
forum: New to Ubuntu
---

### Post by val32 on 2013-01-08
Hello there 

I'm trying out ubuntu as I would like to gain some experience with linux. Im a total noob and the linux world is an entire new universe for me. 
  I'm dualbooting ubuntu along windows 7. 

Running ```
sudo apt-get install
```gives me the following:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cups-bsd : Depends: cups-client (= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu6 is installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.4)
           Depends: grub-pc-bin (= 1.99-21ubuntu3.4)
E: Unmet dependencies. Try using -f.

```After that, I've tried as suggested
```
sudo apt-get -f install
```which gives me 
```
                                   sudo apt-get -f install 
 Reading package lists... Done 
 Building dependency tree        
 Reading state information... Done 
 Correcting dependencies... Done 
 The following packages were automatically installed and are no longer required: 
   libaccess-bridge-java libx264-116 libiso9660-7 caribou libaccess-bridge-java-jni libvpx0 libmatroska4 libnl1 
   libid3tag0 libmusicbrainz4c2a 
 Use 'apt-get autoremove' to remove them. 
 The following extra packages will be installed: 
   cups-bsd grub-pc 
 The following packages will be upgraded: 
   cups-bsd grub-pc 
 2 upgraded, 0 newly installed, 0 to remove and 1 not upgraded. 
 38 not fully installed or removed. 
 Need to get 0 B/184 kB of archives. 
 After this operation, 0 B of additional disk space will be used. 
 Do you want to continue [Y/n]? y 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 Setting up resolvconf (1.63ubuntu16) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing resolvconf (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 Setting up apparmor (2.7.102-0ubuntu3.7) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing apparmor (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 Setting up cups (1.5.3-0ubuntu5.1) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing cups (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of printer-driver-hpcups: 
  printer-driver-hpcups depends on cups; however: 
   Package cups is not configured yet. 
 dpkg: error processing printer-driver-hpcups (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of hplip: 
  hplip depends on printer-driver-hpcups (= 3.12.2-1ubuntu3.1); however: 
   Package printer-driver-hpcups is not configured yet. 
  hplip depends on cups (>= 1.1.20); however: 
   Package cups is not configured yet. 
 dpkg: error processing hplip (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of printer-driver-postscript-hp: 
  printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.1); however: 
   Package hplip is not configured yet. 
 dpkg: error processing printer-driver-postscript-hp (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-minimal: 
  ubuntuNo apport report written because MaxReports is reached already 
                                                                      No apport report written because MaxReports is reached already 
          No apport report written because MaxReports is reached already 
                                                                        No apport report written because MaxReports is reached already 
            -minimal depends on resolvconf; however: 
   Package resolvconf is not configured yet. 
 dpkg: error processing ubuntu-minimal (--configure): 
  dependency problems - leaving unconfigured 
 Setting up man-db (2.6.1-2ubuntu1) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing man-db (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               Setting up memtest86+ (4.20-1.1ubuntu1) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing memtest86+ (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of ubuntu-standard: 
  ubuntu-standard depends on man-db; however: 
   Package man-db is not configured yet. 
  ubuntu-standard depends on memtest86+; however: 
   Package memtest86+ is not configured yet. 
 dpkg: error processing ubuntu-standard (--configure): 
  dependency problems - leaving unconfigured 
 Setting up ufw (0.31.1-1) ... 
 No apport report written because MaxReports is reached already 
                                                               No apport report written because MaxReports is reached already 
   debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing ufw (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 Setting up dictionaries-common (1.12.1ubuntu2) ... 
 No apport report written because MaxReports is reached already 
                                                               debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing dictionaries-common (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of aspell: 
  aspell depends on dictionaries-common (>> 0.40); however: 
   Package dictionaries-common is not configured yet. 
 dpkg: error processing aspell (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of bluez-cups: 
  bluez-cups depends on cups; however: 
   Package cups is not configured yet. 
 dpkg: error processing bluez-cups (--configure): 
  dependency problems - leaving unconfigured 
 Setting up checkbox-gtk (0.13.7) ... 
 No apport report written because MaxReports is reached already 
                                                               No apport report written because MaxReports is reached already 
   No apport report written because MaxReports is reached already 
                                                                 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing checkbox-gtk (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               Setting up checkbox-qt (0.13.7) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing checkbox-qt (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of printer-driver-gutenprint: 
  printer-driver-gutenprint depends on cups (>= 1.3.0); however: 
   Package cups is not configured yet. 
 dpkg: error processing printer-driver-gutenprint (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of cups-driver-gutenprint: 
  cups-driver-gutenprint depends on printer-driver-gutenprint; however: 
   Package printer-driver-gutenprint is not configured yet. 
 dpkg: error processing cups-driver-gutenprint (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               Setting up flashplugin-installer (11.2.202.258ubuntu0.12.04.1) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing flashplugin-installer (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of grub-pc: 
  grub-pc depends on grub2-common (= 1.99-21ubuntu3.4); however: 
   Version of grub2-common on system is 1.99-21ubuntu3.7. 
  grub-pc depends on grub-pc-bin (= 1.99-21ubuntu3.4); however: 
   Version of grub-pc-bin on system is 1.99-21ubuntu3.7. 
 dpkg: error processing grub-pc (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of hplip-cups: 
  hplip-cups depends on printer-driver-hpcups; however: 
   Package printer-driver-hpcups is not configured yet. 
 dpkg: error processing hplip-cups (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of hunspell-en-us: 
  hunspell-en-us depends on dictionaries-common (>= 0.10); however: 
   Package dictionaries-common is not configured yet. 
 dpkg: error processing hunspNo apport report written because MaxReports is reached already 
                                                                                           No apport report written because MaxReports is reached already 
                               No apport report written because MaxReports is reached already 
                                                                                             No apport report written because MaxReports is reached already 
                                 ell-en-us (--configure): 
  dependency problems - leaving unconfigured 
 Setting up libpam-cap (1:2.22-1ubuntu3) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing libpam-cap (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               Setting up libpam-gnome-keyring (3.2.2-2ubuntu4) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing libpam-gnome-keyring (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               Setting up samba-common (2:3.6.3-2ubuntu2.3) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing samba-common (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of samba-common-bin: 
  samba-common-bin depends on samba-common (>= 2:3.4.0~pre1-2); however: 
   Package samba-common is not configured yet. 
 dpkg: error processing samba-common-bin (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of nautilus-share: 
  nautilus-share depends on samba-common (>= 3.0.27a); however: 
   Package samba-common is not configured yet. 
  nautilus-share depends on samba-common-bin | samba-common (<< 2:3.4.0~pre2-1~0); however: 
   Package samba-common-bin is not configured yet. 
   Version of samba-common on system is 2:3.6.3-2ubuntu2.3. 
 dpkg: error processing nautilus-share (--configure): 
  dependency problems - leaving unconfigured 
 Setting up printer-driver-pnm2ppa (1.13+nondbs-0ubuntu1) ... 
 No apport report written because MaxReports is reached already 
                                                               No apport report written because MaxReports is reached already 
   No apport report written because MaxReports is reached already 
                                                                 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing printer-driver-pnm2ppa (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of pnm2ppa: 
  pnm2ppa depends on printer-driver-pnm2ppa; however: 
   Package printer-driver-pnm2ppa is not configured yet. 
 dpkg: error processing pnm2ppa (--configure): 
  dependency problems - leaving unconfigured 
 Setting up update-inetd (4.41) ... 
 No apport report written because MaxReports is reached already 
                                                               No apport report written because MaxReports is reached already 
   debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing update-inetd (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of sane-utils: 
  sane-utils depends on update-inetd (>= 4.31); however: 
   Package update-inetd is not configured yet. 
 dpkg: error processing sane-utils (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of smbclient: 
  smbclient depends on samba-common (= 2:3.6.3-2ubuntu2.3); however: 
   Package samba-common is not configured yet. 
 dpkg: error processing smbclient (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of ubuntu-desktop: 
  ubuntu-desktop depends on checkbox-qt; however: 
   Package checkbox-qt is not configured yet. 
  ubuntu-desktop depends on printer-driver-pnm2ppa; however: 
   Package printer-driver-pnm2ppa is not configured yet. 
 dpkg: error processing ubuntu-desktop (--configure): 
  dependency problems - No apport report written because MaxReports is reached already 
                                                                                      No apport report written because MaxReports is reached already 
                          No apport report written because MaxReports is reached already 
                                                                                        No apport report written because MaxReports is reached already 
                            leaving unconfigured 
 Setting up unattended-upgrades (0.76ubuntu1) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing unattended-upgrades (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 dpkg: dependency problems prevent configuration of cups-bsd: 
  cups-bsd depends on cups-client (= 1.5.3-0ubuntu5.1); however: 
   Version of cups-client on system is 1.5.3-0ubuntu6. 
  cups-bsd depends on update-inetd; however: 
   Package update-inetd is not configured yet. 
 dpkg: error processing cups-bsd (--configure): 
  dependency problems - leaving unconfigured 
 dpkg: dependency problems prevent configuration of indicator-printers: 
  indicator-printers depends on cups (>= 1.5); however: 
   Package cups is not configured yet. 
 dpkg: error processing indicator-printers (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               No apport report written because MaxReports is reached already 
   No apport report written because MaxReports is reached already 
                                                                 Setting up console-setup (1.70ubuntu5) ... 
 debconf: DbDriver "config": /var/cache/debconf/config.dat is locked by another process: Resource temporarily unavailable 
 dpkg: error processing console-setup (--configure): 
  subprocess installed post-installation script returned error exit status 1 
 No apport report written because MaxReports is reached already 
                                                               dpkg: dependency problems prevent configuration of kbd: 
  kbd depends on console-setup; however: 
   Package console-setup is not configured yet. 
 dpkg: error processing kbd (--configure): 
  dependency problems - leaving unconfigured 
 No apport report written because MaxReports is reached already 
                                                               Errors were encountered while processing: 
  resolvconf 
  apparmor 
  cups 
  printer-driver-hpcups 
  hplip 
  printer-driver-postscript-hp 
  ubuntu-minimal 
  man-db 
  memtest86+ 
  ubuntu-standard 
  ufw 
  dictionaries-common 
  aspell 
  bluez-cups 
  checkbox-gtk 
  checkbox-qt 
  printer-driver-gutenprint 
  cups-driver-gutenprint 
  flashplugin-installer 
  grub-pc 
  hplip-cups 
  hunspell-en-us 
  libpam-cap 
  libpam-gnome-keyring 
  samba-common 
  samba-common-bin 
  nautilus-share 
  printer-driver-pnm2ppa 
  pnm2ppa 
  update-inetd 
  sane-utils 
  smbclient 
  ubuntu-desktop 
  unattended-upgrades 
  cups-bsd 
  indicator-printers 
  console-setup 
  kbd 
 E: Sub-process /usr/bin/dpkg returned an error code (1) 
  
```
I've tried to upgrade the distro before, and it failed. So I thought i'd update everything first before giving it another try.  sudo apt-get upgrade is giving me the same error as sudo apt-get install


Some help would really be appreciated.

---

### Post by ibjsb4 on 2013-01-08
> locked by another process: Resource temporarily unavailable

You probably have the software center open while trying to use the terminal.  You can have only one package manager open at a time.  Close everything and in terminal:

```
sudo apt-get update
```

---

### Post by val32 on 2013-01-08
After restart: sudo apt-get update: 
```
Ign http://security.ubuntu.com precise-security InRelease
Ign http://archive.ubuntu.com precise InRelease
Ign http://archive.ubuntu.com precise-updates InRelease
Hit http://security.ubuntu.com precise-security Release.gpg
Hit http://archive.ubuntu.com precise Release.gpg
Hit http://security.ubuntu.com precise-security Release
Get:1 http://archive.ubuntu.com precise-updates Release.gpg [198 B]
Hit http://archive.ubuntu.com precise Release   
Get:2 http://archive.ubuntu.com precise-updates Release [49.6 kB]
Hit http://security.ubuntu.com precise-security/main amd64 Packages           
Hit http://security.ubuntu.com precise-security/restricted amd64 Packages
Hit http://security.ubuntu.com precise-security/universe amd64 Packages
Hit http://security.ubuntu.com precise-security/multiverse amd64 Packages
Hit http://security.ubuntu.com precise-security/main i386 Packages
Hit http://security.ubuntu.com precise-security/restricted i386 Packages
Hit http://security.ubuntu.com precise-security/universe i386 Packages
Hit http://security.ubuntu.com precise-security/multiverse i386 Packages
Hit http://security.ubuntu.com precise-security/main TranslationIndex
Hit http://security.ubuntu.com precise-security/multiverse TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/universe TranslationIndex
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
Hit http://security.ubuntu.com precise-security/main Translation-en
Hit http://security.ubuntu.com precise-security/multiverse Translation-en
Hit http://archive.ubuntu.com precise/restricted TranslationIndex
Hit http://security.ubuntu.com precise-security/restricted Translation-en
Hit http://archive.ubuntu.com precise/universe TranslationIndex
Get:3 http://archive.ubuntu.com precise-updates/main amd64 Packages [449 kB]
Hit http://security.ubuntu.com precise-security/universe Translation-en
Get:4 http://archive.ubuntu.com precise-updates/restricted amd64 Packages [8,366 B]
Get:5 http://archive.ubuntu.com precise-updates/universe amd64 Packages [164 kB]
Get:6 http://archive.ubuntu.com precise-updates/multiverse amd64 Packages [8,671 B]
Get:7 http://archive.ubuntu.com precise-updates/main i386 Packages [457 kB]
Get:8 http://archive.ubuntu.com precise-updates/restricted i386 Packages [8,374 B]
Get:9 http://archive.ubuntu.com precise-updates/universe i386 Packages [166 kB]
Get:10 http://archive.ubuntu.com precise-updates/multiverse i386 Packages [9,675 B]
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
Fetched 1,321 kB in 1s (1,295 kB/s)
Reading package lists... Done

```

Then again, sudo apt-get install:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cups-bsd : Depends: cups-client (= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu6 is installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.4)
           Depends: grub-pc-bin (= 1.99-21ubuntu3.4)
E: Unmet dependencies. Try using -f.

```

---

### Post by Gremlinzzz on 2013-01-08
Seem like a lot of packages need fixing
sudo apt-get -f install
sudo apt-get update
sudo apt-get upgrade

---

### Post by sudodus on 2013-01-08
Welcome to the Ubuntu Forums,val32 :-) 

> **ibjsb4 said:**
> You probably have the software center open while trying to use the terminal.  You can have only one package manager open at a time.  Close everything and in terminal:

```
sudo apt-get update
```
+1

and then to get almost all new packages available
```
sudo apt-get upgrade
```

and if some packages were held back (and you want the new versions)
```
sudo apt-get dist-upgrade
```

Then, when you want a new package, for example ***htop***, run
```
sudo apt-get install htop
```

Learn more about apt-get reading the manual page about it
```
man apt-get
```

Edit: A lot of posting at the same time ;-)

---

### Post by val32 on 2013-01-08
sudo apt-get upgrade & sudo apt-get dist-upgrade both give me the following: 

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cups-bsd : Depends: cups-client (= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu6 is installed
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.4)
           Depends: grub-pc-bin (= 1.99-21ubuntu3.4)
E: Unmet dependencies. Try using -f.

```> **sudodus said:**
> Edit: A lot of posting at the same time :wink:
-Edit: Yes, indeed. Amazing community, faster than light one might add ;) Thanks in advance guys, appreciate the help. I know how frustrating it can be to help a noob. Sry about that.

---

### Post by sudodus on 2013-01-08
Which version and flavour of Ubuntu are you installing?

Version:
- 12.04 LTS has long time support and is stable

- 12.10 is the newest officially release version, not as stable yet, but contains newer drivers and software

- (13.04) Raring Ringtail is still under development, avoid it unless you have a lot of experience with Ubuntu.

Flavour:
[vanilla] Ubuntu with desktop environment gnome 3 and Unity
Kubuntu with desktop environment KDE
Lubuntu with desktop environment LXDE (ultra light-weight)
Xubuntu with desktop environment XFCE (light-weight)

---

### Post by val32 on 2013-01-08
I'm using Ubuntu 12.04.1 LTS

---

### Post by sudodus on 2013-01-08
****We should be able to fix your problem with this version.

Try uninstalling the packages with problems and reinstall them again:

```
sudo apt-get remove cups-bsd
sudo apt-get remove grub-pc
```
and run
```
sudo apt-get update
```
and then re-install them
```
sudo apt-get install cups-bsd
sudo apt-get install grub-pc
```

If still problems, remove also those packages that are not compatible, and then install **cups-bsd** and ***grub-pc***, and afterwards re-install ***cups-client, grub2-common*** and **grub-pc-bin**

---

### Post by val32 on 2013-01-08
I always get the same: 

I've typed: sudo apt-get remove cups-bsd

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.4)
           Depends: grub-pc-bin (= 1.99-21ubuntu3.4)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```sudo apt-get remove grub-pc gives this: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups-bsd : Depends: cups-client (= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu6 is to be installed
 grub-gfxpayload-lists : Depends: grub-pc (>= 1.99~20101210-1ubuntu2)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

sudo apt-get update seems to work, no errors. 

sudo apt-get install cups-bsd:
```
 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 grub-pc : Depends: grub2-common (= 1.99-21ubuntu3.4)
           Depends: grub-pc-bin (= 1.99-21ubuntu3.4)
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```After sudo apt-get install grub-pc: 
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cups-bsd : Depends: cups-client (= 1.5.3-0ubuntu5.1) but 1.5.3-0ubuntu6 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

---

### Post by sudodus on 2013-01-08
Do you have another program open, that also wants to manage installed packages, for example Synaptic, Software-Center?

In that case close it and try again with apt-get!

If still problems, reboot the computer and try these commands again!

---

### Post by Chardrazle on 2013-03-04
> **val32 said:**
> I always get the same: 

I've typed: sudo apt-get remove cups-bsd



Bit late in the day, but you probably need to remove all the items in one call to avoid the dependency problem.

For example:

```
sudo apt-get remove grub-common grub-gfxpayload-lists grub-pc grub-pc-bin grub2-common
```

Note: this will likely roll you back to grub v1.

---


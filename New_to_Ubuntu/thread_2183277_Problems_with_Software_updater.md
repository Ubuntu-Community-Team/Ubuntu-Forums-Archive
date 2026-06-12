---
title: "Problems with Software updater"
date: 2013-10-24
forum: New to Ubuntu
---

### Post by Ant01 on 2013-10-24
Im having problems using the softwareupdater with ubuntu 13.10  All the updates get half way and then seem to freeze. I've left them running overnight but nothing. The more I try the more unstable the updater seems to get.

Any ideas?

---

### Post by grahammechanical on 2013-10-24
Does the utility not give you any error messages? Try running these two commands and then report the error messages here.

```
sudo apt-get update
```
```
sudo apt-get upgrade
```

You could also try removing any PPAs from your software sources. The software installed through those PPAs may not be packaged for 13.10 and that will cause Software Updater to have issues.

Regards.

---

### Post by Ant01 on 2013-10-24
Not sure what PPAs are?

antoine@TOVA:~$ sudo apt-get update
[sudo] password for antoine: 
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy InRelease                                   
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release.gpg                                 
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security InRelease
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy Release     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release.gpg              
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security Release
Hit [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main i386 Packages                 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en_ZA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe i386 Packages
Ign [http://extras.ubuntu.com](http://extras.ubuntu.com) saucy/main Translation-en               
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse i386 Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en     
Hit [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/main Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/multiverse Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/restricted Translation-en_ZA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) saucy-security/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy InRelease
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates InRelease
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports InRelease
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports Release.gpg
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports Release
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/multiverse i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/main Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/multiverse Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/restricted Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/universe Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/multiverse i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/main Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/multiverse Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/restricted Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/universe Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/main Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/restricted Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/universe Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/multiverse Sources
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/main i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/restricted i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/universe i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/multiverse i386 Packages
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/main Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/multiverse Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/restricted Translation-en
Hit [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/universe Translation-en
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-updates/universe Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/main Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/multiverse Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/restricted Translation-en_ZA
Ign [http://za.archive.ubuntu.com](http://za.archive.ubuntu.com) saucy-backports/universe Translation-en_ZA
Reading package lists... Done

---

### Post by Ant01 on 2013-10-24
antoine@TOVA:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following packages will be upgraded:
  gir1.2-gudev-1.0 libgudev-1.0-0 libpam-systemd libprocps0 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libudev1 procps python3-distupgrade
  systemd-services ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  udev
14 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 1*993 kB of archives.
After this operation, 4*096 B disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libprocps0 i386 1:3.3.3-2ubuntu8 [34,0 kB]
Get:2 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main udev i386 204-0ubuntu19 [1*046 kB]
Get:3 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libudev1 i386 204-0ubuntu19 [37,2 kB]
Get:4 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-daemon0 i386 204-0ubuntu19 [8*742 B]
Get:5 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libpam-systemd i386 204-0ubuntu19 [25,7 kB]
Get:6 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main systemd-services i386 204-0ubuntu19 [344 kB]
Get:7 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-login0 i386 204-0ubuntu19 [27,8 kB]
Get:8 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libgudev-1.0-0 i386 1:204-0ubuntu19 [14,2 kB]
Get:9 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main libsystemd-journal0 i386 204-0ubuntu19 [59,8 kB]
Get:10 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main procps i386 1:3.3.3-2ubuntu8 [221 kB]
Get:11 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-release-upgrader-gtk all 1:0.205.1 [10,3 kB]
Get:12 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main ubuntu-release-upgrader-core all 1:0.205.1 [24,3 kB]
Get:13 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main python3-distupgrade all 1:0.205.1 [136 kB]
Get:14 [http://za.archive.ubuntu.com/ubuntu/](http://za.archive.ubuntu.com/ubuntu/) saucy-updates/main gir1.2-gudev-1.0 i386 204-0ubuntu19 [3*622 B]
Fetched 1*993 kB in 1min 18s (25,3 kB/s)  
(Reading database ... 167529 files and directories currently installed.)
Removing ttf-mscorefonts-installer ...
(Reading database ... 167530 files and directories currently installed.)
Preparing to replace libprocps0:i386 1:3.3.3-2ubuntu7 (using .../libprocps0_1%3a3.3.3-2ubuntu8_i386.deb) ...
Unpacking replacement libprocps0:i386 ...
Preparing to replace udev 204-0ubuntu18 (using .../udev_204-0ubuntu19_i386.deb) ...
Adding 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
Unpacking replacement udev ...
Preparing to replace libudev1:i386 204-0ubuntu18 (using .../libudev1_204-0ubuntu19_i386.deb) ...
Unpacking replacement libudev1:i386 ...
Preparing to replace libsystemd-daemon0:i386 204-0ubuntu18 (using .../libsystemd-daemon0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-daemon0:i386 ...
Preparing to replace libpam-systemd:i386 204-0ubuntu18 (using .../libpam-systemd_204-0ubuntu19_i386.deb) ...
Unpacking replacement libpam-systemd:i386 ...
Preparing to replace systemd-services 204-0ubuntu18 (using .../systemd-services_204-0ubuntu19_i386.deb) ...
Unpacking replacement systemd-services ...
Preparing to replace libsystemd-login0:i386 204-0ubuntu18 (using .../libsystemd-login0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-login0:i386 ...
Preparing to replace libgudev-1.0-0:i386 1:204-0ubuntu18 (using .../libgudev-1.0-0_1%3a204-0ubuntu19_i386.deb) ...
Unpacking replacement libgudev-1.0-0:i386 ...
Preparing to replace libsystemd-journal0:i386 204-0ubuntu18 (using .../libsystemd-journal0_204-0ubuntu19_i386.deb) ...
Unpacking replacement libsystemd-journal0:i386 ...
Preparing to replace procps 1:3.3.3-2ubuntu7 (using .../procps_1%3a3.3.3-2ubuntu8_i386.deb) ...
Unpacking replacement procps ...
Preparing to replace ubuntu-release-upgrader-gtk 1:0.205 (using .../ubuntu-release-upgrader-gtk_1%3a0.205.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-gtk ...
Preparing to replace ubuntu-release-upgrader-core 1:0.205 (using .../ubuntu-release-upgrader-core_1%3a0.205.1_all.deb) ...
Unpacking replacement ubuntu-release-upgrader-core ...
Preparing to replace python3-distupgrade 1:0.205 (using .../python3-distupgrade_1%3a0.205.1_all.deb) ...
Unpacking replacement python3-distupgrade ...
Preparing to replace gir1.2-gudev-1.0 204-0ubuntu18 (using .../gir1.2-gudev-1.0_204-0ubuntu19_i386.deb) ...
Unpacking replacement gir1.2-gudev-1.0 ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up libprocps0:i386 (1:3.3.3-2ubuntu8) ...
Setting up libudev1:i386 (204-0ubuntu19) ...
Setting up udev (204-0ubuntu19) ...
udev stop/waiting
udev start/running, process 5953
Removing 'diversion of /bin/udevadm to /bin/udevadm.upgrade by fake-udev'
update-initramfs: deferring update (trigger activated)
Setting up libsystemd-daemon0:i386 (204-0ubuntu19) ...
Setting up systemd-services (204-0ubuntu19) ...
Setting up libpam-systemd:i386 (204-0ubuntu19) ...
Setting up libsystemd-login0:i386 (204-0ubuntu19) ...
Setting up libgudev-1.0-0:i386 (1:204-0ubuntu19) ...
Setting up libsystemd-journal0:i386 (204-0ubuntu19) ...
Setting up procps (1:3.3.3-2ubuntu8) ...
procps stop/waiting
Setting up python3-distupgrade (1:0.205.1) ...
Setting up ubuntu-release-upgrader-core (1:0.205.1) ...
Setting up ubuntu-release-upgrader-gtk (1:0.205.1) ...
Setting up gir1.2-gudev-1.0 (204-0ubuntu19) ...
Processing triggers for libc-bin ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.11.0-12-generic
antoine@TOVA:~$

---

### Post by Ant01 on 2013-10-24
Thanks, Its seems to be working after the upgrade but im not sure what you mean by PPAs ?

---

### Post by ||0BL1v10N|| on 2013-10-24
PPA's Are personal package archives. They are stored in repositories. Think of them as packages in the cloud. When you utilise the command: sudo apt-get install <thisprogram> you are instructing the terminal that you are the sudo user and you are requesting to get the PPA's for <thisprogram>. 

Hope this clears PPA's up for you,

Niall

---

### Post by Ant01 on 2013-10-24
Thank you for the help

---


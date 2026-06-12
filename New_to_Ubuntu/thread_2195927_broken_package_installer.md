---
title: "broken package installer"
date: 2013-12-27
forum: New to Ubuntu
---

### Post by antobbo on 2013-12-27
Hi all, a while ago after installing some updates, I started to have problems with the package system which is now broken and I can't install any update anymore. 


I run the following command in a terminal: apt-get install -f
and this is the output I got:

```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get install -f
[sudo] password for antobbo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.2.0-32 firefox-globalmenu linux-headers-3.2.0-32-generic libllvm3.0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  hplip printer-driver-hpcups
Suggested packages:
  hplip-gui hplip-doc system-config-printer
The following packages will be upgraded:
  hplip printer-driver-hpcups
2 upgraded, 0 newly installed, 0 to remove and 185 not upgraded.
11 not fully installed or removed.
Need to get 0 B/393 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up procps (1:3.2.8-11ubuntu6.2) ...
FATAL: Module bbswitch not found.
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups:
 cups depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on libhpmud0 (= 3.12.2-1ubuntu3.2); however:
  Version of libhpmud0 on system is 3.12.2-1ubuntu3.3.
 hplip depends on libsane-hpaio (= 3.12.2-1ubuntu3.2); however:
  Version of libsane-hpaio on system is 3.12.2-1ubuntu3.3.
 hplip depends on hplip-data (= 3.12.2-1ubuntu3.2); however:
  Version of hplip-data on system is 3.12.2-1No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                                                                         No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                          No apport report written because MaxReports has already been reached
                                                                                                                                                              No apport report written because MaxReports has already been reached
                                                       ubuntu3.3.
 hplip depends on printer-driver-hpcups (= 3.12.2-1ubuntu3.2); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.2); however:
  Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
Setting up whoopsie (0.1.33) ...
FATAL: Module bbswitch not found.
invoke-rc.d: initscript whoopsie, action "start" failed.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
No apport report written because MaxReports has already been reached
                                                                    Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
FATAL: Module bbswitch not found.
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Setting up bumblebee (3.2.1-1~preciseppa6) ...
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        No apport report written because MaxReports has already been reached
                                 FATAL: Module bbswitch not found.
invoke-rc.d: initscript bumblebeed, action "start" failed.
dpkg: error processing bumblebee (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumblebee-nvidia:
 bumblebee-nvidia depends on bumblebee (= 3.2.1-1~preciseppa6); however:
  Package bumblebee is not configured yet.
dpkg: error processing bumblebee-nvidia (--configure):
 dependency problems - leaving unconfigured
Processing triggers for initramfs-tools ...
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        update-initramfs: Generating /boot/initrd.img-3.5.0-42-generic
Errors were encountered while processing:
 procps
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 whoopsie
 rsyslog
 apport-gtk
 samba
 bumblebee
 bumblebee-nvidia
E: Sub-process /usr/bin/dpkg returned an error code (1)
antobbo@antobbo-xps17-ubuntu:~$ 



```




Now, does anybody have an idea as to what to do? I am in big troubles here because I can't install anything anymore. 
My specs are:
```
antobbo@antobbo-xps17-ubuntu:~$ lsb_release -a
LSB Version:	core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04.3 LTS
Release:	12.04
Codename:	precise

```


I will be grateful for any help
thanks

---

### Post by fantab on 2013-12-27
Post the output of :

df -h

You may have to remove the packages that are causing problems, and reinstall those.

---

### Post by antobbo on 2013-12-27
thanks fantab. Here is the output of the that command, as you asked:
```
antobbo@antobbo-xps17-ubuntu:~$ df -h
Filesystem      Size  Used Avail Use% Mounted on
/dev/sda5       156G  120G   29G  81% /
udev            3.9G  4.0K  3.9G   1% /dev
tmpfs           1.6G  1.2M  1.6G   1% /run
none            5.0M     0  5.0M   0% /run/lock
none            3.9G  1.2M  3.9G   1% /run/shm
antobbo@antobbo-xps17-ubuntu:~$
```
Now, about removing the packages that cause problems, well, I have tried that already. So, take the hplip for example. If I remove it, it causes other problems:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get remove hplip
[sudo] password for antobbo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 printer-driver-postscript-hp : Depends: hplip (>= 3.12.2-1ubuntu3.2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
antobbo@antobbo-xps17-ubuntu:~$ 



```

SHould I remove all the packages in the list?

 procps
 cups
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 whoopsie
 rsyslog
 apport-gtk
 samba
 bumblebee
 bumblebee-nvidia

---

### Post by fantab on 2013-12-27
Yes the following package have to be removed and then reinstalled. Lets try this:

```
sudo dpkg --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
sudo apt-get remove --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
sudo apt-get autoremove
sudo apt-get -f install
sudo apt-get clean
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
```

If you get any errors at any stage stop and report back the error.

---

### Post by antobbo on 2013-12-27
Thanks for your help fantab. So, I started from the first command, and I didn't get that far... I got some errors/warning. Here's the output:

```
antobbo@antobbo-xps17-ubuntu:~$ sudo dpkg --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
[sudo] password for antobbo: 
dpkg: dependency problems prevent removal of procps:
 ubuntu-minimal depends on procps.
 udev depends on procps; however:
  Package procps is to be removed.
 openssh-server depends on procps; however:
  Package procps is to be removed.
 ppp depends on procps.
 wine1.4 depends on procps.
 lsb-core depends on procps; however:
  Package procps is to be removed.
dpkg: error processing procps (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of cups:
 printer-driver-gutenprint depends on cups (>= 1.3.0).
 bluez-cups depends on cups.
 indicator-printers depends on cups (>= 1.5).
dpkg: error processing cups (--purge):
 dependency problems - not removing
(Reading database ... 769256 files and directories currently installed.)
Removing printer-driver-hpcups ...
Removing hplip ...
Purging configuration files for hplip ...
Removing printer-driver-postscript-hp ...
Removing whoopsie ...
Purging configuration files for whoopsie ...
userdel: user whoopsie is currently logged in
/usr/sbin/deluser: `/usr/sbin/userdel whoopsie' returned error code 8. Exiting.
dpkg: dependency problems prevent removal of rsyslog:
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is to be removed.
dpkg: error processing rsyslog (--purge):
 dependency problems - not removing
Removing apport-gtk ...
Removing samba ...
Purging configuration files for samba ...
Removing configuration file /etc/default/samba...
Removing configuration file /etc/default/samba...
Removing bumblebee ...
Purging configuration files for bumblebee ...
dpkg: warning: while removing bumblebee, directory '/usr/share/doc/bumblebee' not empty so not removed.
Removing bumblebee-nvidia ...
update-alternatives: using /usr/lib/nvidia-304/ld.so.conf to provide /etc/ld.so.conf.d/x86_64-linux-gnu_GL.conf (x86_64-linux-gnu_gl_conf) in auto mode.
update-alternatives: using /usr/lib/nvidia-304/alt_ld.so.conf to provide /etc/ld.so.conf.d/i386-linux-gnu_GL.conf (i386-linux-gnu_gl_conf) in auto mode.
Purging configuration files for bumblebee-nvidia ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for ufw ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-42-generic
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 procps
 cups
 rsyslog
antobbo@antobbo-xps17-ubuntu:~$ 

```Happy to try the rest of them if you want me to.
thanks

---

### Post by fantab on 2013-12-27
Try the second command... and continue till the last but one, ie don't run 'apt-get install'...
Do NOT shutdown Ubuntu untill you have re-installed all the removed packages.
Do you have 'Synaptic' installed, if you then remove those three packages with it.... If you don't have it installed then ignore it.

---

### Post by antobbo on 2013-12-27
OK, so I run the second one but it didn't work,here's the output:
```
groups: cannot find name for group ID 1001
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get remove --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
[sudo] password for antobbo: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
antobbo@antobbo-xps17-ubuntu:~$ 

```I would like to bring your attention to the first line in the output:
```
groups: cannot find name for group ID 1001

```This appeared when I opened the console, could it be the result of the first command?
Third command returns this too:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get autoremove
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
antobbo@antobbo-xps17-ubuntu:~$ 

```I skipped the forth because it is an install and run the fifth:
```
sudo apt-get clean
```
Then I run the sixth:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-amd64_Packages'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_source_Sources'
antobbo@antobbo-xps17-ubuntu:~$ 

```

Finally, I run the second last command and again get the same error towards the end:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get update && sudo apt-get dist-upgrade
Get:1 http://ppa.launchpad.net precise Release.gpg [316 B]
Get:2 http://dl.google.com stable Release.gpg [198 B]                                                                                                                     
Get:3 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                                                
Get:4 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                                                
Get:5 http://ppa.launchpad.net precise Release.gpg [316 B]                                                                                                                
Get:6 http://extras.ubuntu.com precise Release.gpg [72 B]                                                                                                                 
Get:7 http://gb.archive.ubuntu.com precise Release.gpg [198 B]                                                                                                            
Get:8 http://gb.archive.ubuntu.com precise-updates Release.gpg [198 B]                                                                                                    
Get:9 http://gb.archive.ubuntu.com precise-backports Release.gpg [198 B]                                                                                                  
Get:10 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                                                 
Get:11 http://dl.google.com stable Release [1,338 B]                                                                                                                      
Get:12 http://extras.ubuntu.com precise Release [11.9 kB]                                                                                                                 
Get:13 http://deb.opera.com stable Release.gpg [198 B]                                                                                                                    
Get:14 http://gb.archive.ubuntu.com precise Release [49.6 kB]                                                                                                  
Get:15 http://ppa.launchpad.net precise Release [11.9 kB]                                                                      
Get:16 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                  
Get:17 http://deb.opera.com stable Release [1,718 B]                                                                                    
Get:18 http://ppa.launchpad.net precise Release [11.9 kB]                                                                                              
Get:19 http://gb.archive.ubuntu.com precise-updates Release [49.6 kB]                                                                       
Get:20 http://dl.google.com stable/main amd64 Packages [469 B]                                                                                                            
Get:21 http://security.ubuntu.com precise-security Release.gpg [198 B]                                                                                     
Get:22 http://extras.ubuntu.com precise/main Sources [8,130 B]                                                                                          
Get:23 http://ppa.launchpad.net precise/main Sources [2,243 B]                                                                                          
Get:24 http://deb.opera.com stable/non-free amd64 Packages [931 B]                                                                                      
Get:25 http://gb.archive.ubuntu.com precise-backports Release [49.6 kB]                                                                                 
Get:26 http://dl.google.com stable/main i386 Packages [464 B]
Ign http://dl.google.com stable/main TranslationIndex                                                                                                                     
Get:27 http://extras.ubuntu.com precise/main amd64 Packages [10.8 kB]                                                                                                     
Get:28 http://ppa.launchpad.net precise/main amd64 Packages [4,060 B]                                                                                           
Get:29 http://deb.opera.com stable/non-free i386 Packages [933 B]                                                                                                         
Ign http://deb.opera.com stable/non-free TranslationIndex                                                                                                                
Get:30 http://gb.archive.ubuntu.com precise/main Sources [934 kB]                                                                                                
Get:31 http://ppa.launchpad.net precise/main i386 Packages [4,350 B]                                                                                                    
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                                  
Get:32 http://ppa.launchpad.net precise/main Sources [499 B]                                                                                                            
Get:33 http://extras.ubuntu.com precise/main i386 Packages [10.8 kB]                                                                                                   
Ign http://extras.ubuntu.com precise/main TranslationIndex                                                                                                  
Get:34 http://ppa.launchpad.net precise/main amd64 Packages [576 B]                                                                               
Get:35 http://ppa.launchpad.net precise/main i386 Packages [576 B]                                                                                                        
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                               
Get:36 http://ppa.launchpad.net precise/main Sources [8,371 B]                                                                                  
Get:37 http://ppa.launchpad.net precise/main amd64 Packages [19.2 kB]                                                                                                     
Get:38 http://security.ubuntu.com precise-security Release [49.6 kB]                                                                                                      
Get:39 http://ppa.launchpad.net precise/main i386 Packages [19.2 kB]                                                                                                  
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                                               
Get:40 http://ppa.launchpad.net precise/main Sources [1,206 B]                                                                                             
Get:41 http://ppa.launchpad.net precise/main amd64 Packages [2,817 B]                                                                                                  
Get:42 http://ppa.launchpad.net precise/main i386 Packages [2,817 B]                                                                                                      
Ign http://ppa.launchpad.net precise/main TranslationIndex                                                                                                                
Ign http://dl.google.com stable/main Translation-en_GB                                                                                                                    
Ign http://dl.google.com stable/main Translation-en                                                                                                        
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                                                                         
Ign http://ppa.launchpad.net precise/main Translation-en                                            
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                         
Ign http://ppa.launchpad.net precise/main Translation-en                                                                  
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                                               
Ign http://ppa.launchpad.net precise/main Translation-en                                            
Ign http://deb.opera.com stable/non-free Translation-en_GB                                          
Ign http://ppa.launchpad.net precise/main Translation-en_GB                                         
Ign http://extras.ubuntu.com precise/main Translation-en_GB                                         
Ign http://ppa.launchpad.net precise/main Translation-en                                            
Ign http://deb.opera.com stable/non-free Translation-en                                             
Get:43 http://security.ubuntu.com precise-security/main Sources [95.0 kB]                           
Ign http://extras.ubuntu.com precise/main Translation-en                                
Get:44 http://gb.archive.ubuntu.com precise/restricted Sources [5,470 B]                
Get:45 http://gb.archive.ubuntu.com precise/universe Sources [5,019 kB]                     
Get:46 http://security.ubuntu.com precise-security/restricted Sources [2,494 B]             
Get:47 http://security.ubuntu.com precise-security/universe Sources [29.9 kB]               
Get:48 http://security.ubuntu.com precise-security/multiverse Sources [1,792 B]             
Get:49 http://security.ubuntu.com precise-security/main amd64 Packages [349 kB]              
Get:50 http://security.ubuntu.com precise-security/restricted amd64 Packages [4,627 B]     
Get:51 http://security.ubuntu.com precise-security/universe amd64 Packages [86.5 kB]
Get:52 http://security.ubuntu.com precise-security/multiverse amd64 Packages [2,446 B]         
Get:53 http://security.ubuntu.com precise-security/main i386 Packages [369 kB]               
Get:54 http://security.ubuntu.com precise-security/restricted i386 Packages [4,620 B]          
Get:55 http://security.ubuntu.com precise-security/universe i386 Packages [90.7 kB]             
Get:56 http://security.ubuntu.com precise-security/multiverse i386 Packages [2,642 B]           
Get:57 http://security.ubuntu.com precise-security/main TranslationIndex [74 B]                  
Get:58 http://security.ubuntu.com precise-security/multiverse TranslationIndex [72 B]
Get:59 http://security.ubuntu.com precise-security/restricted TranslationIndex [72 B]
Get:60 http://security.ubuntu.com precise-security/universe TranslationIndex [73 B]
Get:61 http://security.ubuntu.com precise-security/main Translation-en [164 kB]     
Get:62 http://gb.archive.ubuntu.com precise/multiverse Sources [155 kB]     
Get:63 http://gb.archive.ubuntu.com precise/main amd64 Packages [1,273 kB]                      
Get:64 http://gb.archive.ubuntu.com precise/restricted amd64 Packages [8,452 B]                    
Get:65 http://gb.archive.ubuntu.com precise/universe amd64 Packages [4,786 kB]                    
Get:66 http://security.ubuntu.com precise-security/multiverse Translation-en [1,299 B]            
Get:67 http://security.ubuntu.com precise-security/restricted Translation-en [1,253 B]           
Get:68 http://security.ubuntu.com precise-security/universe Translation-en [54.8 kB]                
Get:69 http://gb.archive.ubuntu.com precise/multiverse amd64 Packages [119 kB]                     
Get:70 http://gb.archive.ubuntu.com precise/main i386 Packages [1,274 kB]
Get:71 http://gb.archive.ubuntu.com precise/restricted i386 Packages [8,431 B]
Get:72 http://gb.archive.ubuntu.com precise/universe i386 Packages [4,796 kB]
Get:73 http://gb.archive.ubuntu.com precise/multiverse i386 Packages [121 kB]
Get:74 http://gb.archive.ubuntu.com precise/main TranslationIndex [3,706 B]
Get:75 http://gb.archive.ubuntu.com precise/multiverse TranslationIndex [2,676 B]
Get:76 http://gb.archive.ubuntu.com precise/restricted TranslationIndex [2,596 B]
Get:77 http://gb.archive.ubuntu.com precise/universe TranslationIndex [2,922 B]
Get:78 http://gb.archive.ubuntu.com precise-updates/main Sources [430 kB]
Get:79 http://gb.archive.ubuntu.com precise-updates/restricted Sources [7,039 B]
Get:80 http://gb.archive.ubuntu.com precise-updates/universe Sources [101 kB]
Get:81 http://gb.archive.ubuntu.com precise-updates/multiverse Sources [8,468 B]
Get:82 http://gb.archive.ubuntu.com precise-updates/main amd64 Packages [719 kB]
Get:83 http://gb.archive.ubuntu.com precise-updates/restricted amd64 Packages [11.4 kB]
Get:84 http://gb.archive.ubuntu.com precise-updates/universe amd64 Packages [226 kB]
Get:85 http://gb.archive.ubuntu.com precise-updates/multiverse amd64 Packages [14.2 kB]
Get:86 http://gb.archive.ubuntu.com precise-updates/main i386 Packages [741 kB]
Get:87 http://gb.archive.ubuntu.com precise-updates/restricted i386 Packages [11.5 kB]                                                                                    
Get:88 http://gb.archive.ubuntu.com precise-updates/universe i386 Packages [230 kB]                                                                                       
Get:89 http://gb.archive.ubuntu.com precise-updates/multiverse i386 Packages [14.4 kB]                                                                                    
Get:90 http://gb.archive.ubuntu.com precise-updates/main TranslationIndex [3,564 B]                                                                                       
Get:91 http://gb.archive.ubuntu.com precise-updates/multiverse TranslationIndex [2,605 B]                                                                                 
Get:92 http://gb.archive.ubuntu.com precise-updates/restricted TranslationIndex [2,461 B]                                                                                 
Get:93 http://gb.archive.ubuntu.com precise-updates/universe TranslationIndex [2,850 B]                                                                                   
Get:94 http://gb.archive.ubuntu.com precise-backports/main Sources [4,225 B]                                                                                              
Get:95 http://gb.archive.ubuntu.com precise-backports/restricted Sources [14 B]                                                                                           
Get:96 http://gb.archive.ubuntu.com precise-backports/universe Sources [36.4 kB]                                                                                          
Get:97 http://gb.archive.ubuntu.com precise-backports/multiverse Sources [5,311 B]                                                                                        
Get:98 http://gb.archive.ubuntu.com precise-backports/main amd64 Packages [4,800 B]                                                                                       
Get:99 http://gb.archive.ubuntu.com precise-backports/restricted amd64 Packages [14 B]                                                                                    
Get:100 http://gb.archive.ubuntu.com precise-backports/universe amd64 Packages [37.9 kB]                                                                                  
Get:101 http://gb.archive.ubuntu.com precise-backports/multiverse amd64 Packages [5,206 B]                                                                                
Get:102 http://gb.archive.ubuntu.com precise-backports/main i386 Packages [4,809 B]                                                                                       
Get:103 http://gb.archive.ubuntu.com precise-backports/restricted i386 Packages [14 B]                                                                                    
Get:104 http://gb.archive.ubuntu.com precise-backports/universe i386 Packages [37.7 kB]                                                                                   
Get:105 http://gb.archive.ubuntu.com precise-backports/multiverse i386 Packages [5,178 B]                                                                                 
Get:106 http://gb.archive.ubuntu.com precise-backports/main TranslationIndex [72 B]                                                                                       
Get:107 http://gb.archive.ubuntu.com precise-backports/multiverse TranslationIndex [72 B]                                                                                 
Get:108 http://gb.archive.ubuntu.com precise-backports/restricted TranslationIndex [70 B]                                                                                 
Get:109 http://gb.archive.ubuntu.com precise-backports/universe TranslationIndex [73 B]                                                                                   
Get:110 http://gb.archive.ubuntu.com precise/main Translation-en_GB [96.4 kB]                                                                                             
Get:111 http://gb.archive.ubuntu.com precise/main Translation-en [726 kB]                                                                                                 
Get:112 http://gb.archive.ubuntu.com precise/multiverse Translation-en_GB [79.8 kB]                                                                                       
Get:113 http://gb.archive.ubuntu.com precise/multiverse Translation-en [93.4 kB]                                                                                          
Get:114 http://gb.archive.ubuntu.com precise/restricted Translation-en_GB [2,406 B]                                                                                       
Get:115 http://gb.archive.ubuntu.com precise/restricted Translation-en [2,395 B]                                                                                          
Get:116 http://gb.archive.ubuntu.com precise/universe Translation-en_GB [5,492 B]                                                                                         
Get:117 http://gb.archive.ubuntu.com precise/universe Translation-en [3,341 kB]                                                                                           
Get:118 http://gb.archive.ubuntu.com precise-updates/main Translation-en_GB [96.4 kB]                                                                                     
Get:119 http://gb.archive.ubuntu.com precise-updates/main Translation-en [325 kB]                                                                                         
Get:120 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en_GB [79.8 kB]                                                                               
Get:121 http://gb.archive.ubuntu.com precise-updates/multiverse Translation-en [8,293 B]                                                                                  
Get:122 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en_GB [2,406 B]                                                                               
Get:123 http://gb.archive.ubuntu.com precise-updates/restricted Translation-en [2,663 B]                                                                                  
Get:124 http://gb.archive.ubuntu.com precise-updates/universe Translation-en_GB [5,492 B]                                                                                 
Get:125 http://gb.archive.ubuntu.com precise-updates/universe Translation-en [132 kB]                                                                                     
Get:126 http://gb.archive.ubuntu.com precise-backports/main Translation-en [4,235 B]                                                                                      
Get:127 http://gb.archive.ubuntu.com precise-backports/multiverse Translation-en [4,610 B]                                                                                
Get:128 http://gb.archive.ubuntu.com precise-backports/restricted Translation-en [14 B]                                                                                   
Get:129 http://gb.archive.ubuntu.com precise-backports/universe Translation-en [27.6 kB]                                                                                  
Fetched 27.8 MB in 8s (3,099 kB/s)                                                                                                                                        
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```



I don't know why this /var/lib/dpkg/lock is not available 
I looks like I have synaptic. I haven't removed the three packages as yet
procps
 cups
 rsyslog
I thought I let you have a look at the above first and if it is ok I will attempt to remove them
thanks for your help so far

---

### Post by antobbo on 2013-12-27
Ah sorry, as a little addendum, I have noticed something interesting. When I looked up the 3 packages in synaptic, procps has an exclamation mark on it. Under installed version it says  1:3.2.8-11ubuntu6.2. The second, cups, under installed version says 1.5.3-0ubuntu8 and the third [COLOR=#000000]rsyslog, like the first one has an exclamation mark next to it[/COLOR]

---

### Post by deadflowr on 2013-12-27
To clarify, when you run the sudo apt-get <command> and get the 
/var/lib/dpkg/lock is unavailable, is synaptic open?

Which is what it seems to be.

---

### Post by antobbo on 2013-12-27
uhm...it didn't occur to me, sorry!. OK, I closed synaptic and done the whole thing again.
so, first command:
```
groups: cannot find name for group ID 1001
antobbo@antobbo-xps17-ubuntu:~$ sudo dpkg --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
[sudo] password for antobbo: 
dpkg: warning: there's no installed package matching printer-driver-hpcups
dpkg: warning: there's no installed package matching hplip
dpkg: warning: there's no installed package matching printer-driver-postscript-hp
dpkg: warning: there's no installed package matching whoopsie
dpkg: warning: there's no installed package matching apport-gtk
dpkg: warning: there's no installed package matching samba
dpkg: warning: there's no installed package matching bumblebee
dpkg: warning: there's no installed package matching bumblebee-nvidia
dpkg: dependency problems prevent removal of procps:
 ubuntu-minimal depends on procps.
 udev depends on procps; however:
  Package procps is to be removed.
 openssh-server depends on procps; however:
  Package procps is to be removed.
 ppp depends on procps.
 wine1.4 depends on procps.
 lsb-core depends on procps; however:
  Package procps is to be removed.
dpkg: error processing procps (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of cups:
 printer-driver-gutenprint depends on cups (>= 1.3.0).
 bluez-cups depends on cups.
 indicator-printers depends on cups (>= 1.5).
dpkg: error processing cups (--purge):
 dependency problems - not removing
dpkg: dependency problems prevent removal of rsyslog:
 ubuntu-minimal depends on rsyslog; however:
  Package rsyslog is to be removed.
dpkg: error processing rsyslog (--purge):
 dependency problems - not removing
Errors were encountered while processing:
 procps
 cups
 rsyslog

```
Second:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get remove --purge procps cups printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie rsyslog apport-gtk samba bumblebee bumblebee-nvidia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package apport-gtk is not installed, so not removed
Package samba is not installed, so not removed
Package whoopsie is not installed, so not removed
Package hplip is not installed, so not removed
Package printer-driver-hpcups is not installed, so not removed
Package printer-driver-postscript-hp is not installed, so not removed
Package bumblebee is not installed, so not removed
Package bumblebee-nvidia is not installed, so not removed
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 openssh-client : Depends: adduser (>= 3.10) but it is not going to be installed
                  Depends: passwd
 openssh-server : Depends: upstart-job
                  Depends: adduser (>= 3.9) but it is not going to be installed
                  Depends: procps
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.



```
Third:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  firefox-globalmenu libllvm3.0:i386 linux-headers-3.2.0-32 linux-headers-3.2.0-32-generic tdb-tools
0 upgraded, 0 newly installed, 5 to remove and 181 not upgraded.
3 not fully installed or removed.
After this operation, 88.0 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 769025 files and directories currently installed.)
Removing firefox-globalmenu ...
Removing libllvm3.0:i386 ...
Removing linux-headers-3.2.0-32-generic ...
Removing linux-headers-3.2.0-32 ...
Removing tdb-tools ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for man-db ...
Setting up procps (1:3.2.8-11ubuntu6.2) ...
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: dependency problems prevent configuration of cups:
 cups depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 5
Errors were encountered while processing:
 procps
 cups
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
antobbo@antobbo-xps17-ubuntu:~$ 



```

Fourth:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 181 not upgraded.
3 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up procps (1:3.2.8-11ubuntu6.2) ...
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: dependency problems prevent configuration of cups:
 cups depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (5.8.6-1ubuntu8.5) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 5
Errors were encountered while processing:
 procps
 cups
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
antobbo@antobbo-xps17-ubuntu:~$ 



```
Seventh:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get clean
antobbo@antobbo-xps17-ubuntu:~$

```
Eighth:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo rm /var/lib/apt/lists/* -vf
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-amd64_Packages'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_non-free_binary-i386_Packages'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release'
removed `/var/lib/apt/lists/deb.opera.com_opera_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release'
removed `/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_Release.gpg'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/extras.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-backports_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise_universe_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_main_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_multiverse_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_Release'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_Release.gpg'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_restricted_source_Sources'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Index'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_i18n_Translation-en%5fGB'
removed `/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_precise-updates_universe_source_Sources'
removed `/var/lib/apt/lists/lock'
rm: cannot remove `/var/lib/apt/lists/partial': Is a directory
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_bumblebee_stable_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_disper-dev_ppa_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_ubuntu-x-swat_x-updates_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_binary-i386_Packages'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_main_source_Sources'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release'
removed `/var/lib/apt/lists/ppa.launchpad.net_webupd8team_java_ubuntu_dists_precise_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_main_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_multiverse_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_Release.gpg'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_i18n_Translation-en'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_restricted_source_Sources'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-amd64_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_binary-i386_Packages'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Index'
removed `/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_precise-security_universe_i18n_Translation-en'
removed `/var/lib/apt/lists/secur

```
And I left off the last one.
Now I will proceed to unistal the 3 packages and install them again using synaptic

---

### Post by antobbo on 2013-12-27
...the last famous words...
When I attempted to remove the first of the infamous 3 packages procps, when marked for removal in synaptic a message warned me that there are about 200 extra packages that will have to be removed to complete the action (some are applications that I use on a regular basis), and some of them seems to be essential to the point that just before I confirm the deletion another message says that this modification will make the system very unstable. The other two seem to have a less detrimental effect
cups
rsyslog
However, I have attempted to remove 
cups
rsyslog
but it looks like they have been partially removed (somehow those are related to the procps package). I tried to re mark them for installation but now I get an error message for cups:

```
E: procps: subprocess installed post-installation script returned error exit status 5
E: rsyslog: subprocess installed post-installation script returned error exit status 5
E: cups: dependency problems - leaving unconfigured
E: printer-driver-gutenprint: dependency problems - leaving unconfigured
```

and this one for rsyslog
```
E: procps: subprocess installed post-installation script returned error exit status 5
E: cups: dependency problems - leaving unconfigured
E: rsyslog: subprocess installed post-installation script returned error exit status 5
E: printer-driver-gutenprint: dependency problems - leaving unconfigured
```

---

### Post by fantab on 2013-12-27
Hmm... looks like you have more issues then what met the eye.
Except the remaining three packages all seemed to have be worked well.

In 'Synaptic' under 'edit' menu you will find 'Fix Broken Packages', run it and see if it helps. It does the same job as 'apt-get -f install'.

Then:
```
sudo dpkg --configure -a --force-all
sudo apt-get install --reinstall procps cups rsyslog
sudo apt-get install printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie apport-gtk samba bumblebee bumblebee-nvidia
```

---

### Post by antobbo on 2013-12-28
thanks again fantab. Well, unfortunately it's never easy :-(.
Anyway, I did what you said, run "fix broken packages" in synaptic and at the bottom I had a message saying that all the dependencies were fixed.
Then I run the commands, and here is the output (still problems with those darn packages I am afraid):
```
groups: cannot find name for group ID 1001
antobbo@antobbo-xps17-ubuntu:~$ sudo dpkg --configure -a --force-all
[sudo] password for antobbo: 
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: cups: dependency problems, but configuring anyway as you requested:
 cups depends on procps; however:
  Package procps is not configured yet.
Setting up cups (1.5.3-0ubuntu8) ...
invoke-rc.d: initscript cups, action "start" failed.
dpkg: error processing cups (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: printer-driver-gutenprint: dependency problems, but configuring anyway as you requested:
 printer-driver-gutenprint depends on cups (>= 1.3.0); however:
  Package cups is not configured yet.
Setting up printer-driver-gutenprint (5.2.8~pre1-0ubuntu2.1) ...
Errors were encountered while processing:
 rsyslog
 cups
antobbo@antobbo-xps17-ubuntu:~$ 



```
Then the second command:
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get install --reinstall procps cups rsyslog
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  procps
1 upgraded, 0 newly installed, 2 reinstalled, 0 to remove and 179 not upgraded.
3 not fully installed or removed.
Need to get 235 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main procps amd64 1:3.2.8-11ubuntu6.3 [235 kB]
Fetched 235 kB in 0s (791 kB/s)
Setting up procps (1:3.2.8-11ubuntu6.2) ...
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 5
dpkg: dependency problems prevent configuration of cups:
 cups depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 5
Errors were encountered while processing:
 procps
 cups
 rsyslog
E: Sub-process /usr/bin/dpkg returned an error code (1)
antobbo@antobbo-xps17-ubuntu:~$ 



```

And finally the third one (at the end of which there is a longer list of packages that seem to have some problems):
```
antobbo@antobbo-xps17-ubuntu:~$ sudo apt-get install printer-driver-hpcups hplip printer-driver-postscript-hp whoopsie apport-gtk samba bumblebee bumblebee-nvidia
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libpam-smbpass libpam-winbind libwbclient0 python-apport samba-common smbclient tdb-tools winbind
Suggested packages:
  hplip-gui hplip-doc system-config-printer openbsd-inetd inet-superserver smbldap-tools ldb-tools ctdb cifs-utils
The following NEW packages will be installed
  apport-gtk bumblebee bumblebee-nvidia hplip printer-driver-hpcups printer-driver-postscript-hp samba tdb-tools whoopsie
The following packages will be upgraded:
  libpam-smbpass libpam-winbind libwbclient0 python-apport samba-common smbclient winbind
7 upgraded, 9 newly installed, 0 to remove and 173 not upgraded.
3 not fully installed or removed.
Need to get 29.7 MB of archives.
After this operation, 27.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main bumblebee amd64 3.2.1-1~preciseppa6 [63.9 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main libpam-winbind amd64 2:3.6.3-2ubuntu2.9 [625 kB]
Get:3 http://ppa.launchpad.net/bumblebee/stable/ubuntu/ precise/main bumblebee-nvidia amd64 3.2.1-1~preciseppa6 [6,090 B]
Get:4 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main winbind amd64 2:3.6.3-2ubuntu2.9 [4,422 kB]
Get:5 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main libwbclient0 amd64 2:3.6.3-2ubuntu2.9 [29.8 kB]
Get:6 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main smbclient amd64 2:3.6.3-2ubuntu2.9 [14.1 MB]
Get:7 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main libpam-smbpass amd64 2:3.6.3-2ubuntu2.9 [759 kB]                                                          
Get:8 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main samba-common all 2:3.6.3-2ubuntu2.9 [325 kB]                                                              
Get:9 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main whoopsie amd64 0.1.33 [24.6 kB]                                                                           
Get:10 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main python-apport all 2.0.1-0ubuntu17.6 [81.1 kB]                                                            
Get:11 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main apport-gtk all 2.0.1-0ubuntu17.6 [9,400 B]                                                               
Get:12 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-hpcups amd64 3.12.2-1ubuntu3.3 [305 kB]                                                   
Get:13 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main hplip amd64 3.12.2-1ubuntu3.3 [88.3 kB]                                                                  
Get:14 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main printer-driver-postscript-hp all 3.12.2-1ubuntu3.3 [780 kB]                                              
Get:15 http://gb.archive.ubuntu.com/ubuntu/ precise-updates/main samba amd64 2:3.6.3-2ubuntu2.9 [8,040 kB]                                                                
Get:16 http://gb.archive.ubuntu.com/ubuntu/ precise/main tdb-tools amd64 1.2.9-4 [23.2 kB]                                                                                
Fetched 29.7 MB in 11s (2,500 kB/s)                                                                                                                                       
Preconfiguring packages ...
(Reading database ... 746964 files and directories currently installed.)
Preparing to replace libpam-winbind 2:3.6.3-2ubuntu2.8 (using .../libpam-winbind_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Unpacking replacement libpam-winbind ...
Preparing to replace winbind 2:3.6.3-2ubuntu2.8 (using .../winbind_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
 * Stopping the Winbind daemon winbind                                                                                                                              [ OK ] 
Unpacking replacement winbind ...
Preparing to replace libwbclient0 2:3.6.3-2ubuntu2.8 (using .../libwbclient0_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Unpacking replacement libwbclient0 ...
Preparing to replace smbclient 2:3.6.3-2ubuntu2.8 (using .../smbclient_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Unpacking replacement smbclient ...
Preparing to replace libpam-smbpass 2:3.6.3-2ubuntu2.8 (using .../libpam-smbpass_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Unpacking replacement libpam-smbpass ...
Preparing to replace samba-common 2:3.6.3-2ubuntu2.8 (using .../samba-common_2%3a3.6.3-2ubuntu2.9_all.deb) ...
Unpacking replacement samba-common ...
Selecting previously unselected package whoopsie.
Unpacking whoopsie (from .../whoopsie_0.1.33_amd64.deb) ...
Preparing to replace python-apport 2.0.1-0ubuntu17.5 (using .../python-apport_2.0.1-0ubuntu17.6_all.deb) ...
Unpacking replacement python-apport ...
Selecting previously unselected package apport-gtk.
Unpacking apport-gtk (from .../apport-gtk_2.0.1-0ubuntu17.6_all.deb) ...
Selecting previously unselected package printer-driver-hpcups.
Unpacking printer-driver-hpcups (from .../printer-driver-hpcups_3.12.2-1ubuntu3.3_amd64.deb) ...
Selecting previously unselected package hplip.
Unpacking hplip (from .../hplip_3.12.2-1ubuntu3.3_amd64.deb) ...
Selecting previously unselected package printer-driver-postscript-hp.
Unpacking printer-driver-postscript-hp (from .../printer-driver-postscript-hp_3.12.2-1ubuntu3.3_all.deb) ...
Selecting previously unselected package samba.
Unpacking samba (from .../samba_2%3a3.6.3-2ubuntu2.9_amd64.deb) ...
Selecting previously unselected package tdb-tools.
Unpacking tdb-tools (from .../tdb-tools_1.2.9-4_amd64.deb) ...
Selecting previously unselected package bumblebee.
Unpacking bumblebee (from .../bumblebee_3.2.1-1~preciseppa6_amd64.deb) ...
Selecting previously unselected package bumblebee-nvidia.
Unpacking bumblebee-nvidia (from .../bumblebee-nvidia_3.2.1-1~preciseppa6_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for ufw ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-42-generic
Setting up procps (1:3.2.8-11ubuntu6.2) ...
FATAL: Module bbswitch not found.
invoke-rc.d: initscript procps, action "start" failed.
dpkg: error processing procps (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of cups:
 cups depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing cups (--configure):
 dependency problems - leaving unconfigured
Setting up rsyslog (5.8.6-1ubuntu8.6) ...
No apport report written because the error message indicates it's a follow-up error from a previous failure.
                                                                                                            Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
FATAL: Module bbswitch not found.
invoke-rc.d: initscript rsyslog, action "restart" failed.
dpkg: error processing rsyslog (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libwbclient0 (2:3.6.3-2ubuntu2.9) ...
Setting up samba-common (2:3.6.3-2ubuntu2.9) ...
Setting up winbind (2:3.6.3-2ubuntu2.9) ...
 * Starting the Winbind daemon winbind                                                                                                                              [ OK ] 
Setting up libpam-winbind (2:3.6.3-2ubuntu2.9) ...
Setting up smbclient (2:3.6.3-2ubuntu2.9) ...
Setting up libpam-smbpass (2:3.6.3-2ubuntu2.9) ...
Setting up whoopsie (0.1.33) ...
FATAL: Module bbswitch not found.
invoke-rc.d: initscript whoopsie, action "start" failed.
dpkg: error processing whoopsie (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up python-apport (2.0.1-0ubuntu17.6) ...
No apport report written because MaxReports has already been reached
                                                                    dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-hpcups:
 printer-driver-hpcups depends on cups; however:
  Package cups is not configured yet.
dpkg: error processing printer-driver-hpcups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of hplip:
 hplip depends on printer-driver-hpcups (= 3.12.2-1ubuntu3.3); however:
  Package printer-driver-hpcups is not configured yet.
 hplip depends on cups (>= 1.1.20); however:
  Package cups is not configured yet.
dpkg: error processing hplip (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of printer-driver-postscript-hp:
 printer-driver-postscript-hp depends on hplip (>= 3.12.2-1ubuntu3.3No apport report written because MaxReports has already been reached
                                                                                                                                        No apport report written because MaxReports has already been reached
                                 No apport report written because MaxReports has already been reached
                                                                                                     No apport report written because MaxReports has already been reached
                                                                                                                                                                         No apport report written because MaxReports has already been reached
                                                                  ); however:
  Package hplip is not configured yet.
dpkg: error processing printer-driver-postscript-hp (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of samba:
 samba depends on procps; however:
  Package procps is not configured yet.
dpkg: error processing samba (--configure):
 dependency problems - leaving unconfigured
Setting up tdb-tools (1.2.9-4) ...
update-alternatives: using /usr/bin/tdbbackup.tdbtools to provide /usr/bin/tdbbackup (tdbbackup) in auto mode.
Setting up bumblebee (3.2.1-1~preciseppa6) ...
Adding members from group(s) 'adm sudo admin' to 'bumblebee':
antobbo
Adding user antobbo to group bumblebee
FATAL: Module bbswitch not found.
invoke-rc.d: initscript bumblebeed, action "start" failed.
dpkg: error processing bumblebee (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of bumblebee-nvidia:
 bumblebee-nvidia depends on bumblebee (= 3.2.1-1~preciseppa6); however:
  Package bumblebee is not configured yet.
dpkg: error processing bumblebee-nvidia (--configure):
 dependency problems - leaving unconfigured
Processing triggers for libc-bin ...
No apport report written because MaxReports has already been reached
                                                                    No apport report written because MaxReports has already been reached
                                                                                                                                        ldconfig deferred processing now taking place
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.5.0-42-generic
Errors were encountered while processing:
 procps
 cups
 rsyslog
 whoopsie
 apport-gtk
 printer-driver-hpcups
 hplip
 printer-driver-postscript-hp
 samba
 bumblebee
 bumblebee-nvidia
E: Sub-process /usr/bin/dpkg returned an error code (1)
antobbo@antobbo-xps17-ubuntu:~$ 



```

What do you think I should do now?
thanks

---

### Post by fantab on 2013-12-28
Well I've run out of ideas... it seems it will be easier if you re-install Ubuntu; unless you get better help here. 

Have you tried Ubuntu "Recovery Mode" from Grub Menu? It will be listed under 'Ubuntu Advanced options'... 
Once you boot into recovery mode try 'dpkg' option and see if it helps, also try 'failsafe graphics'. 
If it doesn't help then perhaps reinstalling Ubuntu is good idea, simple, clean and fresh.

---

### Post by antobbo on 2013-12-29
thanks for your help fantab. I have got to say that the idea of reinstalling everything has crossed my mind already, but then I will have to reinstall everything and that's quite a big put-off because I have an awful lot of applications that will need reinstalling. That said, if there isn't any other way then, so be it.
No I haven't tried the recovery mode because to be honest I am not that confident when it comes to repair/diagnose faults in ubuntu  - as you might have probably noticed already. I guess I save everything on an external HD and reinstall the whole thing (I have dual boot on my machine - win 7 and ubuntu, so I will have to be careful not to wipe everything out)

Thanks for trying anyway, much appreciated :-)!

---


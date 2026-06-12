---
title: "[SOLVED] reg:- Pulse audio sound."
date: 2008-11-26
forum: New to Ubuntu
---

### Post by halovivek on 2008-11-26
hi 
i have followed the pulse audio sound.
till now i dont have any sound.
thanks
please provide the solution i have pasted what i followed.
please help me
halovivek@halovivek-laptop:~$ sudo su
[sudo] password for halovivek:
root@halovivek-laptop:/home/halovivek# $ mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
bash: $: command not found
root@halovivek-laptop:/home/halovivek# $ sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf
bash: $: command not found
root@halovivek-laptop:/home/halovivek# mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/
cp: cannot stat `/root/.pulse': No such file or directory
cp: cannot stat `/root/.asound*': No such file or directory
cp: cannot stat `/etc/asound.conf': No such file or directory
root@halovivek-laptop:/home/halovivek# sudo apt-get install libasound2-plugins padevchooser libao-pulse libsdl1.2debian-pulseaudio flashplugin-nonfree
Reading package lists... Done
Building dependency tree
Reading state information... Done
padevchooser is already the newest version.
flashplugin-nonfree is already the newest version.
The following packages were automatically installed and are no longer required:
  libnss3-0d
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  libsdl1.2debian-alsa
The following NEW packages will be installed:
  libao-pulse libasound2-plugins libsdl1.2debian-pulseaudio
0 upgraded, 3 newly installed, 1 to remove and 0 not upgraded.
Need to get 327kB of archives.
After this operation, 594kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe libao-pulse 0.9.3-1 [7428B]
Get:2 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main libasound2-plugins 1.0.15-1ubuntu3 [117kB]
Get:3 [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe libsdl1.2debian-pulseaudio 1.2.13-1ubuntu1 [203kB]
Fetched 327kB in 0s (975kB/s)
dpkg: libsdl1.2debian-alsa: dependency problems, but removing anyway as you request:
 libsdl1.2debian depends on libsdl1.2debian-alsa (= 1.2.13-1ubuntu1) | libsdl1.2debian-all (= 1.2.13-1ubuntu1) | libsdl1.2debian-esd (= 1.2.13-1ubuntu1) | libsdl1.2debian-arts (= 1.2.13-1ubuntu1) | libsdl1.2debian-oss (= 1.2.13-1ubuntu1) | libsdl1.2debian-nas (= 1.2.13-1ubuntu1) | libsdl1.2debian-pulseaudio (= 1.2.13-1ubuntu1); however:
  Package libsdl1.2debian-alsa is to be removed.
  Package libsdl1.2debian-all is not installed.
  Package libsdl1.2debian-esd is not installed.
  Package libsdl1.2debian-arts is not installed.
  Package libsdl1.2debian-oss is not installed.
  Package libsdl1.2debian-nas is not installed.
  Package libsdl1.2debian-pulseaudio is not installed.
(Reading database ... 156668 files and directories currently installed.)
Removing libsdl1.2debian-alsa ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Selecting previously deselected package libao-pulse.
(Reading database ... 156660 files and directories currently installed.)
Unpacking libao-pulse (from .../libao-pulse_0.9.3-1_amd64.deb) ...
Replaced by files in installed package libao2 ...
Selecting previously deselected package libasound2-plugins.
Unpacking libasound2-plugins (from .../libasound2-plugins_1.0.15-1ubuntu3_amd64.deb) ...
Selecting previously deselected package libsdl1.2debian-pulseaudio.
Unpacking libsdl1.2debian-pulseaudio (from .../libsdl1.2debian-pulseaudio_1.2.13-1ubuntu1_amd64.deb) ...
Setting up libao-pulse (0.9.3-1) ...
Setting up libasound2-plugins (1.0.15-1ubuntu3) ...
Setting up libsdl1.2debian-pulseaudio (1.2.13-1ubuntu1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

root@halovivek-laptop:/home/halovivek# sudo apt-get remove --purge libflashsupport flashplugin-nonfree-extrasound
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package libflashsupport is not installed, so not removed
E: Couldn't find package flashplugin-nonfree-extrasound

root@halovivek-laptop:/home/halovivek# pulseaudio & pavucontrol
W: main.c: This program is not intended to be run as root (unless --system is specified).
[1] 7673
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0
ALSA lib control.c:909:(snd_ctl_open_noupdate) Invalid CTL front:0

(pavucontrol:7674): Gtk-CRITICAL **: gtk_widget_get_clipboard: assertion `gtk_widget_has_screen (widget)' failed

(pavucontrol:7674): Gtk-CRITICAL **: gtk_clipboard_set_with_owner: assertion `clipboard != NULL' failed

root@halovivek-laptop:/home/halovivek# sudo apt-get update && sudo apt-get dist-upgrade
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy Release.gpg
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Translation-en_US
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy Release
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Packages
Ign cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Packages
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1) hardy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports Release.gpg
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Translation-en_US
Ign [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports Release
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Translation-en_US
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Get:2 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/main Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/universe Sources
Get:3 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid Release [27.6kB]
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-updates/multiverse Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Packages
Get:4 [http://dl.google.com](http://dl.google.com) stable Release [1300B]
Ign [http://dl.google.com](http://dl.google.com) stable Release
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Packages
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/main Sources
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/restricted Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/universe Sources
Hit [http://se.archive.ubuntu.com](http://se.archive.ubuntu.com) hardy-backports/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources
Get:5 [http://dl.google.com](http://dl.google.com) stable/non-free Packages [966B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release.gpg
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Translation-en_US
Get:6 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Packages [5161B]
Get:7 [http://ppa.launchpad.net](http://ppa.launchpad.net) intrepid/main Sources [1237B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) intrepid/non-free Sources
Fetched 36.5kB in 3s (11.5kB/s)
W: GPG error: [http://dl.google.com](http://dl.google.com) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/main/binary-amd64/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

W: Failed to fetch cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release amd64 (20080702.1)]/dists/hardy/restricted/binary-amd64/Packages.gz  Please use apt-cdrom tomake this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

E: Some index files failed to download, they have been ignored, or old ones used instead.

root@halovivek-laptop:/home/halovivek# aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SB [HDA ATI SB], device 0: ALC883 Analog [ALC883 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: HDMI [HDA ATI HDMI], device 3: ATI HDMI [ATI HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by halovivek on 2008-12-29
hi i have solved this thanks:)

---

### Post by Efros on 2008-12-29
Some indication as to how you resolved this issue would help other users.

---

### Post by halovivek on 2008-12-29
> **Efros said:**
> Some indication as to how you resolved this issue would help other users.

using this threat i have solved the problem.
[http://ubuntuforums.org/showthread.php?t=1005416](http://ubuntuforums.org/showthread.php?t=1005416)

the solution is 
i have the code as below
Code:
sudo gedit /etc/modprobe.d/alsa-base
Add this to the end:

Code:
# added by myself
alias snd-card-0 snd-hda-intel
options snd-hda-intel model=auto

Reboot and it then works.

---


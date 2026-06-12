---
title: "HOWTO: Install vmware.bundle, add directx support, fix ubersensitive mouse ingame"
date: 2009-11-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mo3head on 2009-11-27
[center][http://3.bp.blogspot.com/_22IKBwE2p4M/Swvow-GKHAI/AAAAAAAAABs/ZeDJZOQOJkY/s1600/Screenshot.png](http://3.bp.blogspot.com/_22IKBwE2p4M/Swvow-GKHAI/AAAAAAAAABs/ZeDJZOQOJkY/s1600/Screenshot.png)
[http://4.bp.blogspot.com/_22IKBwE2p4M/Swvontxs-WI/AAAAAAAAABk/EhXSELRv40o/s1600/Screenshotvm.png](http://4.bp.blogspot.com/_22IKBwE2p4M/Swvontxs-WI/AAAAAAAAABk/EhXSELRv40o/s1600/Screenshotvm.png)[/center]
Hello,
lets start.
What we need:
[LIST]
[*]Vmware binary
[*]Root access
[*]Microsoft Windows iso/cd
[/LIST]

First download the vmware binary, preferably [_VMWare Workstation_]("http://downloads.vmware.com/d/info/desktop_downloads/vmware_workstation/7_0").
When you are finished downloading open up your console.
We have to install the required packages now:
```
sudo aptitude install build-essential linux-kernel-headers
```
AFter that change to your workdirectory (where you saved the VMware.bundle).
```
[cd /media/FATTT/apps/
```
Now execute the VMware binary.
```
gksudo bash ./VMware-Workstation-Full-7.0.0-102739.x86_64.bundle
```
The VMware installer will guide you trough the installation.
Here a little example how it can look like:
```
**h4ck@b0x:~$ sudo aptitude install build-essential linux-kernel-headers**

Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "linux-kernel-devel"
Couldn't find any package whose name or description matched "linux-kernel-devel"
The following NEW packages will be installed:
build-essential dpkg-dev{a} fakeroot{a} g++{a} g++-4.4{a}
libstdc++6-4.4-dev{a} patch{a}
0 packages upgraded, 7 newly installed, 0 to remove and 45 not upgraded.
Need to get 7,832kB of archives. After unpacking 25.6MB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 http://us.archive.ubuntu.com karmic/main libstdc++6-4.4-dev 4.4.1-4ubuntu8 [1,526kB]
Get:2 http://us.archive.ubuntu.com karmic/main g++-4.4 4.4.1-4ubuntu8 [5,498kB]
Get:3 http://us.archive.ubuntu.com karmic/main g++ 4:4.4.1-1ubuntu2 [1,448B]
Get:4 http://us.archive.ubuntu.com karmic/main patch 2.5.9-5 [101kB]
Get:5 http://us.archive.ubuntu.com karmic/main dpkg-dev 1.15.4ubuntu2 [573kB]
Get:6 http://us.archive.ubuntu.com karmic/main build-essential 11.4 [7,170B]
Get:7 http://us.archive.ubuntu.com karmic/main fakeroot 1.12.4ubuntu1 [126kB]
Fetched 7,832kB in 11s (693kB/s) 
Selecting previously deselected package libstdc++6-4.4-dev.
(Reading database ... 116779 files and directories currently installed.)
Unpacking libstdc++6-4.4-dev (from .../libstdc++6-4.4-dev_4.4.1-4ubuntu8_amd64.deb) ...
Selecting previously deselected package g++-4.4.
Unpacking g++-4.4 (from .../g++-4.4_4.4.1-4ubuntu8_amd64.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.4.1-1ubuntu2_amd64.deb) ...
Selecting previously deselected package patch.
Unpacking patch (from .../patch_2.5.9-5_amd64.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.15.4ubuntu2_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.4_amd64.deb) ...
Selecting previously deselected package fakeroot.
Unpacking fakeroot (from .../fakeroot_1.12.4ubuntu1_amd64.deb) ...
Processing triggers for man-db ...
Setting up patch (2.5.9-5) ...
Setting up dpkg-dev (1.15.4ubuntu2) ...
Setting up fakeroot (1.12.4ubuntu1) ...
update-alternatives: using /usr/bin/fakeroot-sysv to provide /usr/bin/fakeroot (fakeroot) in auto mode.

Setting up libstdc++6-4.4-dev (4.4.1-4ubuntu8) ...
Setting up g++-4.4 (4.4.1-4ubuntu8) ...
Setting up g++ (4:4.4.1-1ubuntu2) ...
update-alternatives: using /usr/bin/g++ to provide /usr/bin/c++ (c++) in auto mode.

Setting up build-essential (11.4) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done


**h4ck@b0x:~$ cd "/media/E4D051A4D0517E2C/_APPS LINUX"**

**h4ck@b0x:~$ gksudo bash ./VMware-Workstation-Full-7.0.0-203739.x86_64.bundle**
```
Executed commands are highlighted.

Alright when finished installing open up your VMware Workstation.
Click on "Create new Virtual Machine".
Follow the wizard, mount your win iso or insert your windows cd.
When done installing windows, close VMware.
Browse to your installation path, open up your .vmx and add these 3 lines to add the directx support:
```
mks.enable3d = TRUE
svga.vramSize = 67108864
vmmouse.present = FALSE
```
Add these 2 lines to fix the HIGH mouse sensitivity ingame ( happens usually in rpgs )
```
vmmouse.present = "FALSE"
pref.motionUngrab = "FALSE"
```
Save the file and open your VMWare Workstation, start your windows, when finished loading hit the "VM" button on the top and click on "Install VMware Tools".
An installationwizard should start, if it doesnt browse to drive D:\ and start the autorun.

Now we are finished, if you want you can now download/install whatever game you like :)

I did try this tutorial with this specs :
OS: Linux
Release: 2.6.31-14-generic
Version: #48-Ubuntu SMP Fri Oct 16 14:05:01 UTC 2009
Architecture: x86_64
AMD Athlon(tm) 7750 Dual-Core Processor
MemTotal: 4057696 kB
Graphic: Zotac GeForce 9600 GT

Games tested were Atlantica online and RAPPELZ (both mmorpgs), had NO fps lags nor sound lags.
Though if you experience small sound lags, either restart your game or disable sound :(

---


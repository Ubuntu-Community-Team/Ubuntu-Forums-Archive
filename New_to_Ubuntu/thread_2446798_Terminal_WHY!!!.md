---
title: "Terminal WHY!!!"
date: 2020-07-07
forum: New to Ubuntu
---

### Post by lars2435 on 2020-07-07
****mynamedevice.etc***********:/usr/src/intel-i915-backport-3.8-dkms-3.8.6.0$ 
The files are there^^^^^^^

sudo apt-get purge intel-i915-backport-3.8-dkms-3.8.6.0
[sudo] password for miki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-i915-backport-3.8-dkms-3.8.6.0
E: Couldn't find any package by glob 'intel-i915-backport-3.8-dkms-3.8.6.0'
E: Couldn't find any package by regex 'intel-i915-backport-3.8-dkms-3.8.6.0'

Why can't I get rid of these files?

Then this:
":/usr/src/intel-i915-backport-3.8-dkms-3.8.6.0$ sudo add-apt purge intel-i915-backport-3.8-dkms-3.8.6.0[sudo] password for miki: 
sudo: add-apt: command not found"

So how do I become the owner of root directory ????

---

### Post by ajgreeny on 2020-07-07
Because you have the wrong name for it; most package file names are not appended with the version number.

I'm  not on my Xubuntu box at the moment so can't  search but you may find it easier to search and remove unwanted packages using synaptic, though you'll  have to install it first as it's  no longer a default Ubuntu package.

---

### Post by lars2435 on 2020-07-07
Then I wanted to install chromeOS and straight up copied the code the web page gave ([https://www.chromium.org/chromium-os/quick-start-guide](https://www.chromium.org/chromium-os/quick-start-guide)) 
Went to terminal and terminal said NO!  WHY! I can't do anything in this OS (Ubuntu)

(sudo apt-get install git-core gitk git-gui subversion curl lvm2 thin-provisioning-tools python-pkg-resources python-virtualenv python-oauth2client[sudo] password for miki: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'git' instead of 'git-core'
Package python-virtualenv is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


E: Package 'python-virtualenv' has no installation candidate
E: Unable to locate package python-oauth2client

---

### Post by Holger_Gehrke on 2020-07-07
The package manager can only remove stuff that was installed from a package. 

You can use dpkg - the lower level of the package-manager - to find out what package a file or directory is part of.
```

dpkg -S /usr/src/intel-i915-backport-3.8-dkms-3.8.6.0

```
If that outputs something along the lines of "can't find it", then these files were not installed through the package manager and you have to uninstall them manually. 

Since packages.ubuntu.com says that there's no official package containing that directory, you either installed it from a package from some unofficial source or outside of package management.

Holger

---

### Post by ajgreeny on 2020-07-07
I think perhaps we should go back to the very beginning and try to find out exactly what you are trying to do and why you need to remove that intel-i915  package.

Are you also aware that chromium and Chrome OS are not applications but complete operating systems; you do not install them in Ubuntu but use Ubuntu to build them from source code (actually that is chromium OS only as Chrome OS is proprietary and I'm  not sure you can get source code for that) and then install the OS separately from Ubuntu.

---

### Post by lars2435 on 2020-07-07
I was in a haze when I installed them (hope "haze" is not too politically uncorrect for the masters of Ibuntiu) but I did something along with - install by preload.. Apparently I did something outside the normal lines of conduct for Ubuntu.. however it was in an attempt to make full utilization of my hardware (northbridge) and GPU/GPU as it was lacking

---

### Post by lars2435 on 2020-07-07
Yes I am well aware that chromium OS is an OS .. Basically what I'm trying to do is to have a dual boot system and I need to partition my mounted ssd so I can utilize half of it for an android OS in ZSF file format.. but I don'f want a linux based android OS as those **** (politically incorrect word) so I need to find a way to boot from UEFI to ? Android stuff files (OS) ((Android 10))

---

### Post by lars2435 on 2020-07-07
btw. I did the thing u said "Holger_Gehrke" and this came up 
(dpkg -S /usr/src/intel-i915-backport-3.8-dkms-3.8.6.0intel-i915-backport-3.8-dkms: /usr/src/intel-i915-backport-3.8-dkms-3.8.6.0)

Anyway thanks for the feedback :guitar:

---

### Post by lars2435 on 2020-07-07
also did this:

Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-bt-dw1550-0.1 DKMS files...
Building for 5.4.0-40-generic
Building for architecture x86_64
Building initial module for 5.4.0-40-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/oem-bt-dw1550-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.4.0-40-generic (x86_64)
Consult /var/lib/dkms/oem-bt-dw1550/0.1/build/make.log for more information.
dpkg: error processing package oem-bt-dw1550-dkms (--configure):
 installed oem-bt-dw1550-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 intel-i915-backport-3.8-dkms
 alsa-hda-lts-quantal-dkms
 oem-bt-dw1550-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
miki@miki-Latitude-E7240:~$ sudo su
root@miki-Latitude-E7240:/home/miki# sudo apt-get purge intel-i915-backport-3.8-dkms-3.8.6.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-i915-backport-3.8-dkms-3.8.6.0
E: Couldn't find any package by glob 'intel-i915-backport-3.8-dkms-3.8.6.0'
E: Couldn't find any package by regex 'intel-i915-backport-3.8-dkms-3.8.6.0'
root@miki-Latitude-E7240:/home/miki# sudo apt-get purge intel-i915-backport-3.8-dkms-3.8.6.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-i915-backport-3.8-dkms-3.8.6.0
E: Couldn't find any package by glob 'intel-i915-backport-3.8-dkms-3.8.6.0'
E: Couldn't find any package by regex 'intel-i915-backport-3.8-dkms-3.8.6.0'
root@miki-Latitude-E7240:/home/miki#

---

### Post by ActionParsnip on 2020-07-07
If you are root, you don't need sudo. Are you logging in to the desktop as root (not recommended)?

---

### Post by Holger_Gehrke on 2020-07-07
> **lars2435 said:**
> btw. I did the thing u said "Holger_Gehrke" and this came up 
(dpkg -S /usr/src/intel-i915-backport-3.8-dkms-3.8.6.0
**intel-i915-backport-3.8-dkms**: /usr/src/intel-i915-backport-3.8-dkms-3.8.6.0)


The part I put in **bold **is the package name. You should be able to remove it with
```

sudo apt purge intel-i915-backport-3.8-dkms

```

And the instructions for compiling chromiumos to which you linked are for Ubuntu 16.04. If you are running a different release of Ubuntu then some of the packages they tell you to install either have a different name or aren't available for that release.

Holger

---

### Post by lars2435 on 2020-07-07
Now this happened:

sudo su
root@miki-Latitude-E7240:/home/miki# sudo apt-get purge intel-i915-backport-3.8-dkms-3.8.6.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-i915-backport-3.8-dkms-3.8.6.0
E: Couldn't find any package by glob 'intel-i915-backport-3.8-dkms-3.8.6.0'
E: Couldn't find any package by regex 'intel-i915-backport-3.8-dkms-3.8.6.0'
root@miki-Latitude-E7240:/home/miki# sudo apt-get purge intel-i915-backport-3.8-dkms-3.8.6.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package intel-i915-backport-3.8-dkms-3.8.6.0
E: Couldn't find any package by glob 'intel-i915-backport-3.8-dkms-3.8.6.0'
E: Couldn't find any package by regex 'intel-i915-backport-3.8-dkms-3.8.6.0'
root@miki-Latitude-E7240:/home/miki# 
root@miki-Latitude-E7240:/home/miki# sudo apt-get purge intel-i915-backport-3.8-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  intel-i915-backport-3.8-dkms*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 1.865 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 181438 files and directories currently installed.)
Removing intel-i915-backport-3.8-dkms (3.8.6.0) ...


------------------------------
Deleting module version: 3.8.6.0
completely from the DKMS tree.
------------------------------
Done.
Setting up alsa-hda-lts-quantal-dkms (0.1) ...
Removing old alsa-hda-lts-quantal-0.1 DKMS files...


------------------------------
Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Loading new alsa-hda-lts-quantal-0.1 DKMS files...
First Installation: checking all kernels...
Building only for 5.4.0-40-generic
Building for architecture x86_64
Building initial module for 5.4.0-40-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/alsa-hda-lts-quantal-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.4.0-40-generic (x86_64)
Consult /var/lib/dkms/alsa-hda-lts-quantal/0.1/build/make.log for more information.
dpkg: error processing package alsa-hda-lts-quantal-dkms (--configure):
 installed alsa-hda-lts-quantal-dkms package post-installation script subprocess returned error exit status 10
Setting up oem-bt-dw1550-dkms (0.1) ...
Removing old oem-bt-dw1550-0.1 DKMS files...


------------------------------
Deleting module version: 0.1
completely from the DKMS tree.
------------------------------
Done.
Loading new oem-bt-dw1550-0.1 DKMS files...
Building for 5.4.0-40-generic
Building for architecture x86_64
Building initial module for 5.4.0-40-generic
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/oem-bt-dw1550-dkms.0.crash'
Error! Bad return status for module build on kernel: 5.4.0-40-generic (x86_64)
Consult /var/lib/dkms/oem-bt-dw1550/0.1/build/make.log for more information.
dpkg: error processing package oem-bt-dw1550-dkms (--configure):
 installed oem-bt-dw1550-dkms package post-installation script subprocess returned error exit status 10
Errors were encountered while processing:
 alsa-hda-lts-quantal-dkms
 oem-bt-dw1550-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@miki-Latitude-E7240:/home/miki#

---

### Post by Holger_Gehrke on 2020-07-07
Dynamic Kernel Module Support (dkms) allows kernel modules - a fancy way of saying low-level driver software - to be distributed separately from the kernel and compiled on the system where they are supposed to be used. At a guess I'd say these are a sound driver (alsa-hda-lts-quantal-dkms) and perhaps a Bluetooth driver (oem-bt-dw1550-dkms). Within reason these modules run with a wide range of kernel versions, but it looks like these modules can't be compiled to work with the kernel you're using (5.4.0-40? Since my 18.04 has 5.3.0-61, I think you're probably running 20.04, right ?). You don't even get a report in /var/crash/ for what's wrong, since there is already a report for this and the installation routine won't overwrite it.

Holger

---


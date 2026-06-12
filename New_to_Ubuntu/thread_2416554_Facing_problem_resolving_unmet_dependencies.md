---
title: "Facing problem resolving unmet dependencies"
date: 2019-04-11
forum: New to Ubuntu
---

### Post by apverma13 on 2019-04-11
hi,

I'm using Ubuntu 18.04 and facing problem with unmet dependencies while installing anything new.

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gnome-boxes : Depends: libspice-client-glib-2.0-8 (>= 0.33) but it is not going to be installed
               Depends: libspice-client-gtk-3.0-5 (>= 0.32) but it is not going to be installed
               Depends: libvirt-glib-1.0-0 (>= 0.2.3~) but it is not going to be installed
               Depends: libvirt-daemon but it is not installable
               Depends: tracker (>= 2.0) but it is not going to be installed
               Recommends: qemu-system-x86 but it is not installable
E: Unable to correct problems, you have held broken packages.

```

I've tried a few solutions posted on forums but northing is working out.
Can you please help? Thank you.

---

### Post by TheFu on 2019-04-11
```
sudo apt update
sudo apt dist-upgrade
```

Run those first.  It is like that the the system hasn't been properly maintained and the packages available aren't the ones in the cache any more.  If you have been patching weekly, let us know that.

Without actually telling us what you've tried before, how can we know?

---

### Post by apverma13 on 2019-04-12
I've tried

```

          sudo apt update
sudo apt dist-upgrade 

```

also 

```

sudo apt-get autoclean
sudo apt-get -f install
sudo dpkg --configure -a
sudo apt-get -f install


```

```

sudo apt-get update
sudo apt-get -u dist-upgrade
sudo apt-get -o Debug::pkgProblemResolver=yes dist-upgrade
sudo apt-get remove --dry-run package-name

```

```

sudo apt-get update
sudo apt-get -u dist-upgrade
sudo apt-get clean package-name
sudo apt-get install --reinstall package-name

```

I've been trying to update wine on my laptop when it didn't worked I removed it.

I've tried to check broken packages in synaptic package manager found nothing then used following steps from fourm posts,

```

sudo dpkg --remove --force-remove-reinstreq package_name 

sudo apt-get update
```

 i found out the package name using some other code but forgot which one.

---

### Post by apverma13 on 2019-04-12
I'm not very sure what exactly is causing  the unmet dependencies error but now I can't install any new package like discord, or wine or gnome boxes.

---

### Post by deadflowr on 2019-04-12
Look at what each of those packages apt policy outputs are:
```
apt policy libspice-client-glib-2.0-8
apt policy libspice-client-gtk-3.0-5
apt policy libvirt-glib-1.0-0
apt policy libvirt-daemon
apt policy tracker
apt policy qemu-system-x86
apt policy gnome-boxes
```
post back the results.

---

### Post by TheFu on 2019-04-12
Helpful to know what you tried. Thanks.  Also need to see the success AND failures, if any. Seeing issues, without the command ran, less useful.

If you've ever installed any .deb files directly, those can hold back any dependent files. Best to stick with official Canonical repositories as much as possible, then use trusted, reputable, PPAs.  If a .deb package is the only option, then keep track of it, so any dependency problems like that can be addressed by removal.

Best to NOT use dpkg directly, unless absolutely needed.


This only needs to be run every 6 hrs or so.
```
sudo apt-get update
```
Doing it more often won't hurt, but isn't likely to matter unless a specific package or dependency you are dealing with is being actively deployed during that time.

Was this clean?
```
sudo apt dist-upgrade
```
No errors?

**Aptitude** has a broken package fix option. After you check the policies, but be worth trying.

On my system, 
```
$ sudo apt policy gnome-boxes
gnome-boxes:
  Installed: 3.18.1-1.1
  Candidate: 3.18.1-1.1
  Version table:
 *** 3.18.1-1.1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) xenial/universe amd64 Packages
        100 /var/lib/dpkg/status
```

Do you have some other hypervisor already installed?  It the system kvm capable?

---

### Post by apverma13 on 2019-04-12
that' what i got after running code u mentioned,

[LIST=1]
[*]apt policy libspice-client-glib-2.0-8 
[/LIST]
```

libspice-client-glib-2.0-8:
  Installed: (none)
  Candidate: 0.34-1.1build1
  Version table:
     0.34-1.1build1 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

2. apt policy libspice-client-gtk-3.0-5

```

libspice-client-gtk-3.0-5:
  Installed: (none)
  Candidate: 0.34-1.1build1
  Version table:
     0.34-1.1build1 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

3. apt policy libvirt-glib-1.0-0

```

libvirt-glib-1.0-0:
  Installed: (none)
  Candidate: 1.0.0-1
  Version table:
     1.0.0-1 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

4. apt policy libvirt-daemon

```

libvirt-daemon:
  Installed: (none)
  Candidate: (none)
  Version table:


```

5. apt policy tracker
```

tracker:
  Installed: (none)
  Candidate: 2.0.3-1ubuntu4
  Version table:
     2.0.3-1ubuntu4 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages

```

6. apt policy qemu-system-x86

```

qemu-system-x86:
  Installed: (none)
  Candidate: (none)
  Version table:


```

7. apt policy gnome-boxes
```

gnome-boxes:
  Installed: (none)
  Candidate: 3.28.1-1
  Version table:
     3.28.1-1 500
        500 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 Packages


```

---

### Post by deadflowr on 2019-04-13
So both packages which show nothing are in main.
Check that main is enabled.

Easily done in Software and Updates, main is also known as the Canonical repository.

---

### Post by apverma13 on 2019-04-13
sudo apt-get update gives back,

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```

I had to look up what hypervisor means :). Yeah I had virtualbox installed earlier with win7 for work.
Machine is kvm capable. 
```
egrep -c '(vmx|svm)' /proc/cpuinfo
```
gives 4 as output but

```

cat /sys/hypervisor/properties/capabilities

```
gives
```
cat: /sys/hypervisor/properties/capabilities: No such file or directory
```
and kvm-ok gives
```
Command 'kvm-ok' not found, but can be installed with:

sudo apt install cpu-checker
```
and when i tried to install cpu-checker using this command it gives
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package cpu-checker is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

```

---

### Post by apverma13 on 2019-04-13
Thank you for the quick reply. Yeah main was not enabled. I've enabled it now.

---

### Post by apverma13 on 2019-04-13
After enabling main. I ran sudo apt-update then sudo apt-upgrade.

After a lot of upgrading a i got an error saying that my kernel is unsigned so grub can't be upgraded.

```

Errors were encountered while processing:
 grub-efi-amd64
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Should i go to an older version?

---

### Post by TheFu on 2019-04-13
[https://askubuntu.com/questions/763472/what-can-i-do-to-fix-this-error-on-grub-efi](https://askubuntu.com/questions/763472/what-can-i-do-to-fix-this-error-on-grub-efi) has some ideas about this issue.

> 
Should i go to an older version? 
of what?

---

### Post by apverma13 on 2019-04-13
I mean older version of Kernel.
It's 5.0.0-050000-generic right now.

Any other suggestion for unsigned kernel? so grub can upgrade
btw installing gnome boxes also gave same error

```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  augeas-lenses cpu-checker dmeventd ibverbs-providers ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaio1 libaugeas0 libcacard0 libcue1
  libdevmapper-event1.02.1 libenca0 libfdt1 libgif7 libgovirt-common libgovirt2 libgsf-1-114 libgsf-1-common libgtk-vnc-2.0-0 libgvnc-1.0-0
  libibverbs1 libiptcdata0 libiscsi7 liblvm2app2.2 liblvm2cmd2.02 libnetcf1 libnl-route-3-200 libosinfo-1.0-0 libosinfo-bin libphodav-2.0-0
  libphodav-2.0-common librados2 librbd1 librdmacm1 libreadline5 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5 libspice-server1
  libtagc0 libtracker-control-2.0-0 libtracker-miner-2.0-0 libusbredirhost1 libusbredirparser1 libvirt-daemon
  libvirt-daemon-driver-storage-rbd libvirt-glib-1.0-0 libvirt0 libxen-4.9 libxenstore3.0 libxml2-utils lvm2 msr-tools osinfo-db
  qemu-block-extra qemu-kvm qemu-system-common qemu-system-x86 qemu-utils seabios sharutils spice-client-glib-usb-acl-helper tracker
  tracker-extract tracker-miner-fs
Suggested packages:
  augeas-doc augeas-tools libosinfo-l10n gstreamer1.0-plugins-bad gstreamer1.0-libav libvirt-daemon-driver-storage-gluster
  libvirt-daemon-driver-storage-sheepdog libvirt-daemon-driver-storage-zfs libvirt-daemon-system numad thin-provisioning-tools samba vde2
  sgabios ovmf debootstrap sharutils-doc bsd-mailx | mailx
The following NEW packages will be installed:
  augeas-lenses cpu-checker dmeventd gnome-boxes ibverbs-providers ipxe-qemu ipxe-qemu-256k-compat-efi-roms libaio1 libaugeas0 libcacard0
  libcue1 libdevmapper-event1.02.1 libenca0 libfdt1 libgif7 libgovirt-common libgovirt2 libgsf-1-114 libgsf-1-common libgtk-vnc-2.0-0
  libgvnc-1.0-0 libibverbs1 libiptcdata0 libiscsi7 liblvm2app2.2 liblvm2cmd2.02 libnetcf1 libnl-route-3-200 libosinfo-1.0-0 libosinfo-bin
  libphodav-2.0-0 libphodav-2.0-common librados2 librbd1 librdmacm1 libreadline5 libspice-client-glib-2.0-8 libspice-client-gtk-3.0-5
  libspice-server1 libtagc0 libtracker-control-2.0-0 libtracker-miner-2.0-0 libusbredirhost1 libusbredirparser1 libvirt-daemon
  libvirt-daemon-driver-storage-rbd libvirt-glib-1.0-0 libvirt0 libxen-4.9 libxenstore3.0 libxml2-utils lvm2 msr-tools osinfo-db
  qemu-block-extra qemu-kvm qemu-system-common qemu-system-x86 qemu-utils seabios sharutils spice-client-glib-usb-acl-helper tracker
  tracker-extract tracker-miner-fs
0 upgraded, 65 newly installed, 0 to remove and 19 not upgraded.
3 not fully installed or removed.
Need to get 22.6 MB of archives.
After this operation, 101 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libiscsi7 amd64 1.17.0-1.1 [55.4 kB]
Get:2 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libnl-route-3-200 amd64 3.2.29-0ubuntu3 [146 kB]
Get:3 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libibverbs1 amd64 17.1-1ubuntu0.1 [44.5 kB]
Get:4 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 librados2 amd64 12.2.11-0ubuntu0.18.04.1 [2,683 kB]
Get:5 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 librbd1 amd64 12.2.11-0ubuntu0.18.04.1 [920 kB]                          
Get:6 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 qemu-block-extra amd64 1:2.11+dfsg-1ubuntu7.12 [39.4 kB]                 
Get:7 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 qemu-system-common amd64 1:2.11+dfsg-1ubuntu7.12 [662 kB]                
Get:8 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 augeas-lenses all 1.10.1-2 [300 kB]                                              
Get:9 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 msr-tools amd64 1.3-2build1 [9,760 B]                                            
Get:10 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 cpu-checker amd64 0.7-0ubuntu7 [6,862 B]                                        
Get:11 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libdevmapper-event1.02.1 amd64 2:1.02.145-4.1ubuntu3 [10.9 kB]                  
Get:12 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 liblvm2cmd2.02 amd64 2.02.176-4.1ubuntu3 [586 kB]                               
Get:13 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 dmeventd amd64 2:1.02.145-4.1ubuntu3 [30.4 kB]                                  
Get:14 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgovirt-common all 0.3.4-2 [14.1 kB]                                      
Get:15 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgovirt2 amd64 0.3.4-2 [35.0 kB]                                          
Get:16 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgvnc-1.0-0 amd64 0.7.2-1 [56.3 kB]                                       
Get:17 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgtk-vnc-2.0-0 amd64 0.7.2-1 [24.6 kB]                                    
Get:18 http://in.archive.ubuntu.com/ubuntu bionic-updates/universe amd64 osinfo-db all 0.20180929-1ubuntu0.1 [76.7 kB]                       
Get:19 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libosinfo-1.0-0 amd64 1.1.0-1 [68.5 kB]                                     
Get:20 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libcacard0 amd64 1:2.5.0-3 [19.6 kB]                                            
Get:21 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libphodav-2.0-common all 2.2-2 [7,900 B]                                    
Get:22 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libphodav-2.0-0 amd64 2.2-2 [21.8 kB]                                       
Get:23 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libusbredirparser1 amd64 0.7.1-1 [13.6 kB]                                      
Get:24 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libusbredirhost1 amd64 0.7.1-1 [17.6 kB]                                        
Get:25 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 spice-client-glib-usb-acl-helper amd64 0.34-1.1build1 [10.8 kB]             
Get:26 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libspice-client-glib-2.0-8 amd64 0.34-1.1build1 [322 kB]                    
Get:27 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libspice-client-gtk-3.0-5 amd64 0.34-1.1build1 [47.9 kB]                    
Get:28 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libvirt0 amd64 4.0.0-1ubuntu8.8 [1,249 kB]                              
Get:29 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libvirt-glib-1.0-0 amd64 1.0.0-1 [111 kB]                                   
Get:30 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libosinfo-bin amd64 1.1.0-1 [22.1 kB]                                       
Get:31 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libaugeas0 amd64 1.10.1-2 [159 kB]                                              
Get:32 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libnetcf1 amd64 1:0.2.8-1ubuntu2 [46.4 kB]                                      
Get:33 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libxenstore3.0 amd64 4.9.2-0ubuntu1 [19.7 kB]                                   
Get:34 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libxen-4.9 amd64 4.9.2-0ubuntu1 [399 kB]                                        
Get:35 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libvirt-daemon amd64 4.0.0-1ubuntu8.8 [2,173 kB]                        
Get:36 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libtracker-control-2.0-0 amd64 2.0.3-1ubuntu4 [12.6 kB]                         
Get:37 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 tracker amd64 2.0.3-1ubuntu4 [242 kB]                                       
Get:38 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 gnome-boxes amd64 3.28.1-1 [960 kB]                                         
Get:39 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 ibverbs-providers amd64 17.1-1ubuntu0.1 [160 kB]                        
Get:40 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 ipxe-qemu all 1.0.0+git-20180124.fbe8c52d-0ubuntu2.2 [912 kB]           
Get:41 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 ipxe-qemu-256k-compat-efi-roms all 1.0.0+git-20150424.a25a16d-0ubuntu2 [545 kB] 
Get:42 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libaio1 amd64 0.3.110-5 [6,448 B]                                               
Get:43 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libcue1 amd64 1.4.0-1 [25.2 kB]                                             
Get:44 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libenca0 amd64 1.19-1 [54.0 kB]                                             
Get:45 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libgif7 amd64 5.1.4-2 [30.6 kB]                                                 
Get:46 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgsf-1-common all 1.14.41-2 [96.8 kB]                                     
Get:47 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libgsf-1-114 amd64 1.14.41-2 [97.1 kB]                                      
Get:48 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 liblvm2app2.2 amd64 2.02.176-4.1ubuntu3 [433 kB]                                
Get:49 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libreadline5 amd64 5.2+dfsg-3build1 [99.5 kB]                                   
Get:50 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libspice-server1 amd64 0.14.0-1ubuntu2.4 [345 kB]                       
Get:51 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libtagc0 amd64 1.11.1+dfsg.1-0.2build2 [15.9 kB]                                
Get:52 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libtracker-miner-2.0-0 amd64 2.0.3-1ubuntu4 [62.2 kB]                           
Get:53 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libvirt-daemon-driver-storage-rbd amd64 4.0.0-1ubuntu8.8 [15.4 kB]      
Get:54 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 libxml2-utils amd64 2.9.4+dfsg1-6.1ubuntu1.2 [35.8 kB]                  
Get:55 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 lvm2 amd64 2.02.176-4.1ubuntu3 [929 kB]                                         
Get:56 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 libfdt1 amd64 1.4.5-3 [15.7 kB]                                                 
Get:57 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 librdmacm1 amd64 17.1-1ubuntu0.1 [56.0 kB]                              
Get:58 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 seabios all 1.10.2-1ubuntu1 [128 kB]                                            
Get:59 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 qemu-system-x86 amd64 1:2.11+dfsg-1ubuntu7.12 [5,190 kB]                
Get:60 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 qemu-kvm amd64 1:2.11+dfsg-1ubuntu7.12 [13.2 kB]                        
Get:61 http://in.archive.ubuntu.com/ubuntu bionic-updates/main amd64 qemu-utils amd64 1:2.11+dfsg-1ubuntu7.12 [868 kB]                       
Get:62 http://in.archive.ubuntu.com/ubuntu bionic/main amd64 sharutils amd64 1:4.15.2-3 [155 kB]                                             
Get:63 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 libiptcdata0 amd64 1.0.4-6ubuntu1 [20.7 kB]                                 
Get:64 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 tracker-extract amd64 2.0.4-1 [616 kB]                                      
Get:65 http://in.archive.ubuntu.com/ubuntu bionic/universe amd64 tracker-miner-fs amd64 2.0.4-1 [68.5 kB]                                    
Fetched 22.6 MB in 3min 47s (99.8 kB/s)                                                                                                      
Extracting templates from packages: 100%
Selecting previously unselected package libiscsi7:amd64.
(Reading database ... 301700 files and directories currently installed.)
Preparing to unpack .../00-libiscsi7_1.17.0-1.1_amd64.deb ...
Unpacking libiscsi7:amd64 (1.17.0-1.1) ...
Selecting previously unselected package libnl-route-3-200:amd64.
Preparing to unpack .../01-libnl-route-3-200_3.2.29-0ubuntu3_amd64.deb ...
Unpacking libnl-route-3-200:amd64 (3.2.29-0ubuntu3) ...
Selecting previously unselected package libibverbs1:amd64.
Preparing to unpack .../02-libibverbs1_17.1-1ubuntu0.1_amd64.deb ...
Unpacking libibverbs1:amd64 (17.1-1ubuntu0.1) ...
Selecting previously unselected package librados2.
Preparing to unpack .../03-librados2_12.2.11-0ubuntu0.18.04.1_amd64.deb ...
Unpacking librados2 (12.2.11-0ubuntu0.18.04.1) ...
Selecting previously unselected package librbd1.
Preparing to unpack .../04-librbd1_12.2.11-0ubuntu0.18.04.1_amd64.deb ...
Unpacking librbd1 (12.2.11-0ubuntu0.18.04.1) ...
Selecting previously unselected package qemu-block-extra:amd64.
Preparing to unpack .../05-qemu-block-extra_1%3a2.11+dfsg-1ubuntu7.12_amd64.deb ...
Unpacking qemu-block-extra:amd64 (1:2.11+dfsg-1ubuntu7.12) ...
Selecting previously unselected package qemu-system-common.
Preparing to unpack .../06-qemu-system-common_1%3a2.11+dfsg-1ubuntu7.12_amd64.deb ...
Unpacking qemu-system-common (1:2.11+dfsg-1ubuntu7.12) ...
Selecting previously unselected package augeas-lenses.
Preparing to unpack .../07-augeas-lenses_1.10.1-2_all.deb ...
Unpacking augeas-lenses (1.10.1-2) ...
Selecting previously unselected package msr-tools.
Preparing to unpack .../08-msr-tools_1.3-2build1_amd64.deb ...
Unpacking msr-tools (1.3-2build1) ...
Selecting previously unselected package cpu-checker.
Preparing to unpack .../09-cpu-checker_0.7-0ubuntu7_amd64.deb ...
Unpacking cpu-checker (0.7-0ubuntu7) ...
Selecting previously unselected package libdevmapper-event1.02.1:amd64.
Preparing to unpack .../10-libdevmapper-event1.02.1_2%3a1.02.145-4.1ubuntu3_amd64.deb ...
Unpacking libdevmapper-event1.02.1:amd64 (2:1.02.145-4.1ubuntu3) ...
Selecting previously unselected package liblvm2cmd2.02:amd64.
Preparing to unpack .../11-liblvm2cmd2.02_2.02.176-4.1ubuntu3_amd64.deb ...
Unpacking liblvm2cmd2.02:amd64 (2.02.176-4.1ubuntu3) ...
Selecting previously unselected package dmeventd.
Preparing to unpack .../12-dmeventd_2%3a1.02.145-4.1ubuntu3_amd64.deb ...
Unpacking dmeventd (2:1.02.145-4.1ubuntu3) ...
Selecting previously unselected package libgovirt-common.
Preparing to unpack .../13-libgovirt-common_0.3.4-2_all.deb ...
Unpacking libgovirt-common (0.3.4-2) ...
Selecting previously unselected package libgovirt2:amd64.
Preparing to unpack .../14-libgovirt2_0.3.4-2_amd64.deb ...
Unpacking libgovirt2:amd64 (0.3.4-2) ...
Selecting previously unselected package libgvnc-1.0-0:amd64.
Preparing to unpack .../15-libgvnc-1.0-0_0.7.2-1_amd64.deb ...
Unpacking libgvnc-1.0-0:amd64 (0.7.2-1) ...
Selecting previously unselected package libgtk-vnc-2.0-0:amd64.
Preparing to unpack .../16-libgtk-vnc-2.0-0_0.7.2-1_amd64.deb ...
Unpacking libgtk-vnc-2.0-0:amd64 (0.7.2-1) ...
Selecting previously unselected package osinfo-db.
Preparing to unpack .../17-osinfo-db_0.20180929-1ubuntu0.1_all.deb ...
Unpacking osinfo-db (0.20180929-1ubuntu0.1) ...
Selecting previously unselected package libosinfo-1.0-0:amd64.
Preparing to unpack .../18-libosinfo-1.0-0_1.1.0-1_amd64.deb ...
Unpacking libosinfo-1.0-0:amd64 (1.1.0-1) ...
Selecting previously unselected package libcacard0:amd64.
Preparing to unpack .../19-libcacard0_1%3a2.5.0-3_amd64.deb ...
Unpacking libcacard0:amd64 (1:2.5.0-3) ...
Selecting previously unselected package libphodav-2.0-common.
Preparing to unpack .../20-libphodav-2.0-common_2.2-2_all.deb ...
Unpacking libphodav-2.0-common (2.2-2) ...
Selecting previously unselected package libphodav-2.0-0:amd64.
Preparing to unpack .../21-libphodav-2.0-0_2.2-2_amd64.deb ...
Unpacking libphodav-2.0-0:amd64 (2.2-2) ...
Selecting previously unselected package libusbredirparser1:amd64.
Preparing to unpack .../22-libusbredirparser1_0.7.1-1_amd64.deb ...
Unpacking libusbredirparser1:amd64 (0.7.1-1) ...
Selecting previously unselected package libusbredirhost1:amd64.
Preparing to unpack .../23-libusbredirhost1_0.7.1-1_amd64.deb ...
Unpacking libusbredirhost1:amd64 (0.7.1-1) ...
Selecting previously unselected package spice-client-glib-usb-acl-helper.
Preparing to unpack .../24-spice-client-glib-usb-acl-helper_0.34-1.1build1_amd64.deb ...
Unpacking spice-client-glib-usb-acl-helper (0.34-1.1build1) ...
Selecting previously unselected package libspice-client-glib-2.0-8:amd64.
Preparing to unpack .../25-libspice-client-glib-2.0-8_0.34-1.1build1_amd64.deb ...
Unpacking libspice-client-glib-2.0-8:amd64 (0.34-1.1build1) ...
Selecting previously unselected package libspice-client-gtk-3.0-5:amd64.
Preparing to unpack .../26-libspice-client-gtk-3.0-5_0.34-1.1build1_amd64.deb ...
Unpacking libspice-client-gtk-3.0-5:amd64 (0.34-1.1build1) ...
Selecting previously unselected package libvirt0:amd64.
Preparing to unpack .../27-libvirt0_4.0.0-1ubuntu8.8_amd64.deb ...
Unpacking libvirt0:amd64 (4.0.0-1ubuntu8.8) ...
Selecting previously unselected package libvirt-glib-1.0-0:amd64.
Preparing to unpack .../28-libvirt-glib-1.0-0_1.0.0-1_amd64.deb ...
Unpacking libvirt-glib-1.0-0:amd64 (1.0.0-1) ...
Selecting previously unselected package libosinfo-bin.
Preparing to unpack .../29-libosinfo-bin_1.1.0-1_amd64.deb ...
Unpacking libosinfo-bin (1.1.0-1) ...
Selecting previously unselected package libaugeas0:amd64.
Preparing to unpack .../30-libaugeas0_1.10.1-2_amd64.deb ...
Unpacking libaugeas0:amd64 (1.10.1-2) ...
Selecting previously unselected package libnetcf1:amd64.
Preparing to unpack .../31-libnetcf1_1%3a0.2.8-1ubuntu2_amd64.deb ...
Unpacking libnetcf1:amd64 (1:0.2.8-1ubuntu2) ...
Selecting previously unselected package libxenstore3.0:amd64.
Preparing to unpack .../32-libxenstore3.0_4.9.2-0ubuntu1_amd64.deb ...
Unpacking libxenstore3.0:amd64 (4.9.2-0ubuntu1) ...
Selecting previously unselected package libxen-4.9:amd64.
Preparing to unpack .../33-libxen-4.9_4.9.2-0ubuntu1_amd64.deb ...
Unpacking libxen-4.9:amd64 (4.9.2-0ubuntu1) ...
Selecting previously unselected package libvirt-daemon.
Preparing to unpack .../34-libvirt-daemon_4.0.0-1ubuntu8.8_amd64.deb ...
Unpacking libvirt-daemon (4.0.0-1ubuntu8.8) ...
Selecting previously unselected package libtracker-control-2.0-0:amd64.
Preparing to unpack .../35-libtracker-control-2.0-0_2.0.3-1ubuntu4_amd64.deb ...
Unpacking libtracker-control-2.0-0:amd64 (2.0.3-1ubuntu4) ...
Selecting previously unselected package tracker.
Preparing to unpack .../36-tracker_2.0.3-1ubuntu4_amd64.deb ...
Unpacking tracker (2.0.3-1ubuntu4) ...
Selecting previously unselected package gnome-boxes.
Preparing to unpack .../37-gnome-boxes_3.28.1-1_amd64.deb ...
Unpacking gnome-boxes (3.28.1-1) ...
Selecting previously unselected package ibverbs-providers:amd64.
Preparing to unpack .../38-ibverbs-providers_17.1-1ubuntu0.1_amd64.deb ...
Unpacking ibverbs-providers:amd64 (17.1-1ubuntu0.1) ...
Selecting previously unselected package ipxe-qemu.
Preparing to unpack .../39-ipxe-qemu_1.0.0+git-20180124.fbe8c52d-0ubuntu2.2_all.deb ...
Unpacking ipxe-qemu (1.0.0+git-20180124.fbe8c52d-0ubuntu2.2) ...
Selecting previously unselected package ipxe-qemu-256k-compat-efi-roms.
Preparing to unpack .../40-ipxe-qemu-256k-compat-efi-roms_1.0.0+git-20150424.a25a16d-0ubuntu2_all.deb ...
Unpacking ipxe-qemu-256k-compat-efi-roms (1.0.0+git-20150424.a25a16d-0ubuntu2) ...
Selecting previously unselected package libaio1:amd64.
Preparing to unpack .../41-libaio1_0.3.110-5_amd64.deb ...
Unpacking libaio1:amd64 (0.3.110-5) ...
Selecting previously unselected package libcue1.
Preparing to unpack .../42-libcue1_1.4.0-1_amd64.deb ...
Unpacking libcue1 (1.4.0-1) ...
Selecting previously unselected package libenca0:amd64.
Preparing to unpack .../43-libenca0_1.19-1_amd64.deb ...
Unpacking libenca0:amd64 (1.19-1) ...
Selecting previously unselected package libgif7:amd64.
Preparing to unpack .../44-libgif7_5.1.4-2_amd64.deb ...
Unpacking libgif7:amd64 (5.1.4-2) ...
Selecting previously unselected package libgsf-1-common.
Preparing to unpack .../45-libgsf-1-common_1.14.41-2_all.deb ...
Unpacking libgsf-1-common (1.14.41-2) ...
Selecting previously unselected package libgsf-1-114:amd64.
Preparing to unpack .../46-libgsf-1-114_1.14.41-2_amd64.deb ...
Unpacking libgsf-1-114:amd64 (1.14.41-2) ...
Selecting previously unselected package liblvm2app2.2:amd64.
Preparing to unpack .../47-liblvm2app2.2_2.02.176-4.1ubuntu3_amd64.deb ...
Unpacking liblvm2app2.2:amd64 (2.02.176-4.1ubuntu3) ...
Selecting previously unselected package libreadline5:amd64.
Preparing to unpack .../48-libreadline5_5.2+dfsg-3build1_amd64.deb ...
Unpacking libreadline5:amd64 (5.2+dfsg-3build1) ...
Selecting previously unselected package libspice-server1:amd64.
Preparing to unpack .../49-libspice-server1_0.14.0-1ubuntu2.4_amd64.deb ...
Unpacking libspice-server1:amd64 (0.14.0-1ubuntu2.4) ...
Selecting previously unselected package libtagc0:amd64.
Preparing to unpack .../50-libtagc0_1.11.1+dfsg.1-0.2build2_amd64.deb ...
Unpacking libtagc0:amd64 (1.11.1+dfsg.1-0.2build2) ...
Selecting previously unselected package libtracker-miner-2.0-0:amd64.
Preparing to unpack .../51-libtracker-miner-2.0-0_2.0.3-1ubuntu4_amd64.deb ...
Unpacking libtracker-miner-2.0-0:amd64 (2.0.3-1ubuntu4) ...
Selecting previously unselected package libvirt-daemon-driver-storage-rbd.
Preparing to unpack .../52-libvirt-daemon-driver-storage-rbd_4.0.0-1ubuntu8.8_amd64.deb ...
Unpacking libvirt-daemon-driver-storage-rbd (4.0.0-1ubuntu8.8) ...
Selecting previously unselected package libxml2-utils.
Preparing to unpack .../53-libxml2-utils_2.9.4+dfsg1-6.1ubuntu1.2_amd64.deb ...
Unpacking libxml2-utils (2.9.4+dfsg1-6.1ubuntu1.2) ...
Selecting previously unselected package lvm2.
Preparing to unpack .../54-lvm2_2.02.176-4.1ubuntu3_amd64.deb ...
Unpacking lvm2 (2.02.176-4.1ubuntu3) ...
Selecting previously unselected package libfdt1:amd64.
Preparing to unpack .../55-libfdt1_1.4.5-3_amd64.deb ...
Unpacking libfdt1:amd64 (1.4.5-3) ...
Selecting previously unselected package librdmacm1:amd64.
Preparing to unpack .../56-librdmacm1_17.1-1ubuntu0.1_amd64.deb ...
Unpacking librdmacm1:amd64 (17.1-1ubuntu0.1) ...
Selecting previously unselected package seabios.
Preparing to unpack .../57-seabios_1.10.2-1ubuntu1_all.deb ...
Unpacking seabios (1.10.2-1ubuntu1) ...
Selecting previously unselected package qemu-system-x86.
Preparing to unpack .../58-qemu-system-x86_1%3a2.11+dfsg-1ubuntu7.12_amd64.deb ...
Unpacking qemu-system-x86 (1:2.11+dfsg-1ubuntu7.12) ...
Selecting previously unselected package qemu-kvm.
Preparing to unpack .../59-qemu-kvm_1%3a2.11+dfsg-1ubuntu7.12_amd64.deb ...
Unpacking qemu-kvm (1:2.11+dfsg-1ubuntu7.12) ...
Selecting previously unselected package qemu-utils.
Preparing to unpack .../60-qemu-utils_1%3a2.11+dfsg-1ubuntu7.12_amd64.deb ...
Unpacking qemu-utils (1:2.11+dfsg-1ubuntu7.12) ...
Selecting previously unselected package sharutils.
Preparing to unpack .../61-sharutils_1%3a4.15.2-3_amd64.deb ...
Unpacking sharutils (1:4.15.2-3) ...
Selecting previously unselected package libiptcdata0.
Preparing to unpack .../62-libiptcdata0_1.0.4-6ubuntu1_amd64.deb ...
Unpacking libiptcdata0 (1.0.4-6ubuntu1) ...
Selecting previously unselected package tracker-extract.
Preparing to unpack .../63-tracker-extract_2.0.4-1_amd64.deb ...
Unpacking tracker-extract (2.0.4-1) ...
Selecting previously unselected package tracker-miner-fs.
Preparing to unpack .../64-tracker-miner-fs_2.0.4-1_amd64.deb ...
Unpacking tracker-miner-fs (2.0.4-1) ...
Setting up seabios (1.10.2-1ubuntu1) ...
Setting up ipxe-qemu-256k-compat-efi-roms (1.0.0+git-20150424.a25a16d-0ubuntu2) ...
Setting up libtagc0:amd64 (1.11.1+dfsg.1-0.2build2) ...
Setting up libspice-server1:amd64 (0.14.0-1ubuntu2.4) ...
Setting up grub-efi-amd64 (2.02-2ubuntu8.13) ...
/boot/vmlinuz-5.0.0-050000-generic is unsigned.
E: Your kernels are not signed with a key known to your firmware. This system will fail to boot in a Secure Boot environment.
dpkg: error processing package grub-efi-amd64 (--configure):
 installed grub-efi-amd64 package post-installation script subprocess returned error exit status 1
Processing triggers for mime-support (3.60ubuntu1) ...
Processing triggers for ureadahead (0.100.0-20) ...
Setting up libgvnc-1.0-0:amd64 (0.7.2-1) ...
Setting up libgtk-vnc-2.0-0:amd64 (0.7.2-1) ...
Processing triggers for desktop-file-utils (0.23-1ubuntu3.18.04.2) ...
Setting up libtracker-control-2.0-0:amd64 (2.0.3-1ubuntu4) ...
Processing triggers for install-info (6.5.0.dfsg.1-2) ...
Setting up libgovirt-common (0.3.4-2) ...
Setting up tracker (2.0.3-1ubuntu4) ...
Setting up libgsf-1-common (1.14.41-2) ...
Setting up libvirt0:amd64 (4.0.0-1ubuntu8.8) ...
Processing triggers for libglib2.0-0:amd64 (2.56.3-0ubuntu0.18.04.1) ...
Setting up sharutils (1:4.15.2-3) ...
Setting up libiscsi7:amd64 (1.17.0-1.1) ...
Setting up libusbredirparser1:amd64 (0.7.1-1) ...
Setting up libxml2-utils (2.9.4+dfsg1-6.1ubuntu1.2) ...
Setting up libxenstore3.0:amd64 (4.9.2-0ubuntu1) ...
Setting up libnl-route-3-200:amd64 (3.2.29-0ubuntu3) ...
Setting up libphodav-2.0-common (2.2-2) ...
Setting up libgif7:amd64 (5.1.4-2) ...
Setting up libgsf-1-114:amd64 (1.14.41-2) ...
Setting up msr-tools (1.3-2build1) ...
dpkg: dependency problems prevent configuration of grub-efi-amd64-signed:
 grub-efi-amd64-signed depends on grub-efi-amd64 | grub-pc; however:
  Package grub-efi-amd64 is not configured yet.
  Package grub-pc is not installed.

dpkg: error processing package grub-efi-amd64-signed (--configure):
 dependency problems - leaving unconfigured
Setting up libdevmapper-event1.02.1:amd64 (2:1.02.145-4.1ubuntu3) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up libcue1 (1.4.0-1) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Setting up libaio1:amd64 (0.3.110-5) ...
Setting up osinfo-db (0.20180929-1ubuntu0.1) ...
Setting up libvirt-glib-1.0-0:amd64 (1.0.0-1) ...
Setting up cpu-checker (0.7-0ubuntu7) ...
Setting up libphodav-2.0-0:amd64 (2.2-2) ...
Processing triggers for systemd (237-3ubuntu10.19) ...
Setting up augeas-lenses (1.10.1-2) ...
Setting up libcacard0:amd64 (1:2.5.0-3) ...
Setting up liblvm2app2.2:amd64 (2.02.176-4.1ubuntu3) ...
Processing triggers for man-db (2.8.3-2ubuntu0.1) ...
Setting up libxen-4.9:amd64 (4.9.2-0ubuntu1) ...
Processing triggers for gnome-menus (3.13.3-11ubuntu1.1) ...
Setting up libreadline5:amd64 (5.2+dfsg-3build1) ...
Setting up libgovirt2:amd64 (0.3.4-2) ...
Processing triggers for hicolor-icon-theme (0.17-2) ...
Setting up ipxe-qemu (1.0.0+git-20180124.fbe8c52d-0ubuntu2.2) ...
Setting up libiptcdata0 (1.0.4-6ubuntu1) ...
Setting up libenca0:amd64 (1.19-1) ...
Setting up spice-client-glib-usb-acl-helper (0.34-1.1build1) ...
Setting up libfdt1:amd64 (1.4.5-3) ...
Setting up libtracker-miner-2.0-0:amd64 (2.0.3-1ubuntu4) ...
Setting up libibverbs1:amd64 (17.1-1ubuntu0.1) ...
Setting up libosinfo-1.0-0:amd64 (1.1.0-1) ...
Setting up libusbredirhost1:amd64 (0.7.1-1) ...
Setting up libaugeas0:amd64 (1.10.1-2) ...
Setting up tracker-extract (2.0.4-1) ...
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Setting up librdmacm1:amd64 (17.1-1ubuntu0.1) ...
Setting up librados2 (12.2.11-0ubuntu0.18.04.1) ...
Setting up libosinfo-bin (1.1.0-1) ...
Setting up ibverbs-providers:amd64 (17.1-1ubuntu0.1) ...
Setting up tracker-miner-fs (2.0.4-1) ...
Setting up libnetcf1:amd64 (1:0.2.8-1ubuntu2) ...
Setting up libspice-client-glib-2.0-8:amd64 (0.34-1.1build1) ...
Setting up libspice-client-gtk-3.0-5:amd64 (0.34-1.1build1) ...
Setting up librbd1 (12.2.11-0ubuntu0.18.04.1) ...
Setting up qemu-block-extra:amd64 (1:2.11+dfsg-1ubuntu7.12) ...
Setting up qemu-utils (1:2.11+dfsg-1ubuntu7.12) ...
Setting up libvirt-daemon (4.0.0-1ubuntu8.8) ...
Setting up qemu-system-common (1:2.11+dfsg-1ubuntu7.12) ...
Created symlink /etc/systemd/system/multi-user.target.wants/qemu-kvm.service &#8594; /lib/systemd/system/qemu-kvm.service.
Setting up gnome-boxes (3.28.1-1) ...
Setting up libvirt-daemon-driver-storage-rbd (4.0.0-1ubuntu8.8) ...
Setting up qemu-system-x86 (1:2.11+dfsg-1ubuntu7.12) ...
Setting up qemu-kvm (1:2.11+dfsg-1ubuntu7.12) ...
Setting up liblvm2cmd2.02:amd64 (2.02.176-4.1ubuntu3) ...
Setting up dmeventd (2:1.02.145-4.1ubuntu3) ...
Created symlink /etc/systemd/system/sockets.target.wants/dm-event.socket &#8594; /lib/systemd/system/dm-event.socket.
dm-event.service is a disabled or a static unit, not starting it.
Setting up lvm2 (2.02.176-4.1ubuntu3) ...
update-initramfs: deferring update (trigger activated)
Created symlink /etc/systemd/system/sysinit.target.wants/blk-availability.service &#8594; /lib/systemd/system/blk-availability.service.
Created symlink /etc/systemd/system/sysinit.target.wants/lvm2-monitor.service &#8594; /lib/systemd/system/lvm2-monitor.service.
Created symlink /etc/systemd/system/sysinit.target.wants/lvm2-lvmetad.socket &#8594; /lib/systemd/system/lvm2-lvmetad.socket.
Created symlink /etc/systemd/system/sysinit.target.wants/lvm2-lvmpolld.socket &#8594; /lib/systemd/system/lvm2-lvmpolld.socket.
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Processing triggers for systemd (237-3ubuntu10.19) ...
Processing triggers for ureadahead (0.100.0-20) ...
Processing triggers for initramfs-tools (0.130ubuntu3.7) ...
update-initramfs: Generating /boot/initrd.img-5.0.0-050000-generic
Errors were encountered while processing:
 grub-efi-amd64
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by TheFu on 2019-04-13
I know what I would do, but others likely disagree. Don't know if it is viable for you or not.

I'd backup the data, settings, and list of installed packages (not versions, just package names).  Then I'd nuke this system from orbit. Only way to be sure.
And start over, but the next time, I'd patch weekly, not disable the core repos, and stick with the normal kernels provided by the distro.  I wouldn't install any software from .deb files directly.  Stick with the Canonical repos and only a few, trusted, reputable, PPAs.

In about 30 min, I'd have a fresh, new, working, system. This is an important skill to have, yes?

_**New is the enemy of stable.**_

5.0.0-050000-generic  is NOT an older kernel.  It is so new that no shipping ubuntu distro uses it. For 18.04, stick with this: [https://wiki.ubuntu.com/Kernel/Support#A18.04.x_Ubuntu_Kernel_Support](https://wiki.ubuntu.com/Kernel/Support#A18.04.x_Ubuntu_Kernel_Support) Looks like v4.15 is the supported kernel today.

This might not fit your needs. IDK. Also, you could be 1 command away from a fix. I just don't know exactly what that is.

---

### Post by apverma13 on 2019-04-13
Thank you for the suggestions.

I do patch regularly.
I sometime need to Install using .deb as I use use mobile data while traveling.

I was wondering if going from kernel 5.0 to 4.15 (as you mentioned) would help?

And if reinstalling the OS is the only option left I'd do it but which one do you suggest 18.04 or 16.04. I had lot less problems in 16.04?

---

### Post by TheFu on 2019-04-14
Only option?  I don't know.  If it takes 45 min to solve this and you know how to avoid it in the future, why not do it?

Manually installing a .deb file will often lock dependencies. "APT Hell" is real. You are in it.  Only you can guess how that happened. I have systems that have been carefully maintained since 2009, upgraded from LTS to LTS over the last decade and these are all fine.  OTOH, I have a laptop that has had the OS reinstalled about once a year as I moved laptops since 2010, retaining all the data, just starting fresh with a new OS install.  It started on an Asus EEE, moved to an Acer C720 Chromebook, then a Toshiba CC3550 Chromebook and now it is on an Asus F510 laptop.  Just did that last move about 2 months ago.  Took 45 minutes to have "my laptop" back. Loaded with all my data, my programs, my system settings, my GUI tweaks.
Did the same thing to a desktop box 2 weeks ago.  Core i7-920 (from 2009 legacy boot) moved the physical disk to an AMD Ryzen, then added an SSD, did a fresh OS install to switch to UEFI boot and restored my data, my programs, my system settings and my GUI tweaks.  It is 'my system' in less than an hour.

At this point, I've probably spent more time considering this issue than it would take to reinstall and restore YOU data, programs, system settings. I can't imagine how much time you've spent on this.

As for 18.04 vs 16.04 - that's a question only you can answer.  My new Ryzen box got 16.04, but I do some non-standard network things and netplan has too many problems still to be useful to me.  Also, I hate snaps and snapd.  I'm not interested in debugging code anymore.

---

### Post by DuckHook on 2019-04-15
> **TheFu said:**
> I know what I would do, but others likely disagree.
This "other" agrees with TheFu completely.

@OP

Unless you are a:

[LIST=1]
[*]Developer
[*]Tester
[*]Masochist
[/LIST]
Do not install unsupported kernels into your main box. The place to maniacally break your system is within a VM. Your production box must be kept pristine.

Incidentally, even when travelling, it is possible to box unusual needs inside a VM. It may take a bit more configuration to share certain resources, but it's way safer and you don't break anything critical.

---

### Post by apverma13 on 2019-04-22
Nuked it last week. Working just fine. Thanks for all your help guys. &#128074;&#127996;

---

### Post by mörgæs on 2019-04-22
Good, please mark the thread 'solved'.

---


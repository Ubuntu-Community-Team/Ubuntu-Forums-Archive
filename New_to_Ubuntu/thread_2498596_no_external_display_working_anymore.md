---
title: "no external display working anymore"
date: 2024-06-21
forum: New to Ubuntu
---

### Post by dfrusone on 2024-06-21
Dear support, after 1 year of working with ubuntu 22.04 i got a terrible problem. The external Display stopped working suddently. I Startet my second partition whit Windows, and it's working without problems. No Hardware issue.

i tried different fixes in the communities, but in all the other situations, the hdmi/usb c port is visible, but not in mine:

Please Help

xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1920 x 1080, current 1920 x 1080, maximum 1920 x 1080
default connected primary 1920x1080+0+0 0mm x 0mm
1920x1080 77.00* 

sudo get-edid | parse-edid 
Place your finger on the fingerprint reader
This is read-edid version 3.0.2. Prepare for some fun.
Attempting to use i2c interface
No EDID on bus 0
No EDID on bus 1
No EDID on bus 2
Looks like no busses have an EDID. Sorry!
Attempting to use the classical VBE interface

Performing real mode VBE call
Interrupt 0x10 ax=0x4f00 bx=0x0 cx=0x0
Function unsupported
Call failed

VBE version 0
VBE string at 0x0 "O\&#65533;."

VBE/DDC service about to be called
Report DDC capabilities

Performing real mode VBE call
Interrupt 0x10 ax=0x4f15 bx=0x0 cx=0x0
Function unsupported
Call failed

Reading next EDID block

VBE/DDC service about to be called
Read EDID

Performing real mode VBE call
Interrupt 0x10 ax=0x4f15 bx=0x1 cx=0x0
Function unsupported
Call failed

The EDID data should not be trusted as the VBE call failed
Error: output block unchanged
I'm sorry nothing was successful. Maybe try some other arguments
if you played with them, or send an email to Matthew Kern <pyrophobicman@gmail.com>.
Partial Read... Try again

inxi -G
Graphics:
Device-1: Intel WhiskeyLake-U GT2 [UHD Graphics 620] driver: N/A
Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo
Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: vesa
unloaded: fbdev,modesetting gpu: N/A resolution: 1920x1080~77Hz
OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2

lspci -k | grep VGA
00:02.0 VGA compatible controller: Intel Corporation WhiskeyLake-U GT2 [UHD Graphics 620] (rev 02)

glxinfo | grep "OpenGL version"
OpenGL version string: 4.5 (Compatibility Profile) Mesa 23.2.1-1ubuntu3.1~22.04.2  
 
 
 lsusb
Bus 004 Device 005: ID 0bda:0411 Realtek Semiconductor Corp. Hub
Bus 004 Device 004: ID 0bda:8153 Realtek Semiconductor Corp. RTL8153 Gigabit Ethernet Adapter
Bus 004 Device 002: ID 0bda:0411 Realtek Semiconductor Corp. Hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 0951:1666 Kingston Technology DataTraveler 100 G3/G4/SE9 G2/50
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 017: ID 0a5c:5843 Broadcom Corp. 58200
Bus 001 Device 005: ID 0bda:5673 Realtek Semiconductor Corp. Integrated_Webcam_HD
Bus 001 Device 012: ID 8087:0029 Intel Corp. AX200 Bluetooth
Bus 001 Device 006: ID 0bda:1100 Realtek Semiconductor Corp. HID Device
Bus 001 Device 011: ID 03f0:354a HP, Inc Slim Keyboard
Bus 001 Device 008: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 001 Device 004: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub
Bus 001 Device 002: ID 0bda:5411 Realtek Semiconductor Corp. RTS5411 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



journal -xb


~
~
~
lines 11980-12026/12026 (END)
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (II) event7 - Logitech USB Optical Mouse: device removed
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb1/1-1/1-1.2/1-1.2.1/1-1.2.1:1.0/0003:046D:C077.0010>
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 13)
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (**) Option "AccelerationScheme" "none"
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (**) Logitech USB Optical Mouse: (accel) selected scheme none/0
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (II) event7 - Logitech USB Optical Mouse: is tagged by udev as: Mouse
giu 21 10:05:21 Lat7400 /usr/libexec/gdm-x-session[3705]: (II) event7 - Logitech USB Optical Mouse: device is a pointer
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 31 with keysym 31 (keycode a).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 33 with keysym 33 (keycode c).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 34 with keysym 34 (keycode d).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 35 with keysym 35 (keycode e).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 36 with keysym 36 (keycode f).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 37 with keysym 37 (keycode 10).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 38 with keysym 38 (keycode 11).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 39 with keysym 39 (keycode 12).
giu 21 10:05:22 Lat7400 gnome-shell[3904]: Window manager warning: Overwriting existing binding of keysym 32 with keysym 32 (keycode b).
giu 21 10:05:22 Lat7400 ModemManager[1618]: <info> [base-manager] couldn't check support for device '/sys/devices/pci0000:00/0000:00:1d.0/0000:03:00.0/0000:04:02.0/0000:39:00.0/usb>
giu 21 10:05:22 Lat7400 boltd[1626]: probing: timeout, done: [2342847] (2000000)
~

---

### Post by him610 on 2024-06-22
@dfrusone
It appears you have no driver for your intel UHD graphics 620
```
Device-1: Intel WhiskeyLake-U GT2 [UHD Graphics 620] driver: N/A
```

The intel graphics driver is part of the base *buntu installation. This is what mine looks like...
```
$ inxi -Gx
Graphics:
  Device-1: Intel HD Graphics 610 vendor: ASRock driver: i915 v: kernel
    bus-ID: 00:02.0
 
```

---

### Post by dfrusone on 2024-06-23
Thanks a lot for your reply.

I already tried to install the driver with this procedure, but this is the result

$ sudo apt install -y gpg-agent wget
wget -qO - [https://repositories.intel.com/graphics/intel-graphics.key](https://repositories.intel.com/graphics/intel-graphics.key) |
  sudo apt-key add -
sudo apt-add-repository \
  'deb [arch=amd64] [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) focal main'
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
wget is already the newest version (1.21.2-2ubuntu1).
gpg-agent is already the newest version (2.2.27-3ubuntu2.1).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Warning: apt-key is deprecated. Manage keyring files in trusted.gpg.d instead (see apt-key(8)).
OK
Repository: 'deb [arch=amd64] [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) focal main'
Description:
Archive for codename: focal components: main
More info: [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu)
Adding repository.
Press [ENTER] to continue or Ctrl-c to cancel.
Adding deb entry to /etc/apt/sources.list.d/archive_uri-https_repositories_intel_com_graphics_ubuntu-jammy.list
Adding disabled deb-src entry to /etc/apt/sources.list.d/archive_uri-https_repositories_intel_com_graphics_ubuntu-jammy.list
Get:1 [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) focal InRelease [3.195 B]
Hit:2 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) focal InRelease                        
Hit:3 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                        
Hit:4 [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) jammy InRelease           
Hit:5 [https://deb.nodesource.com/node_21.x](https://deb.nodesource.com/node_21.x) nodistro InRelease                  
Hit:6 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:7 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease           
Hit:8 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                         
Get:9 [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04) ./ InRelease [1.604 B]
Get:11 [https://mega.nz/linux/repo/xUbuntu_22.04](https://mega.nz/linux/repo/xUbuntu_22.04) ./ InRelease [2.961 B]         
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                
Hit:13 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-security InRelease        
Hit:14 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-updates InRelease         
Hit:15 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-security InRelease      
Hit:16 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease              
Hit:17 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-updates InRelease       
Hit:10 [https://hub-dist.unity3d.com/artifactory/hub-debian-prod-local](https://hub-dist.unity3d.com/artifactory/hub-debian-prod-local) unstable InRelease
Hit:18 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease               
Ign:19 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) disco InRelease                         
Hit:20 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) disco Release                
Hit:21 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) groovy InRelease
Hit:22 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy InRelease
Get:23 [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) focal/main amd64 Packages [198 kB]
Hit:24 [https://ppa.launchpadcontent.net/mozillateam/thunderbird-next/ubuntu](https://ppa.launchpadcontent.net/mozillateam/thunderbird-next/ubuntu) jammy InRelease
Hit:25 [https://ppa.launchpadcontent.net/slgobinath/safeeyes/ubuntu](https://ppa.launchpadcontent.net/slgobinath/safeeyes/ubuntu) jammy InRelease
Hit:26 [https://ppa.launchpadcontent.net/uunicorn/open-fprintd/ubuntu](https://ppa.launchpadcontent.net/uunicorn/open-fprintd/ubuntu) jammy InRelease
Fetched 206 kB in 5s (39,1 kB/s)                
Reading package lists... Done
W: [https://repositories.intel.com/graphics/ubuntu/dists/focal/InRelease:](https://repositories.intel.com/graphics/ubuntu/dists/focal/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [https://hub.unity3d.com/linux/repos/deb/dists/unstable/InRelease:](https://hub.unity3d.com/linux/repos/deb/dists/unstable/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [http://linux.dropbox.com/ubuntu/dists/disco/Release.gpg:](http://linux.dropbox.com/ubuntu/dists/disco/Release.gpg:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
dfrusone@Lat7400:~$ sudo apt update
sudo apt install \
  intel-opencl-icd \
  intel-level-zero-gpu level-zero \
  intel-media-va-driver-non-free libmfx1
Hit:1 [http://dell.archive.canonical.com](http://dell.archive.canonical.com) focal InRelease
Hit:2 [https://linux.teamviewer.com/deb](https://linux.teamviewer.com/deb) stable InRelease                        
Hit:3 [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) focal InRelease           
Get:4 [https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04](https://download.opensuse.org/repositories/home:/npreining:/debian-ubuntu-onedrive/xUbuntu_22.04) ./ InRelease [1.604 B]
Hit:5 [https://dl.google.com/linux/chrome/deb](https://dl.google.com/linux/chrome/deb) stable InRelease                  
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy InRelease                         
Get:7 [https://mega.nz/linux/repo/xUbuntu_22.04](https://mega.nz/linux/repo/xUbuntu_22.04) ./ InRelease [2.961 B]          
Hit:8 [https://deb.nodesource.com/node_21.x](https://deb.nodesource.com/node_21.x) nodistro InRelease                  
Hit:9 [https://packages.microsoft.com/repos/ms-teams](https://packages.microsoft.com/repos/ms-teams) stable InRelease           
Hit:11 [https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu](https://ppa.launchpadcontent.net/gezakovacs/ppa/ubuntu) groovy InRelease 
Hit:12 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-updates InRelease                
Hit:13 [https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu](https://ppa.launchpadcontent.net/mozillateam/ppa/ubuntu) jammy InRelease 
Hit:14 [https://ppa.launchpadcontent.net/mozillateam/thunderbird-next/ubuntu](https://ppa.launchpadcontent.net/mozillateam/thunderbird-next/ubuntu) jammy InRelease
Hit:15 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-backports InRelease              
Hit:16 [https://ppa.launchpadcontent.net/slgobinath/safeeyes/ubuntu](https://ppa.launchpadcontent.net/slgobinath/safeeyes/ubuntu) jammy InRelease
Hit:17 [https://ppa.launchpadcontent.net/uunicorn/open-fprintd/ubuntu](https://ppa.launchpadcontent.net/uunicorn/open-fprintd/ubuntu) jammy InRelease
Hit:18 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-security InRelease        
Hit:19 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) jammy-security InRelease               
Hit:10 [https://hub-dist.unity3d.com/artifactory/hub-debian-prod-local](https://hub-dist.unity3d.com/artifactory/hub-debian-prod-local) unstable InRelease
Hit:20 [https://esm.ubuntu.com/apps/ubuntu](https://esm.ubuntu.com/apps/ubuntu) jammy-apps-updates InRelease         
Hit:21 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-security InRelease
Hit:22 [https://repositories.intel.com/graphics/ubuntu](https://repositories.intel.com/graphics/ubuntu) jammy InRelease
Hit:23 [https://esm.ubuntu.com/infra/ubuntu](https://esm.ubuntu.com/infra/ubuntu) jammy-infra-updates InRelease
Ign:24 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) disco InRelease
Hit:25 [http://linux.dropbox.com/ubuntu](http://linux.dropbox.com/ubuntu) disco Release
Fetched 4.565 B in 6s (747 B/s)                                                
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
5 packages can be upgraded. Run 'apt list --upgradable' to see them.
W: [https://repositories.intel.com/graphics/ubuntu/dists/focal/InRelease:](https://repositories.intel.com/graphics/ubuntu/dists/focal/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [https://hub.unity3d.com/linux/repos/deb/dists/unstable/InRelease:](https://hub.unity3d.com/linux/repos/deb/dists/unstable/InRelease:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
W: [http://linux.dropbox.com/ubuntu/dists/disco/Release.gpg:](http://linux.dropbox.com/ubuntu/dists/disco/Release.gpg:) Key is stored in legacy trusted.gpg keyring (/etc/apt/trusted.gpg), see the DEPRECATION section in apt-key(8) for details.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
intel-level-zero-gpu is already the newest version (1.3.26241.33-647~22.04).
intel-media-va-driver-non-free is already the newest version (23.2.1-647~22.04).
intel-opencl-icd is already the newest version (23.17.26241.33-647~22.04).
level-zero is already the newest version (1.11.0-647~22.04).
libmfx1 is already the newest version (23.2.1-647~22.04).
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
dfrusone@Lat7400:~$ inxi -G
Graphics:
  Device-1: Intel WhiskeyLake-U GT2 [UHD Graphics 620] driver: N/A
  Device-2: Realtek Integrated_Webcam_HD type: USB driver: uvcvideo
  Display: x11 server: X.Org v: 1.21.1.4 driver: X: loaded: vesa
    unloaded: fbdev,modesetting gpu: N/A resolution: 1920x1080~77Hz
  OpenGL: renderer: llvmpipe (LLVM 15.0.7 256 bits)
    v: 4.5 Mesa 23.2.1-1ubuntu3.1~22.04.2

---

### Post by dfrusone on 2024-06-26
Can't understand. When i make the Intel procedure to install the Intel driver, everytime it cames the notification, die driver are up to date and already the newest version. But why can't the driver be loaded? Why there ist Driver: N/A?

Ho can i force the use of the inteldriver? Why it worket for 1 year, and now it needs other driver?

Can somebody help Please? I'm working singe 1 Week without my second screen. and it's not nice. i don't want to reinstall my notebook because of a driver problem :(

Somebody has experience in loading/unloading driver or using the Kernel defaults?

Thanks a lot!

---

### Post by dfrusone on 2024-06-27
Dear All,

i solved the prolbem by removing the last kernel, and reinstall it with the audo apt upgrade command.

thanks to all

---

### Post by dfrusone on 2024-06-28
Now the External display works again, but i can't install the original Intel UHD 620 Driver with the procedure described. 

How can i swicht from the Kernel Driver Whiskeylake to the original intel driver? They should be already installed.

thanks a lot!

---


---
title: "Howto Verto Nvidia GeForce FX 5500 PCI"
date: 2005-12-29
forum: Outdated Tutorials &amp; Tips
---

### Post by greenwom on 2005-12-29
If any one knows a more correct way, please post it.

I pluged the card in, booted up 
X failed then the system goes to command line.
You need to know the cards BusID so run

```
 sudo X :1 -scanpci
```  

Look for this line ```
(2:11:0) unknown chip (DeviceId 0x0326) from nVidia Corporation

```

back up and then edit your /etc/X11/xorg.conf

change your card info to this
```
Section "Device"
	Identifier	"NVIDIA GeForce FX5500"
	Driver		"nvidia"
	BusID		"PCI:2:11:0"
#	Option		"UseFBDev"		"true"  ##don't know if you need this
EndSection
```
You will also have to change the device name towards the end of the xorg.conf file.  Look at the 'device' by the screen resolution options.
Also if you try 'startx' it'll show you what else is jacked (by line number)

Then do this
```
apt-get install nvidia-glx
apt-get install nvidia-settings
```

Then 
```
sudo nvidia-glx-config enable
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```
Then add this (it's a new file so it will be lank)
Insert the following lines into the new file
```

[Desktop Entry]
Name=NVIDIA Settings
Comment=NVIDIA Settings
Exec=nvidia-settings
Icon=
Terminal=false
Type=Application
Categories=Application;System;

```
Then reboot

Also look at [http://ubuntuguide.org/#installnvidiadriver](http://ubuntuguide.org/#installnvidiadriver)

---

### Post by apox64928 on 2008-01-22
ok this didn't work for me
this code:sudo nvidia-glx-config enable
came up with:
sudo: nvidia-glx-config: command not found

and this code:
 sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
did nothing at all.

---


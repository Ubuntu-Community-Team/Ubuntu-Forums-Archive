---
title: "compiz fusion will not enable."
date: 2008-05-31
forum: New to Ubuntu
---

### Post by PatrickMoore on 2008-05-31
so far ive reinstalled my nvidia drivers to no avail  reinstalled all the compiz applications with nothing

in termianl when i type compiz i get
```
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present.
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

 anyone else with this issue. i know ive been posting about this for the last day or so but im really frustrated with this.

---

### Post by sayakb on 2008-05-31
Try:
```
metacity --replace
compiz --replace &
```

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> Try:
```
metacity --replace
compiz --replace &
```

i got this

```
patrick@patrick-laptop:~$ metacity --replace
patrick@patrick-laptop:~$ compiz --replace &
Checking for Xgl: [1] 7669
patrick@patrick-laptop:~$ not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by sayakb on 2008-05-31
At a terminal:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by PatrickMoore on 2008-05-31
```
patrick@patrick-laptop:~$ sudo dpkg-reconfigure -phigh xserver-xorg
[sudo] password for patrick: 
xserver-xorg postinst warning: overwriting possibly-customised configuration
   file; backup in /etc/X11/xorg.conf.20080531152911
patrick@patrick-laptop:~$ 

```

i am not sure what to do now

---

### Post by Joeb454 on 2008-05-31
Does it still not work?

I get a similar error - it looks like Compiz cannot find a screen to use

---

### Post by dracayr on 2008-05-31
try again compiz --replace

---

### Post by sayakb on 2008-05-31
It just reset the X configuration file. That seems to be fine. Do you still have the compiz problem?

---

### Post by PatrickMoore on 2008-05-31
> **dracayr said:**
> try again compiz --replace


same thing

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> It just reset the X configuration file. That seems to be fine. Do you still have the compiz problem?

yeah same thing

---

### Post by sayakb on 2008-05-31
```
sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg
```

Issuing the first command will remove about 24MB or more of archives. Let it continue. Do not restart X before issuing the second command.

---

### Post by dracayr on 2008-05-31
are you the only user currently logged in? If another user is logged on using compiz, you won't be able to use it

dracayr

---

### Post by sayakb on 2008-05-31
> **dracayr said:**
> are you the only user currently logged in? If another user is logged on using compiz, you won't be able to use it

dracayr

Are you sure..? I have an alternate user always logged in. I don't use metacity on any of my accounts either ;)

---

### Post by dracayr on 2008-05-31
when I had a second user logged in simultaneously, I couldn't use compiz. I googled and found that it couldn't be used with multiple users, but maybe that has changed now..

Edit:[https://bugs.launchpad.net/xorg-server/+bug/137745](https://bugs.launchpad.net/xorg-server/+bug/137745)

dracayr

---

### Post by PatrickMoore on 2008-05-31
> **dracayr said:**
> when I had a second user logged in simultaneously, I couldn't use compiz. I googled and found that it couldn't be used with multiple users, but maybe that has changed now..

dracayr

i should be the only one logged in there are no other users registered

i typed in the purge command (i assume) and got

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

---

### Post by dracayr on 2008-05-31
> **PatrickMoore said:**
> 
i typed in the purge command (i assume) and got

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

so you were trying to reintall it? do you have synaptic,the installation manager or the update manager open? If so, close them, then you should be able to uninstall

dracayr

---

### Post by sayakb on 2008-05-31
> **dracayr said:**
> when I had a second user logged in simultaneously, I couldn't use compiz. I googled and found that it couldn't be used with multiple users, but maybe that has changed now..

Edit:[https://bugs.launchpad.net/xorg-server/+bug/137745](https://bugs.launchpad.net/xorg-server/+bug/137745)

dracayr

You're right.. My God, I didn't notice this :o

> **PatrickMoore said:**
> i should be the only one logged in there are no other users registered

i typed in the purge command (i assume) and got

```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

```

Do you have synaptic or update manager running? If yes, then close all other package managers.

EDIT:  Lolz.. same reply.. happened twice today!!

---

### Post by sayakb on 2008-05-31
Hardy is full of bugs.. unfortunately. I'm thinking of switching back to Gutsy.. My USB doesn't work upon wake from suspend, I have about 10-12 freezes a day, and now this amazing new bug..

---

### Post by dracayr on 2008-05-31
10-12 freezes O_O

the only problem I have with hardy is that the system crashes when I open totem. But I have vlc for that :)

edit:but if you mean that bug with the multiple users and compiz, that isn't only hardy..

dracayr

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> You're right.. My God, I didn't notice this :o



Do you have synaptic or update manager running? If yes, then close all other package managers.

EDIT:  Lolz.. same reply.. happened twice today!!

it looks like everything is installing ok. it removed twice the amount of what its currently installing.

---

### Post by sayakb on 2008-05-31
> **dracayr said:**
> the only problem I have with hardy is that the system crashes when I open totem. But I have vlc for that :)

Exactly.. totem, realPlayer 10, or today morning it was even pidgin (it froze when I clicked on the notification area icon)
This is starting to irritate me :(

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> ```
sudo apt-get purge xserver-xorg
sudo apt-get install xserver-xorg
```

Issuing the first command will remove about 24MB or more of archives. Let it continue. Do not restart X before issuing the second command.

```
 sudo apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i810 xserver-xorg-video-intel
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
Suggested packages:
  gsynaptics ksynaptics qsynaptics wacom-tools
The following NEW packages will be installed:
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7338kB/7685kB of archives.
After this operation, 23.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9 [4423kB]
Get:2 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-evdev 1:1.2.0-1ubuntu2 [38.5kB]
Get:3 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-kbd 1:1.2.2-3ubuntu1 [25.8kB]
Get:4 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-mouse 1:1.2.3-2 [48.1kB]
Get:5 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-synaptics 0.14.7~git20070706-1ubuntu4 [67.4kB]
Get:6 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-vmmouse 1:12.4.3-1ubuntu1 [15.6kB]
Get:7 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-wacom 1:0.7.9.8-0ubuntu3 [54.9kB]
Get:8 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-all 1:7.3+10ubuntu10 [1034B]
Get:9 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-apm 1:1.1.1-10 [71.3kB]
Get:10 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-ark 1:0.6.0-9 [14.5kB]
Get:11 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-ati 1:6.8.0-1 [482kB]
Get:12 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-chips 1:1.1.1-9 [82.3kB]
Get:13 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-cirrus 1:1.1.0-8 [46.8kB]
Get:14 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-cyrix 1:1.1.0-8 [23.7kB]
Get:15 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-dummy 1:0.2.0-7 [11.6kB]
Get:16 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-fbdev 1:0.3.1-4 [15.8kB]
Get:17 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-glint 1:1.1.1-8 [99.1kB]
Get:18 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-i128 1:1.2.1-4 [34.7kB]
Get:19 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-i810 2:1.7.4-0ubuntu7 [146kB]
Get:20 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-mga 1:1.4.8.dfsg.1-1 [113kB]
Get:21 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-neomagic 1:1.1.1-8 [44.6kB]
Get:22 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-nv 1:2.1.8-1ubuntu1 [108kB]
Get:23 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-openchrome 1:0.2.901-0ubuntu4 [118kB]
Get:24 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-rendition 1:4.1.3.dfsg.1-4 [32.7kB]
Get:25 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-s3 1:0.5.0-4 [35.9kB]
Get:26 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-s3virge 1:1.9.1-7 [43.4kB]
Get:27 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-savage 1:2.1.3-5 [90.0kB]
Get:28 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-siliconmotion 1:1.5.1-3 [57.4kB]
Get:29 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-sis 1:0.9.3-6 [296kB]
Get:30 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-sisusb 1:0.8.1-9 [44.8kB]
Get:31 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tdfx 1:1.3.0-6 [45.4kB]
Get:32 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tga 1:1.1.0-9ubuntu1 [30.8kB]
Get:33 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-trident 1:1.2.4-1 [81.3kB]
Get:34 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tseng 1:1.1.1-4 [34.4kB]
Get:35 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-v4l 1:0.1.1-6ubuntu1 [22.8kB]
Get:36 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vesa 1:1.3.0-4ubuntu4 [23.5kB]
Get:37 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vga 1:4.1.0-8 [18.2kB]
Get:38 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-via 1:0.2.2-5 [160kB]
Get:39 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vmware 1:10.15.2-1ubuntu2 [31.9kB]
Get:40 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-voodoo 1:1.1.1-5 [22.8kB]
Get:41 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-all 1:7.3+10ubuntu10 [1178B]
Get:42 http://us.archive.ubuntu.com hardy/main xserver-xorg 1:7.3+10ubuntu10 [180kB]
Fetched 7338kB in 1min56s (62.9kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package xserver-xorg-core.
(Reading database ... 159548 files and directories currently installed.)
Unpacking xserver-xorg-core (from .../xserver-xorg-core_2%3a1.4.1~git20080131-1ubuntu9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-evdev.
Unpacking xserver-xorg-input-evdev (from .../xserver-xorg-input-evdev_1%3a1.2.0-1ubuntu2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-kbd.
Unpacking xserver-xorg-input-kbd (from .../xserver-xorg-input-kbd_1%3a1.2.2-3ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-mouse.
Unpacking xserver-xorg-input-mouse (from .../xserver-xorg-input-mouse_1%3a1.2.3-2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-synaptics.
Unpacking xserver-xorg-input-synaptics (from .../xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-vmmouse.
Unpacking xserver-xorg-input-vmmouse (from .../xserver-xorg-input-vmmouse_1%3a12.4.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-wacom.
Unpacking xserver-xorg-input-wacom (from .../xserver-xorg-input-wacom_1%3a0.7.9.8-0ubuntu3_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-all.
Unpacking xserver-xorg-input-all (from .../xserver-xorg-input-all_1%3a7.3+10ubuntu10_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-apm.
Unpacking xserver-xorg-video-apm (from .../xserver-xorg-video-apm_1%3a1.1.1-10_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-ark.
Unpacking xserver-xorg-video-ark (from .../xserver-xorg-video-ark_1%3a0.6.0-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.8.0-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-chips.
Unpacking xserver-xorg-video-chips (from .../xserver-xorg-video-chips_1%3a1.1.1-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-cirrus.
Unpacking xserver-xorg-video-cirrus (from .../xserver-xorg-video-cirrus_1%3a1.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-cyrix.
Unpacking xserver-xorg-video-cyrix (from .../xserver-xorg-video-cyrix_1%3a1.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-dummy.
Unpacking xserver-xorg-video-dummy (from .../xserver-xorg-video-dummy_1%3a0.2.0-7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-fbdev.
Unpacking xserver-xorg-video-fbdev (from .../xserver-xorg-video-fbdev_1%3a0.3.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-glint.
Unpacking xserver-xorg-video-glint (from .../xserver-xorg-video-glint_1%3a1.1.1-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-i128.
Unpacking xserver-xorg-video-i128 (from .../xserver-xorg-video-i128_1%3a1.2.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-i810.
Unpacking xserver-xorg-video-i810 (from .../xserver-xorg-video-i810_2%3a1.7.4-0ubuntu7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-intel.
Unpacking xserver-xorg-video-intel (from .../xserver-xorg-video-intel_2%3a2.2.1-1ubuntu13_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-mga.
Unpacking xserver-xorg-video-mga (from .../xserver-xorg-video-mga_1%3a1.4.8.dfsg.1-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-neomagic.
Unpacking xserver-xorg-video-neomagic (from .../xserver-xorg-video-neomagic_1%3a1.1.1-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-nv.
Unpacking xserver-xorg-video-nv (from .../xserver-xorg-video-nv_1%3a2.1.8-1ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-openchrome.
Unpacking xserver-xorg-video-openchrome (from .../xserver-xorg-video-openchrome_1%3a0.2.901-0ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-rendition.
Unpacking xserver-xorg-video-rendition (from .../xserver-xorg-video-rendition_1%3a4.1.3.dfsg.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-s3.
Unpacking xserver-xorg-video-s3 (from .../xserver-xorg-video-s3_1%3a0.5.0-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-s3virge.
Unpacking xserver-xorg-video-s3virge (from .../xserver-xorg-video-s3virge_1%3a1.9.1-7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-savage.
Unpacking xserver-xorg-video-savage (from .../xserver-xorg-video-savage_1%3a2.1.3-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-siliconmotion.
Unpacking xserver-xorg-video-siliconmotion (from .../xserver-xorg-video-siliconmotion_1%3a1.5.1-3_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-sis.
Unpacking xserver-xorg-video-sis (from .../xserver-xorg-video-sis_1%3a0.9.3-6_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-sisusb.
Unpacking xserver-xorg-video-sisusb (from .../xserver-xorg-video-sisusb_1%3a0.8.1-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tdfx.
Unpacking xserver-xorg-video-tdfx (from .../xserver-xorg-video-tdfx_1%3a1.3.0-6_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tga.
Unpacking xserver-xorg-video-tga (from .../xserver-xorg-video-tga_1%3a1.1.0-9ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-trident.
Unpacking xserver-xorg-video-trident (from .../xserver-xorg-video-trident_1%3a1.2.4-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tseng.
Unpacking xserver-xorg-video-tseng (from .../xserver-xorg-video-tseng_1%3a1.1.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-v4l.
Unpacking xserver-xorg-video-v4l (from .../xserver-xorg-video-v4l_1%3a0.1.1-6ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vesa.
Unpacking xserver-xorg-video-vesa (from .../xserver-xorg-video-vesa_1%3a1.3.0-4ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vga.
Unpacking xserver-xorg-video-vga (from .../xserver-xorg-video-vga_1%3a4.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-via.
Unpacking xserver-xorg-video-via (from .../xserver-xorg-video-via_1%3a0.2.2-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vmware.
Unpacking xserver-xorg-video-vmware (from .../xserver-xorg-video-vmware_1%3a10.15.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-voodoo.
Unpacking xserver-xorg-video-voodoo (from .../xserver-xorg-video-voodoo_1%3a1.1.1-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-all.
Unpacking xserver-xorg-video-all (from .../xserver-xorg-video-all_1%3a7.3+10ubuntu10_amd64.deb) ...
Selecting previously deselected package xserver-xorg.
Unpacking xserver-xorg (from .../xserver-xorg_1%3a7.3+10ubuntu10_all.deb) ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xserver-xorg-core (2:1.4.1~git20080131-1ubuntu9) ...
Setting up xserver-xorg-input-evdev (1:1.2.0-1ubuntu2) ...
Setting up xserver-xorg-input-kbd (1:1.2.2-3ubuntu1) ...
Setting up xserver-xorg-input-mouse (1:1.2.3-2) ...
Setting up xserver-xorg-input-synaptics (0.14.7~git20070706-1ubuntu4) ...
Setting up xserver-xorg-input-vmmouse (1:12.4.3-1ubuntu1) ...
Setting up xserver-xorg-input-wacom (1:0.7.9.8-0ubuntu3) ...
 * Doing Wacom setup...                                                  [ OK ] 

Setting up xserver-xorg-input-all (1:7.3+10ubuntu10) ...
Setting up xserver-xorg-video-apm (1:1.1.1-10) ...
Setting up xserver-xorg-video-ark (1:0.6.0-9) ...
Setting up xserver-xorg-video-ati (1:6.8.0-1) ...
Setting up xserver-xorg-video-chips (1:1.1.1-9) ...
Setting up xserver-xorg-video-cirrus (1:1.1.0-8) ...
Setting up xserver-xorg-video-cyrix (1:1.1.0-8) ...
Setting up xserver-xorg-video-dummy (1:0.2.0-7) ...
Setting up xserver-xorg-video-fbdev (1:0.3.1-4) ...
Setting up xserver-xorg-video-glint (1:1.1.1-8) ...
Setting up xserver-xorg-video-i128 (1:1.2.1-4) ...
Setting up xserver-xorg-video-i810 (2:1.7.4-0ubuntu7) ...
Setting up xserver-xorg-video-intel (2:2.2.1-1ubuntu13) ...

Setting up xserver-xorg-video-mga (1:1.4.8.dfsg.1-1) ...
Setting up xserver-xorg-video-neomagic (1:1.1.1-8) ...
Setting up xserver-xorg-video-nv (1:2.1.8-1ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.901-0ubuntu4) ...
Setting up xserver-xorg-video-rendition (1:4.1.3.dfsg.1-4) ...
Setting up xserver-xorg-video-s3 (1:0.5.0-4) ...
Setting up xserver-xorg-video-s3virge (1:1.9.1-7) ...
Setting up xserver-xorg-video-savage (1:2.1.3-5) ...
Setting up xserver-xorg-video-siliconmotion (1:1.5.1-3) ...
Setting up xserver-xorg-video-sis (1:0.9.3-6) ...
Setting up xserver-xorg-video-sisusb (1:0.8.1-9) ...
Setting up xserver-xorg-video-tdfx (1:1.3.0-6) ...
Setting up xserver-xorg-video-tga (1:1.1.0-9ubuntu1) ...
Setting up xserver-xorg-video-trident (1:1.2.4-1) ...
Setting up xserver-xorg-video-tseng (1:1.1.1-4) ...
Setting up xserver-xorg-video-v4l (1:0.1.1-6ubuntu1) ...
Setting up xserver-xorg-video-vesa (1:1.3.0-4ubuntu4) ...
Setting up xserver-xorg-video-vga (1:4.1.0-8) ...
Setting up xserver-xorg-video-via (1:0.2.2-5) ...

Setting up xserver-xorg-video-vmware (1:10.15.2-1ubuntu2) ...
Setting up xserver-xorg-video-voodoo (1:1.1.1-5) ...
Setting up xserver-xorg-video-all (1:7.3+10ubuntu10) ...
Setting up xserver-xorg (1:7.3+10ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

does this look ok?

---

### Post by sayakb on 2008-05-31
> **PatrickMoore said:**
> it looks like everything is installing ok. it removed twice the amount of what its currently installing.

By default, xserver-xorg installs numerous VGA drivers. Just to be sure, also do:
```
sudo apt-get install xserver-xorg*
```
That * sign would install all X server packages.

---

### Post by sayakb on 2008-05-31
> **PatrickMoore said:**
> ```
 sudo apt-get install xserver-xorg
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-evdev
  xserver-xorg-input-kbd xserver-xorg-input-mouse xserver-xorg-input-synaptics
  xserver-xorg-input-vmmouse xserver-xorg-input-wacom xserver-xorg-video-all
  xserver-xorg-video-apm xserver-xorg-video-ark xserver-xorg-video-ati
  xserver-xorg-video-chips xserver-xorg-video-cirrus xserver-xorg-video-cyrix
  xserver-xorg-video-dummy xserver-xorg-video-fbdev xserver-xorg-video-glint
  xserver-xorg-video-i128 xserver-xorg-video-i810 xserver-xorg-video-intel
  xserver-xorg-video-mga xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
Suggested packages:
  gsynaptics ksynaptics qsynaptics wacom-tools
The following NEW packages will be installed:
  xserver-xorg xserver-xorg-core xserver-xorg-input-all
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-input-vmmouse
  xserver-xorg-input-wacom xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i810 xserver-xorg-video-intel xserver-xorg-video-mga
  xserver-xorg-video-neomagic xserver-xorg-video-nv
  xserver-xorg-video-openchrome xserver-xorg-video-rendition
  xserver-xorg-video-s3 xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo
0 upgraded, 43 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 7338kB/7685kB of archives.
After this operation, 23.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com hardy/main xserver-xorg-core 2:1.4.1~git20080131-1ubuntu9 [4423kB]
Get:2 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-evdev 1:1.2.0-1ubuntu2 [38.5kB]
Get:3 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-kbd 1:1.2.2-3ubuntu1 [25.8kB]
Get:4 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-mouse 1:1.2.3-2 [48.1kB]
Get:5 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-synaptics 0.14.7~git20070706-1ubuntu4 [67.4kB]
Get:6 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-vmmouse 1:12.4.3-1ubuntu1 [15.6kB]
Get:7 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-wacom 1:0.7.9.8-0ubuntu3 [54.9kB]
Get:8 http://us.archive.ubuntu.com hardy/main xserver-xorg-input-all 1:7.3+10ubuntu10 [1034B]
Get:9 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-apm 1:1.1.1-10 [71.3kB]
Get:10 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-ark 1:0.6.0-9 [14.5kB]
Get:11 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-ati 1:6.8.0-1 [482kB]
Get:12 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-chips 1:1.1.1-9 [82.3kB]
Get:13 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-cirrus 1:1.1.0-8 [46.8kB]
Get:14 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-cyrix 1:1.1.0-8 [23.7kB]
Get:15 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-dummy 1:0.2.0-7 [11.6kB]
Get:16 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-fbdev 1:0.3.1-4 [15.8kB]
Get:17 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-glint 1:1.1.1-8 [99.1kB]
Get:18 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-i128 1:1.2.1-4 [34.7kB]
Get:19 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-i810 2:1.7.4-0ubuntu7 [146kB]
Get:20 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-mga 1:1.4.8.dfsg.1-1 [113kB]
Get:21 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-neomagic 1:1.1.1-8 [44.6kB]
Get:22 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-nv 1:2.1.8-1ubuntu1 [108kB]
Get:23 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-openchrome 1:0.2.901-0ubuntu4 [118kB]
Get:24 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-rendition 1:4.1.3.dfsg.1-4 [32.7kB]
Get:25 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-s3 1:0.5.0-4 [35.9kB]
Get:26 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-s3virge 1:1.9.1-7 [43.4kB]
Get:27 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-savage 1:2.1.3-5 [90.0kB]
Get:28 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-siliconmotion 1:1.5.1-3 [57.4kB]
Get:29 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-sis 1:0.9.3-6 [296kB]
Get:30 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-sisusb 1:0.8.1-9 [44.8kB]
Get:31 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tdfx 1:1.3.0-6 [45.4kB]
Get:32 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tga 1:1.1.0-9ubuntu1 [30.8kB]
Get:33 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-trident 1:1.2.4-1 [81.3kB]
Get:34 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-tseng 1:1.1.1-4 [34.4kB]
Get:35 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-v4l 1:0.1.1-6ubuntu1 [22.8kB]
Get:36 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vesa 1:1.3.0-4ubuntu4 [23.5kB]
Get:37 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vga 1:4.1.0-8 [18.2kB]
Get:38 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-via 1:0.2.2-5 [160kB]
Get:39 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-vmware 1:10.15.2-1ubuntu2 [31.9kB]
Get:40 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-voodoo 1:1.1.1-5 [22.8kB]
Get:41 http://us.archive.ubuntu.com hardy/main xserver-xorg-video-all 1:7.3+10ubuntu10 [1178B]
Get:42 http://us.archive.ubuntu.com hardy/main xserver-xorg 1:7.3+10ubuntu10 [180kB]
Fetched 7338kB in 1min56s (62.9kB/s)                                           
Extracting templates from packages: 100%
Preconfiguring packages ...
Selecting previously deselected package xserver-xorg-core.
(Reading database ... 159548 files and directories currently installed.)
Unpacking xserver-xorg-core (from .../xserver-xorg-core_2%3a1.4.1~git20080131-1ubuntu9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-evdev.
Unpacking xserver-xorg-input-evdev (from .../xserver-xorg-input-evdev_1%3a1.2.0-1ubuntu2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-kbd.
Unpacking xserver-xorg-input-kbd (from .../xserver-xorg-input-kbd_1%3a1.2.2-3ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-mouse.
Unpacking xserver-xorg-input-mouse (from .../xserver-xorg-input-mouse_1%3a1.2.3-2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-synaptics.
Unpacking xserver-xorg-input-synaptics (from .../xserver-xorg-input-synaptics_0.14.7~git20070706-1ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-vmmouse.
Unpacking xserver-xorg-input-vmmouse (from .../xserver-xorg-input-vmmouse_1%3a12.4.3-1ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-wacom.
Unpacking xserver-xorg-input-wacom (from .../xserver-xorg-input-wacom_1%3a0.7.9.8-0ubuntu3_amd64.deb) ...
Selecting previously deselected package xserver-xorg-input-all.
Unpacking xserver-xorg-input-all (from .../xserver-xorg-input-all_1%3a7.3+10ubuntu10_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-apm.
Unpacking xserver-xorg-video-apm (from .../xserver-xorg-video-apm_1%3a1.1.1-10_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-ark.
Unpacking xserver-xorg-video-ark (from .../xserver-xorg-video-ark_1%3a0.6.0-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-ati.
Unpacking xserver-xorg-video-ati (from .../xserver-xorg-video-ati_1%3a6.8.0-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-chips.
Unpacking xserver-xorg-video-chips (from .../xserver-xorg-video-chips_1%3a1.1.1-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-cirrus.
Unpacking xserver-xorg-video-cirrus (from .../xserver-xorg-video-cirrus_1%3a1.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-cyrix.
Unpacking xserver-xorg-video-cyrix (from .../xserver-xorg-video-cyrix_1%3a1.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-dummy.
Unpacking xserver-xorg-video-dummy (from .../xserver-xorg-video-dummy_1%3a0.2.0-7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-fbdev.
Unpacking xserver-xorg-video-fbdev (from .../xserver-xorg-video-fbdev_1%3a0.3.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-glint.
Unpacking xserver-xorg-video-glint (from .../xserver-xorg-video-glint_1%3a1.1.1-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-i128.
Unpacking xserver-xorg-video-i128 (from .../xserver-xorg-video-i128_1%3a1.2.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-i810.
Unpacking xserver-xorg-video-i810 (from .../xserver-xorg-video-i810_2%3a1.7.4-0ubuntu7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-intel.
Unpacking xserver-xorg-video-intel (from .../xserver-xorg-video-intel_2%3a2.2.1-1ubuntu13_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-mga.
Unpacking xserver-xorg-video-mga (from .../xserver-xorg-video-mga_1%3a1.4.8.dfsg.1-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-neomagic.
Unpacking xserver-xorg-video-neomagic (from .../xserver-xorg-video-neomagic_1%3a1.1.1-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-nv.
Unpacking xserver-xorg-video-nv (from .../xserver-xorg-video-nv_1%3a2.1.8-1ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-openchrome.
Unpacking xserver-xorg-video-openchrome (from .../xserver-xorg-video-openchrome_1%3a0.2.901-0ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-rendition.
Unpacking xserver-xorg-video-rendition (from .../xserver-xorg-video-rendition_1%3a4.1.3.dfsg.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-s3.
Unpacking xserver-xorg-video-s3 (from .../xserver-xorg-video-s3_1%3a0.5.0-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-s3virge.
Unpacking xserver-xorg-video-s3virge (from .../xserver-xorg-video-s3virge_1%3a1.9.1-7_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-savage.
Unpacking xserver-xorg-video-savage (from .../xserver-xorg-video-savage_1%3a2.1.3-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-siliconmotion.
Unpacking xserver-xorg-video-siliconmotion (from .../xserver-xorg-video-siliconmotion_1%3a1.5.1-3_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-sis.
Unpacking xserver-xorg-video-sis (from .../xserver-xorg-video-sis_1%3a0.9.3-6_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-sisusb.
Unpacking xserver-xorg-video-sisusb (from .../xserver-xorg-video-sisusb_1%3a0.8.1-9_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tdfx.
Unpacking xserver-xorg-video-tdfx (from .../xserver-xorg-video-tdfx_1%3a1.3.0-6_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tga.
Unpacking xserver-xorg-video-tga (from .../xserver-xorg-video-tga_1%3a1.1.0-9ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-trident.
Unpacking xserver-xorg-video-trident (from .../xserver-xorg-video-trident_1%3a1.2.4-1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-tseng.
Unpacking xserver-xorg-video-tseng (from .../xserver-xorg-video-tseng_1%3a1.1.1-4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-v4l.
Unpacking xserver-xorg-video-v4l (from .../xserver-xorg-video-v4l_1%3a0.1.1-6ubuntu1_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vesa.
Unpacking xserver-xorg-video-vesa (from .../xserver-xorg-video-vesa_1%3a1.3.0-4ubuntu4_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vga.
Unpacking xserver-xorg-video-vga (from .../xserver-xorg-video-vga_1%3a4.1.0-8_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-via.
Unpacking xserver-xorg-video-via (from .../xserver-xorg-video-via_1%3a0.2.2-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-vmware.
Unpacking xserver-xorg-video-vmware (from .../xserver-xorg-video-vmware_1%3a10.15.2-1ubuntu2_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-voodoo.
Unpacking xserver-xorg-video-voodoo (from .../xserver-xorg-video-voodoo_1%3a1.1.1-5_amd64.deb) ...
Selecting previously deselected package xserver-xorg-video-all.
Unpacking xserver-xorg-video-all (from .../xserver-xorg-video-all_1%3a7.3+10ubuntu10_amd64.deb) ...
Selecting previously deselected package xserver-xorg.
Unpacking xserver-xorg (from .../xserver-xorg_1%3a7.3+10ubuntu10_all.deb) ...
Setting up msttcorefonts (2.4) ...

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
Error parsing proxy URL http://:8080/: Invalid host name.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error processing msttcorefonts (--configure):
 subprocess post-installation script returned error exit status 1
Setting up xserver-xorg-core (2:1.4.1~git20080131-1ubuntu9) ...
Setting up xserver-xorg-input-evdev (1:1.2.0-1ubuntu2) ...
Setting up xserver-xorg-input-kbd (1:1.2.2-3ubuntu1) ...
Setting up xserver-xorg-input-mouse (1:1.2.3-2) ...
Setting up xserver-xorg-input-synaptics (0.14.7~git20070706-1ubuntu4) ...
Setting up xserver-xorg-input-vmmouse (1:12.4.3-1ubuntu1) ...
Setting up xserver-xorg-input-wacom (1:0.7.9.8-0ubuntu3) ...
 * Doing Wacom setup...                                                  [ OK ] 

Setting up xserver-xorg-input-all (1:7.3+10ubuntu10) ...
Setting up xserver-xorg-video-apm (1:1.1.1-10) ...
Setting up xserver-xorg-video-ark (1:0.6.0-9) ...
Setting up xserver-xorg-video-ati (1:6.8.0-1) ...
Setting up xserver-xorg-video-chips (1:1.1.1-9) ...
Setting up xserver-xorg-video-cirrus (1:1.1.0-8) ...
Setting up xserver-xorg-video-cyrix (1:1.1.0-8) ...
Setting up xserver-xorg-video-dummy (1:0.2.0-7) ...
Setting up xserver-xorg-video-fbdev (1:0.3.1-4) ...
Setting up xserver-xorg-video-glint (1:1.1.1-8) ...
Setting up xserver-xorg-video-i128 (1:1.2.1-4) ...
Setting up xserver-xorg-video-i810 (2:1.7.4-0ubuntu7) ...
Setting up xserver-xorg-video-intel (2:2.2.1-1ubuntu13) ...

Setting up xserver-xorg-video-mga (1:1.4.8.dfsg.1-1) ...
Setting up xserver-xorg-video-neomagic (1:1.1.1-8) ...
Setting up xserver-xorg-video-nv (1:2.1.8-1ubuntu1) ...
Setting up xserver-xorg-video-openchrome (1:0.2.901-0ubuntu4) ...
Setting up xserver-xorg-video-rendition (1:4.1.3.dfsg.1-4) ...
Setting up xserver-xorg-video-s3 (1:0.5.0-4) ...
Setting up xserver-xorg-video-s3virge (1:1.9.1-7) ...
Setting up xserver-xorg-video-savage (1:2.1.3-5) ...
Setting up xserver-xorg-video-siliconmotion (1:1.5.1-3) ...
Setting up xserver-xorg-video-sis (1:0.9.3-6) ...
Setting up xserver-xorg-video-sisusb (1:0.8.1-9) ...
Setting up xserver-xorg-video-tdfx (1:1.3.0-6) ...
Setting up xserver-xorg-video-tga (1:1.1.0-9ubuntu1) ...
Setting up xserver-xorg-video-trident (1:1.2.4-1) ...
Setting up xserver-xorg-video-tseng (1:1.1.1-4) ...
Setting up xserver-xorg-video-v4l (1:0.1.1-6ubuntu1) ...
Setting up xserver-xorg-video-vesa (1:1.3.0-4ubuntu4) ...
Setting up xserver-xorg-video-vga (1:4.1.0-8) ...
Setting up xserver-xorg-video-via (1:0.2.2-5) ...

Setting up xserver-xorg-video-vmware (1:10.15.2-1ubuntu2) ...
Setting up xserver-xorg-video-voodoo (1:1.1.1-5) ...
Setting up xserver-xorg-video-all (1:7.3+10ubuntu10) ...
Setting up xserver-xorg (1:7.3+10ubuntu10) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 msttcorefonts
E: Sub-process /usr/bin/dpkg returned an error code (1)

```does this look ok?

Yes, seems fine to me..
It seems the you have installed 23.9MB of packages, which is almost similar to the default 24MB.
Just issue the xserver-xorg* installation, if it doesn't get too huge..

---

### Post by dracayr on 2008-05-31
yeah, hardy has some kind of new video playback..

lol, the search function on ubuntu.com triggers a SQL error and a javascript error

dracayr

---

### Post by PatrickMoore on 2008-05-31
still cannot enable compiz

---

### Post by sayakb on 2008-05-31
```
glxinfo
```
Post the output.

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> ```
glxinfo
```
Post the output.


```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:
    GLX_ARB_get_proc_address, GLX_ARB_multisample, GLX_EXT_visual_info, 
    GLX_EXT_visual_rating, GLX_EXT_import_context, GLX_SGI_video_sync, 
    GLX_NV_swap_group, GLX_NV_video_out, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer, 
    GLX_SGI_swap_control, GLX_NV_float_buffer, GLX_ARB_fbconfig_float, 
    GLX_EXT_fbconfig_packed_float, GLX_EXT_texture_from_pixmap, 
    GLX_EXT_framebuffer_sRGB
GLX version: 1.3
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float, GLX_ARB_get_proc_address
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce Go 6150/PCI/SSE2
OpenGL version string: 2.1.2 NVIDIA 169.12
OpenGL extensions:
    GL_ARB_color_buffer_float, GL_ARB_depth_texture, GL_ARB_draw_buffers, 
    GL_ARB_fragment_program, GL_ARB_fragment_program_shadow, 
    GL_ARB_fragment_shader, GL_ARB_half_float_pixel, GL_ARB_imaging, 
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query, 
    GL_ARB_pixel_buffer_object, GL_ARB_point_parameters, GL_ARB_point_sprite, 
    GL_ARB_shadow, GL_ARB_shader_objects, GL_ARB_shading_language_100, 
    GL_ARB_texture_border_clamp, GL_ARB_texture_compression, 
    GL_ARB_texture_cube_map, GL_ARB_texture_env_add, 
    GL_ARB_texture_env_combine, GL_ARB_texture_env_dot3, GL_ARB_texture_float, 
    GL_ARB_texture_mirrored_repeat, GL_ARB_texture_non_power_of_two, 
    GL_ARB_texture_rectangle, GL_ARB_transpose_matrix, 
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader, 
    GL_ARB_window_pos, GL_ATI_draw_buffers, GL_ATI_texture_float, 
    GL_ATI_texture_mirror_once, GL_S3_s3tc, GL_EXT_texture_env_add, 
    GL_EXT_abgr, GL_EXT_bgra, GL_EXT_blend_color, 
    GL_EXT_blend_equation_separate, GL_EXT_blend_func_separate, 
    GL_EXT_blend_minmax, GL_EXT_blend_subtract, GL_EXT_compiled_vertex_array, 
    GL_EXT_Cg_shader, GL_EXT_depth_bounds_test, GL_EXT_draw_range_elements, 
    GL_EXT_fog_coord, GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample, 
    GL_EXT_framebuffer_object, GL_EXT_gpu_program_parameters, 
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil, 
    GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object, GL_EXT_point_parameters, 
    GL_EXT_rescale_normal, GL_EXT_secondary_color, 
    GL_EXT_separate_specular_color, GL_EXT_shadow_funcs, 
    GL_EXT_stencil_two_side, GL_EXT_stencil_wrap, GL_EXT_texture3D, 
    GL_EXT_texture_compression_s3tc, GL_EXT_texture_cube_map, 
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_filter_anisotropic, 
    GL_EXT_texture_lod, GL_EXT_texture_lod_bias, GL_EXT_texture_mirror_clamp, 
    GL_EXT_texture_object, GL_EXT_texture_sRGB, GL_EXT_timer_query, 
    GL_EXT_vertex_array, GL_IBM_rasterpos_clip, 
    GL_IBM_texture_mirrored_repeat, GL_KTX_buffer_region, GL_NV_blend_square, 
    GL_NV_copy_depth_to_color, GL_NV_depth_clamp, GL_NV_fence, 
    GL_NV_float_buffer, GL_NV_fog_distance, GL_NV_fragment_program, 
    GL_NV_fragment_program_option, GL_NV_fragment_program2, 
    GL_NV_framebuffer_multisample_coverage, GL_NV_half_float, 
    GL_NV_light_max_exponent, GL_NV_multisample_filter_hint, 
    GL_NV_occlusion_query, GL_NV_packed_depth_stencil, GL_NV_pixel_data_range, 
    GL_NV_point_sprite, GL_NV_primitive_restart, GL_NV_register_combiners, 
    GL_NV_register_combiners2, GL_NV_texgen_reflection, 
    GL_NV_texture_compression_vtc, GL_NV_texture_env_combine4, 
    GL_NV_texture_expand_normal, GL_NV_texture_rectangle, 
    GL_NV_texture_shader, GL_NV_texture_shader2, GL_NV_texture_shader3, 
    GL_NV_vertex_array_range, GL_NV_vertex_array_range2, GL_NV_vertex_program, 
    GL_NV_vertex_program1_1, GL_NV_vertex_program2, 
    GL_NV_vertex_program2_option, GL_NV_vertex_program3, 
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 
    GL_SGIX_depth_texture, GL_SGIX_shadow, GL_SUN_slice_accum

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x21 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x22 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x24 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x25 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x26 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x27 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x28 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x29 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x2a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x2b 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x2e 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x2f 24 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x30 24 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x31 24 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x32 24 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x33 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x34 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x35 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x36 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x37 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x38 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x39 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x3a 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x3b 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x3c 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x3d 24 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x3e 24 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x3f 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x40 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x41 24 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x42 24 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x43 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x44 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x45 24 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x46 24 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x47 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x48 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x49 24 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x4a 24 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x4b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4c 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x4d 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x4e 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x4f 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x50 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x51 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x52 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x53 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x54 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x55 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x56 24 dc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x57 24 dc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x58 24 dc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x59 24 dc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x5a 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5b 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x5c 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x5d 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x5e 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x5f 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x60 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x61 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x62 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x63 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x64 24 dc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x65 24 dc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x66 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x67 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x68 24 dc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x69 24 dc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x6a 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6b 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x6c 24 dc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x6d 24 dc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x6e 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x6f 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x70 24 dc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x71 24 dc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x23 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x72 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x73 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  0 0 None
0x74 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  0 0 None
0x75 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x76 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x77 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  0 0 None
0x78 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  0 0 None
0x79 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7a 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7b 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  0 0 None
0x7c 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  0 0 None
0x7d 32 tc  0 32  0 r  y  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x7e 32 tc  0 32  0 r  y  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x7f 32 tc  0 32  0 r  .  .  8  8  8  0  4  0  0 16 16 16 16  0 0 None
0x80 32 tc  0 32  0 r  .  .  8  8  8  8  4  0  0 16 16 16 16  0 0 None
0x81 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x82 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x83 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x84 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x85 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  2 1 Ncon
0x86 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  2 1 Ncon
0x87 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  0 16 16 16 16  4 1 Ncon
0x88 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  0 16 16 16 16  4 1 Ncon
0x89 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8a 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8b 32 tc  0 32  0 r  y  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x8c 32 tc  0 32  0 r  y  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x8d 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  2 1 Ncon
0x8e 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  2 1 Ncon
0x8f 32 tc  0 32  0 r  .  .  8  8  8  0  4 24  8 16 16 16 16  4 1 Ncon
0x90 32 tc  0 32  0 r  .  .  8  8  8  8  4 24  8 16 16 16 16  4 1 Ncon
0x91 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x92 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x93 32 tc  0 32  0 r  y  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x94 32 tc  0 32  0 r  y  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon
0x95 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  2 1 Ncon
0x96 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  2 1 Ncon
0x97 32 tc  0 32  0 r  .  .  8  8  8  0  4 16  0 16 16 16 16  4 1 Ncon
0x98 32 tc  0 32  0 r  .  .  8  8  8  8  4 16  0 16 16 16 16  4 1 Ncon

```

---

### Post by sayakb on 2008-05-31
It doesn't seem like a driver problem either. Give a last try. Do:
```
metacity --replace &
sudo apt-get purge compiz
sudo apt-get install compiz
compiz --replace &
```

---

### Post by PatrickMoore on 2008-05-31
> **LinuxIsInnovation said:**
> It doesn't seem like a driver problem either. Give a last try. Do:
```
metacity --replace &
sudo apt-get purge compiz
sudo apt-get install compiz
compiz --replace &
```
 
the first three worked well. then i  went for the fourth.

```
patrick@patrick-laptop:~$ compiz --replace &
Checking for Xgl: [2] 7231
patrick@patrick-laptop:~$ not present. 
Detected PCI ID for VGA: 00:05.0 0300: 10de:0244 (rev a2) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Another composite manager is already running on screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

---

### Post by dracayr on 2008-05-31
I suppose desktop effects won't work either?

dracayr

---

### Post by PatrickMoore on 2008-05-31
yep same thing

---

### Post by dracayr on 2008-05-31
just for clarification; I formulated that a bit strange. I meant If you enable desktop effects (wobbly windows, etc) in System>preferences>Apperance, then the desktop effects won't work?

dracayr

---

### Post by PatrickMoore on 2008-05-31
> **dracayr said:**
> just for clarification; I formulated that a bit strange. I meant If you enable desktop effects (wobbly windows, etc) in System>preferences>Apperance, then the desktop effects won't work?

dracayr

that is correct

---

### Post by dracayr on 2008-05-31
maybe you should try the real compiz experts at [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/)

dracayr

---

### Post by PatrickMoore on 2008-05-31
will do thanks for the help though

---


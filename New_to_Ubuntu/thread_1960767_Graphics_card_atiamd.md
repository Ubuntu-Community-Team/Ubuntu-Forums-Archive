---
title: "Graphics card ati/amd"
date: 2012-04-18
forum: New to Ubuntu
---

### Post by BeMyManikin on 2012-04-18
I have just built my new computer and it is AWESOME, but I cant seem to get the video to work on all websites. I went to youtube, and some of the videos come out smaller than the allotted space. On the NBC website, I can't watch any episodes of shows I missed...

[U][IMG]http://desmond.imageshack.us/Himg687/scaled.php?server=687&filename=adddrivers.png&res=landing[/IMG]

[/U] The first one says that something can't activate... The image I saved got over written I guess (I put it under a different name, but screen shot it pissing me off). Anyway, I was wondering if anyone can help?

(I will post more screen shots when I get back on that computer)

I did activate the bottom one, and NBC videos are still inaccessible.

---

### Post by ronaldbrijo on 2012-04-18
Ah, i had the same problem with internet videos.

I suppose ur using firefox? The problem is with firefox and not ur video drivers. I use Google Chrome instead. It has better flash and java properties.

Hope it works for u.

---

### Post by ronaldbrijo on 2012-04-18
regarding the graphics driver... not too sure the ati driver installed 1st time for me.

try downloading the driver direct from ati website and install manually?

---

### Post by ewz on 2012-04-18
Hi what release of Ubuntu are you using 11.10 12.04 ? 
What type of ATI graphics card do you have ?
have you installed any propiretary drivers yet, 

There was a bug in the post release version a while ago or 12.04, I'm not sure if it has been fixed yet, 

Have you tryed installing the the one je post release just below the post release version ? 
I'm rusing that friver and have had no issues with it full screen flash in firefox works fine

---

### Post by mastablasta on 2012-04-18
maybe videos need octoshape if they are not using adobe flash...

---

### Post by BeMyManikin on 2012-04-19
> **ronaldbrijo said:**
> Ah, i had the same problem with internet videos.

I suppose ur using firefox? The problem is with firefox and not ur video drivers. I use Google Chrome instead. It has better flash and java properties.

Hope it works for u.

I actually don't like chrome...

> **ronaldbrijo said:**
> regarding the graphics driver... not too sure the ati driver installed 1st time for me.

try downloading the driver direct from ati website and install manually?

Still have the same problem after doing it manually... Maybe the problem isn't my graphics card...

> **ewz said:**
> Hi what release of Ubuntu are you using 11.10 12.04 ? 
What type of ATI graphics card do you have ?
have you installed any propiretary drivers yet, 

There was a bug in the post release version a while ago or 12.04, I'm not sure if it has been fixed yet, 

Have you tryed installing the the one je post release just below the post release version ? 
I'm rusing that friver and have had no issues with it full screen flash in firefox works fine
11.10, and I think it's a radeon hd 5450
Yes I have, that's when I checked the video on nbc


> **mastablasta said:**
> maybe videos need octoshape if they are not using adobe flash...

I have no idea what that means, but please continue.

---

### Post by mastablasta on 2012-04-19
> **BeMyManikin said:**
>  
I have no idea what that means, but please continue.
 
[http://en.wikipedia.org/wiki/Octoshape](http://en.wikipedia.org/wiki/Octoshape)
 
also sometimes it happens that users installs multiple isntances of flash in that case all flash needs to be pruged and only the propper one installed. 
 
i suggest installign restricted extras package to solve most playback problems.

---

### Post by BeMyManikin on 2012-04-19
[IMG]http://s14.postimage.org/fpcactdnl/add_driv.png[/IMG]
When I try to install the top one I get:
[IMG]http://s15.postimage.org/pb4fje0mz/Driver_error.png[/IMG]
it only shows this white rectangle:
[IMG]http://s16.postimage.org/ug72apmwl/Nbc_lack_of_video.png[/IMG]
I put in lspci and got:
```
00:00.0 Host bridge: ATI Technologies Inc RD890 PCI to PCI bridge (external gfx0 port B) (rev 02)
00:02.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port B)
00:04.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port D)
00:09.0 PCI bridge: ATI Technologies Inc RD890 PCI to PCI bridge (PCI express gpp port H)
00:11.0 SATA controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 SATA Controller [IDE mode] (rev 40)
00:12.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:12.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:13.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:13.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 42)
00:14.1 IDE interface: ATI Technologies Inc SB7x0/SB8x0/SB9x0 IDE Controller (rev 40)
00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA) (rev 40)
00:14.3 ISA bridge: ATI Technologies Inc SB7x0/SB8x0/SB9x0 LPC host controller (rev 40)
00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge (rev 40)
00:14.5 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI2 Controller
00:15.0 PCI bridge: ATI Technologies Inc SB700/SB800/SB900 PCI to PCI bridge (PCIE port 0)
00:16.0 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB OHCI0 Controller
00:16.2 USB Controller: ATI Technologies Inc SB7x0/SB8x0/SB9x0 USB EHCI Controller
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 15h Processor Function 5
**01:00.0 VGA compatible controller: ATI Technologies Inc Cedar PRO [Radeon HD 5450]**
01:00.1 Audio device: ATI Technologies Inc Manhattan HDMI Audio [Mobility Radeon HD 5000 Series]
02:00.0 USB Controller: Etron Technology, Inc. EJ168 USB 3.0 Host Controller (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```
Thank you for the help again!

---

### Post by mastablasta on 2012-04-19
> **BeMyManikin said:**
> 
When I try to install the top one I get:
 

 
because your driver is already installed. you need to remove it and purge it first and then install new one (if you so wish).
 
unfortunatelly the site with instrucitons on how to do this is now 404. :confused:

---

### Post by BeMyManikin on 2012-04-19
> **mastablasta said:**
> [http://en.wikipedia.org/wiki/Octoshape](http://en.wikipedia.org/wiki/Octoshape)
 
also sometimes it happens that users installs multiple isntances of flash in that case all flash needs to be pruged and only the propper one installed. 
 
i suggest installign restricted extras package to solve most playback problems.

I did the 
```
sudo apt-get install ubuntu-restricted-extras
```
and checked the site, and it says that flash is not installed

---

### Post by BeMyManikin on 2012-04-19
now i tried installing from software center it had this
[IMG]http://s15.postimage.org/ot2ziwrej/adobe_wtf.png[/IMG]

I did sudo apt-get install adobe-flashplugin:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installeReading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobeReading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be usedReading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ....
Do you want to continue [Y/n]? yReading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursReading package lists... Done
Building dependency tree       
Reading state information... DoneReading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...or1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...d, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package adobe-flashplugin is not installed, so not removed
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
epic@epic-delta:~$ sudo apt-get install adobe-flashplugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libkrb5-3:i386 libatk1.0-0:i386 libk5crypto3:i386 libxfixes3:i386 libxcomposite1:i386
  libcairo2:i386 libgnutls26:i386 libtasn1-3:i386 libfreetype6:i386 libexpat1:i386
  libdatrie1:i386 libavahi-common-data:i386 libgdk-pixbuf2.0-0:i386 libxcb1:i386
  libxau6:i386 libpixman-1-0:i386 libcups2:i386 libxinerama1:i386 libkrb5support0:i386
  libxft2:i386 libice6:i386 libxdmcp6:i386 libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ... libgcrypt11:i386 libthai0:i386
  libkeyutils1:i386 libxrender1:i386 libtiff4:i386 libjasper1:i386 libpng12-0:i386
  libjpeg62:i386 libavahi-client3:i386 libx11-6:i386 libfontconfig1:i386
  libpango1.0-0:i386 libsm6:i386 libxdamage1:i386 libxcb-render0:i386
  libgssapi-krb5-2:i386 libxi6:i386 libxcursor1:i386 libxcb-shm0:i386 libxt6:i386
  libxext6:i386 libavahi-common3:i386 libxrandr2:i386 libgtk2.0-0:i386
  libgpg-error0:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  adobe-flash-properties-gtk
Suggested packages:
  konqueror-nsplugins ttf-bitstream-vera ttf-dejavu ttf-xfree86-nonfree xfs
The following packages will be REMOVED:
  adobe-flash-properties-gtk:i386 adobe-flashplugin:i386
The following NEW packages will be installed:
  adobe-flash-properties-gtk adobe-flashplugin
0 upgraded, 2 newly installed, 2 to remove and 0 not upgraded.
Need to get 7,014 kB of archives.
After this operation, 1,839 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flashplugin amd64 11.2.202.233-0oneiric1 [6,880 kB]
Get:2 http://archive.canonical.com/ubuntu/ oneiric/partner adobe-flash-properties-gtk amd64 11.2.202.233-0oneiric1 [134 kB]
Fetched 7,014 kB in 9s (735 kB/s)                                                        
(Reading database ... 153532 files and directories currently installed.)
Removing adobe-flash-properties-gtk:i386 ...
Removing adobe-flashplugin:i386 ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Selecting previously deselected package adobe-flashplugin.
(Reading database ... 153505 files and directories currently installed.)
Unpacking adobe-flashplugin (from .../adobe-flashplugin_11.2.202.233-0oneiric1_amd64.deb) ...
Selecting previously deselected package adobe-flash-properties-gtk.
Unpacking adobe-flash-properties-gtk (from .../adobe-flash-properties-gtk_11.2.202.233-0oneiric1_amd64.deb) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Setting up adobe-flashplugin (11.2.202.233-0oneiric1) ...
Setting up adobe-flash-properties-gtk (11.2.202.233-0oneiric1) ...
```
It doesn't show that it has finished above, but on the terminal put it back to input mode

The site still says this:
[IMG]http://s13.postimage.org/uacakyslz/nbc_flash.png[/IMG]

man... this is aggravating... Oh and on the sites like imageshack.us, it won't let me click the browse button, and it disappears as well, so I can't use it at all. I don't know if it is due to the same problem, but I thought I'd throw it out there if it is.

---

### Post by BeMyManikin on 2012-04-20
must be adobe then, so I will start a new one about my problems with adobe flash

---

### Post by mastablasta on 2012-04-20
why didnt' you just install restricted extras package?
 
have you tried flash aid plugin for firefox?

---

### Post by BeMyManikin on 2012-04-21
I did the restrictions, and it didn't work. Then I did the flash-aid install.
IT WORKED LIKE A CHARM!!!!
THANK YOU!

---


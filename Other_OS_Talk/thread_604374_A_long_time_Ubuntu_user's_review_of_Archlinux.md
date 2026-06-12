---
title: "A long time Ubuntu user's review of Archlinux"
date: 2007-11-06
forum: Other OS Talk
---

### Post by kpkeerthi on 2007-11-06
UBUNTU - This wonderful beginner friendly distro helped me get started with Linux and I've been using it for about 18 months. Though I wanted to switch to Linux back in 2004, I couldn't stick to it (SUSE) until I discovered Ubuntu. Thanks to Ubuntu and the community. I heard good things about Arch in the forums and blogs and last week was perfect to get my hands dirty with it as I had a bit of leisure time.
 
 The basic Arch's philosophy is to keep things simple. That does not mean things would be easy with Arch which became clear as I began the installation process :) 
 
 I downloaded and burned the iso (~150 MB), freed up 30 GB on my hard disk and fired the installer. Though command line based, I found the installer to be fairly intuitive. I chose to install from CD rather than FTP as I wanted to get up and running fast. The CD contains 'core' packages, sufficient enough to get a basic linux system running.
 
 Unlike ubuntu's installer, there is no 'Use largest contiguous free space' option to automatically install onto available free space. Partitioning should be done manually in Arch. I created root and swap partitions and filesystems using the 'cfdisk' utility supplied with the installer. At the end of the installation I chose to install GRUB to my boot partition (and not MBR). Then booted into Vista and used EasyBCD to set-up dual boot using Vista's Boot loader. I rebooted and kept my fingers crossed. Arch booted fine - A sign of relief for me.
 
 One thing that I immediately noticed was that Arch booted quickly. I did not time it but it was apparently faster. The base system has no desktop environment. I added an user account for me and then as a root changed timezone, locale and host information in /etc/rc.conf. Most of the system-wide configuration like locale, hostname, IP, kernel modules, startup daemons, etc. is centrally stored in this file. Simple and elegant.
 
 The installer automatically configured static IP for my interface. Though I didn't have to do this, I  changed the config to use DHCP. Internet was quirky until I disabled IPv6.
 
 Arch uses pacman for package management. I find pacman to be flexible, robust, fast, simple and takes care of managing dependencies well. Its command-line based (there is also an optional GUI to it) and is similar to aptitude/apt-get in ubuntu. Here is a comparison of the most commonly used commands: 
 
 	aptitude update => pacman -Sy
 	aptitude dist-upgrade => pacman -Syu
 	aptitude (re)install <package> => pacman -S <package>
 	aptitude remove <package> => pacman -Rs <package>
 	aptitude purge <package> => pacman -Rsn <package>
 	aptitude search <keyword> => pacman -Ss <keyword>
 	aptitude clean => pacman -Scc
 
 'pacman -Syu' (full system upgrade) was not responding at all. But I could ping to the repository server. pacman started working now, found a few updates and installed without a hitch. I still had to ping to the repository server every time I wanted to use pacman. Strange. I found that DNS was incorrectly configured in /etc/resolv.conf. It had my router's IP instead of my ISP provided DNS. I changed the file with proper nameserver values and configured dhcpcd not to overwrite resolv.conf on subsequent reboots. Ah.. fixed my pacman issue. The best part of pacman is that it can be configured to use download managers (like aria2, for example) to download packages from multiple mirrors simultaneously for faster downloads. Impressive. You can also prioritize your mirrors by editing the files in /etc/pacman.d/ folder. 
 
 Arch has Arch Build System (ABS). If you are familiar with Gentoo's portage, its similar to that. But for now I decided to stick with the binary repositores.
 
 Now that I have a basic working system I also enabled 'community' repository and installed gnome, gdm, alsa, networkmanager, nvidia binary driver, compiz(-fusion), open office, firefox & plugins, brasero, mplayer, f-spot, banshee, conky, cpufreq-utils, bluetooth and a couple of packages to optimize font rendering on LCD - pretty much everything for my 'desktop' use. Unlike ubuntu, I had to configure most of the packages manually but thats how Arch has been designed to work. It took me a good 4 hours to get everything customized and configured to my liking. It was a good learning experience. It was fun to setup an Operating System starting off with just a kernel and then add only the packages that I need and use (much less bloat). I often referred to Gentoo's wiki wherever I needed help configuring a package. Arch's wiki was also useful but I advice beginners to exercise a little more care as they could be out-dated. 
 
 Things I like about Arch:
 	- Lean setup.
 	- i686 optimized and fast. 
 		 I know this is subjective. But Arch is definitely faster on my hardware compared to Ubuntu. Apps load faster and feel snappier. Firefox, Openoffice and Acrobat have never been as snappier and light as they are in Arch for me. These were the most sluggiest in Ubuntu for me. 
 		
 	- Rolling release cycle. 'pacman -Syu' keeps me up-to-date with the new releases of the packages. I do not have to download and burn another iso to upgrade.
 	- Rich official repositories.
 
 While Arch is fast, customizable and lean, it probably will not appeal to you if you are a linux beginner. If you are willing to learn and have time, I suggest you give Arch a try. Every distribution is unique in its own way and what works for me may not for you. You are your best judge.
 
 Have I completely switched over to Arch? 
 Not yet. So far I'm happy with Arch and I was successful in my first install. Arch tends to be more 'bleeding edge' as newer versions of packages are continuously added to the main repository as they are released. I'm not sure if that would ever break my setup. I think I'll wait for another few weeks and take a decision. So far its been stable for me.

- Have a nice day.
 ---------------------------------------------------------------
 Checkout Arch installation screenshots here [http://news.softpedia.com/news/How-to-Install-Arch-Linux-59239.shtml](http://news.softpedia.com/news/How-to-Install-Arch-Linux-59239.shtml)

 The Arch Philosophy [http://wiki.archlinux.org/index.php/The_Arch_Way](http://wiki.archlinux.org/index.php/The_Arch_Way)

---

### Post by undine on 2007-11-06
Thanks for the review. I too have heard good things about Arch, and I especially like some of the eyecandy available for KDEMod :) However, even though I have been using Ubuntu/Linux for quite some time now, I feel that I still need just a little hand-holding, particularly through the installation process. It's not that I wouldn't be able to muddle my way through eventually, but rather that I have a lot of sensitive data that I can't afford to imperil :P So even though it sounds like a great disto, I think I'm going to stick with Ubuntu for now; at least until I get another PC besides my current two.

---

### Post by b9anders on 2007-11-06
you should have that data backuped as soon as possible in any case then or moved to a separate partition.

---

### Post by david_2001 on 2007-11-06
> **kpkeerthi said:**
> UBUNTU - This wonderful beginner friendly distro helped me get started with Linux and I've been using it for about 18 months. Though I wanted to switch to Linux back in 2004, I couldn't stick to it (SUSE) until I discovered Ubuntu. Thanks to Ubuntu and the community. I heard good things about Arch in the forums and blogs and last week was perfect to get my hands dirty with it as I had a bit of leisure time...

A good and fair review.  I'm just looking back through the notes and aide memoires that I made when I was installing Arch and there really wasn't anything nasty or unpleasant to cope with, though sorting out usb device permissions and groups names took a little effort (I'm always happier when devices belong to their proper groups):
```
User Groups
===========
# gpasswd -a david audio
# gpasswd -a david video
# gpasswd -a david optical
# gpasswd -a david disk
# gpasswd -a david storage
# gpasswd -a david floppy

Sound
=====
# pacman -Sy alsa-lib alsa-utils alsa-oss

Make sure that snd-mixer-oss and snd-pcm-oss are at the end of the list of sound-related MODULES in /etc/rc.conf, after snd-hda-intel. Add alsa to the DAEMONS in /etc/rc.conf.  (Possibly add the following to /etc/rc.local: /usr/bin/amixer set Front 100% unmute >/dev/null 2>&1)

Fonts
=====
Display Size/DPI
In order to get correct sizing for fonts the display size must be set for your desired DPI. For nVidia drivers you may have to disable automatic detection of DPI to set it manually. There is also an easier way to set DPI on these cards. Either or both of the following lines can be set in the device section for your nVidia card.

  Option   "UseEdidDpi" "false"
  Option   "DPI" "96 x 96

Install X Fonts
# pacman -Sy xorg-fonts-100dpi font-bitstream-speedo gsfonts ttf-ms-fonts ttf-cheapskate artwiz-fonts ttf-bitstream-vera 

Download free PowerPoint Viewer (PowerPointViewer.exe) from http://www.microsoft.com/downloads/details.aspx?FamilyID=048dc840-14e1-467d-8dca-19d2a8fd7485&displaylang=en

# cabextract PowerPointViewer.exe
# cabextract ppviewer.cab
# ls *TTF

Then goto the Adding Fonts Wiki page (http://wiki.archlinux.org/index.php/Adding_fonts)

Check the font paths in /etc/X11/xorg.conf for the correct path to the TTF fonts directory: /usr/share/fonts/TTF

NTP
===
http://wiki.archlinux.org/index.php/NTP

Lirc
====
http://wiki.archlinux.org/index.php/Lirc

CUPS
====
http://wiki.archlinux.org/index.php/CUPS

CUPS-PDF
========
Hint: The cups-pdf printer is Postscript/Color.

To make ~/PDF the print destination edit /etc/cups/cups-pdf.conf and change the Out key:

### Key: Out
##  CUPS-PDF output directory 
##  special qualifiers: 
##     ${HOME} will be expanded to the user's home directory
##     ${USER} will be expanded to the user name
##  in case it is an NFS export make sure it is exported without
##  root_squash! 
### Default: /var/spool/cups-pdf/${USER}

Out ${HOME}/PDF

Gnome Menu Editor
=================
# pacman -Sy alacarte

More Gnome Themes
=================
# pacman -Sy ubuntulooks tango-icon-theme tango-icon-theme-extras

No Wastebasket on Desktop
=========================
Run gconf-editor and then change apps -> nautilus -> desktop

DVB-t and DVD
=============
# pacman -Sy linuxtv-dvb-apps kaffeine libdvdcss

Dictionary
==========
# pacman -Sy aspell-en

Enabling shellcompletion
========================
# pacman -S bash-completion

and add

if [ -f /etc/bash_completion ]; then
    . /etc/bash_completion
fi

to .bashrc

Firefox Branding
================
Problems with online banking and "Bon Echo":  http://wiki.archlinux.org/index.php/Firefox

Arch 64 32-bit Compatibility
============================
# pacman -Sy lib32-glibc lib32-qt lib32-alsa-lib lib32-nvidia-utils

Part or all the nspluginwrapper wrapper stuff, some of which overlaps:

pacman -Sy gtk2 libxt linux32 lib32-gcc lib32-libxmu lib32-libx11 lib32-libxext lib32-libxt lib32-glibc lib32-libxau lib32-libsm lib32-libice lib32-fontconfig lib32-libxrender lib32-libxinerama lib32-libxrandr lib32-libxcursor lib32-libxfixes lib32-libxft lib32-freetype2 lib32-zlib lib32-expat lib32-gtk2 lib32-atk lib32-pango lib32-glib2 lib32-cairo lib32-libxi lib32-libpng lib32-pcre lib32-alsa-lib

and (!!!)

# pacman -Sy lib32-libx11 lib32-libxcb (but not lib32-libxml2, which just seems to make everything else fall over)

Totem gstreamer plugins (minimum)
=================================
# pacman -Sy gstreamer0.10-bad gstreamer0.10-ugly gstreamer0.10-ffmpeg gstreamer0.10-mpeg2dec gstreamer0.10-lame gstreamer0.10-mad

More Multimedia
===============
# pacman -Sy ffmpeg mplayer mplayer-plugin mplayer-skins transcode acidrip

USB Device Permissions
======================
# groupadd -K GID_MAX=999 usb
# gpasswd -a david usb

Then edit /etc/fstab and add the following line, substituting the GID for usb (from /etc/group):
none                   /proc/bus/usb usbfs     devgid=101,devmode=664,nodev,noexec,nosuid    0      0

Add /etc/udev/rules.d/local.rules:

<------Start------>
# My local udev rules
# Updated 26-Oct-07

ACTION!="add", GOTO="local_rules_end"
ENV{DEVTYPE}=="usb_device", GOTO="local_rules_begin"
SUBSYSTEM=="usb_device", GOTO="local_rules_begin"
SUBSYSTEM!="usb_device", GOTO="local_rules_end"

LABEL="local_rules_begin"

# Epson Perfection 3170 Photo
# Also set correct owners and permissions in /dev/bus/usb here because of the problems with 54-gphoto.rules and 53-libsane.rules
ATTRS{idVendor}=="04b8", ATTRS{idProduct}=="0116", MODE="0664", GROUP="scanner", ENV{libsane_matched}="yes"

# Photosmart D6160 printer
# Create device node with correct root:lp owners in /proc/bus/usb
ATTRS{idVendor}=="03f0", ATTRS{idProduct}=="c502", RUN+="/bin/sh -c '/bin/chown root:lp /proc/$name;/bin/chmod 0664 /proc/$name'"

GOTO="local_rules_end"

# Scanner only: The following rule will disable USB autosuspend for the device, copied from libsane.rules
ENV{libsane_matched}=="yes", RUN+="/bin/sh -c 'test -e /sys/$env{DEVPATH}/power/level && echo on > /sys/$env{DEVPATH}/power/level'"

LABEL="local_rules_end"
<------End------>

VirtualBox
==========
http://wiki.archlinux.org/index.php/VirtualBox

There are problems with USB (devices detected but communication is not reliable).  This seems to be something to do with VirtualBox not liking kernel 2.6.23.

"IMPORTANT:
Anytime your kernel version changes due to upgrade, recompile, etc., you will need to rebuid the virtualbox kernel module using "vbox_build_module". This binary will be located in one of the following locations: /sbin, /bin, or /usr/bin and must be executed with superuser priveleges. After rebuilding the module, don't forget to load it with: modprobe vboxdrv.!"

Compiz-Fusion
=============
The Arch Wiki (http://wiki.archlinux.org/index.php/Compiz) is not up to date with the latest packages!

If compiling from the git source using AUR PKGBUILDs then make sure that kdebase, dbus-qt3, pyqt4 and pyrex are installed first.

AUR compiz-fusion git packages, in compilation/installation order:
compiz-git.tar.gz
compiz-bcop-git.tar.gz
compiz-fusion-plugins-main-git.tar.gz
compiz-fusion-plugins-extra-git.tar.gz
libcompizconfig-git.tar.gz
compizconfig-python-git.tar.gz
ccsm-git.tar.gz
emerald-git.tar.gz
emerald-themes-git.tar.gz
fusion-icon-git.tar.gz

If the Fusion-Icon icon is missing from menus then run the following command:
# gtk-update-icon-cache -f /usr/share/icons/hicolor

ProjectX
========
Add "export LIBXCB_ALLOW_SLOPPY_LOCK=1" to /etc/profile.d/xorg.sh if ProjectX fails to start with the following error:
java: xcb_xlib.c:82: xcb_xlib_unlock: Assertion `c->xlib.lock' failed.
```

---

### Post by kellemes on 2007-11-08
Thanks for the review.. well done.
I wonder if an Archer just got born. :popcorn:

---

### Post by Slychilde on 2007-11-08
> I know this is subjective. But Arch is definitely faster on my hardware compared to Ubuntu. Apps load faster and feel snappier. Firefox, Openoffice and Acrobat have never been as snappier and light as they are in Arch for me. These were the most sluggiest in Ubuntu for me.

That's mostly because of the lean part you mentioned.  If you were to do a base (no gui) install of Ubuntu where you chose only the packages you needed, you'd get roughly the same thing.  They're both definitely awesome distros, though. :)

---

### Post by kgas on 2008-11-14
I installed Arch linux in one of my laptop. What I feel the difference is Arch will give the learning curve and the Ubuntu will work out of box and ready to go. Arch's bleeding  technology keeps your machine up to date with the price of some bugs( you can roll back and avoid further updates thro' pacman config file). I feel all Distros are good enough to try and I will come back after trying debian and gentoo.

---

### Post by WaeV on 2008-11-14
This helped me a lot, I've been looking for a faster disto that's more of a challenge.  Thanks!

---

### Post by absolutezero1287 on 2009-01-05
I have made the full switch to arch and I couldn't be happier. One thing that bugs me about Ubuntu are the metapackages. I tried to do a minimal build and was dissapointed when I tried to install xf86-video-intel. Installing that one driver meant that I had to install every other available X driver. So either way, you're going to get uneeded bloat.

---

### Post by gjoellee on 2009-01-05
I used Ubuntu for 1,5 years, I wanted to try Arch Linux because Arch Linux users having to much fun! And I tried it, learned about Arch and set it up. Now I am never going back to Ubuntu unless something amazing happens.

However my opinion of Arch Linux users, are people who want the computer to do exactly what you want it to do, and as well this requires some knowledge about Linux.

---

### Post by kelvin spratt on 2009-01-05
I'm dyslexic and it took several attempts for me to install Arch Linux 2 years ago but it was worth the time and effort. its a fabulous distro. Don't get me wrong it has faults lots of faults but you can usually find a work around thanks mainly to the simple etc config files the wiki + forums, Arch get very addictive and is the most customisable distro you can build as you decide what you want nobody else.

---

### Post by crimesaucer on 2009-01-05
While I liked this review and agreed with a lot of things you said, I thought I might clarify and add a few points and tips.




> **kpkeerthi said:**
> "I chose to install from CD rather than FTP as I wanted to get up and running fast. The CD contains 'core' packages, sufficient enough to get a basic linux system running."
 

FTP should technically be the faster way. 

If you know your hardware is supported and your internet connection is already working with Linux, then I would recommend trying the FTP install first.... especially if you are going to use DHCP.

The FTP install will configure your connection automatically..... if you run into problems with your connection then you can try to connect manually or just start over using the CD.

When you install using the FTP install, it installs the most recent ARCH base/base dev packages so you don't have to use pacman -Syu to catch up to the current rolling release.... thus saving more time because you don't install "twice".


> **kpkeerthi said:**
> "The installer automatically configured static IP for my interface. Though I didn't have to do this, I  changed the config to use DHCP."


With the FTP install you could of selected the option of DHCP and had it configured automatically and then saved to your rc.conf. 




Next:

> **kpkeerthi said:**
> "I found that DNS was incorrectly configured in /etc/resolv.conf. It had my router's IP instead of my ISP provided DNS. I changed the file with proper nameserver values..." 


> **kpkeerthi said:**
> "I added an user account for me and then as a root changed timezone, locale and host information in /etc/rc.conf. Most of the system-wide configuration like locale, hostname, IP, kernel modules, startup daemons, etc. is centrally stored in this file. Simple and elegant."


There is a section in the install for editing files using nano or vi. It's good to know the proper info before you start the install, that way you can edit all of these important files and configure the /etc/rc.conf and /etc/resolv.conf so you don't have to go back and edit it latter.




Next:

> **kpkeerthi said:**
> "Arch's wiki was also useful but I advice beginners to exercise a little more care as they could be out-dated." 
 

This is the one statement that I do not agree with. The Arch wikis are constantly updated to work with new releases of packages and kernel versions.

If the wikis aren't up to date then they are "flagged" as out of date and are soon edited to work. If a wiki page doesn't contain enough information than it is flagged as a "stub" containing partial information or possibly inaccurate info.

At the very bottom of the page in the lower left corner is the date of the latest update to each wiki page.

Once you get use to Archlinux you will also see that the forums are usually up to date with any bug/fix problems, as is the bug tracker and the comments of the AUR.




Next:

> **kpkeerthi said:**
> "One thing that I immediately noticed was that Arch booted quickly."


Check out these wiki pages for even faster boot: 

[http://wiki.archlinux.org/index.php/Daemons#Starting_Daemons_in_Background](http://wiki.archlinux.org/index.php/Daemons#Starting_Daemons_in_Background)
[http://wiki.archlinux.org/index.php/Fast_boot_without_recompiling_the_kernel](http://wiki.archlinux.org/index.php/Fast_boot_without_recompiling_the_kernel)




Next:

> **kpkeerthi said:**
> "Arch has Arch Build System (ABS). If you are familiar with Gentoo's portage, its similar to that. But for now I decided to stick with the binary repositores."
 

Arch has both ABS and AUR for building packages. You can even make your own PKGBUILD to build packages. There is also the "pacbuilder-svn" app to pull and build packages from those repositories (like portage), using your custom C[XX]FLAGS/MAKEFLAGS that you edit into your /etc/makepkg.conf file. 
 



Next: 

> **kpkeerthi said:**
> 
commonly used commands: 
 
 	aptitude update => pacman -Sy
 	aptitude dist-upgrade => pacman -Syu
 	aptitude (re)install <package> => pacman -S <package>
 	aptitude remove <package> => pacman -Rs <package>
 	aptitude purge <package> => pacman -Rsn <package>
 	aptitude search <keyword> => pacman -Ss <keyword>
 	aptitude clean => pacman -Scc



A couple of good commands to go with this list are:

```

pacman -U
pacman -Q
pacman -Rd

```

With "pacman -U" you can install you own ABS/AUR packages, or an old package version from your /var/cache/pacman/pkg to replace your current package (if it's broken and not working) as long as you haven't cleaned them out with "pacman -Sc" or "pacman -Scc"

With "pacman -Q" you can search for your installed packages and versions.

With "pacman -Rd" you can remove a package and skip the dependency conflicts. (this is good if you have to uninstall something like nvidia-utils to replace it with nvidia-utils-beta).... it's not recommended but sometime you need to use it. (just like "pacman -Uf")




Next:

> **kpkeerthi said:**
> "Impressive. You can also prioritize your mirrors by editing the files in /etc/pacman.d/ folder." 
 

A good tip is to use the rankmirrors command to get the fastest mirrors first.

```

rankmirrors -v /etc/pacman.d/mirrorlist

```

Then copy the order and of fastest mirrors to slowest mirrors and paste that into the /etc/pacman.d/mirrorlist




Next:

> **kpkeerthi said:**
> "Apps load faster and feel snappier. Firefox..."
 	
	
Try the AUR package called "Firefox-optimised" (edit your /etc/makepkg.conf first). It's super fast on my notebook.


Anyway, your review was a good read and I don't mean to sound like a know-it-all or anything.... I just really like Arch so I thought I would share a bit about my experience with you.

.... and I'll post my newest Arch inspired theme that I made to finish this post: 

[IMG]http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-7.png[/IMG]
[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-6.png](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-8-6.png)

---

### Post by jbrown96 on 2009-01-05
Nice review. I tried Arch a few months ago, but I was busy with school and never got it working properly. I'm going to take a fresh look at it.

Crimesaucer: you said that you put that theme together; is it posted anywhere? Is that XFCE (I think the mouse is the xfce icon)? Could you share some info on how to reproduce it? It's very nice.

---

### Post by kpkeerthi on 2009-01-06
@crimesauser
Thanks. I wrote this review on November 6th, 2007. A lot has changed in Arch-Core/Installer/WIKI/ABS/AUR since then. Some of my observations in the review may no longer be valid or ceased to exist.

---

### Post by crimesaucer on 2009-01-06
> **kpkeerthi said:**
> @crimesauser
Thanks. I wrote this review on November 6th, 2007. A lot has changed in Arch-Core/Installer/WIKI/ABS/AUR since then. Some of my observations in the review may no longer be valid or ceased to exist.


I'm sorry, I didn't know it was an old post. It's funny, I started using Arch in Sept/Oct of 2007, and I was on a crappy notebook with a Celeron M chip..... so I really liked the i686 minimal install too, and it did feel much faster than the xubuntu distro I had been using up until that point.


Also at that time the install CD was much more difficult, and the 2007.08 CD would not boot properly for me until they fixed it with 2007.08.1..... and even better with 2007.08.2 when they changed pacman. (before that you had to install with the older 2007.05 Duke CD and then upgrade)


I also didn't know the first thing about the FTP install method back then, but I do recommend it now.


I still remember the wikis being pretty good after the install (maybe they were a little cluttered for the beginner install section..... I actually used this old guide that was easier to follow: [http://www.raiden.net/?cat=2&aid=276](http://www.raiden.net/?cat=2&aid=276) ).


Anyway it was a good review and I didn't mean to make it seem that it was inaccurate or anything..... and for a review back in fall of 2007 it's pretty close to the beginner experience that I had then.

---

### Post by crimesaucer on 2009-01-06
> **jbrown96 said:**
> Crimesaucer: you said that you put that theme together; is it posted anywhere? Is that XFCE (I think the mouse is the xfce icon)? Could you share some info on how to reproduce it? It's very nice.

Yes, I use xfce4 and love it. Thank you for the complement. 


I make my xfce4-panel transparent with a cario-patch from the xfce4 website: [http://blog.xfce.org/?p=177](http://blog.xfce.org/?p=177)

Dwonload the patch: [http://www.loculus.nl/xfce/files/panel-cairo.patch](http://www.loculus.nl/xfce/files/panel-cairo.patch)


Be sure to edit the version number from 4.4.2 to 4.4.3, plus I edit the paths to use the exact directory path and I use the "diff -ur" command instead of "Index:" You can see how I edit the patch and the Arch PKGBUILD in this post here: [http://ubuntuforums.org/showpost.php?p=6476227&postcount=74](http://ubuntuforums.org/showpost.php?p=6476227&postcount=74)


Then I use the compiz-fusion plugin called "blur" to make it look better.


I haven't uploaded/shared any of my new murrine-svn themes or emerald themes. 


I have uploaded some old xfce4 and clearlooks-glossy themes, and some old emerald themes to gnome-looks and xfce4-looks.... but I haven't gotten around to sharing any of my recent murrine-svn themes or my older clearlooks-glossy themes that I've made in the last 10+ months.


As for icons, those are the hydroxygen icon pack that are on gnome-looks.org


And the screenlets are the regular screenlets with some modifications to the python script to use the same font. I also remake most of the background.svg images with Inkscape.

---

### Post by handy on 2009-01-08
[quote=Crimesaucer]There is a section in the install for editing files using nano or vi. It's good to know the proper info before you start the install, that way you can edit all of these important files and configure the /etc/rc.conf and /etc/resolv.conf so you don't have to go back and edit it latter. [/quote]

The /etc/resolv.conf gets overwritten every time the network is started, so for those people that find they need to make a permanent addition to it, in Arch you edit the /etc/resolve.conf.head file, adding as many nameserver IP's as you require,  like so:

nameserver ***.***.***.***
nameserver ***.***.***.***

By the way, nice review OP. :-)

---

### Post by crimesaucer on 2009-01-08
> **handy said:**
> The /etc/resolv.conf gets overwritten every time the network is started, so for those people that find they need to make a permanent addition to it, in Arch you edit the /etc/resolve.conf.head file, adding as many nameserver IP's as you require,  like so:

nameserver ***.***.***.***
nameserver ***.***.***.***

By the way, nice review OP. :-)

Or do what I do with OpenDNS: [http://wiki.archlinux.org/index.php/OpenDNS](http://wiki.archlinux.org/index.php/OpenDNS)

---

### Post by handy on 2009-01-09
> **crimesaucer said:**
> Or do what I do with OpenDNS: [http://wiki.archlinux.org/index.php/OpenDNS](http://wiki.archlinux.org/index.php/OpenDNS)

I have /etc/resolve.conf.head write the address of my IPCop firewall/router/proxy server's address to /etc/resolve.conf each time that machine is booted up or it joins the network. The IPCop box is set up to automatically find/use my ISP's DNS's.  

I have used OpenDNS for a while a couple of years ago, though these days I'm happy with the performance of my current ISP's services.

---


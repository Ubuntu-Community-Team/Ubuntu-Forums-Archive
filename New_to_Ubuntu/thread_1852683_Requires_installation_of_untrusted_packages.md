---
title: "Requires installation of untrusted packages"
date: 2011-09-30
forum: New to Ubuntu
---

### Post by BruceCM on 2011-09-30
The Update manager came up with a load of stuff but hardly started before saying "Requires installation of untrusted packages

The action would require the installation of packages from unauthenticated sources."
Details: "aptdaemon aptdaemon-data banshee banshee-extension-soundmenu banshee-extension-ubuntuonemusicstore bluez bluez-alsa bluez-cups bluez-gstreamer geoclue grub-gfxpayload-lists kdebase-runtime kdebase-runtime-data kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools language-pack-en language-pack-en-base language-pack-gnome-en language-pack-gnome-en-base libbluetooth3 libgeoclue0 libgl1-mesa-dri libgl1-mesa-glx libglu1-mesa libkatepartinterfaces4 libkcmutils4 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 liblircclient0 libnepomuk4 libnepomukquery4a libnepomukutils4 libplasma3 libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-gnome libreoffice-gtk libreoffice-help-en-us libreoffice-impress libreoffice-math libreoffice-style-human libreoffice-writer libsolid4 libthreadweaver4 libxi6 light-themes linux-firmware plasma-scriptengine-declarative plasma-scriptengine-javascript python-aptdaemon python-aptdaemon-gtk python-aptdaemon.gtk3widgets python-aptdaemon.gtkwidgets python-cupshelpers python-uno software-center system-config-printer-common system-config-printer-gnome system-config-printer-udev ttf-opensymbol unattended-upgrades uno-libs3 upstart ure whois xserver-xorg-video-intel"

---

### Post by cgroza on 2011-09-30
Did you add any PPAs lately?

---

### Post by BruceCM on 2011-09-30
Don't think so! Other than chrome? Not sure how adding sources would make the ones already there suddenly 'untrusted', though.

---

### Post by dwasifar on 2011-09-30
If you add an untrusted repo, and that repo contains later versions of things already installed on your system, the next update will try to update them from the new source.  This is likely the reason for the error message you received.

---

### Post by BruceCM on 2011-09-30
Well, I re-installed Ubuntu from it's disk, since I've not had it that long. As far as I know, the only software 'source' I've 'added' is for Chrome. Now, for some reason, after installing & updating, etc, it just freezes! (Currently got the disc in, using it from there, where it works OK but obviously that's a short term 'solution'!)

---

### Post by dwasifar on 2011-09-30
> **BruceCM said:**
> Well, I re-installed Ubuntu from it's disk, since I've not had it that long. As far as I know, the only software 'source' I've 'added' is for Chrome. Now, for some reason, after installing & updating, etc, it just freezes! (Currently got the disc in, using it from there, where it works OK but obviously that's a short term 'solution'!)

Which version of Ubuntu did you install, and can you describe the conditions leading up to the freezing?

---

### Post by BruceCM on 2011-10-01
11.04 Natty Narwhal, etc. VLC played 2 or 3 of my videos & pretty much stopped. It wouldn't close & clicking anywhere else got no reaction but the power button still shut down, supposedly properly.
When restarted, I got into my emails, with Firefox but that then stopped in much the same way! It'd be nice to even get Windows 'not responding' pop up & options. This is more like when I first had Vista, with it's 'not responding', where I was lucky if the task manager there would open, let alone do anything!
Only, here, since clicking anywhere didn't get any reaction, I couldn't goto system settings, open a terminal, etc!
I've since reinstalled it again but have hit the same problem, after doing the extra drivers & updates, before installing other software. Not sure how much more I can say that's likely to be helpful!

---

### Post by mörgæs on 2011-10-01
Changed the title to a more descriptive one.

If you are planning to reinstall again,you could try Xubuntu.

---

### Post by BruceCM on 2011-10-02
Probably will try it at least! Had problems with Kubuntu, too, so tried to re-install Ubuntu, using the whole drive but it claimed there was some problem with the CD for that.Managed to reinstall Kubuntu, which is currently working well.
Downloaded Ubuntu again & burning it to disc, having reformatted the one it was on back to DVD rw on my parents windows laptop. Don't really have access to that very often but I happened to be visiting & it was easier to borrow their laptop to do that on, while I was there.
Guess we'll call this thread solved, anyway, thanks!:)

---


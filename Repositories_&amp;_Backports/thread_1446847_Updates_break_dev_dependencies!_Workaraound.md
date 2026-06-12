---
title: "Updates break dev dependencies! Workaraound?"
date: 2010-04-04
forum: Repositories &amp; Backports
---

### Post by Jeremylc on 2010-04-04
I installed Karmic Netbook.  I used it for awhile, applying software updates as athey became available (just over a month or so).  I decided I wanted to recompile some things so I could, perhaps, patch in some features I'd like.(*)  I'll use a real example here to show explicitly the problem.

$ sudo apt-get build-dep fluidsynth
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have unmet dependencies:
  libpulse-dev: Depends: libpulse0 (= 1:0.9.19-0ubuntu4) but 1:0.9.19-0ubuntu4.1 is to be installed
                Depends: libpulse-mainloop-glib0 (= 1:0.9.19-0ubuntu4) but 1:0.9.19-0ubuntu4.1 is to be installed
                Depends: libpulse-browse0 (= 1:0.9.19-0ubuntu4) but 1:0.9.19-0ubuntu4.1 is to be installed
E: Build-dependencies for fluidsynth could not be satisfied.



Okay, so I can "force" libpulse0 to the version that libpulse-dev expects (it's not even minor revision different), so...

$ sudo apt-get install libpulse0=1:0.9.19-0ubuntu4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnomenu0-2 libglobalmenu-gnome libgconfmm-2.6-1c2 gnome-globalmenu-common libglademm-2.4-1c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  gnome-applet-globalmenu gnome-applets gnome-control-center gnome-globalmenu gnome-media gnome-panel gnome-session gnome-settings-daemon indicator-applet indicator-applet-session indicator-messages indicator-session libpulse-browse0 libpulse-mainloop-glib0 padevchooser
  paman paprefs pavucontrol pavumeter pulseaudio pulseaudio-esound-compat pulseaudio-module-gconf pulseaudio-module-udev pulseaudio-module-x11 pulseaudio-module-zeroconf pulseaudio-utils
The following packages will be DOWNGRADED:
  libpulse0
0 upgraded, 0 newly installed, 1 downgraded, 26 to remove and 5 not upgraded.
Need to get 234kB of archives.
After this operation, 18.8MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.


Gah!!  These packages were installed before libpulse 1:0.9.19-0ubuntu4 was upgraded to version 1:0.9.19-0ubuntu4.1, why do they have to be removed?

Or, more to the point,  why wasn't the -dev package updated to depend on the correct non -dev package?  I've been road blocked by this on ANY build-dependencies I've tried to install. It seems like NONE of the -dev packages were updated as part of the software update process.

Other than formatting my drive and reinstalling the base distro, with NO updates EVER, is there a way around this?

If, when it becomes available, I do a dist-upgrade to Lucid, will I then be able to install build-dependencies?

Or, is there a way to force everything back to the versions that were installed from the ISO I used initially?


*) Side note, I've been making themes for the NetBook launcher, and I really need to have non-white text.

---


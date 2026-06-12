---
title: "Desktop/unity does not finish loading frequently"
date: 2011-10-05
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by madjr on 2011-10-05
at least 40% of the time the desktop does not finish loading and all you get is some global menu

attached is pic


edit:
might be this bug:
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859908](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/859908)

---

### Post by ngsupb on 2011-10-05
> **madjr said:**
> at least 40% of the time the desktop does not finish loading and all you get is some global menu

attached is pic

The same issue. Just booted in after the last updates and got an empty desktop. 
Will try to restart.:popcorn:

---

### Post by garvinrick4 on 2011-10-05
I had that same a while back and I went into advanced settings (gnome-tweak-tool) 
and changed my theme back to Radiance from Esco. 
EDIT: Saw a Unity upgrade in my updates today.

---

### Post by garvinrick4 on 2011-10-05
Not same fix and rambled a bit and deleted my ramblings, 3rd cup of coffee within the hour.

---

### Post by madjr on 2011-10-05
> **garvinrick4 said:**
> I had that same a while back and I went into advanced settings (gnome-tweak-tool) 
and changed my theme back to Radiance from Esco. Anyway have not tried all the 
GTK themes nor windows themes but after change never had problem again. Did not investigate
farther than that.

default ambiance theme here

---

### Post by garvinrick4 on 2011-10-05
> default ambiance theme hereNot same fix then,  same exact problem though but again it was a while back.

---

### Post by mc4man on 2011-10-05
I have a different login issue though it does involve 'some' logins, not all.
In this case seen on installs from various daily's starting on 09/27 & continuing with one from yesterday.
[https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054](https://bugs.launchpad.net/ubuntu/+source/lightdm/+bug/863054)

While it's being resolved have gotten tired of it happeneing & have returned to gdm where my logins are fine. You could give that a try..

---

### Post by garvinrick4 on 2011-10-05
Downloaded these today and reproduced same as OP.
Start-Date: 2011-10-05  14:02:15
Commandline: apt-get upgrade
Upgrade: libido3-0.1-0:amd64 (0.3.0-0ubuntu2, 0.3.0-0ubuntu3), unity:amd64 (4.20.0-0ubuntu2, 4.22.0-0ubuntu2), libc-bin:amd64 (2.13-20ubuntu4, 2.13-20ubuntu5), libgnome-desktop-3-2:amd64 (3.2.0-0ubuntu3, 3.2.0-0ubuntu4), gwibber-service-identica:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), gir1.2-gmenu-3.0:amd64 (3.2.0-0ubuntu1, 3.2.0-0ubuntu2), pulseaudio-module-bluetooth:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), libgnome-control-center1:amd64 (3.2.0-0ubuntu4, 3.2.0-0ubuntu5), pulseaudio:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), gnome-settings-daemon:amd64 (3.2.0-0ubuntu4, 3.2.0-0ubuntu5), python-piston-mini-client:amd64 (0.5+bzr45-0ubuntu1, 0.6+bzr48-0ubuntu1), libpython2.7:amd64 (2.7.2-5, 2.7.2-5ubuntu1), unity-common:amd64 (4.20.0-0ubuntu2, 4.22.0-0ubuntu2), gnome-menus:amd64 (3.2.0-0ubuntu1, 3.2.0-0ubuntu2), lightdm:amd64 (1.0.1-0ubuntu1, 1.0.1-0ubuntu3), libunity-core-4.0-4:amd64 (4.20.0-0ubuntu2, 4.22.0-0ubuntu2), logrotate:amd64 (3.7.8-6ubuntu4, 3.7.8-6ubuntu5), gwibber-service-twitter:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), gwibber-service-facebook:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), pulseaudio-module-x11:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), python-apt:amd64 (0.8.0ubuntu8, 0.8.0ubuntu9), usb-creator-gtk:amd64 (0.2.33, 0.2.34), pulseaudio-module-gconf:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), python-apt-common:amd64 (0.8.0ubuntu8, 0.8.0ubuntu9), software-center:amd64 (5.0, 5.0.1.2), libdbus1.0-cil:amd64 (0.7.0-3ubuntu1, 0.7.0-4), python2.7:amd64 (2.7.2-5, 2.7.2-5ubuntu1), libgnome-menu-3-0:amd64 (3.2.0-0ubuntu1, 3.2.0-0ubuntu2), gnome-desktop3-data:amd64 (3.2.0-0ubuntu3, 3.2.0-0ubuntu4), pulseaudio-esound-compat:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), multiarch-support:amd64 (2.13-20ubuntu4, 2.13-20ubuntu5), libgwibber2:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), libpulse-mainloop-glib0:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), unity-services:amd64 (4.20.0-0ubuntu2, 4.22.0-0ubuntu2), gwibber-service:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), bash-completion:amd64 (1.3-1ubuntu5, 1.3-1ubuntu6), usb-creator-common:amd64 (0.2.33, 0.2.34), libc6-dev:amd64 (2.13-20ubuntu4, 2.13-20ubuntu5), apparmor:amd64 (2.7.0~beta1+bzr1774-1ubuntu1, 2.7.0~beta1+bzr1774-1ubuntu2), python2.7-minimal:amd64 (2.7.2-5, 2.7.2-5ubuntu1), liblightdm-gobject-1-0:amd64 (1.0.1-0ubuntu1, 1.0.1-0ubuntu3), openssl:amd64 (1.0.0e-2ubuntu3, 1.0.0e-2ubuntu4), libpulse0:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), gwibber:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), libc-dev-bin:amd64 (2.13-20ubuntu4, 2.13-20ubuntu5), unity-lens-applications:amd64 (0.4.10-0ubuntu2, 0.4.10-0ubuntu3), libc6:amd64 (2.13-20ubuntu4, 2.13-20ubuntu5), libgwibber-gtk2:amd64 (3.2.0-0ubuntu2, 3.2.0.1-0ubuntu1), pulseaudio-utils:amd64 (1.0-0ubuntu1, 1.0-0ubuntu2), libssl1.0.0:amd64 (1.0.0e-2ubuntu3, 1.0.0e-2ubuntu4)
End-Date: 2011-10-05  14:04:54

---

### Post by effenberg0x0 on 2011-10-05
What happens if you switch to VT (using Ctrl+Alt+F1 to F6), login with your username and password and run the following command:
```

DISPLAY=:0.0 /usr/bin/ccsm
```

And then switch back to the desktop with Ctrl+Alt+F7.

If you do see the window for CompizConfig Settings Manager, activate the Unity Plugin, Composite and OpenGL. It might crash while you're doing it because applying changes to cssm is unstable at this point of development. 

Switch back to the VT and run:
```
unity --reset
sudo service lightdm restart
```

Report specific errors and messages you get during this process.

Regards,
Effenberg

---

### Post by cariboo on 2011-10-05
I had the same thing happen earlier today on my netbook a simple:

```
sudo aptitude reinstall unity
```

solved my problem.

---

### Post by garvinrick4 on 2011-10-05
Three reboots after caraboo907's post and reinstall of unity, no instances of problem.

---

### Post by madjr on 2011-10-05
got this error:

```
sudo: aptitude: command not found
```

might take a few hours to confirm it, but do you guys mind mentioning it in the bug report to help the developers close this bug soon.

thanks

---

### Post by garvinrick4 on 2011-10-06
> got this error:sudo: aptitude: command not found

```
sudo apt-get install aptitude
```[Your Debian Aptitude | GarfieldTech]("http://www.garfieldtech.com/blog/your-debian-aptitude")
```
Package: aptitude                        
New: yes
State: installed
Automatically installed: no
Version: 0.6.4-1ubuntu2
Priority: optional
Section: admin
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 7,188 k
Depends: libapt-pkg4.11 (>= 0.8.16~exp5ubuntu1), libboost-iostreams1.46.1 (>=
         1.46.1-1), libc6 (>= 2.4), libcwidget3, libept1, libgcc1 (>= 1:4.1.1),
         libncursesw5 (>= 5.6+20070908), libsigc++-2.0-0c2a (>= 2.0.2),
         libsqlite3-0 (>= 3.6.5), libstdc++6 (>= 4.6), libxapian22
Recommends: sensible-utils, apt-xapian-index, libparse-debianchangelog-perl
Suggests: aptitude-doc-en | aptitude-doc, tasksel, debtags
Conflicts: ia32-apt-get (< 22), ia32-apt-get (< 22), aptitude
Description: terminal-based package manager (terminal interface only)
 aptitude is a package manager with a number of useful features, including: a
 mutt-like syntax for matching packages in a flexible manner, dselect-like
 persistence of user actions, the ability to retrieve and display the Debian
 changelog of most packages, and a command-line mode similar to that of apt-get.
 
 [COLOR=Red]aptitude is also Y2K-compliant, non-fattening, naturally cleansing, and
 housebroken. 
 [/COLOR]
 This package contains a version of aptitude compiled with only the classic
 terminal-based interface (using curses).  For an experimental graphical
 interface, see the package aptitude-gtk.

```

---

### Post by Bimps on 2011-10-06
Having the same problem after running Update Manager and updating all the packages. Tried to file a report when compiz crashed, but apparently it was invalid as some "..amd64..." (sorry don't remember the name) stuff in the report was missing.

I reformatted my "/" partition and reinstalled Beta 2. Loads fine. Updated all 490 packages through Update Manager, and Ubuntu won't load. Only the wallpaper is displayed. Compiz crashed and I was offered to report the problem, and I clicked report. 5 seconds later a window appears telling me the following:

"*The problem cannot be reported*: *This is not a genuine Ubuntu package*"

No software was installed by me after reinstalling. I ran Update Manager immediately after installing Ubuntu.

---

### Post by cariboo on 2011-10-06
> **madjr said:**
> got this error:

```
sudo: aptitude: command not found
```

might take a few hours to confirm it, but do you guys mind mentioning it in the bug report to help the developers close this bug soon.

thanks

Aptitude isn't installed by default, but because you are posting in this sub-forum, I assumed you know what tools are available by default, and what has to be installed after the initial installation. Synaptic is another package that isn't installed by default, but you see many references to it int this sub-forum.

---

### Post by madjr on 2011-10-06
> **cariboo907 said:**
> Aptitude isn't installed by default, but because you are posting in this sub-forum, I assumed you know what tools are available by default, and what has to be installed after the initial installation. Synaptic is another package that isn't installed by default, but you see many references to it int this sub-forum.

hehe i just read rumors, then i go an see and the poor things are not there anymore *sniff*

anyway i havent used an aptitude command in over 2 years! i think aptitude should had been the default because it lets you do all sorts of stuff (including reinstall), specially now that we dont have synaptic installed, but maybe apt-get is probably safer for new users?

---


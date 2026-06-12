---
title: "Lubuntu 11.10 Live"
date: 2011-08-11
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by coover on 2011-08-11
I heard that Lubuntu might be something that would be worthwhile installing, so I downloaded the latest version, placed the .iso on a DVD (it was too big for a CD) and booted live from it. The boot ended at the command line. I do not know the commands ... what do I do now?

---

### Post by mikewhatever on 2011-08-11
You should try the latest stable version, which is Lubuntu 11.04. 11.10 is a development version, it's not ready yet.

---

### Post by uRock on 2011-08-11
Moved to *Ubuntu +1* where the developmental release is discussed.

---

### Post by coover on 2011-08-11
I'll try 11.04.

---

### Post by garvinrick4 on 2011-08-11
```
start lxdm
```
I believe will do it in the Live CD.(wrong see below please)
EDIT: I just booted a 11.04 had to use sudo below is correct code to get a GUI.
```
sudo start lxdm
```

---

### Post by garvinrick4 on 2011-08-11
##While I am here a few packages to get used to in Lubuntu (11.04 image)
```
ubuntu@ubuntu:~$ aptitude show lxdm
Package: lxdm                     
State: installed
Automatically installed: no
Version: 0.3.0-0ubuntu5
Priority: optional
Section: universe/x11
Maintainer: Julien Lavergne <gilir@ubuntu.com>
Uncompressed Size: 963 k
Depends: libc6 (>= 2.4), libcairo2 (>= 1.2.4), libck-connector0 (>= 0.2.1),
         libdbus-1-3 (>= 1.0.2), libgdk-pixbuf2.0-0 (>= 2.22.0), libglib2.0-0
         (>= 2.24.0), libgtk2.0-0 (>= 2.24.0), libpam0g (>= 0.99.7.1),
         libpango1.0-0 (>= 1.14.0), libx11-6, libxcb1, debconf (>= 1.2.9) |
         debconf-2.0, upstart-job, x11-utils | xbase-clients | xmessage,
         lsb-base (>= 3.0-6), gtk2-engines-pixbuf, librsvg2-common,
         libpam-runtime (>= 0.76-14), libpam-modules, iso-codes
Recommends: lxsession (>= 0.4.0), lxde-common, locales-all
Provides: x-display-manager
Description: GUI login manager for LXDE
 lxdm is a lightweight GUI login manager which can be used as a dropped-in
 replacement for GDM or KDM. 

```

```
ubuntu@ubuntu:~$ aptitude show openbox
Package: openbox                  
State: installed
Automatically installed: no
Version: 3.4.11.2-0ubuntu3
Priority: optional
Section: universe/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 1,507 k
Depends: libc6 (>= 2.4), libfontconfig1 (>= 2.8.0), libfreetype6 (>= 2.2.1),
         libglib2.0-0 (>= 2.24.0), libice6 (>= 1:1.0.0), libobparser21,
         libobrender21, libpango1.0-0 (>= 1.14.0), libsm6,
         libstartup-notification0 (>= 0.10), libx11-6, libxau6, libxext6,
         libxft2 (> 2.1.1), libxinerama1, libxml2 (>= 2.7.4), libxrandr2,
         libxrender1
Recommends: openbox-themes
Suggests: obconf, menu, ttf-dejavu, python, libxml2-dev
Conflicts: menu (< 2.1.12)
Provides: x-session-manager, x-window-manager
Description: standards compliant, fast, light-weight, extensible window manager
 Openbox works with your applications, and makes your desktop easier to manage.
 This is because the approach to its development was the opposite of what seems
 to be the general case for window managers.  Openbox was written first to
 comply with standards and to work properly.  Only when that was in place did
 the team turn to the visual interface. 
 
 Openbox is fully functional as a stand-alone working environment, or can be
 used as a drop-in replacement for the default window manager in the GNOME or
 KDE desktop environments. 
 
 Openbox 3 is a completely new breed of window manager.  It is not based upon
 any existing code base, although the visual appearance has been based upon
 that of Blackbox.  Openbox 2 was based on the Blackbox 0.65.0 codebase. 
 
 Some of the things to look for in Openbox are: 
 
 * ICCCM and EWMH compliance! 
 * Very fast 
 * Chainable key bindings 
 * Customizable mouse actions 
 * Window resistance 
 * Multi-head Xinerama support! 
 * Pipe menus
Homepage: http://www.openbox.org

ubuntu@ubuntu:~$ 

```

```
ubuntu@ubuntu:~$ aptitude show lxde
Package: lxde                     
State: not installed
Version: 0.5.0-4ubuntu3
Priority: optional
Section: universe/x11
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 36.9 k
Depends: lxde-core (>= 0.5.0-4ubuntu3), lxappearance (>= 0.4.0), lxinput (>=
         0.1.1), lxsession-edit, lxshortcut, gpicview (>= 0.1.9), lxterminal,
         leafpad, xarchiver, lxrandr, obconf, lxde-icon-theme
Recommends: lxdm | x-display-manager, chromium-browser | iceweasel |
            www-browser, lxmusic, menu-xdg, xserver-xorg, policykit-1-gnome,
            galculator, amixer, scrot
Suggests: lxlauncher, lxtask
Description: Meta-package for the Lightweight X11 Desktop Environment
 LXDE (the Lightweight X11 Desktop Environment) is a new project aimed to
 provide a new desktop environment which is lightweight and fast. 
 
 This package is a metapackage depends on the core components and recommended
 components of the LXDE. It includes lxde-core, lxappearance, lxinput,
 lxsession-edit, lxshortcut, gpicview, lxterminal, lxmusic, leafpad and
 xarchiver. 
 
 If you just want to pick and choose the core components then feel free to
 remove this package.
Homepage: http://lxde.org

ubuntu@ubuntu:~$ 

```

---

### Post by Sworddragon on 2011-08-11
> **coover said:**
> I heard that Lubuntu might be something that would be worthwhile installing, so I downloaded the latest version, placed the .iso on a DVD (it was too big for a CD) and booted live from it. The boot ended at the command line. I do not know the commands ... what do I do now?

Is Lubuntu using LXDM as login manager? If yes this is maybe the problem because lxdm 0.4.0-0ubuntu1 is currently broken.

---

### Post by Catharsis on 2011-08-11
> **Sworddragon said:**
> Is Lubuntu using LXDM as login manager? If yes this is maybe the problem because lxdm 0.4.0-0ubuntu1 is currently broken.

It is? That's very curious because I'm typing this post from it :)

---

### Post by I2k4 on 2011-08-11
Many or most users try Lubuntu, instead of full bore Ubuntu, because of hardware limitations, as in older machines or netbooks.  On that score 11.xx is a big miss.  I tried and rejected 11.04, and returned to 10.10, which is snappy on weak machines.  Just a heads up.

---

### Post by Sworddragon on 2011-08-11
> **Catharsis said:**
> It is? That's very curious because I'm typing this post from it :)

Are you using a GeForce graphics card with nvidia-current? On my system (even a reinstalling) my screen gets black after X starts and switches to LXDM. This happens even in VirtualBox.

---

### Post by Catharsis on 2011-08-11
> **Sworddragon said:**
> Are you using a GeForce graphics card with nvidia-current? On my system (even a reinstalling) my screen gets black after X starts and switches to LXDM. This happens even in VirtualBox.

Nope, running an Intel 855GM here. Do you have a bug report link for that? I'd like to take a look, if nothing else to stay up-to-date and informed with Lubuntu's development status.

---

### Post by Sworddragon on 2011-08-12
> **Catharsis said:**
> Nope, running an Intel 855GM here. Do you have a bug report link for that? I'd like to take a look, if nothing else to stay up-to-date and informed with Lubuntu's development status.

[https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/823621](https://bugs.launchpad.net/ubuntu/+source/lxdm/+bug/823621)

Maybe this is a bug that triggers only on a special condition. LXDM 0.4.1 was a few days after 0.4.0 released but it is not in the repository now. Maybe this version will fix the problem. At least I can stay on LXDM 0.3.0 as a workaround.

---

### Post by kansasnoob on 2011-08-12
I've found it best to start the Lubuntu DE with one of the following two commands (if X fails to start on it's own):

```
sudo service lxdm start
```

Or:

```
sudo /etc/init.d/lxdm restart
```

If using the live CD/DVD/USB I think the proper "username" is **ubuntu** rather than **lubuntu** ATM, and you'd of course just leave the password blank :)

There had been some discussion on the mailing list about switching to lightdm. If the Lubuntu devs decide to do that I'd expect to see it by the first Oneiric beta.

---


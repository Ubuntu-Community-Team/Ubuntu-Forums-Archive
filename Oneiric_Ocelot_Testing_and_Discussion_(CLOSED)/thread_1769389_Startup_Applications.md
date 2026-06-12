---
title: "Startup Applications"
date: 2011-05-27
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by sparker256 on 2011-05-27
I have installed from a daily live build and seem to be missing the "Startup Applications". Should this be installed and if so how do I install it.

Thanks Bill

---

### Post by garvinrick4 on 2011-05-27
windows key/a type in "main menu" go to System/preferences/startup applications and check mark it.
Main Menu is called "alacarte"
Package: alacarte                        
State: installed
Automatically installed: no
Version: 0.13.2-2ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 352 k
Depends: python (>= 2.4), python-support (>= 0.90.0), python-gtk2 (>= 2.13.0),
         python-gmenu (>= 2.27.92), gnome-menus (>= 2.27.92), python-gobject (>=
         2.15.1)
Recommends: gnome-panel
Conflicts: smeg (< 0.8-0ubuntu1)
Replaces: smeg
Provides: smeg
Description: easy GNOME menu editing tool
 Alacarte is an easy-to-use menu editor for GNOME that can add and edit new
 entries and menus. It works with the freedesktop.org menu specification and
 should work with any desktop environment that uses the spec.

---

### Post by sparker256 on 2011-05-28
> **garvinrick4 said:**
> windows key/a type in "main menu" go to System/preferences/startup applications and check mark it.
Main Menu is called "alacarte"
Package: alacarte                        
State: installed
Automatically installed: no
Version: 0.13.2-2ubuntu1
Priority: optional
Section: utils
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Uncompressed Size: 352 k
Depends: python (>= 2.4), python-support (>= 0.90.0), python-gtk2 (>= 2.13.0),
         python-gmenu (>= 2.27.92), gnome-menus (>= 2.27.92), python-gobject (>=
         2.15.1)
Recommends: gnome-panel
Conflicts: smeg (< 0.8-0ubuntu1)
Replaces: smeg
Provides: smeg
Description: easy GNOME menu editing tool
 Alacarte is an easy-to-use menu editor for GNOME that can add and edit new
 entries and menus. It works with the freedesktop.org menu specification and
 should work with any desktop environment that uses the spec.

After it started I remembered that I had used "main menu" before but did not think that was the issue. Thanks for the quick response.

Bill

---

### Post by VinDSL on 2011-05-29
I installed my 'Startup Applications Preferences' in the Launcher.

Easier to get at...  ;)


[INDENT](Click to expand)

[[IMG]http://vindsl.com/images/vindsl-desktop-29-may-2011(600x480).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-29-may-2011.png")[/INDENT]

---

### Post by MacUntu on 2011-05-29
gnome-session-properties - working fine here.

---

### Post by ubername on 2011-05-30
Why doesn't the unity applications searcher find 'Startup Applications' or 'gnome-sessions-property'? (i.e., if I type 'start' in the unity search bar, I get some options, e.g. 'Startup disk creator' but not 'Startup applications')
On Edit - Well, it does now find it, having checked the option on 'main menu', but I swear it didn't before!(and it still finds it after unchecking it in main menu.)

---

### Post by MacUntu on 2011-05-30
Because /usr/share/applications/session-properties.desktop contains the line NoDisplay=true. Feel free to report a bug against gnome-session-common.

---

### Post by ubername on 2011-05-30
> **MacUntu said:**
> Because /usr/share/applications/session-properties.desktop contains the line NoDisplay=true. Feel free to report a bug against gnome-session-common.
Interesting. Any clues why it now shows it, even though /usr/share/applications/session-properties.desktop still contains the line NoDisplay=true?

---

### Post by MacUntu on 2011-05-30
It's been changed deliberately: [https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-startup-applications](https://blueprints.launchpad.net/ubuntu/+spec/desktop-o-startup-applications)

---


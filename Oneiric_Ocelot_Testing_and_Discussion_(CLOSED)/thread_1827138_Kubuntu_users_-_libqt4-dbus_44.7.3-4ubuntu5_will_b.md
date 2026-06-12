---
title: "Kubuntu users - libqt4-dbus 4:4.7.3-4ubuntu5 will break your system"
date: 2011-08-17
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by tghe-retford on 2011-08-17
Just upgraded via aptitude safe-upgrade and libqt4-dbus 4:4.7.3-4ubuntu5 will cause D-Bus to fail and you'll be stuck at a command line. May be worth holding updates if you value not being stuck at a said command line or need a working desktop, until it is fixed.

---

### Post by Harry33 on 2011-08-17
> **tghe-retford said:**
> Just upgraded via aptitude safe-upgrade and libqt4-dbus 4:4.7.3-4ubuntu5 will cause D-Bus to fail and you'll be stuck at a command line. May be worth holding updates if you value not being stuck at a said command line or need a working desktop, until it is fixed.

At least in Ubuntu (Gnome3) vlc (which depends on that libqt4-dbus) works OK with it.

---

### Post by tghe-retford on 2011-08-17
> **Harry33 said:**
> At least in Ubuntu (Gnome3) vlc (which depends on that libqt4-dbus) works OK with it.
On my system, the message comes up when X starts, KDM appears, but login fails and you're kicked back to the KDM login screen. Your only option from there is to go back to a virtual terminal to downgrade the package.

Bug report: [https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/825689](https://bugs.launchpad.net/ubuntu/+source/qt4-x11/+bug/825689)

Workaround: Install qt4-dev-tools for now...

---

### Post by buzzmandt on 2011-08-17
this buggers todays live cd as well 8-17

---

### Post by seenthelite on 2011-08-17
> **tghe-retford said:**
> Just upgraded via aptitude safe-upgrade and libqt4-dbus 4:4.7.3-4ubuntu5 will cause D-Bus to fail and you'll be stuck at a command line. May be worth holding updates if you value not being stuck at a said command line or need a working desktop, until it is fixed.
  
 Thank you.

---

### Post by inportb on 2011-08-17
Ha. Fluxbox to the rescue :x

---

### Post by iClouseau88 on 2011-08-17
Hi,

After KDM login, my screen shows:

```

"Could not start dbus. Can you call qdbus?"

```

Then I logged in via the terminal and typed qdbus.

```

"qdbus is not currently installed.  You can install it via sudo apt-get install libqt4-dbus"

```

I forgot that libqt4-dbus is already installed in yesterday's update, so tried to install it via the above command. The screen now shows that libqt4-dbus is already installed.

Looks like a dilemma, until I found that the problem is described in launchpad.net, Bug#[COLOR="Blue"]827815[/COLOR].

In my case, the work-around is to install [COLOR="Blue"]qt4-dev-tools[/COLOR]. The solution to install qt4-x11 as described in launchpad.net for Bug#827815 does not work for me, since the terminal shows "unable to locate package qt4-x11".

---

### Post by Coplen on 2011-08-18
Install qt4-dev-tools

---

### Post by zenarcher on 2011-08-18
Thanks for the suggestion.  That fixed the issue for me.

Regards,
zenarcher

---

### Post by tghe-retford on 2011-08-18
libqt4-dbus 4:4.7.3-4ubuntu6 has now hit the repositories with a new package, 'qdbus', installed alongside when using aptitude safe-upgrade. The qt4-dev-tools workaround is no longer needed. This bug is now fixed.

---

### Post by buzzmandt on 2011-08-18
I can confirm this is fixed, I waited till today to upgrade to get the dbus proper.

However, please note, if you use apt-get for upgrades you must use dist-upgrade to get it.

---

### Post by iClouseau88 on 2011-08-18
My safe approach:

1. Because "muon" is error-prone, I prefer "synaptic":

```

sudo apt-get install synaptic

```

I purposely use "apt-get" instead of "aptitude" during alpha stage, for safety reasons.

2. Looked for, found and upgraded "libqt4-dbus" to the latest version 4:4.7.3-4ubuntu6 all using synaptic. Several packages are upgraded and "qdbus" is installed as part of the process.

:D

---


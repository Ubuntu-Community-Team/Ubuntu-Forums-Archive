---
title: "Suspends Randomly"
date: 2011-12-11
forum: New to Ubuntu
---

### Post by cowlip1 on 2011-12-11
Hi,
I opened a bug about this but didn't get any responses.  Since upgrading to Natty, my system will suspend after about 15 minutes, ignoring whatever Power option I set (e.g., don't suspend).  

[https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/901898](https://bugs.launchpad.net/ubuntu/+source/gnome-settings-daemon/+bug/901898)

Here are my gconf settings in text:

gsettings list-recursively org.gnome.settings-daemon.plugins.power
org.gnome.settings-daemon.plugins.power active true
org.gnome.settings-daemon.plugins.power button-hibernate 'hibernate'
org.gnome.settings-daemon.plugins.power button-power 'interactive'
org.gnome.settings-daemon.plugins.power button-sleep 'suspend'
org.gnome.settings-daemon.plugins.power button-suspend 'suspend'
org.gnome.settings-daemon.plugins.power critical-battery-action 'hibernate'
org.gnome.settings-daemon.plugins.power idle-brightness 30
org.gnome.settings-daemon.plugins.power idle-dim-ac false
org.gnome.settings-daemon.plugins.power idle-dim-battery true
org.gnome.settings-daemon.plugins.power idle-dim-time 10
org.gnome.settings-daemon.plugins.power lid-close-ac-action 'suspend'
org.gnome.settings-daemon.plugins.power lid-close-battery-action 'suspend'
org.gnome.settings-daemon.plugins.power notify-perhaps-recall true
org.gnome.settings-daemon.plugins.power percentage-action 2
org.gnome.settings-daemon.plugins.power percentage-critical 3
org.gnome.settings-daemon.plugins.power percentage-low 10
org.gnome.settings-daemon.plugins.power priority 1
org.gnome.settings-daemon.plugins.power sleep-display-ac 900
org.gnome.settings-daemon.plugins.power sleep-display-battery 900
org.gnome.settings-daemon.plugins.power sleep-inactive-ac false
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-timeout 0
org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'suspend'
org.gnome.settings-daemon.plugins.power sleep-inactive-battery true
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-timeout 0
org.gnome.settings-daemon.plugins.power sleep-inactive-battery-type 'suspend'
org.gnome.settings-daemon.plugins.power time-action 120
org.gnome.settings-daemon.plugins.power time-critical 300
org.gnome.settings-daemon.plugins.power time-low 1200
org.gnome.settings-daemon.plugins.power use-time-for-policy true

---

### Post by editheraven on 2011-12-11
try

```

dbus-launch gsettings set org.gnome.settings-daemon.plugins.power sleep-inactive-ac-type 'nothing'

```

---

### Post by cowlip1 on 2011-12-11
Thx, we'll see how that goes.  If I want to specify a certain time (other than that strange 15 minute sleep that I don't want), can I insert that value in that key as well?

---

### Post by editheraven on 2011-12-11
Why don't you just use power management from main system menu>preferences or gconf-editor?

---

### Post by cowlip1 on 2011-12-11
Hi,

It ignores the setting in System Preferences, please see the bug I linked above.

Also sadly the tweak didn't work :( Still suspending after 15 minutes.

---


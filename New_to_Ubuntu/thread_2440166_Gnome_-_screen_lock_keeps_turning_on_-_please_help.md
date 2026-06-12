---
title: "Gnome - screen lock keeps turning on - please help."
date: 2020-04-06
forum: New to Ubuntu
---

### Post by bjohas on 2020-04-06
Hello all, 

I'm trying again in this forum as I didn't get a reponse - this is really killing me, please help!

I have disabled all screen locking / dimming / power saving: both from Settings, but also checking gnomesettings on the commandline. 


[LIST]
[*]gsettings get org.gnome.desktop.screensaver lock-delay
[*]uint32 0
[*]gsettings get org.gnome.desktop.screensaver lock-enabled
[*]false
[*]gsettings get org.gnome.desktop.session idle-delay
[*]uint32 0
[*]gsettings get org.gnome.settings-daemon.plugins.power idle-dim
[*]false
[*]gsettings get com.ubuntu.touch.system dim-timeout
[*]uint32 3600
[*]gsettings get org.gnome.settings-daemon.plugins.power	sleep-inactive-ac-timeout
[*]3600
[*]gsettings get org.gnome.settings-daemon.plugins.power	sleep-inactive-ac-type
[*]'nothing'
[*]gsettings get org.gnome.settings-daemon.plugins.power	sleep-inactive-battery-timeout
[*]7200
[*]gsettings get org.gnome.settings-daemon.plugins.power	sleep-inactive-battery-type
[*]'nothing'
[/LIST]

Nevertheless Ubuntu 19.10 / Gnome keeps randomly locking screen. During some hours it'll happen e.g. 5-10 times, sometimes consecutively so I have to keep having an unlocking battle with gnome, then it does not happen at all for another hour.


This is really disruptive ...... and killing me ...... please please help!
[URL="https://ubuntuforums.org/showthread.php?t=2439791"]
https://ubuntuforums.org/showthread.php?t=2439791[/URL]

---

### Post by bjohas on 2020-04-19
I wasn't able to find a fix via the Ubuntu / gnome-settings, but it did occur to me that I could uninstall the screensaver itself:
```
sudo apt remove gnome-screensaver
```
While that has completely disabled the screen saver, it's also definitely stopped the accidental locks. (Locking by closing laptop lid and via keyboard shortcut etc still works.)

---


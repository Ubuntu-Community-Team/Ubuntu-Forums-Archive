---
title: "Turn off lock screen"
date: 2017-04-28
forum: New to Ubuntu
---

### Post by bob brazie on 2017-04-28
New to ubuntu gnome not ubuntu.
Is there a way to turn off and not use the lock screen?
I would like it to wake from the blank screen on my set time and see the desktop.
I have it set to wake and not ask for a password but I have to take the additional step and move the lock screen to see my desktop.
I am the only person using this machine and have no worries about any data loss. 
I did a Google search at did not find anything helpful with this question.
Thanks in advance. Bob.

---

### Post by LastDino on 2017-04-28
Okay, it would help if you could tell your Ubuntu version..

But does this not work?


[LIST=1]
[*]Start the application "Settings"
[*]Choose "Privacy" under the "Personal" heading
[*]Choose "Screen Lock"
[*]Toggle "Automatic Screen Lock" from the default "ON" to "OFF"
[/LIST]

---

### Post by bob brazie on 2017-04-28
I did set it to off but the lock screen is still shown when I wake it up after the time I set in power/blank screen.

---

### Post by LastDino on 2017-04-28
This used to work on older version not sure if it will work for u as u have not given version

> gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'

> gsettings set org.gnome.desktop.screensaver ubuntu-lock-on-suspend 'false'

---

### Post by bob brazie on 2017-04-28
Sorry. The new version 17.04.
I am using it as my main system now in anticipation of it being the standard next LTS release. So far I like it but not sure if it is "better".

---

### Post by LastDino on 2017-04-28
I have not yet tried 17.04 yet, but might as well give a try to those commands.

---

### Post by #&amp;thj^% on 2017-04-28
Try this one **"gnome-shell-extension-caffeine"**
> 
This GNOME Shell extension provides an icon which can be toggled to
inhibit the actions that would normally be taken when the system is idle,
including screen locking, screensaver and automatic suspend. By default
it also inhibits idle actions while any window is full-screen, and it can
be configured to inhibit idle actions while user-specified applications
have any window open.

Please note that each user will need to enable the extension manually, for
example using gnome-tweak-tool."

```
apt policy gnome-shell-extension-caffeine
gnome-shell-extension-caffeine:
  Installed: 0~git20161228-1ubuntu2
  Candidate: 0~git20161228-1ubuntu2
  Version table:
 *** 0~git20161228-1ubuntu2 500
        500 http://us.archive.ubuntu.com/ubuntu zesty/universe amd64 Packages
        500 http://us.archive.ubuntu.com/ubuntu zesty/universe i386 Packages
        100 /var/lib/dpkg/status


```

---

### Post by Dennis N on 2017-04-28
On my system (Ubuntu Gnome 17.04), the lock screen doesn't display if I select:

**Tweak tool > Desktop > Lock Screen > Mode > None**.

With this setting, it just goes blank when locked.

---

### Post by #&amp;thj^% on 2017-04-28
Yep same here:
```
echo $DESKTOP_SESSION
gnome-wayland


```
But the caffeine extension works a treat.
After installing it you will have to restart your session via:
```
killall -HUP gnome-shell

```
Then open Gnome-Tweak and enable caffeine. 
Then toggle the icon.

---


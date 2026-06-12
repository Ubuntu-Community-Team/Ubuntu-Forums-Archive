---
title: "Ubuntu loads and logs in but no icons or menu items"
date: 2013-03-01
forum: New to Ubuntu
---

### Post by cciustn on 2013-03-01
I have been running Ubuntu Desktop for weeks but did some installing of programs today and had some issues loading a video editor. I rebooted and when os was reloaded I am totally missing all icons and menu's. I can get to command line and task manager. 

I found this but " [COLOR=#000000]Use dconf editor Go to org-gnome-desktop-background and tick "Show desktop icons" " cannot get to dconf editor. 

Is this the problem or does any other ideas ?[/COLOR]

---

### Post by DiabolicalClaptrap on 2013-03-01
Sounds like something fudged your desktop environment.
[URL="http://www.tuxgarage.com/2011/05/enable-desktop-cube-in-unity-ubuntu.html"]
[/URL]First, back up your Unity settings through ccsm (sudo apt-get install compizconfig-settings-manager in terminal if you don't have it) by:

Hitting preferences on the left side, then exporting your profile to a directory you can easily get to.

Then try

```
unity --reset
```

when logged in Unity and in a terminal.

---

### Post by Bashing-om on 2013-03-01
The command "unity --reset" is no longer valid in 12.10 and above.

@ 		cciustn ; What version are you runnung ?
[INDENT=2]Try'n to help

[/INDENT]

---

### Post by cciustn on 2013-03-01
thanks all for the replies, I got it with the following fix, it was a pain to fix. 

Make sure the 'unity' package is installed

For those who were missing the 'ubuntu-desktop' metapackage in a  pre-Unity version of Ubuntu for some reason, the 'unity' package didn't  get installed during the upgrade. So we need to check if it's installed:

dpkg -l | grep unity

If 'unity' is listed in the output, proceed with the next step. If not, install it (and its dependencies):

sudo apt-get update
sudo apt-get install unity

Also, if you don't have any sound reason against that, make sure the  'ubuntu-desktop' metapackage is installed as well, to prevent this kind  of situation in the future. Similar to the above step, check if it's  installed:

dpkg -l | grep ubuntu-desktop

If 'ubuntu-desktop' is not listed, install it:

sudo apt-get update
sudo apt-get install ubuntu-desktop

---


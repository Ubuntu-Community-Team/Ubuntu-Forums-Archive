---
title: "How to hide &quot;home&quot; folder from showing up on my desktop"
date: 2022-05-03
forum: New to Ubuntu
---

### Post by jmichaels29 on 2022-05-03
Ubuntu 20.02 lts clean install

The "files" folder in the dash does the job already.   So, how do I hide the "home" folder from being on the desktop ?

---

### Post by #&amp;thj^% on 2022-05-03
open terminal
```
gsettings set org.gnome.shell.extensions.desktop-icons show-home false
```
should disappear right away

---

### Post by jmichaels29 on 2022-05-03
hmmm, what did I type wrong please sir

screenshot attached

p.s. Gnome Tweaks worked to do it with in Ubuntu 20.x lts, but gnome tweaks is different with 22.x lts installed (has not "extensions" in 22.x lts)....   I'm still willing to use terminal to do this if I can type the right thing in....

---

### Post by #&amp;thj^% on 2022-05-03
Nothing you did wrong, try instead:
```
gsettings set org.gnome.nautilus.desktop home-icon-visible false
```

---

### Post by jmichaels29 on 2022-05-03
hmmmm, must be a typo somewhere...
I'll keep trying as long as you keep sending me command lines...

screenshot attached

---

### Post by #&amp;thj^% on 2022-05-03
ok this is a typo "Ubuntu 20.02 lts" right??
your on 22.04 now.
show this please:
```
echo $DESKTOP_SESSION
```
One more for good practice:
```
env|grep XDG
```

---

### Post by jmichaels29 on 2022-05-03
yea, I'm on the latest lts release - 22.04  lts

sorry

OS screenshot attached

sorry - I need to learn how to enter code tags

michael@michael-HP-EliteDesk-800-G1-SFF:~$ echo $DESKTOP_SESSION
ubuntu
michael@michael-HP-EliteDesk-800-G1-SFF:~$ env|grep XDG
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg
XDG_MENU_PREFIX=gnome-
XDG_SESSION_DESKTOP=ubuntu
XDG_SESSION_TYPE=wayland
XDG_CURRENT_DESKTOP=ubuntu:GNOME
XDG_SESSION_CLASS=user
XDG_RUNTIME_DIR=/run/user/1000
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share/:/usr/share/:/var/lib/snapd/desktop
michael@michael-HP-EliteDesk-800-G1-SFF:~$

---

### Post by #&amp;thj^% on 2022-05-03
I have to think on this one>>"XDG_SESSION_TYPE=wayland"
give me a beat to test some things.
what shows from this:
```
apt policy gnome-shell-extension-prefs
```

---

### Post by jmichaels29 on 2022-05-03
I did a clean install - formatted the HD when doing so.

michael@michael-HP-EliteDesk-800-G1-SFF:~$ apt policy gnome-shell-extension-prefs
gnome-shell-extension-prefs:
  Installed: (none)
  Candidate: 42.0-2ubuntu1
  Version table:
     42.0-2ubuntu1 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) jammy/universe amd64 Packages
michael@michael-HP-EliteDesk-800-G1-SFF:~$

---

### Post by #&amp;thj^% on 2022-05-03
There you go, please run:
```
sudo apt install gnome-shell-extension-prefs
```
after it installed you'll be able to find it your menu "All Applications"
you'll find what you need there.

---

### Post by jmichaels29 on 2022-05-03
I'm curious if this is the same as "extensions" in the software center.  With it, I'm able to remove the home folder from the desktop; however, I'm unable to create a folder on the desktop or move a folder to the desktop. 
Just curious...

---

### Post by #&amp;thj^% on 2022-05-03
> **jmichaels29 said:**
> I'm curious if this is the same as "extensions" in the software center.  
Just curious...
IJDK
you may have disabled the wrong setting: IE disable desktop icons, vs hide Home folder.
install it if your not happy, uninstall it easy enough.

---

### Post by jmichaels29 on 2022-05-03
Well, if they're the same thing, this is the only options.
Turning off the 2nd switch down, does remove the "home" folder from the desktop; however, it also makes it impossible to to create a folder on the desktop or move a folder to the desktop from another folder inside files.

---

### Post by #&amp;thj^% on 2022-05-03
This is what I had .
see screenshot
FWIW I have not used a software center or manager for years.

---

### Post by Dennis N on 2022-05-03
> **jmichaels29 said:**
> Ubuntu 20.02 lts clean install

The "files" folder in the dash does the job already.   So, how do I hide the "home" folder from being on the desktop ?

Just use the new Settings dialog. Look under "Appearance". Flip the switch shown by the arrow to OFF (mine is off). See below.

---

### Post by jmichaels29 on 2022-05-03
oops.  I toggled the last option, which made my dock disappear.  Now all I have is a home folder on the desktop.  Dlon't know how to re-launch "extensions" to toggle and turn my dock back on....

OOOPS!

I can ctrl+alt+t to cause my terminal to open.  What would I type into terminal to cause the extensions app to launch  (?)

---

### Post by jmichaels29 on 2022-05-03
ok, I solved the problem.  Found the extensions program in the bin folder and right clicked it to run it

now that's solved...


for future reference though - how do I 1) find and 2) run a program from just terminal

---

### Post by grahammechanical on 2022-05-03
I have not seen anything in 20.04 system settings that allows us to remove the home folder icon from the desktop. But we can do it in 22.04 system setting>appearance. Click the Show Personal folder icon.

In 22.04 the home folder icon is on the bottom right of the screen. In system settings>appearance we get four options to set the position of new desktop icons.

Regards

---

### Post by Dennis N on 2022-05-03
> **jmichaels29 said:**
> I'm curious if this is the same as "extensions" in the software center.  With it, I'm able to remove the home folder from the desktop; however, I'm unable to create a folder on the desktop or move a folder to the desktop. 
Just curious...

Another way, is just right-click on the desktop and select "Desktop Icons Settings" (see attachment) which opens the same dialog as in post #15. See the directions there.

---

### Post by jmichaels29 on 2022-05-03
> **grahammechanical said:**
> I have not seen anything in 20.04 system settings that allows us to remove the home folder icon from the desktop. But we can do it in 22.04 system setting>appearance. Click the Show Personal folder icon.

In 22.04 the home folder icon is on the bottom right of the screen. In system settings>appearance we get four options to set the position of new desktop icons.

Regards

Thanks SO MUCH for your info.!

Also, it can be done in 20.04 with two programs, found in this thread:
[https://ubuntuforums.org/showthread.php?t=2473778](https://ubuntuforums.org/showthread.php?t=2473778)

---

### Post by jmichaels29 on 2022-05-03
> **Dennis N said:**
> Another way, is just right-click on the desktop and select "Desktop Icons Settings" (see attachment) which opens the same dialog as in post #15. See the directions there.

Thanks so much!

---

### Post by Tadaen_Sylvermane on 2022-05-05
No offense to my friends here. I found the setting in exactly 3 seconds by typing home into the search bar of dconf-editor. Nobody suggested this?

Forgive me if I upset someone with this.

---


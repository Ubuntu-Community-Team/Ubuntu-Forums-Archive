---
title: "reinstall nVidia 140M driver in 8.04?"
date: 2008-09-03
forum: New to Ubuntu
---

### Post by lengo on 2008-09-03
I just upgraded from 7.10 to 8.04. What a trip! After much finagling, I finally got my nVidia 140M (on a Lenovo T61) to accept "Normal" mode in Preferences > Appearance > Visual Effects (I want to use Compiz . . . isn't that why everyone uses Linux?! :-) ). I think this was after using EnvyNG to install the drivers. Before that I kept getting the odd situation that the restricted nVidia diver was 'Enabled' but 'Not in use' . . . I found a bug referring to that [Edit: [#216650]("https://bugs.launchpad.net/jockey/+bug/216650")], that appeared to be solved by fixing something called 'jockey'. I tried using Synaptic Package Manager to update 'jockey', but there wasn't any update option. So, being a beginner (an somewhat of an optimist), I uninstalled 'jockey' thinking that when I reinstalled it it would grab the new 'fixed' package. WRONG! That's when things started going really south and I resorted to EnvyNG. And it worked! Compiz bliss! But then, out of the blue, I got an icon up in the right corner (where package update notification is shown) saying that restricted packages needed to be updated . . . I honestly hesitated before upgrading nvidia-glx-new -- honest! -- but figured if Ubuntu was telling me it needed to be upgraded, it needed to be upgraded (after all, it's supposed to be the package managing standard, right?) Well, now everything graphic related is broken . . . On restart (I was prompted to restart) I was informed that my computer would only run in "Low graphics mode"--initially 800x600 and then 640x480 (with NO other options). I got into Synaptic Package Manager and uninstalled everything 'nvidia' (drastic, I know . . . ) and then reinstalled the drivers with EnvyNG. Now I can get 1024x760 (even though the nVidia configuration thingy [Admin > nVidia thingy] accurately recognises my monitor as 1440x900 native), Compiz works, but I really would like to use the native resolution. How best to start over? I'm fairly new to this . . .

---

### Post by Sin@Sin-Sacrifice on 2008-09-03
Have you tried dpkg-reconfigure xserver.xorg From there fill in the blanks for the questions. Reboot... I've come to find that most of the display problems have something to do with either the NVIDIA drivers or xorg.conf... more the latter. Have you recently updated or installed anything?

---

### Post by lengo on 2008-09-04
> **Sin@Sin-Sacrifice said:**
> Have you tried dpkg-reconfigure xserver.xorg From there fill in the blanks for the questions. Reboot... I've come to find that most of the display problems have something to do with either the NVIDIA drivers or xorg.conf... more the latter. Have you recently updated or installed anything?
This is the output of your suggestion:
```
paul@T61-CTO:~$ sudo dpkg-reconfigure xserver.xorg
Package `xserver.xorg' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver.xorg is not installed
```
Now what?:(

---

### Post by lengo on 2008-09-04
I found [this]("http://ubuntuforums.org/showthread.php?t=556822") which indicates that the code line should read:
```
dpkg-reconfigure xserver-xorg
```
'-' rather than '.' between 'xserver' and 'xorg'. I ran it and it took me through what seemed like a keyboard verification process . . . ? Should it have done more? Other? I'm thinking at this point that I need to find a way to save the package updates I've done to removable media (e.g., USB stick; my internet connection is very slow and very 'capped') and reinstall the Heron.

---


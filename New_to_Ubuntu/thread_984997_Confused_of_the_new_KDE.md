---
title: "Confused of the new KDE"
date: 2008-11-17
forum: New to Ubuntu
---

### Post by adudutz on 2008-11-17
I just upgraded my Kubuntu to version 8.10 (from 8.04.1) (an exhausting five-hour upgrade). The problem is, I am really confused of how to manage the packages using Adept (manually), and also when I tried to change settings in the System Settings, I found out that most of the Administrative Mode-only settings (eg. Display driver) are not able to be opened! I've searched for the Administrator button, but it's nowhere to be found. I do not find this problem when I used Kubuntu 8.04.1 using KDE 3.5.

Can anyone help me how to set these things straight? I'm still a n00b to these Kubuntu, Ubuntu, etc, etc things. Please do not ask me to return to KDE 3.5, as there is a slight chance for me to do such thing..

---

### Post by Xiong Chiamiov on 2008-11-27
Were you not using Adept before?  You can always use Synaptic instead, if you prefer.

Systemsettings does not yet have the nifty administrator buttons yet, so you'll need to launch the whole thing as root:
```

kdesudo systemsettings

```
I believe kdesudo should work, but if not, then use gksudo.

---


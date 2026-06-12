---
title: "No system sounds on 14.04 LTS? Is that bug or I screwed up something?"
date: 2014-04-25
forum: New to Ubuntu
---

### Post by LastDino on 2014-04-25
I did fresh install of Xubuntu 14.04 LTS and even though sound notification icon is there, and it's working with songs and videos there are no system sounds. 

I haven't un-installed anything except Mousepad from default set-up. I'm not really knowledgeable about commands tbh as I just recently shifted from XP to Linux, so I don't really know where to look for this as there seems to be no visible indicator/option to tell me system sounds are on or not. (at least I didn't manage to find one)

I tried to look this up on google but didn't find any updated info.
Any and all help is appreciated ^^

---

### Post by LastDino on 2014-04-26
Sorry for double post but I wanted to bump this thread ;D

I've managed to get Log-in sound working by following this thread> [http://ubuntuforums.org/showthread.php?t=1869787&page=2](http://ubuntuforums.org/showthread.php?t=1869787&page=2)

But unfortunately even after doing everything mentioned in the thread no other system sounds are working. :/

---

### Post by Toz on 2014-04-26
> **Goten0007 said:**
> Sorry for double post but I wanted to bump this thread ;D

I've managed to get Log-in sound working by following this thread> [http://ubuntuforums.org/showthread.php?t=1869787&page=2](http://ubuntuforums.org/showthread.php?t=1869787&page=2)

But unfortunately even after doing everything mentioned in the thread no other system sounds are working. :/
Event sounds do work in Xubuntu 14.04. Lets confirm your settings. Can you post back the results for the following:
```
xfconf-query -c xsettings -p /Net/SoundThemeName
env | grep GTK_MODULE
ls /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
which canberra-gtk-play
```

EDIT: Sorry, 2 more:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
```

---

### Post by LastDino on 2014-04-26
> **Toz said:**
> Event sounds do work in Xubuntu 14.04. Lets confirm your settings. Can you post back the results for the following:
```
xfconf-query -c xsettings -p /Net/SoundThemeName
env | grep GTK_MODULE
ls /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
which canberra-gtk-play
```



EDIT: Sorry, 2 more:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
```

I know, I did install it some other PC and its working fine there. That's why I made a thread before giving shot to older thread since it was aimed at older version of Xubuntu.

Result of 1st set.
> glen@Maxwell:~$ env | grep GTK_MODULE
GTK_MODULES=canberra-gtk-module:canberra-gtk-module
glen@Maxwell:~$ ls /usr/share/sounds/$(xfconf-query -c xsettings -p /Net/SoundThemeName)/stereo
bell.ogg               dialog-information.ogg   phone-outgoing-calling.ogg
button-pressed.ogg     dialog-question.ogg      service-login.ogg
button-toggle-off.ogg  dialog-warning.ogg       service-logout.ogg
button-toggle-on.ogg   message-new-instant.ogg  system-ready.ogg
desktop-login.ogg      message.ogg              window-slide.ogg
desktop-logout.ogg     phone-incoming-call.ogg
dialog-error.ogg       phone-outgoing-busy.ogg


Reply of 2nd
> glen@Maxwell:~$ xfconf-query -c xsettings -p /Net/EnableEventSounds
false


And
> glen@Maxwell:~$ xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds
false


I can see that this is where problem is (probably), but I've no idea as to how to change its value to ''True''(?).

Thanks for prompt reply.


Edit: Nvm, I found it. 

I'll let you the result after restart ^^

---

### Post by Toz on 2014-04-26
Using a gui, Settings Manager >> Appearance >> Settings tab.

From a command line:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds -s True
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds -s True
```

---

### Post by LastDino on 2014-04-26
> **Toz said:**
> Using a gui, Settings Manager >> Appearance >> Settings tab.

From a command line:
```
xfconf-query -c xsettings -p /Net/EnableEventSounds -s True
xfconf-query -c xsettings -p /Net/EnableInputFeedbackSounds -s True
```

Yes, its working perfectly now ^^

Just few questions.
1.Since I followed other thread and created those 2 files and installed some stuff mentioned in there, is it going to be problem or should I let it be?
2.There is no sound for mouse clicks and opening windows? Its not a issue but I would like to know anyhow.

Thank you again and sorry for being silly :oops:

---

### Post by Toz on 2014-04-26
> **Goten0007 said:**
> Yes, its working perfectly now ^^
Glad to hear.

> Just few questions.
1.Since I followed other thread and created those 2 files and installed some stuff mentioned in there, is it going to be problem or should I let it be?
The instructions in the other thread are still valid, should be no problem.
> 2.There is no sound for mouse clicks and opening windows? Its not a issue but I would like to know anyhow.
The important thing to remember here is:
1. The freedesktop sound spec (that Xfce is modelled after via libcanberra implementation) only supports some sound events:
> 
    /*
       We generate these sounds:

       dialog-error
       dialog-warning
       dialog-information
       dialog-question
       window-new
       window-close
       window-minimized
       window-unminimized
       window-maximized
       window-unmaximized
       notebook-tab-changed
       dialog-ok
       dialog-cancel
       item-selected
       link-pressed
       link-released
       button-pressed
       button-released
       menu-click
       button-toggle-on
       button-toggle-off
       menu-popup
       menu-popdown
       menu-replace
       tooltip-popup
       tooltip-popdown
       drag-start
       drag-accept
       drag-fail
       expander-toggle-on
       expander-toggle-off

       TODO:
       scroll-xxx
       window-switch
       window-resize-xxx
       window-move-xxx

    */
2. You need to have sound files by those names in your theme's stereo directory for them to be used.

---

### Post by LastDino on 2014-04-26
> **Toz said:**
> Glad to hear.


The instructions in the other thread are still valid, should be no problem.

The important thing to remember here is:
1. The freedesktop sound spec (that Xfce is modelled after via libcanberra implementation) only supports some sound events:

2. You need to have sound files by those names in your theme's stereo directory for them to be used.

Thank you very much again for the info!

---


---
title: "[SOLVED] how can i install realplayer and windows media player?"
date: 2008-09-19
forum: New to Ubuntu
---

### Post by natedogg23 on 2008-09-19
sudo apt-get install cant find them when i try. is there a site or something that will tell me more terminal commands? thats the only one i know

---

### Post by kellemes on 2008-09-19
> **natedogg23 said:**
> sudo apt-get install cant find them when i try. is there a site or something that will tell me more terminal commands? thats the only one i know

[Installing Realplayer]("https://help.ubuntu.com/community/RealPlayerInstallationMethods")
Installing Windows media player? I expect this to be a joke..

---

### Post by Teamgeist on 2008-09-19
[www.medibuntu.org](www.medibuntu.org)

---

### Post by philinux on 2008-09-19
> **Teamgeist said:**
> [www.medibuntu.org]("http://www.medibuntu.org")

Only for Intrepid though, you can download direct from them.

---

### Post by waspbr on 2008-09-19
why would u want to install those, there many open source media players in linux to choose from.

---

### Post by natedogg23 on 2008-09-19
> **kellemes said:**
> [Installing Realplayer]("https://help.ubuntu.com/community/RealPlayerInstallationMethods")
Installing Windows media player? I expect this to be a joke..

unfortunately not. i dont want it but some sites want it to watch sports streams live and totem wont do it

---

### Post by bobnutfield on 2008-09-19
There is an Mplayer plugin for Firefox.  I believe that will play .wmf files.  It may be hard to locate but there are instructions here:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

### Post by anotherdisciple on 2008-09-19
> **natedogg23 said:**
> unfortunately not. i dont want it but some sites want it to watch sports streams live and totem wont do it


I would install vlc mozilla-vlc-plugin and ubuntu-restricted-extras


I prefer vlc over mplayer, but that's just me.

---

### Post by bobnutfield on 2008-09-19
> **anotherdisciple said:**
> I would install vlc mozilla-vlc-plugin and ubuntu-restricted-extras


I prefer vlc over mplayer, but that's just me.

+1 for VLC.  I prefer it as well, and I believe it will play as many or more than Mplayer.  But I recommended Mplayer as it is the most often recommended.

---

### Post by natedogg23 on 2008-09-19
i have vlc it just doesnt want to work 90% of the time. not gonne even mess with real or win media tho. i dont know what im doing quite yet but its only my 1st week. thanks for all your help

---

### Post by halitech on 2008-09-19
best way to learn is jump in and get your feet wet :) 

as anotherdisciple suggested, install vlc, mozilla-vlc-plugin and ubuntu-restricted-extras

just open a terminal and type in```
sudo apt-get install vlc mozilla-vlc-plugin ubuntu-restricted-extras
```

---

### Post by AlanR8 on 2008-09-19
There is NO need to install RealPlayer and Windows Media Player.

There are many "How to" guides out there explaining how to get Linux to play the above media, and to save you some time, here's the one I always follow, I picked it up here so thanks and respect to the author!

> Open Terminal and type:
Code:

sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list

to add the Hardy Medibuntu repository to your software sources


Code:

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

to add the GPG key for Medibuntu


Code:

sudo apt-get install w32codecs libdvdcss2

to install all necessary media codecs and allowing you to play dvds



That done, also install flashplugin-nonfree and mozilla-mplayer via your package manager.

You will now be able to play videos from Utube, BBC streaming content, If in the UK and just about everything else!

Add VLC into the equation and you've got a sweet system!

---

### Post by oldos2er on 2008-09-19
You can download Realplayer from [http://www.real.com/linux](http://www.real.com/linux) ; and there is a version in the Medibuntu repositories as well, as was posted. You could check the Wine forum for info on running Win* Media Player under Ubuntu, whether or not it can be run under Linux, I don't know.

---


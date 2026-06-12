---
title: "Getting started - installing vlc and libre office"
date: 2014-01-04
forum: New to Ubuntu
---

### Post by rachel-g41 on 2014-01-04
Good morning all

Having been 'trialling' lubuntu for weeks with an SD flash, I've at last had my HD replaced and lubuntu 13.10 installed on it. So far I'm very happy and have managed to install a few add-ons and apps with no problem. However I'm stuck with vlc and libre office-

Libreoffice appears in the software centre. I add it to the apps basket, but it doesn't appear there to click for install. I left it for a while and came back to it (thinking maybe office is a big package and needs time) but it's still not ther

As for vlc - which doesn't appear in synaptic: I did the sudo apt-get update, then sudo apt-get install vlc but it's not found. So I went to the vlc page and tried to download it from there but I am asked to choose a package to open the link with. I guess it's the gdebi package manager but I can't see how to browse to it from the window that opens.

Any help much appreciated.

---

### Post by Bucky Ball on 2014-01-04
Try Libreoffice via Synaptics. As for VLC, that's odd. I'll have a bit of a look ...

---

### Post by rachel-g41 on 2014-01-04
Many thanks, I now have libreoffice! Am still working on the vlc.

---

### Post by The Cog on 2014-01-04
vlc is listed in my synaptic, in the Graphics (universe) section. I'm on Xubuntu13.10 which uses the same repositories so it should be there for you too. Do you get any errors when you do apt-get update?

---

### Post by rachel-g41 on 2014-01-04
Thanks, I looked again but I definitely cant see it. I first searched for it but have just browsed through the graphics section and it's not there

---

### Post by ibjsb4 on 2014-01-04
Yes, its in the software center

[http://packages.ubuntu.com/saucy/vlc](http://packages.ubuntu.com/saucy/vlc)

Maybe try loading it from there or here

[https://apps.ubuntu.com/cat/applications/saucy/vlc/](https://apps.ubuntu.com/cat/applications/saucy/vlc/)

You have your universe source open, right?

[ATTACH=CONFIG]249209[/ATTACH]

---

### Post by Bucky Ball on 2014-01-04
Open Update Manager>click Settings bottom left>check you have the Universe repositories enabled as VLC should be there. Mighty strange it isn't.

* Just noticed: As in ibjsb4's screenshot, second on the list.

---

### Post by rachel-g41 on 2014-01-04
Solved - many thanks. It was the comment about the software updater that helped me. I hadn't tried there (I was looking in system tools options and it's in preferences) but when I opened it, it had the Canonical options clicked from a skype installation yesterday. I re-clicked all the others, retried sudo apt-get install vlc and it's working. 

Many thanks and sorry for needing such baby steps - it's all new to me.

---

### Post by Bucky Ball on 2014-01-04
All good. That's what this area's about. You can pass it on. ;)

Enjoy the OS, the forums and the learning curve.

---


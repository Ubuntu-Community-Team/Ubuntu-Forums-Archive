---
title: "Installing murrine"
date: 2008-05-11
forum: New to Ubuntu
---

### Post by Rukaru on 2008-05-11
I just downloaded and extracted murrine, but i don't know what to do next.  I read the page on installing it at the official site, but as I am brand new to ubuntu I have no idea what it is talking about.  Can someone explain it to me please?

---

### Post by Tsurugi13 on 2008-05-11
I never figured out how to use those. Try looking it up in synaptic.

---

### Post by autocrosser on 2008-05-11
Post the link & I'll take a look at it.

---

### Post by MaindotC on 2008-05-11
It is in Synaptic but it says "This package includes the Murrine engine only. Themes have to be installed
to ~/.themes/."

---

### Post by Rukaru on 2008-05-11
> **strAlan said:**
> It is in Synaptic but it says "This package includes the Murrine engine only. Themes have to be installed
to ~/.themes/."
Yeah isn't marrine a whole engine like emerald?

---

### Post by autocrosser on 2008-05-11
Yes--Murrine is just the "engine"--take a look at gnomelook.org to get Murrine-based themes--you can open appearance & "install" or just drop the downloaded theme (in either .tz or .bz2) on it & it will load the theme into your /home .theme folder. It will then ask if you want to use it now or not.....

---

### Post by MaindotC on 2008-05-11
Rukaru - I figured it out.  I have no idea WHY they did this, but when you bunzip the nmc.tar_3.bz2 it will give you the file nmc.tar_3.  If you use the following it will untar the file and shows an installation shell script which you need to install using the directions on [this thread]("http://ubuntuforums.org/showthread.php?t=239378&highlight=murrina").

```

311-laptop:~/Desktop$ bunzip2 nmc.tar_3.bz2 
311-laptop:~/Desktop$ ls
nmc.tar_3

311-laptop:~/Desktop$ tar xvf nmc.tar_3
newmurrineconfigurator/
newmurrineconfigurator/README
newmurrineconfigurator/NEWS
newmurrineconfigurator/src/
newmurrineconfigurator/src/gtkrcengine.py
newmurrineconfigurator/src/gtkrcengine.pyc
newmurrineconfigurator/src/newmurrineconfigurator.py
newmurrineconfigurator/src/previewdialog.py
newmurrineconfigurator/src/previewdialog.pyc
newmurrineconfigurator/src/savedialog.py
newmurrineconfigurator/src/savedialog.pyc
newmurrineconfigurator/src/support.py
newmurrineconfigurator/src/support.pyc
newmurrineconfigurator/src/murrine-config.glade
newmurrineconfigurator/src/preview.glade
newmurrineconfigurator/src/savedialog.glade
newmurrineconfigurator/src/murrine-configurator.png
newmurrineconfigurator/src/murrine-configurator.desktop
newmurrineconfigurator/AUTHORS
newmurrineconfigurator/COPYING
newmurrineconfigurator/install.sh
311@a34lkj2348dsf311-laptop:~/Desktop$ ls
newmurrineconfigurator  nmc.tar_3
311-laptop:~/Desktop$ cd newmurrineconfigurator/
311-laptop:~/Desktop/newmurrineconfigurator$ ls
AUTHORS  COPYING  install.sh  NEWS  README  src

311-laptop:~/Desktop/newmurrineconfigurator$ sudo ./install.sh --prefix=/usr --enable-animation
No prefix given, assuming installation in /usr..
Installing files under /usr...
New Murrine Configurator successefully uninstalled.

Installing files under /usr...
New Murrine Configurator successefully installed.

```

However it looks like I'll have to learn spanish...

---

### Post by MaindotC on 2008-05-11
Cool this theme manager is a little buggy w/ Firefox but for the most part its sweet.

---

### Post by Rukaru on 2008-05-11
Man I wish I could get it..it's still too complicated for me.  I use emerald for the window frame (you know what I mean..the bar with close and minimize) but the default theme manager isn't doing it for me...not customizable enough.

---

### Post by SunnyRabbiera on 2008-05-11
well are you using hardy?
murrine is preinstalled with it

---

### Post by Rukaru on 2008-05-12
> **SunnyRabbiera said:**
> well are you using hardy?
murrine is preinstalled with it

Oh really?  How do I use it?  I do have hardy :)

---

### Post by SunnyRabbiera on 2008-05-12
well you can use it by right clicking on your desktop and selecting "change desktop background" and then in the "theme" tab you can go to customize and in the controls tab select the "human-murrine" engine

this will start you off at least, you can change the colors of it.
you can also install the murrine congurator too if you installed some murrine themes on gnome look or something, you can get it here though its not entirely in english:
[here]("http://www.cimitan.com/murrine/node/8/release")
just download and install the debian installer file it has on there.

---

### Post by autocrosser on 2008-05-12
I've installed & "corrected" the dialogs for murrineconfigurator--I can .tz the changed files if anyone is interested......Still need to change sizing--I'm not seeing all of some of the dialogs--has to do with box sizing & english translation.

Including the changed files--need to be installed in /usr/share/nmc & pulled the icon from the website & resized to 48 for menu use......enjoy!!

---

### Post by MaindotC on 2008-05-12
I didn't have any probelms installing it as I stated above.  I had to figure out this "tar_3" format bit it's fine.

---


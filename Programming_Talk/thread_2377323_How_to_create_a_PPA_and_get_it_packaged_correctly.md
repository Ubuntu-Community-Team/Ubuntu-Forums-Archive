---
title: "How to create a PPA and get it packaged correctly"
date: 2017-11-11
forum: Programming Talk
---

### Post by MadsRH on 2017-11-11
[SIZE=6]Hi[/SIZE]

**Can someone walk me through the steps of creating a PPA and making sure that it is packaged correctly?**

I'm [trying to set up af PPA]("https://community.ubuntu.com/t/new-system-sounds-in-18-04/1557/12") for a sound theme (actually two themes). What files are needed in the folder for this to work and can both themes be included in the same PPA or is it better to create a separate?



Best regards
*MadsRH*

---

### Post by Frogs Hair on 2017-11-11
Ubuntu uses .ogg files located in usr/share/sounds/. I would have a look there for starters and you'll find the old login sound in the ubuntu/stereo folder. double click the files to hear them.

 You have to find a way to create the sounds you and others may like and save them to the ogg format. You can also search for instructions to enable the old desktop login sound.   

Your PPA would require a script or .deb package to install and enable your new sounds. Launchpad.net explains how create a place to host your PPA.

---

### Post by Frogs Hair on 2017-11-11
I used the following in startup applications to enable the old login sound.

Name: Gnome Login Sound
Command: /usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"
Comment: Play a sound at login

---

### Post by mc4man on 2017-11-11
You can easily search 'debian packaging' for numerous links  on how to create a proper source to upload to the ppa to be packaged.
What also can be useful is to apt some current Ubuntu sources & look at how they're  done, what's in the debian/ files, ect. If possible choose sources similar to what you're doing.

(- your debian folder can be quite simple, only a few items required depending on source.., ex. in scr1 of simple binary install, scr. 2 of a library & headers. A theme shouldn't need much..

At the very least make sure devscripts is installed.

---

### Post by MadsRH on 2017-11-12
Thanks for the reply :D

I've downloaded three sound themes to see how they've done. Only one of the three files has the **debian** folder.

Can anyone help me write the Makefile? :confused:

This is what I've got so far: [ATTACH]277500[/ATTACH]

I know it's not the best name, but it's memorable and better than untitled.

I want to use the CC-BY-SA licence. Could this be shipped without any problems (IF one should be so lucky to have this included on the .ISO) or would it be better to go with GPL3?

---

### Post by MadsRH on 2017-11-12
I've put the files on github. Maybe that's an okay solution - it's definitely easier than uploading to a PPA ;)

[https://github.com/madsrh/WoodenBeaver](https://github.com/madsrh/WoodenBeaver)

---

### Post by MadsRH on 2017-11-14
I&#8217;ve uploaded three different suggestions. to Github (see my post from two days ago)  :smiley: PLEASE download, test and post feedback!!!

**DEVELOPERS: **Could someone _please_ help me create the Makefile? and does this project need a debian folder?

---


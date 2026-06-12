---
title: "Problem Booting from USB Drive"
date: 2008-08-30
forum: New to Ubuntu
---

### Post by Cuz314 on 2008-08-30
I did an full install from the Live CD (8.04) to an 8 gig USB drive. When I boot it runs through all the processes, and ask for my user id and password. Once I enter them all i get is a brown screen and the mouse pointer. I have to do a hard shut down. Can any one provide some ddirection on what the problem might be? I'm a newbie so pretend you're talking to a 2 year old.:)

Thanks

---

### Post by swoll1980 on 2008-08-30
> **Cuz314 said:**
> I did an full install from the Live CD (8.04) to an 8 gig USB drive. When I boot it runs through all the processes, and ask for my user id and password. Once I enter them all i get is a brown screen and the mouse pointer. I have to do a hard shut down. Can any one provide some ddirection on what the problem might be? I'm a newbie so pretend you're talking to a 2 year old.:)

Thanks

It sounds like gnome isn't loading for some reason(not installed maybe) before you log in, switch session to terminal, log in, then type gnome-panel see what happens

---

### Post by gmxgeek on 2008-08-30
Concur. Sounds like it boots fine, but has no desktop environment. Do you have a grub menu on startup?

---

### Post by cdtech on 2008-08-30
Do you see the GRUB bootloader? Is the "user" "password" via a terminal or a GUI screen?

---

### Post by Cuz314 on 2008-08-30
I see Grub when it starts to load. it runs through  a couple of text screens. Each line appears to be OK. The user name and password are in a GUI.

---

### Post by Crafty Kisses on 2008-08-30
See if it's detected > lsusb

---

### Post by swoll1980 on 2008-08-30
> **Cuz314 said:**
> I see Grub when it starts to load. it runs through  a couple of text screens. Each line appears to be OK. The user name and password are in a GUI.

You don't have a desktop environment follow the instructions in the first post then I can help you fix it

---

### Post by gmxgeek on 2008-08-30
try going into recovery mode, and dropping into root shell. then type in 

```

dpkg --get-selections | grep -i gnome

```

this is what i have. see if you have basically the same thing.


```

bluez-gnome					install
compiz-gnome					install
firefox-3.0-gnome-support			install
firefox-gnome-support				install
gimp-gnomevfs					install
gnome-about					install
gnome-accessibility-themes			install
gnome-app-install				install
gnome-applets					install
gnome-applets-data				install
gnome-cards-data				install
gnome-control-center				install
gnome-desktop-data				install
gnome-doc-utils					install
gnome-games					install
gnome-games-data				install
gnome-icon-theme				install
gnome-keyring					install
gnome-mag					install
gnome-media					install
gnome-media-common				install
gnome-menus					install
gnome-mime-data					install
gnome-mount					install
gnome-netstatus-applet				install
gnome-nettool					install
gnome-orca					install
gnome-panel					install
gnome-panel-data				install
gnome-pilot					install
gnome-pilot-conduits				install
gnome-power-manager				install
gnome-screensaver				install
gnome-session					install
gnome-settings-daemon				install
gnome-spell					install
gnome-system-monitor				install
gnome-system-tools				install
gnome-terminal					install
gnome-terminal-data				install
gnome-themes					install
gnome-user-guide				install
gnome-utils					install
gnome-volume-manager				install
gstreamer0.10-gnomevfs				install
language-pack-gnome-en				install
language-pack-gnome-en-base			install
libgail-gnome-module				install
libgnome-desktop-2				install
libgnome-desktop-2-7				install
libgnome-keyring0				install
libgnome-keyring1.0-cil				install
libgnome-mag2					install
libgnome-media0					install
libgnome-menu2					install
libgnome-pilot2					install
libgnome-speech7				install
libgnome-vfs2.0-cil				install
libgnome-window-settings1			install
libgnome2-0					install
libgnome2-canvas-perl				install
libgnome2-common				install
libgnome2-perl					install
libgnome2-vfs-perl				install
libgnome2.0-cil					install
libgnomecanvas2-0				install
libgnomecanvas2-common				install
libgnomecups1.0-1				install
libgnomekbd-common				install
libgnomekbd2					install
libgnomekbdui2					install
libgnomeprint2.2-0				install
libgnomeprint2.2-data				install
libgnomeprintui2.2-0				install
libgnomeprintui2.2-common			install
libgnomeui-0					install
libgnomeui-common				install
libgnomevfs2-0					install
libgnomevfs2-bin				install
libgnomevfs2-common				install
libgnomevfs2-extra				install
libpam-gnome-keyring				install
libpolkit-gnome0				install
network-manager-gnome				install
openoffice.org-gnome				install
policykit-gnome					install
python-gnome2					install
python-gnome2-desktop				install
python-gnomecanvas				install
ssh-askpass-gnome				install
system-config-printer-gnome			install
xulrunner-1.9-gnome-support			install

```

---

### Post by swoll1980 on 2008-08-30
Yeah do that instead :)

---

### Post by gmxgeek on 2008-08-30
If you can post that output it would actually be better

---

### Post by cdtech on 2008-08-30
You just may need to reset your xserver:
Boot into recovery mode, log in and type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by gmxgeek on 2008-08-30
> **cdtech said:**
> You just may need to reset your xserver:
Boot into recovery mode, log in and type:
```
sudo dpkg-reconfigure xserver-xorg
```

Well, i think it's a new installation, so X probably isn't the issue. But could be. Try that :)

---

### Post by swoll1980 on 2008-08-30
Would he have a GUI if X was screwed up?

---

### Post by C.S.Cameron on 2008-08-30
I never have a problem installing from Live CD to thumb drive.
Have you tried booting a second computer from the USB device?
There might be a problem booting from a dissimilar computer if you have installed restricted drivers, in which case booting to safe mode usually helps.
If the same thing happens on a second computer, you probably have a bad install and should start over after checking the CD.

---

### Post by Cuz314 on 2008-08-30
I went into terminal mode and typed gnome-panel. the response was "cannot open display". I did do ls and i have two directories: gnome2 and gnome2-private if that helps.

---

### Post by Cuz314 on 2008-08-31
I was unable to copy the output, no way to get it unto another usb drive but as near as I could tell it looked very similar to what you printed. I did not see anything that that didn't say install. I also tried the reconfigure and that did not work. Also now it won't alway boot up. I'm starting to think that i may have a bad install. I got the disk from Ubuntu but i guess that doesn't guarantee a good install.

---

### Post by C.S.Cameron on 2008-08-31
I did 4 USB installs yesterday,
One with an old CD drive, one with a dirty CD, one with fragmented USB drive and one with a clean CD and good CD drive.
Only the one with clean CD with a good drive worked with out problem.
If your install to USB does not work from the start it is either a bad install or your computer is busted.

---

### Post by andrewcmcardle on 2009-01-03
Hi, i'm sorry if this problem has already been resolved, but when i tried to install on the USB i discovered it's a problem with the gnome-keyring package. To fix it...

Boot up and **don't log in**
Switch to a virtual console : [FONT="Courier New"]Ctrl+Alt+F2[/FONT]
Kill x : [FONT="Courier New"]sudo killall gdm[/FONT]
Empty the /tmp folder : [FONT="Courier New"]sudo rm -rf /tmp/*[/FONT]
Start X : [FONT="Courier New"]startx[/FONT]

When x starts perform a full system update with synaptic, or just reinstall the gnome-keyring package
[FONT="Courier New"]sudo apt-get update[/FONT]
[FONT="Courier New"]sudo apt-get install gnome-keyring[/FONT]

---


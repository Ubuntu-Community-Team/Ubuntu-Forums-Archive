---
title: "ATI Beryl KDE Dapper My Guide"
date: 2006-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by calvinthomas on 2006-10-04
This is a slightly adapted guide that got things working for me on KDE, I hope it is helpful for people.

First of all make sure your ATI drivers are up-to-date, to do this follow method 2 from here:

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide")

Now reboot your system and confirm it has worked by opening a terminal and typing:

```
fglrxinfo
```

You should get something similar to this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: MOBILITY RADEON X700 Generic
OpenGL version string: 2.0.6065 (8.29.6)

```

If you do carry on, **if not fix this first** there are guides around the forums for this.

Now update the system:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

And add these to your sources list by doing this:

```
kdesu kate /etc/apt/sources.list
```

and add:

```

deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main
```

Now save and exit, next go to the terminal and add the required key by:

```

wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```

Now update the sources list by typing:

```
sudo apt-get update
```

Now install the required packages by typing this:

```
sudo apt-get install xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings
```

Now we need to create a startup script, to do this, type:

```
kdesu kate /usr/bin/startxgl.sh
```

And paste this into there:

```
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1
# Start KDE
exec startkde
```

Save and exit and make the script executable by typing at a terminal:

```
sudo chmod 755 /usr/bin/startxgl.sh
```

Now create a login manager session like this:
```

kdesu kate /usr/share/xsessions/xgl.desktop
```

Paste into this:

```
[Desktop Entry]
Encoding=UTF-8
Name=Xgl
Exec=/usr/bin/startxgl.sh
Icon=
Type=Application
```

Save and exit.

Now we need to make a startup script for beryl-manager like so:

```
kdesu kate /home/<username>/.kde/Autostart/beryl-manager
```

With <username> replaced with your actual username. 

Now enter into there:

```
#!/bin/bash
/usr/bin/beryl-manager 

```

And make it executable like so:

```
chmod +x /home/<username>/.kde/Autostart/beryl-manager
```

With <username> replaced with your actual username.

Now make sure we have all the latest versions by doing this:

```
sudo apt-get update
sudo apt-get dist-upgrade
```

Now restart your computer, choose sessions, and select XGL and login. Now for me I had to do this:

Look in the system tray and you should see the beryl manager icon click on this and deselect Launch fall-back window manager if beryl crashes

Click on the bery manager icon again and select Window manager > beryl.

You should now see the beryl splash screen and have beryl working, reboot and login to xgl again and you should immediately be in beryl.

**Extras**

To finish off:

```
sudo apt-get install emerald-themes
```

Click on the system tray icon and choose Emerald Theme Manager and select a theme of your liking.

Finally you can change settings of beryl by clicking on the system tray icon and selecting Beryl Settings Manager.

Have Fun!

---

### Post by calvinthomas on 2006-10-04
Fixed various spelling mistakes and a link error, should be fine now, any problems, let me know

Calv

---

### Post by btp302 on 2006-10-09
Thanks, worked nicely, looks better than ole compiz did even a month ago, lots of settings easy to get to in the beryl=manager.

---

### Post by calvinthomas on 2006-10-10
Yea, I think it works a lot better also. I'm glad the guide worked for you

Calv

---

### Post by library.ninja on 2006-10-25
Wow!  Thanks for the guide.  I'm using an Nvidia card and this worked great for me (just ignoring the ATI driver part).
:-D

---

### Post by AngryAmoeba on 2006-10-25
Thanks so much for this guide..this must be the fifth one I've followed and the fifth time I've re-installed Kubuntu because I botched the xgl installation every time due to improper tutorials.  Now my KDE looks maximally sex.  Thanks.  Also, for informational purposes I'm running Kubuntu Dapper 6.06 fully updated as of 10/25/06 with the default fglrx driver and my ATi Radeon Mobility x1400.  Runs fantastic.

---

### Post by shannon.cummins on 2006-11-10
Ok, I followed your guide, and I get the beryl icon in the sys tray but when I make it the manager I lose the window border (if that makes sense, the theme around the window with minimize, close, etc.)  It doesn't freeze, I just cant close or move the windows.  What's the deal?

Kubuntu 6.10
ATI Radeon Mobility 9600

---

### Post by CowzRule on 2006-11-10
> **shannon.cummins said:**
> Ok, I followed your guide, and I get the beryl icon in the sys tray but when I make it the manager I lose the window border (if that makes sense, the theme around the window with minimize, close, etc.)  It doesn't freeze, I just cant close or move the windows.  What's the deal?

Kubuntu 6.10
ATI Radeon Mobility 9600

Try clicking on the Beryl icon in the tray and select quit.

---

### Post by calvinthomas on 2006-11-11
The disappearing window started happening to me also, it is fixed in the latest version of beryl (v0.12)

Calv

---

### Post by AusIV4 on 2006-12-08
I've had the window decorations appear as well, but if I click "Refresh window decorations" a couple of times, it usually winds up okay.

My question is: why is it that when I go to "Log Out"  my only option is End Current Session? I'd like to reboot my computer and shut it down more often than I just want to end the session.

[EDIT]
I might add that the End Current Session option doesn't even work. It does end the session, but it does not take me back to the login window, it just sits there until I turn my computer off (Ctrl - Alt - Backspace does not work).

---

### Post by calvinthomas on 2007-01-27
One of the problems of Beryl in Ubuntu is the loss of the restart and shutdown buttons, it is a bit of a pain, some create a little script to get over this, for me I just open a terminal and type:

sudo reboot - when I want to reboot
sudo shutdown - when I want to shutdown (You can also use sudo halt)

I'm not sure about your other issue though, hopefully, someone else can help.

Calv

---


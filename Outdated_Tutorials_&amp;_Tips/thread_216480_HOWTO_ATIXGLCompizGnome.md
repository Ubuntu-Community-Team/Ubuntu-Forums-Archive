---
title: "HOWTO: ATI/XGL/Compiz/Gnome"
date: 2006-07-15
forum: Outdated Tutorials &amp; Tips
---

### Post by gruvsyco on 2006-07-15
There seems to be a few of these floating around and I have no promises this will work any better than any of the others but, after messing around with different distros to the point of messing up my system and reinstalling a few times this week, here is my method for getting this all up and running pretty quickly.

[I]Note: This just happens to work with my particular video card, ATI AIW Radeon 9600XT.

Note 2: I'm assuming some basic knowledge of getting around in Ubuntu.[/I]

[SIZE="4"]***Part 1:* ATI Driver**[/SIZE]

First thing I do from a clean install is:
[LIST]
[*]open Synaptic and Settings > Repositories.
[*]Find all the unchecked boxes and check them.
[*]Once this is done, refresh.
[*]Search for fglrx
[*]Install xorg-driver-fglrx
[*]Exit Synaptic
[/LIST]
Open a terminal and:
```
sudo aticonfig --initial 
sudo aticonfig --overlay-type=Xv
```

now reboot.  You should now be running the accelerated ATI driver.  You can verify this by opening a terminal and entering:
```
fglrxinfo
```
Look for the following:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 2.0.5814 (8.25.18)
```
then enter:
```
glxinfo
```
and look for:
```
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT Generic
OpenGL version string: 1.2 (2.0.5814 (8.25.18))
```

Hopefully, this is all working.  I've done this exactly, 3 times this week and it's worked every time.

[SIZE="4"]***Part 2:* XGL/Compiz**[/SIZE]

*Note: taken from bluevoodoo1's thread [here]("http://www.ubuntuforums.org/showthread.php?t=174233") and modified slightly for ATI.*

**1. Add new repos to your /etc/apt/sources.list.**
```
sudo gedit /etc/apt/sources.list
```
add these lines...
```
deb http://xgl.compiz.info/ dapper main 
deb http://www.beerorkid.com/compiz/ dapper main
```
...save

Add this key...
```
wget http://www.beerorkid.com/compiz/quinn.key.asc -O - | sudo apt-key add -
```
```
sudo apt-get update
```

**2. Install:**
[LIST]
[*]Open Synaptic and search XGL
[*]select xserver-xgl
[*]search compiz
[*]select compiz, compiz-gnome, gset-compiz
[*]optionally select gcompizthemer, gcompizthemer-themes
[*]apply and exit
[/LIST]

**3. Create a separate Xgl session (GNOME-based).**

First the script.  Open a terminal and...
```
sudo gedit /usr/bin/xgl-gnome.sh
```
Paste this in.
```
#!/bin/bash  

Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 gnome-session
```
Make it executable...
```
sudo chmod 755 /usr/bin/xgl-gnome.sh
```
Now create the session...
```
sudo gedit /usr/share/xsessions/xgl-gnome.desktop
```
paste this in...
```
[Desktop Entry]  
Encoding=UTF-8 
Name=XGL-GNOME
Exec=/usr/bin/xgl-gnome.sh 
Icon= 
Type=Application
```
Make it executable...
sudo chmod 755 /usr/share/xsessions/xgl-gnome.desktop

**4.  Starting XGL-Gnome**

Exit your current session and from GDM, choose XGL-Gnome as your session.  Once you're logged in:
go to System > Preferences > Sessions
select Startup Programs and add
```
gnome-window-decorator
```
AND
```
compiz --replace gconf
```

Now, restart your XGL-Gnome session and you should have a fully functioning XGL/Compiz session.

I hope this works as well for some of you as it has for me.  I can generally get this all working within about 10 minutes of an install now.

---

### Post by charlesbrooking on 2006-07-16
Thanks for a very neatly-presented HOWTO. :)

I followed the steps and almost got it working, but I also had to create a script to start the XGL session properly, as suggested on [http://www.compiz.net/viewtopic.php?id=389]("http://www.compiz.net/viewtopic.php?id=389"):
```
#!/bin/sh 
killall gnome-window-decorator 
wait

gnome-window-decorator & 
compiz --replace gconf &
```
I placed this into a script ('/usr/bin/startcompiz') and added it to my session startup programs instead of having 'gnome-window-decorator' and 'compiz --replace gconf' listed separately.

Another thing I did was run 'gconf-editor' and disable the '/apps/panel/global/enable_animations' option. This made loading applications much faster for me (no waiting while blue borders of increasing size are repeatedly drawn onto the screen while opening new windows).

Hope this helps some other people. :)

---

### Post by mech7 on 2006-07-16
WIth me it says;

> chris@chris-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)


I have an ati x700 mobile ? what now :s

---

### Post by charlesbrooking on 2006-07-16
> WIth me it says;

[QUOTE]chris@chris-laptop:~$ fglrxinfo
display: :0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

I have an ati x700 mobile ? what now :s[/QUOTE]

Make sure you reboot before running 'fglrxinfo'!

Otherwise, if you've followed all the instructions in *Part 1*, then you'll need to give us more information before we can help...

---

### Post by mech7 on 2006-07-16
Yes I have done as it says.. and reboot. I don't know what other info i can give other then i followed the steps and that i have a x700 mobile card :s

---

### Post by FRiEd on 2006-07-16
Just given this a try, this is the closest I have come so far.
Running ATI Radeon Mobility 9700 pro. works fine in normal xfce, tried xgl, it loads, a splash screen comes up, a orangey background shows, then it all goes black, i am left with a white cursor, shortcuts work like alt+f2 for running stuff so i can get to a terminal. but that is it, left me quite confused, anybody have any ideas.

---

### Post by MooBaloo on 2006-07-16
Hmm... It doesn't want to let me install compiz...

```
compiz:
  Depends: libsvg-cairo (>=0.1.6) but 0.1.5-0 is to be installed
```

Edit: nevermind... I need to get the AM64 version of some things

---

### Post by lzfy on 2006-07-16
OMG this works :) 

now it's time to test :D 

@mech7 I have the same card as you, I didn't get any error.

---

### Post by mech7 on 2006-07-16
mmm strange i also dont get any error only the ati drver is not used :O

---

### Post by lzfy on 2006-07-16
> mmm strange i also dont get any error only the ati drver is not used :O

:-k  hmmm you're right :mrgreen: 

my first experiences. First time it crashed after 5 minutes, I rebooted and now running almost 30 min. and no crashes. First time I had banshee running, maybe that caused the crash.

---

### Post by smedstadc on 2006-07-16
I just tried this on my toying around partition. I got it mostly working, however window borders don't draw. So I see the inner frame of any window, but I can't move them, and can't close, minimize or maximize them. They also appear only in the top left corner of my screen covering my system menu... to log out and back in I need to restart the xserver with ctrl-alt-backspace.

Sometimes my gnome-panel fails to load/display as well. But thats not consistent.

Does this sound like I made a mistake somewhere, or could it just be a a bug related to attempting this with an X800 XL? Rather than something older?

No crashes or errors though. Which is always encouraging. :D

---

### Post by smedstadc on 2006-07-16
Hrm. I updated my mesa libraries and the problem went away. It's an auto-update so anybody with the same problem I had should just let one run and you'll probably be good to go.

---

### Post by bsheep on 2006-07-17
I have made your modifications in order to run XGL, everything work well except that in XGL Session I can't directly reboot or halt my system, icons vanish, but I have the other icon (logout, suspend, hibernate etc..). When I come back to default session, without XGL, Reboot and Halt are back. 
Any idea ?

---

### Post by Rackerz on 2006-07-17
I get the same, I think that's just how XGL/Compiz are.

I'm going to use this Howto later, see if I get any improvements on the shattered XGL/Compiz which are already installed.

---

### Post by tuxbaby on 2006-07-17
here is the easiest way I tried.
Have a look.

[http://abrogate.blogspot.com/](http://abrogate.blogspot.com/)

quite well explained

thanks
tux

---

### Post by mrojas73 on 2006-07-18
Workind great on my Compaq Presario2000!

OP, thank you very much for your guide!

---

### Post by Placenta Juan on 2006-08-16
Thanks! Worked perfectly on my ati radeon 9600xt 128mb.

---

### Post by Pallazzio on 2006-08-16
moobaloo

compiz:
  Depends: libsvg-cairo (>=0.1.6) but 0.1.5-0 is to be installed

i get this same error.  how did you resolve it?  thx

---

### Post by kseise on 2006-08-16
Its not working for me with the same ATI Radeon 9600.  I followed the entire How-To and I am stuck in the same situation as Smedstadc was.  No window borders, no fancy effects.  Anyone have a suggestion?

---

### Post by vintage-vinnie on 2006-08-17
same deal here

No window borders, no fancy effects. what gives?

---

### Post by jcalvasina on 2006-12-06
I can't access this repository:

deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main 

Has it been taken down or am I doing something wrong? ](*,)

---


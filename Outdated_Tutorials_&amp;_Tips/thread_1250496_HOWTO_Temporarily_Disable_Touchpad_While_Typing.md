---
title: "HOWTO: Temporarily Disable Touchpad While Typing"
date: 2009-08-26
forum: Outdated Tutorials &amp; Tips
---

### Post by Darkwing-Duck on 2009-08-26
As I have gone back to using Linux once again I installed Ubuntu 9.04 “Jaunty” on my Acer Aspire One netbook. One thing that I noticed is when typing my thumb or part of my hand would touch the mouse sensor pad and click it. Sending whatever I was typing to another place. The easy fix was to disable clicking via the touch pad but I found that I was too used to it so here is a easy script to fix the problem.

You will need to do a couple of things before it will work.

1. You need to have tapping enabled.
2. you will need to edit your xorg.conf to reflect: 

```
SHMConfig “on”
```

If you need help with this open the terminal and type: 
```

sudo gedit /etc/X11/xorg.conf
``` 

Scroll to the bottom of the page. Start a new section and add:

```
SHMConfig "on"
```

Okay, once this is done we will be using a little tool called syndaemon. if you want to know more about this tool you can man syndaemon. But, my basic command should do the trick for you.

Open your terminal again and type in the following:

```
syndaemon -d -t -i 6
```

Okay, I’ll go through what this did for you.
# the -d flag tells syndaemon to run all the time and monitor the keyboard
# the -t flag tells it to only disable tapping and scrolling, not pointer movement.
# the -i flag is how long (in seconds) to disable the touchpad *after* the last keypress

So in a nutshell this will monitor the keyboard for activity and disable tapping for a set number of seconds. You will still be able to have pointer movement but, the click function will be temporally disabled. In the example above I have it set for 6 seconds.

You could try adding that command to your gnome sessions (System > Preferences > Sessions) to have it load at gnome login. This way it will always startup and run.

NOTE: You do NOT have to be root or use the sudo command for this to work.

---

### Post by bodhi.zazen on 2009-08-26
This is a nice trick for most laptops / netbooks.

Just for clarification, the syntax in /etc/X11/xorg.conf is a bit off in the original post.

Using any editor, edit /etc/X11/xorg.conf 

you can use :
sudo nano /etc/X11/xorg.conf
sudo -e /etc/X11/xorg.cong
gksu gedit /etc/X11/xorg.conf , or 
kdesu kate /etc/X11/xorg.conf

In that file you are looking for the Section "InputDevice" for your touchpad (usually identified by the Driver "synaptics" )

Add the option in that section, like this:

```
Section "InputDevice"
Driver "synaptics"
[color=navy]**Option "SHMConfig" "on"**[/color]
EndSection
```

You may have additional options in that section, just add in the SHMConfig line.'

Then restart X

Personally I like

```
syndaemon -d  -i 2
```

Without the -t it disables moving the cursor (mouse) which is annoying if you are typing =)
Also two seconds (-i 2) is agonizing enough , 6 seconds is forever.

Otherwise very nice post, thank you Wonderly :twisted:

---

### Post by xyppy on 2009-08-27
Neither variety worked for me.  My X wouldn't start.

---

### Post by bodhi.zazen on 2009-08-27
Sorry you are having problems. Can you post either your error messages or better your xorg.conf

---

### Post by treesurf on 2009-08-28
Adding that section to my xorg.conf crashed X on restart.

---

### Post by treesurf on 2009-08-28
It turns out that enabling SHMConfig is now done differently for Jaunty and forwards.  It is not done through xorg.conf.   Also syndaemon does not necessarily need to have SHMConfig enabled for it to work correctly.  It works fine without enabling SHMConfig on my laptop.  Here's all the good stuff:

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

For me adding a startup command to disable tapping for one second after typing was simple:

```
syndaemon -d -t -i 1
```

---

### Post by bodhi.zazen on 2009-08-28
Thank you for the update. At the moment it works for me in jaunty (9.04) with the xorg.conf modifications I posted.

Fedora, however, has used the method you linked (hal) for some time so I am not surprised to see ubuntu is changing.

In Fedora hal and xorg edits conflict, so you need to use the method on the Ubuntu wiki. I suspect this will then be the case in 9.10 (Karmic).

---

### Post by xyppy on 2009-08-28
> **treesurf said:**
> It turns out that enabling SHMConfig is now done differently for Jaunty and forwards.  It is not done through xorg.conf.   Also syndaemon does not necessarily need to have SHMConfig enabled for it to work correctly.  It works fine without enabling SHMConfig on my laptop.  Here's all the good stuff:

[https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig](https://help.ubuntu.com/community/SynapticsTouchpad#shmconfig)

For me adding a startup command to disable tapping for one second after typing was simple:

```
syndaemon -d -t -i 1
```

Thanks for the info and link.  I was able to get this to work.  I had to use the -S option to make my system use the syndaemon.

A year of touchpad annoyance is over at last!:biggrin:

---

### Post by dlradlt on 2009-09-11
try a  gui app called touchfreeze 0.2.2 it works well for me its in the repositories


dlr

---

### Post by brandon_h on 2009-10-04
Thanks for that. The touch freeze program would not work for me but this worked great. :D

---

### Post by unc0nn3ct3d on 2011-03-04
Just FYI those edits to the xorg.conf now break Xserver in 10.10

---

### Post by towheedm on 2011-03-04
Not sure about previous releases, but in Maverick do:

```

gconftool-2 --type bool --set /desktop/gnome/peripherals/touchpad/disable_while_typing true
```I myself don't have a touchpad, so have not tested this.

---


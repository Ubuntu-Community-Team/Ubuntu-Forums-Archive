---
title: "Trying to edit some things"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by xdarkday on 2008-06-30
Ok I installed Diablo II through wine yesterday and it seemed that the install worked very well. However, after the first couple intro videos, when it gets to the main menu screen, my monitor says that there is no signal.

I think I located how to fix it
[http://ubuntuforums.org/showpost.php?p=4481079&postcount=68](http://ubuntuforums.org/showpost.php?p=4481079&postcount=68)

Here are my questions;
Do you think this could fix my problem? If so, how do I make these changes?

I know what the xorg.con file is, but have never heard of xrandr.

Make an idiots guide on what I do with both here. Thanks :)

---

### Post by Hospadar on 2008-06-30
you could try it, although I only know about xrandr being for multiple displays and display rotation stuff though.  I spose I could be wrong.

To edit your xorg.conf

in a terminal ```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by whitethorn on 2008-06-30
Ok I'll take a stab at this.  Did you check if your graphic card is being used? Did you use envy-ng to download the newest drivers for it?  Or activate the drivers in

System -> Administration -> Hardware Drivers

I got diablo2 lod running but I use the d2loader patch.  You might want to give it a try. Here's the webpage, 

[http://d2loader.blizzsector.net/](http://d2loader.blizzsector.net/)


If it doesn't help then, try the following.

First off you before you change your xorg.conf, you should first run

xrandr

in a terminal.  You should see a bunch of different screen resolutions posted.  You need to look and see if 800x600 is also posted there.  If it is there then you have to look for a different reason why it isn't working.  If you don't see it there then you need you should first make a backup of your xorg.conf before you start editing it, just in case something goes wrong

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

now you can open the file 

gksudo gedit /etc/X11.xorg.conf 

now you need to find the 

Section "Screen"

and add into the screen section the following.

    SubSection     "Display"
        Depth       16
        Modes      "800x600" "640x480"
    EndSubSection

then close and save it.  Reboot, you probably might just have to restart the x-server but just to be on the safe side.  Hopefully this fixes your problem. 

Oh you might want to check and see if your graphic card is being used.

---

### Post by xdarkday on 2008-06-30
> **whitethorn said:**
> Ok I'll take a stab at this.  Did you check if your graphic card is being used? Did you use envy-ng to download the newest drivers for it?  Or activate the drivers in

System -> Administration -> Hardware Drivers

I got diablo2 lod running but I use the d2loader patch.  You might want to give it a try. Here's the webpage, 

[http://d2loader.blizzsector.net/](http://d2loader.blizzsector.net/)


If it doesn't help then, try the following.

First off you before you change your xorg.conf, you should first run

xrandr

in a terminal.  You should see a bunch of different screen resolutions posted.  You need to look and see if 800x600 is also posted there.  If it is there then you have to look for a different reason why it isn't working.  If you don't see it there then you need you should first make a backup of your xorg.conf before you start editing it, just in case something goes wrong

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak

now you can open the file 

gksudo gedit /etc/X11.xorg.conf 

now you need to find the 

Section "Screen"

and add into the screen section the following.

    SubSection     "Display"
        Depth       16
        Modes      "800x600" "640x480"
    EndSubSection

then close and save it.  Reboot, you probably might just have to restart the x-server but just to be on the safe side.  Hopefully this fixes your problem. 

Oh you might want to check and see if your graphic card is being used.

I did look at the d2loader but really didnt understand how it worked or what it does.

I hope this screen shot helps show that I have the other stuff working. Also just to add, I can tell the game is running because I can hear the music at the main menu, its just not showing the game on my monitor.

---

### Post by whitethorn on 2008-06-30
[http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2](http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2)

Have you looked at this?  It seems running D2vidtest.exe might be the thing your missing. Try following the howto, if you get stuck just ask.

you can find the actual patch for version 1.12a at the link below

[http://us.blizzard.com/support/article.xml?articleId=20758](http://us.blizzard.com/support/article.xml?articleId=20758)

Once you've downloaded it, you should only have to double click on it, and let it run.

---

### Post by xdarkday on 2008-07-02
> **whitethorn said:**
> [http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2](http://ubuntuforums.org/showthread.php?t=362457&highlight=diablo+2)

Have you looked at this?  It seems running D2vidtest.exe might be the thing your missing. Try following the howto, if you get stuck just ask.

you can find the actual patch for version 1.12a at the link below

[http://us.blizzard.com/support/article.xml?articleId=20758](http://us.blizzard.com/support/article.xml?articleId=20758)

Once you've downloaded it, you should only have to double click on it, and let it run.

still not getting the signal during the menu screen damn!

---

### Post by xdarkday on 2008-07-02
Here was the fix

In the Device section:

Option "ModeValidation" "NoXServerModes"

---


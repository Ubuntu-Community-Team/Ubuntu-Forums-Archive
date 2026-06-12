---
title: "Visual affects/compiz"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by jjstein on 2008-04-29
I rather suck at this stuff and always seem to have some form of problem but I recently tried to use envy to install the ati driver.  everything seemed to go ok until it asks if i want xorg.conf configured automatically.  The first five hundred times I tried I clicked yes and i got an error message.  Now, I click yes and it just closes and nothing happens. I have no idea how to fix this.

Also, (this is undoubtedly related) in restricted drivers (system>administration>restricted drivers manager) the ati driver says enabled but the check box is not clicked.  When I click on it, it says ```
Reconfiguring X.org video drivers is not possible: /etc/X11/xorg.conf is invalid or does not exist.
``` 

From this I have gathered that whatever "xorg.conf" is is missing.  How do I alleviate this?


thanks

---

### Post by domace on 2008-04-29
I'm kinda new to Ubuntu to but I if you want to install  a new driver you do not always have to use envy, for some reason envy wouldn't work with my video card so I removed envy and installed the video driver using restricted drivers, and then you have restart your pc and go to BIOS and disable on board video card and boot Ubuntu into recovery and use the following command-

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by domace on 2008-04-29
jjstien you still their? if you dont like this method I could give you a link to a envy guide

---

### Post by iSplicer on 2008-04-29
Maybe you xserver is broken, boot into recovery mode and run

sudo dpkg-reconfigure xserver-xorg

After this, your restricted drivers should be able to work, if not, maybe you need to check all the boxes in your "Software sources" (its in administration)

Good luck

---

### Post by jjstein on 2008-04-29
yeah im here sorry. Got distracted and it just dawned on me to check this.  I've tried other methods but there always seems to be a problem with xorg.conf.  would that other way fix this?

---

### Post by domace on 2008-04-29
and in config settings make sure you have the right pci port setup happened to me and i didn't figure out until 2 hours later lol

---

### Post by iSplicer on 2008-04-29
> **jjstein said:**
> yeah im here sorry. Got distracted and it just dawned on me to check this.  I've tried other methods but there always seems to be a problem with xorg.conf.  would that other way fix this?

As I said, try this:

sudo dpkg-reconfigure xserver-xorg

After this, your restricted drivers should be able to work, if not, maybe you need to check all the boxes in your "Software sources" (its in administration)

Good luck

---

### Post by jjstein on 2008-04-29
well I did that and now I have black screen.  I see a colored bar on the top and bottom of the screen and can do nothing.  how do i un-do this(if at all possible).  I'm just done with this garbage.


Scratch that. I tried it again and it worked.  Scared the hell out of me there.

---

### Post by sdowney717 on 2008-04-29
you can boot to a command prompt and run 

envy -t

This will let you run envy without the gui. And maybe you can get it working, you can also I believe uninstall the ATI driver envy installed using this.

---

### Post by domace on 2008-04-29
Take a look at this thread it may help

[http://ubuntuforums.org/showthread.php?t=716373](http://ubuntuforums.org/showthread.php?t=716373)

 make sure you don't have envy installed while trying to use a restricted driver unless your going to use envy to install it

---

### Post by jjstein on 2008-04-29
It works now.  Thanks everyone.  the video card and everything (finally) is in working order

---

### Post by domace on 2008-04-29
np, you got compiz installed? if you dont get it and enable cube it fun..
ahh ubuntu compiz,,,,,,the king of eye candy

---

### Post by jjstein on 2008-04-29
Wow whole bunch of new problems. Ever since I started back up, everything is going epicly slow. I have a system moniteradd-on on my toolbar and its showing that my proccessor is100% in use. It only appears to be doing this when i have firefox open for some stupid reason. Also, with compiz, the desktop cube is not a cube at all. it is a flat surface with two sides. i can nnot get this to change. help?


I've narrowed it down further: entering text makes it jump to 100%. why!?

Gah maybe not.... doing pretty much anything takes 64673483764 times more processing speed than it needs. this is ridiculous.

---

### Post by sdowney717 on 2008-04-30
goto system - preferences - compiz manager

click general options
under desktop size  put the settings at 4, 1, 1

For the weird browser issue, try installing seamonkey or another browser like Epipany or Opera and see if it is any different.
[https://help.ubuntu.com/community/SeaMonkey](https://help.ubuntu.com/community/SeaMonkey)

here are some things to play around with for firefox
[http://www.ubuntugeek.com/speed-up-firefox-web-browser.html](http://www.ubuntugeek.com/speed-up-firefox-web-browser.html)

I had a terrible slow text problem and it went away after I finally got the ATI driver working properly. 

[http://ubuntuforums.org/showthread.php?t=531677&highlight=firefox+slow+text](http://ubuntuforums.org/showthread.php?t=531677&highlight=firefox+slow+text)

---

### Post by jjstein on 2008-04-30
I have no "system>preferences>compiz" anything. I have advanced desktop affects.  Same thing? I will also try different browsers and see the effect.

---

### Post by sdowney717 on 2008-05-01
from the menu click system, etc...

---

### Post by jjstein on 2008-05-01
I'm aware of that. perhaps I should rephrase. under system>preferences there is nothing with "compiz" in the name.

---

### Post by sdowney717 on 2008-05-02
in terminal type ccsm

hmmm, well perhaps the configuration editor is not installed.
Open synaptic and look for compiz config settings manager

system-admin-synaptic

---

### Post by Saint Angeles on 2008-05-02
make sure you have ccsm:
```
sudo apt-get install compizconfig-settings-manager
```
then make sure you have the latest ATI drivers and have configured your xorg.conf correctly:

[http://ubuntuforums.org/showpost.php?p=4749740&postcount=12](http://ubuntuforums.org/showpost.php?p=4749740&postcount=12)

---

### Post by jjstein on 2008-05-02
> **jjstein said:**
> I have no "system>preferences>compiz" anything. I have advanced desktop affects.  Same thing? I will also try different browsers and see the effect.

^already said I have it.  Actually, compiz is working now (finally) but I can't get my graphics card working right. I was getting an error about xorg.conf not being present but I finally made the error go away.  Still though, everything is incredibly laggy and slow. I used envy to install my drivers and it said everything worked but im not convinced.

---


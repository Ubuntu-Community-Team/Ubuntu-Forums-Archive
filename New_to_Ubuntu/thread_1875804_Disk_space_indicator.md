---
title: "Disk space indicator?"
date: 2011-11-05
forum: New to Ubuntu
---

### Post by d4m1r on 2011-11-05
Does anyone have a recommendation on one? Searching on Google provided nothing relevant :(

The ideal addon would add oval bars under my harddrives in Computer to show how much was left:

[IMG]http://i.imgur.com/NC9AU.png[/IMG]

Now every time I want to check, I have to go to this screen, right click, and hit properties...Note - I don't want something added to my top menu bar or onscreen (like conkey), is there anything specific that will change around **this** window?

---

### Post by enkay009 on 2011-11-05
I don't know if you'd settle for a command-line alternative...

```
df -hl
```This shows you the size of your mounted local partitions (-l) in "human readable" format (-h), Human readable format being the number of bytes rounded to 3 digits and a unit (ex. 1024B would be shown as 1K).

---

### Post by davdo2004 on 2011-11-05
Cick on 'view' in the nautilus global menu bar and put a check next to status bar. You will have the details at the bottom next to where it says 6 items in your screen shot.

---

### Post by Frogs Hair on 2011-11-05
I don't know if this would be of interest or not .

[http://www.omgubuntu.co.uk/2011/06/indicator-syspeek-another-hardware-monitor-applet-for-ubuntu/](http://www.omgubuntu.co.uk/2011/06/indicator-syspeek-another-hardware-monitor-applet-for-ubuntu/)

[https://launchpad.net/~vicox/+archive/syspeek](https://launchpad.net/~vicox/+archive/syspeek)

---

### Post by d4m1r on 2011-11-05
@enkay, doesn't display the name of the media so it is of limited use.

@davdo, it was already checked and it doesn't display the size of the medium at the bottom, only the name.

@frog, those would add further icons to my already cluttered top menu bar :(

---

### Post by dave0109 on 2011-11-05
Not sure if it's one of those things that you just can't do.

Thinking outside the box, you could use conky to monitor the discs and have them shown all the time on your desktop.  I've just added my windows partition to my settings file and it works fine.  See attached screenshot crop.

---

### Post by d4m1r on 2011-11-05
> **dave0109 said:**
> Not sure if it's one of those things that you just can't do.

Thinking outside the box, you could use conky to monitor the discs and have them shown all the time on your desktop.  I've just added my windows partition to my settings file and it works fine.  See attached screenshot crop.


Thanks, but I am aware of that option and my desktop space is too precious to be spammed by 5 HDD's :(

---

### Post by davdo2004 on 2011-11-06
> **d4m1r said:**
> 
@davdo, it was already checked and it doesn't display the size of the medium at the bottom, only the name.

Strange. Here is how it looks on mine. I am running gnome shell btw.


[IMG]http://i.imgur.com/I3PvV.png[/IMG]

---

### Post by d4m1r on 2011-11-06
> **davdo2004 said:**
> Strange. Here is how it looks on mine. I am running gnome shell btw.


[IMG]http://i.imgur.com/I3PvV.png[/IMG]


Try that from the Computer view (where it shows all your hard drives. When you single click on 1, does it show the size at the bottom? If it does either something is broken on my part of Unity doesn't have that script for whatever reason.

---

### Post by davdo2004 on 2011-11-07
Ah, I see what you mean now. From computer view I have to open the drive in question to see the details of remaining space. Single clicking just tells me I have selected that drive.

---

### Post by d4m1r on 2011-11-07
> **davdo2004 said:**
> Ah, I see what you mean now. From computer view I have to open the drive in question to see the details of remaining space. Single clicking just tells me I have selected that drive.

Exactly, annoying isn't it? :(

---


---
title: "Settings are extremely confusing"
date: 2011-12-18
forum: New to Ubuntu
---

### Post by Foobarz on 2011-12-18
Ok so I switched to oneiric and immediately i am mad.

The system settings are so different than natty, and much much much less intuitive
How do I change the iconset? How do I move the window buttons to the right? Where is my good ol theme new wave? How do I add new printers and stuff? HELP!!!

If there is no fix, and I heard that the new system settings is due to the switch to GNOME 3, I AM DEFINITELY SWITCHING BACK TO NATTY.

---

### Post by QIII on 2011-12-18
I wouldn't go back.

Not the least of reasons for this is that I think you would be going back to the 2.6 kernel.

I don't care much for the current state of GNOME, but I used to prefer GNOME 2 to the other choices.  Things change.

This might help:

[http://library.gnome.org/users/](http://library.gnome.org/users/)

Also, you may want to consider other desktop environments if you are not happy with the default fare.

---

### Post by lechien73 on 2011-12-18
Some of Oneiric's settings do seem a bit more restrictive than previous versions. I installed Ubuntu Tweak ([http://ubuntu-tweak.com):](http://ubuntu-tweak.com):)

```
sudo add-apt-repository ppa:tualatrix/next
sudo apt-get update
sudo apt-get install ubuntu-tweak

```
You can click on Themes to change to New Wave, change your icons theme, and move the control buttons location from left to right as well.

Printers are installed by the Printing applet in system settings.

---

### Post by BC59 on 2011-12-18
> How do I change the iconset? Where is my good ol theme new wave?

To change the themes install from Ubuntu Software Center the Advanced Settings.
If you like more themes, you have to download them from [http://ubuntu-art.org/]("http://ubuntu-art.org/"), create a folder /.icons and /.themes and drop them inside, according to the instructions.

---

### Post by bluexrider on 2011-12-18
> **Foobarz said:**
> Ok so I switched to oneiric and immediately i am mad.

The system settings are so different than natty, and much much much less intuitive
How do I change the iconset? How do I move the window buttons to the right? Where is my good ol theme new wave? How do I add new printers and stuff? HELP!!!

If there is no fix, and I heard that the new system settings is due to the switch to GNOME 3, I AM DEFINITELY SWITCHING BACK TO NATTY.
I commend you for going that route. 11.10 is not for everyone however. What was the reason for the move if everything was good where you were?

If you want to change the LOOK and FEEL of Oneiric then use the falback mode. 

```
sudo apt-get install gnome-session-fallback
```

[http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html](http://www.webupd8.org/2011/08/installing-using-classic-gnome-desktop.html)

---

### Post by Foobarz on 2011-12-18
Err, I still can't move buttons to the right side even using Ubuntu Tweak.

No I tried gnome session fallback, I'm good.

Might use MATE like in Linux Mint 12

But I will see how it goes

Another things, whenever I maximize my windows, the window controls go to the top panel. How do I restore the old behavior in natty?

---

### Post by lechien73 on 2011-12-18
If you open Ubuntu Tweak, and go to **Tweaks -> Window Management**, can you move the buttons to the right with that? I prefer the buttons on the left, but I have tested this on my Oneiric installation and it works.

---

### Post by Foobarz on 2011-12-18
Oh never mind thank you

---

### Post by Foobarz on 2011-12-18
Well, thank you all.

But still

WHY UBUNTU WHY
WHY WOULD YOU MAKE THE SETTINGS SO COMPLICATED??????
PLEASE 
RESTORE THE OLD APPEARANCE DIALOG

---

### Post by Foobarz on 2011-12-18
ACTUALLY I STILL HAVE ONE MORE PROBLEM

Maximized windows throw the window controls back to the left 
I already uninstalled the global appmenu
So what do I do now?

---

### Post by lolpenguin on 2011-12-18
You guys missed the obvious: _**GNOME Tweak Tool**_ [except for BC59]
```
sudo apt-get install gnome-tweak-tool
```
It contains settings hidden in GNOME Control Center.

---

### Post by lechien73 on 2011-12-18
Surely the gnome-tweak-tool would only apply if you were using Gnome3 instead of Unity?

When I tried installing it, it wanted to download a whole wodge of stuff including the Gnome shell.

---

### Post by bluexrider on 2011-12-18
> **lolpenguin said:**
> You guys missed the obvious: _**GNOME Tweak Tool**_ [except for BC59]
```
sudo apt-get install gnome-tweak-tool
```It contains settings hidden in GNOME Control Center.
if you are running in fallback this is useful but what does it do for unity?

---


---
title: "sreen brightness"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by Joseph5000 on 2008-07-22
How and where can I adjust my screen brightness. I have the same Ubuntu upgrade on my desktop, and it's way brighter. Additionally, the laptop I am talking about doesn't change brightness in regards to battery or AC power.
Any ideas out there??
thanks a lot

---

### Post by Joseph5000 on 2008-07-22
How and where can I adjust my screen brightness. I have the same Ubuntu upgrade on my desktop, and it's way brighter. Additionally, the laptop I am talking about doesn't change brightness in regards to battery or AC power.
Any ideas out there??
thanks a lot

---

### Post by Locutus_of_Borg on 2008-07-22
```
gnome-power-settings
```
and/or
```
gnome-power-manager
```
should give you screen brightness options

does your laptop not have a hardware key for this?

example: Fn + F8 adjusts my screen brightness

---

### Post by Joseph5000 on 2008-07-22
> **Locutus_of_Borg said:**
> ```
gnome-power-settings
```
and/or
```
gnome-power-manager
```
should give you screen brightness options

does your laptop not have a hardware key for this?

example: Fn + F8 adjusts my screen brightness

Thanks a lot, but Fn+F8 doesn't do anything. And where do I put the other commands??

---

### Post by a0u on 2008-07-22
There's a convenient Brightness [Applet]("https://help.ubuntu.com/community/Applets") that lets you adjust the brightness of the backlight via a slider.  Simply right-click on a panel and select "Add to Panel" to find it.

> **Joseph5000 said:**
> And where do I put the other commands??
Enter the commands inside a [terminal]("https://help.ubuntu.com/community/UsingTheTerminal") - go to "Applications -> Accessories -> Terminal".  Alternatively, you can access the GNOME Power Management through "System -> Preferences -> Power Management", but that's probably not what you are looking for...

---

### Post by Locutus_of_Borg on 2008-07-22
open a terminal and input each of those commands

a new window will open with options for screen brightness when on AC power or battery power

Fn+F8 ws just an example for my laptop, yours likely has something different

---

### Post by Joseph5000 on 2008-07-22
Found applet, but doesn't respond. When I move the mouse over it says "can not get laptop panel brightness"

---

### Post by a0u on 2008-07-22
> **Joseph5000 said:**
> Found applet, but doesn't respond. When I move the mouse over it says "can not get laptop panel brightness"

Apparently, the brightness applet [doesn't work for all laptops](http://ubuntuforums.org/showthread.php?t=559528).  But, as Locutus_of_Borg said, your laptop would likely have some brightness keys built in, but this varies from model to model.  Try doing an Internet search.

---

### Post by Joseph5000 on 2008-07-22
Thanks a lot

---

### Post by a0u on 2008-07-22
> **Joseph5000 said:**
> Thanks a lot
Did you get it to work?  For example, on my Dell laptop, the key combination is Fn + Arrow Up/Down.  If not, can you post some information about your laptop model?

---

### Post by ConMan318 on 2008-07-22
Right-click the top panel, then click 'add to panel'.  Then add the 'brightness applet'.

As far as power saving goes (which I assume you are referring to), System > Prefs > Power Management has settings for both AC power and battery power.  If you want the screen to dim when on battery power, click the 'on battery power' tab and check/uncheck the bottom options as you see fit to dim it when unplugged.

---

### Post by sdennie on 2008-07-23
Threads merged.  Please don't double post.

---

### Post by deadlySniper on 2008-07-23
What type of laptop do you use?

---

### Post by omnibot on 2008-07-23
I have the exact same problem. I have keys on my lappy for screen brightness that do not work. 

the applet does nothing and i get the same error message. 

it's some kind of acpi problem that i have no idea how to fix. 

i'm on a compaq (hp) c700 with an ATI graphics card

---

### Post by the_fury on 2008-11-22
> **Locutus_of_Borg said:**
> ```
gnome-power-settings
```
and/or
```
gnome-power-manager
```
should give you screen brightness options

does your laptop not have a hardware key for this?

example: Fn + F8 adjusts my screen brightness

These don't work. Example:

```

thefury@Upstairs-Laptop:~$ gnome-power-settings
bash: gnome-power-settings: command not found

```

---


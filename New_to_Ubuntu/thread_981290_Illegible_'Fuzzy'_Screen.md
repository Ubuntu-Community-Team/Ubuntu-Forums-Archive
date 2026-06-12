---
title: "Illegible 'Fuzzy' Screen"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by beak02 on 2008-11-13
Hello,

Just installed ubuntu and encountered a massive problem on boot-up.  Basicly the screen is covered in lots of little horizontal lines that distort the picture and make it impossible to do anything.

Any assistance will be grately aprechiated.

---

### Post by handydan918 on 2008-11-13
> **beak02 said:**
> Hello,

Just installed ubuntu and encountered a massive problem on boot-up.  Basicly the screen is covered in lots of little horizontal lines that distort the picture and make it impossible to do anything.

Any assistance will be grately aprechiated.

1) Which version of Ubu?

2) What hardware?

---

### Post by CLomax on 2008-11-13
> **beak02 said:**
> Hello,

Just installed ubuntu and encountered a massive problem on boot-up.  Basicly the screen is covered in lots of little horizontal lines that distort the picture and make it impossible to do anything.

Any assistance will be grately aprechiated.

I think I know what you mean, is it just everything up until you get to your desktop or is it all the time? Anywho, it wouldn't hurt to try this:

> System -> Administration -> Hardware Drivers and making sure the drivers for your graphics card are installed if there are any there.
> Reboot

Failing that...

> Go to Applications -> Accessories -> Terminal and type in the following.
```
sudo gedit /etc/X11/xorg.conf
```
> Scroll down until you see 'Section "Screen"'
> After the line 'Defaultdepth    24' add the following...
```
SubSection "Display"
          Modes       "XXXX YYYY"
          Virtual      XXXX YYYY
EndSubSection
```
Where XXXX is your resolution width and YYYY is your height e.g.

```
SubSection "Display"
          Modes       "1440 900"
          Virtual      1440 900
EndSubSection
```
> Save the file and reboot.

Hope this helps!

---

### Post by beak02 on 2008-11-14
> **handydan918 said:**
> 1) Which version of Ubu?

2) What hardware?

1) Ubuntu Desktop 8.10
2) Running it on the windows partition of my hard drive(could be the problem but the official ubuntu website reconed it was ok), intel processer, 2GB RAM, 32bit graphics card (no i didn't get 64bit by mistake)

---

### Post by beak02 on 2008-11-14
> **CLomax said:**
> I think I know what you mean, is it just everything up until you get to your desktop or is it all the time? Anywho, it wouldn't hurt to try this:

> System -> Administration -> Hardware Drivers and making sure the drivers for your graphics card are installed if there are any there.
> Reboot

Failing that...

> Go to Applications -> Accessories -> Terminal and type in the following.
```
sudo gedit /etc/X11/xorg.conf
```
> Scroll down until you see 'Section "Screen"'
> After the line 'Defaultdepth    24' add the following...
```
SubSection "Display"
          Modes       "XXXX YYYY"
          Virtual      XXXX YYYY
EndSubSection
```
Where XXXX is your resolution width and YYYY is your height e.g.

```
SubSection "Display"
          Modes       "1440 900"
          Virtual      1440 900
EndSubSection
```
> Save the file and reboot.

Hope this helps!

Thanks but i can't get that far into Ubuntu.  I only managed to get past the log in screen because I guessed what it said (and that too several attempts:))

The screen is completely illegible from the point that the orange logo boot up screen disappears.

---

### Post by CLomax on 2008-11-14
> **beak02 said:**
> Thanks but i can't get that far into Ubuntu.  I only managed to get past the log in screen because I guessed what it said (and that too several attempts:))

The screen is completely illegible from the point that the orange logo boot up screen disappears.

Ah, I see. Not a problem if you don't mind getting into the command line...

> CTRL + ALT + F1
> Log in with your credentials
> Instead of ```
sudo gedit /etc/X11/xorg.conf
``` do ```
sudo nano /etc/X11/xorg.conf
```
> Follow the previous instructions from there.

;)

EDIT: Hopefully the command line won't be illegible...

---


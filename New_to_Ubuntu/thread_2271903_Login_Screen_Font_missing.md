---
title: "Login Screen Font missing"
date: 2015-04-02
forum: New to Ubuntu
---

### Post by Sreedhar_Aravindd on 2015-04-02
The fonts are messed up in my login screen, what could be the issue?


Ubuntu 14.04 LTS 64bit.





[IMG]http://img.photobucket.com/albums/v355/redenex/DSC_0007_zpseszzpamv.jpg[/IMG]

---

### Post by dino99 on 2015-04-02
with 'localepurge' check that the needed fonts are active (sudo localepurge)
are you using some 'extra' source packages ?

you can also run:
sudo apt-get update
sudo apt-get install -f 
sudo dpkg --configure -a

---

### Post by Sreedhar_Aravindd on 2015-04-02
Did all of the above, but no luck yet :)

Anything else that I could be missing?

---

### Post by Vladlenin5000 on 2015-04-02
Have you installed additional desktops like Gnome? If so, how?

---

### Post by kyletstrand on 2015-04-02
Not sure if this will relate to your issue, but I found a similar issue:

[http://ubuntuforums.org/showthread.php?t=2174363](http://ubuntuforums.org/showthread.php?t=2174363)

---

### Post by Sreedhar_Aravindd on 2015-04-02
> **Vladlenin5000 said:**
> Have you installed additional desktops like Gnome? If so, how?

Yes I use GNOME, but it was working fine, still is.


This issue is found only on the login screen. This started to appear after I installed fonts (TTF fonts from Windows).

---

### Post by Sreedhar_Aravindd on 2015-04-02
> **kyletstrand said:**
> Not sure if this will relate to your issue, but I found a similar issue:

[http://ubuntuforums.org/showthread.php?t=2174363](http://ubuntuforums.org/showthread.php?t=2174363)

Thanks, but not of help with my issue :)

---

### Post by Vladlenin5000 on 2015-04-02
> **Sreedhar_Aravindd said:**
> This issue is found only on the login screen. This started to appear after I installed fonts (TTF fonts from Windows).

Interesting... It should not interfere with anything else unless a) you changed the font for login screen to one of the Microsoft TTFs and b) the fonts weren't installed properly.

---

### Post by Sreedhar_Aravindd on 2015-04-02
> **Vladlenin5000 said:**
> Interesting... It should not interfere with anything else unless a) you changed the font for login screen to one of the Microsoft TTFs and b) the fonts weren't installed properly.

No I have not replaced any system FONTS with MS fonts.

As for the proper installation, well all the installed fonts works otherwise (on GIMP and other applications). But thanks, this is one aspect I shall check again.

Definitely will update what I find. Thanks again.

---

### Post by Sreedhar_Aravindd on 2015-07-28
Guys, any further help with this, please?

---


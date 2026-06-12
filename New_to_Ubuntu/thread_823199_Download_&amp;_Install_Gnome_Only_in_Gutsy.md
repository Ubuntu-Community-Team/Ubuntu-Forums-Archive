---
title: "Download &amp; Install Gnome Only in Gutsy?"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by bettyhills on 2008-06-09
Is it possible to Download & Install GNOME ALONE in Gutsy 7.10? 

My Ubuntu GG was hosed by the 6/3 automatic update.  Trying to get back to functioning, I followed forum directions that  deleted the gnome packages on my PC (I believe but am not certain.)

Right now, I can boot into the graphical environment and get to the File Browser on top of the EMPTY tan Desktop.  There are no panels, nor menus, nor buttons for trash or shutdown, etc.  Help!!!  I would like to try to get all that back.  I am a total beginner... it is gnome that I want isn't it?

Is it possible to Download & Install GNOME ALONE in Gutsy 7.10? In other words, download it separately from a complete Linux installation.  Just Gnome by itself?

Where can I get it?

Also, from the Recovery Mode, exactly what commands would I use to install the Gnome packages? 

Is there a better way to get everything back?  

Any advice will be greatly appreciated.

---

### Post by SunnyRabbiera on 2008-06-09
yes, there is a way to get gnome's base packages by installing gnome-desktop-environment via the repositories.

---

### Post by Xiong Chiamiov on 2008-06-09
I'm assuming that your internet connection works fine.

I believe that from the recovery console, you have no internet connection.  However, if you boot normally, you can press ctrl+alt+f1 to get to a command prompt that will have everything initialized (meaning, you can download packages).

To install GNOME, run the command
```

sudo aptitude install gnome-core

```

---


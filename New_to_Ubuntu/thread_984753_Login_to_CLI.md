---
title: "Login to CLI"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by transmition on 2008-11-16
I was wondering how I could go about logging directly into the full screen terminal, bypassing gnome so that I would be running a pure CLI system, without a GUI. 

Also, would this be less resource intensive?

---

### Post by Sorivenul on 2008-11-17
First, I would backup your data.  Then there a couple of ways to go about this.

#1. Do a minimal install (there is a CLI only option on the Mini ISO and Alternate CD).  This will give you a CLI-only system "out-of-the-box".  A server install would also work, I suppose.  You could dual-boot this with your current setup.
#2. Remove GDM, which is the graphical login screen.
#3. Install sysv-rc-conf (available in the repositories), run it, and deselect GDM in all runlevels after making note of where it was on to begin with.  When and if you want GDM back, simply run sysv-rc-conf again and return the default settings for GDM.

#3 is my preferred method as it doesn't remove anything, and doesn't do anything that cannot easily be undone.  

As far as resource intensiveness, you're talking about a full X session like GNOME or KDE vs the CLI.  There should be major resource differences, with the CLI being much less intensive.  You will probably want to install a few "must have" CLI applications such as "screen", "htop", a browser like "elinks" or "links2", "finch" which is the CLI version of Pidgin, etc.  

Good luck, and cheers!

---

### Post by transmition on 2008-11-18
Would there be a way to start the GUI after I log into the CLI as opposed to re-enabling GDM? Something along the lines of
```
start GDM
```

---

### Post by Sorivenul on 2008-11-18
> **transmition said:**
> Would there be a way to start the GUI after I log into the CLI as opposed to re-enabling GDM? Something along the lines of
```
start GDM
```
Should do the trick:
```
sudo /etc/init.d/gdm start
```

---

### Post by cardinals_fan on 2008-11-18
> **transmition said:**
> Would there be a way to start the GUI after I log into the CLI as opposed to re-enabling GDM? Something along the lines of
```
start GDM
```
Well, you can start up your desktop with "startx" (assuming you have a valid .xinitrc file).  If you want to restart GDM, Sorivenul has the answer above.

---


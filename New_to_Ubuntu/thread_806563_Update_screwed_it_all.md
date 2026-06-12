---
title: "Update screwed it all"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by sayakb on 2008-05-25
Yesterday, I installed Xubuntu 7.10 on an old pc:
Celeron 633MHz
374MB SDRAM
80GB IDE Hard drive
Intel 810 mobo
1999 BIOS (Which shows "Force ACPI as BIOS 2000 cutoff fails" each time Xubuntu is loaded)

I was working all fine until I installed 156MB of updates. Just after updating, it told me to restart and thats what I did. After I restarted, I couldn't see my desktop icons (it was just orange) though the panels were there. Evidently, thunar was not loaded. So I tried to open Terminal, but doing so just loogged me out and returned me back to GDM. So I can't open any of my drives now, and neither can I open the terminal.

---

### Post by lswest on 2008-05-25
does ctrl+alt+F1 give you tty0?  if so, you can run ```
dpkg --configure -a
``` and see if it fixes anything, or just do ```
sudo apt-get update
sudo apt-get install -f
sudo apt-get upgrade
```  Otherwise you could reinstall thunar with ```
sudo apt-get install --reinstall thunar
```

---

### Post by sayakb on 2008-05-25
I don't seem to have broken packages. Plus, my software sources are up-to-date and all my packages are configured. Should I post the output of these commands?

---

### Post by plucky on 2008-05-25
> So I tried to open Terminal, but doing so just loogged me out and returned me back to GDM. So I can't open any of my drives now, and neither can I open the terminal.

There is a problem in Xubuntu Gutsy with using the terminal.The work around is to set the default depth in xorg.conf to 16 from 24.To do so CTRL+ALT+F1
and ```
sudo dpkg-reconfigure xserver-xorg
``` Go through until default depth and select 16.Logout and restart system.


Or if this doesn't work do ```
sudo apt-get install gnome-terminal
``` as gnome-terminal works.

Once the terminal is working open one and input ```
xfce4-panel
``` to see if your panels startup.

Good Luck

---

### Post by sayakb on 2008-05-25
Unfortunately, I reinstalled Xubuntu again, so the thunar problem is solved. Though I would try out the terminal issue. Thanks :)

---


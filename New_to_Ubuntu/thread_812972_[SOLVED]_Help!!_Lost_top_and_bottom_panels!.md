---
title: "[SOLVED] Help!! Lost top and bottom panels!"
date: 2008-05-30
forum: New to Ubuntu
---

### Post by Sealbhach on 2008-05-30
Most alarming. I installed some updates (after ticking an extra box in the sources in Synaptic). My computer seems to be running fine, except I can't get into Nautilus or see any files.

The compiz cube is working - so I can see it's not a resolution problem.

When I type gnome-panel in the terminal I get:

> 
oliver@oliver-vaio:~$ gnome-panel
The program 'gnome-panel' is currently not installed.  You can install it by typing:
sudo apt-get install gnome-panel
bash: gnome-panel: command not found
oliver@oliver-vaio:~$ 


When I type sudo apt-get install gnome-panel I get:

> oliver@oliver-vaio:~$ sudo apt-get install gnome-panel
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  gnome-panel: Depends: gnome-about (>= 2.10.0-1) but it is not going to be installed
E: Broken packages
oliver@oliver-vaio:~$ 


How do I get my panels back?



.

---

### Post by wpshooter on 2008-05-30
Have you tried booting into recover mode.  And then restart into regular mode.

That happened to me once when I was configuring a computer for my brother-in-law.  Very disturbing occurence.

Good luck.

---

### Post by Sealbhach on 2008-05-30
It didn't work, but thanks. Anyone else? Can I just re-install the gnome desktop somehow?



.

---

### Post by quelx on 2008-05-30
```
sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop
```

---

### Post by Sealbhach on 2008-05-30
Yes, that did the trick!  Thank you!

You can mark this one solved. I had ticked the "proposed updates" box in Synaptic and it seems a newer version of a gnome component caused a problem.

Brilliant ubuntu from you all again. :)


.

---

### Post by david tutton on 2008-06-02
> **quelx said:**
> ```
sudo apt-get update
sudo apt-get --reinstall install ubuntu-desktop
```

Thank you too. Because I use thunderbird mail, I decided to remove evolution. However I should not have removed evolution common which is an integral part of the Gnome desktop. Reinstalling as above solved my problem.
Thanks again :):)

---


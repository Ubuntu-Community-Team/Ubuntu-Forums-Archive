---
title: "[SOLVED] WM no longer runs at startup"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by rockerphil on 2008-05-21
ok, i don't know if this has been asked before, but i'll ask it again. here's what happened. i started playing with various minimalist windows managers like IceWM and Openbox, and ultimately decided to stick with the WM that came with my OS, Fluxbox. well here's the problem, after removing the other WMs Fluxbox no longer runs at startup, so when i punch in my user name and password it gives me a command prompt interface in the corner of my screen from where i can start my WM, but here's the problem, once Fluxbox starts that same command line turns in to a terminal, which if i close out, it kills fluxbox, thus bringing me back to my log in screen. any way y'all can help me put Fluxbox back on my startup? any help would be much appreciated

---

### Post by rockerphil on 2008-05-21
bump. could really use some help on this one guys thanx :)

---

### Post by kellemes on 2008-05-21
> **rockerphil said:**
> bump. could really use some help on this one guys thanx :)

You're using GDM as a login manager?
Have you set your session to Fluxbox? Somewhere in your login screen there should be a button/link to set your default session.

---

### Post by rockerphil on 2008-05-21
not too sure what i'm using as my login manager, i'm using Fluxbuntu on an old Dell Dimension desktop with 128 MB of SD RAM and a 500 MHz Intel Pentium processor. so it's a pretty minimalist install

---

### Post by kellemes on 2008-05-21
> **rockerphil said:**
> not too sure what i'm using as my login manager, i'm using Fluxbuntu on an old Dell Dimension desktop with 128 MB of SD RAM and a 500 MHz Intel Pentium processor. so it's a pretty minimalist install

Just found out fluxbuntu uses SLim as a login manager..
Isn't there some option where you can choose your default session (wm)?

---

### Post by rockerphil on 2008-05-21
not that i can find, like you said, Fluxbuntu uses Slim as it's login manager, so it's basically just a good looking place to punch in your user name and password, the only option i can think of is to completely remove then reinstall Fluxbox, and hopefully that'll make it my default manager again

---

### Post by rockerphil on 2008-05-21
damn, nope. just reinstalled Fluxbox and rebooted. still gotta launch Fluxbox from the terminal upon boot-up. any suggestions guys?

---

### Post by kellemes on 2008-05-21
> **rockerphil said:**
> damn, nope. just reinstalled Fluxbox and rebooted. still gotta launch Fluxbox from the terminal upon boot-up. any suggestions guys?
Just guessing..
Reinstall SLim?

---

### Post by rockerphil on 2008-05-21
problem solved, thanx man, the help was much appreciated

---

### Post by harrybazeegar on 2008-05-21
well you could examine your /etc/inittab file, for onething.

there would be a statement that says
```

id:<some number>:initdefault:

```

this number defines what kind of login your comp will do.
If this number is the starting 'runlevel' of your computer.
# runlevel 0  is  System halt   (Do not use this for initdefault!)
# runlevel 1  is  Single user mode
# runlevel 2  is  Local multiuser without remote network (e.g. NFS)
# runlevel 3  is  Full multiuser with network
# runlevel 4  is  Not used
# runlevel 5  is  Full multiuser with network and xdm
# runlevel 6  is  System reboot (Do not use this for initdefault!)

so if the runlevel is not 5, then the GUI will not come up on booting. 

simple as pie :)

cheers!

---


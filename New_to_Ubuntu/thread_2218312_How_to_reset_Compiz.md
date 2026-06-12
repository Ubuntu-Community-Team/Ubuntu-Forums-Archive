---
title: "How to reset Compiz?"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by fattyz on 2014-04-20
Hi all,  I totally wrecked my desktop last night just clicking around in Compiz.  I couldn't reconstruct or repair what I did but I think I changed a setting under the general tab, maybe in conjunction with changing another setting before things could take effect.  The desktop changed size, shrinking away from the sides of the monitor about an inch all around and things no longer responded to the mouse when it was directly over them.

I struggled back at any rate and now when I start a session just after log in the screen magnifys to the upper left corner of the wallpaper then the desktop.  What I end up with is the upper left corner if you had divided the desktop by 4. Luckily I can run a terminal.  I also have the metacity and I assume unity sessions that are fine.

My question is, can I reset things to default or correct this in some other way?  I don't think I could get to software center or synaptic with the desktop the way it is and I really don't know how to uninstall through terminal.   Perhaps I could uninstall ccsm and re install? 

Thanks so much in advance

---

### Post by grahammechanical on 2014-04-20
To reset Compiz

```
dconf reset -f /org/compiz/
```

to reset unity in 13.10 14.04

```
setsid unity
```

Synaptic Package Manager has a "mark for re-installation" option.

Regards

---

### Post by fattyz on 2014-04-20
Thanks so much.  I got to a unity desktop after I ran this (when I clicked on gnome-flashback).  So I uninstalled gnome flashback and fallback with synaptic, reboot and re-install and I have the same thing.  When I log in with gnome-flashback session I get a unity desktop.  It's an incomplete unity desktop because the panel is not there but it's a unity desktop. 

Edit:  You know what it's more than just that, the Unity session desktop is a mess as well.  I am going to uninstall ccsm and re install.  If that won't work I think it's time to run install 14.04 again.  

I'll let you know.  I really hope I don't have to start over.  It takes so long to put humpty dumpty back together again!

Yours

---

### Post by fattyz on 2014-04-20
Well, I've done it now.  I know this is getting away from the original question (which you solved) but now ... I'm running off the install disk.  I was unable to log in at all.  I'd like to try one more thing and re-install from the disk but it will not allow me this choice (it's greyed out)  If I allow it to delete my install and start fresh (which there is a good possibility I'll end up doing anyway) that's going to cost me lots of work.

Is there a way to just re install?

EDIT:  I got it, tried a couple more times and the disk allows me to re-install saving my current files.

I'll let you guys know how I make out wish me luck!  (What did I do before I had all these computers and cell phones?)

Thanks again

---

### Post by fattyz on 2014-04-20
Fresh Install.

After the re-install there were a couple real obvious problems so, rather than spend more time on something so obviously broken, I figure i'm better off starting over.  Besides, I have all my recent threads here which should allow me to get back to where I was last night, before those ill advised keystrokes, in half the time!

**EDIT**  It is worth noting that after a clean install what took me a couple weeks to set up the first time through only took me a couple hours.  Everything is up and running now and I have just about everything I downloaded before.  So, blow your install up often!  That way you'll remember how you set everything up last time.

Thanks again

Yours,

---


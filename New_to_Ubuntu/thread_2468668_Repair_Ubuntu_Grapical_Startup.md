---
title: "Repair Ubuntu Grapical Startup"
date: 2021-11-07
forum: New to Ubuntu
---

### Post by philly1ms on 2021-11-07
So I was messing around with trying to get VNC working and when I installed lightdm all hell broke loose and now Ubuntu won't start properly when rebooted.  I removed lightdm but my gnome session won't start unless I boot into recovery and startx.  Not sure if that's even running gnome because my second monitor no longer displays.  Any help with repairing my log in session?  Thank you

I'm running Ubuntu 20.04.3 64-bit 
Gnome Version is 3.36.8

---

### Post by tea for one on 2021-11-07
Have you tried this via a terminal:-
```
sudo dpkg-reconfigure gdm3
```

---

### Post by philly1ms on 2021-11-07
When I do that I get:

 gdm.service is not active, cannot reload.
invoke-rc.d: initscript gdm3, action "reload" failed.

---

### Post by tea for one on 2021-11-07
Have you rebooted?

---

### Post by grahammechanical on 2021-11-07
Try rebooting into recovery mode>Root - Root shell prompt and then running the command to reconfigure GDM3.

When you installed LightDM you also configured it and that process disabled GDM3. Then you removed LightDM and now you do not have a working display server to present the login screen. The correct procedure would have been to configure GDM3 and then remove LightDM after first making sure that GDM3 was working. I think that configuring GDM3 before the desktop loads might work. You may even need to re-install GDM3.

Regards

P.S. I do not think that LightDM is crafted to load Gnome 3 shell. I would load Unity 7 if that user interface was installed.

---

### Post by philly1ms on 2021-11-07
I'm up and running.  The reboot got me back into Gnome desktop.  Thanks for the help and information.  I really want to give up Windows completely.

---

### Post by tea for one on 2021-11-08
> **philly1ms said:**
> I'm up and running.  The reboot got me back into Gnome desktop.
That's good news.
It is useful to mark the thread as solved to help other forum members/searchers.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---


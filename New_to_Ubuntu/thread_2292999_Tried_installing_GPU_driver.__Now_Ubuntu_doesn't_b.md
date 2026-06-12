---
title: "Tried installing GPU driver.  Now Ubuntu doesn't boot"
date: 2015-09-01
forum: New to Ubuntu
---

### Post by andrew257 on 2015-09-01
Hi everyone, I'm new to Linux.  I decided I should probably give it a go on my PC since I will be using it a lot in my classes.  

One of the first things I wanted to take care of was getting my display drivers installed so I could install Steam.  After attempting the installation for a little while, I thought I had it right.  After I performed *aticonfig --initial*, I was recommended to restart the computer.  However, on booting up, the system freezes in the loading screen.  Does anybody have a solution to at least get the system running again?

More information:

[COLOR=#000000]Using Ubuntu Gnome 15.04[/COLOR]

[COLOR=#000000]This is a desktop[/COLOR]

[COLOR=#000000]GPU: R9 280X[/COLOR]

[COLOR=#000000]How I installed: Downloaded proprietary driver, tried sudo sh [installation file][/COLOR]
[COLOR=#000000]Terminal says I'm missing dependencies. I install those dependencies and try again. This time it seems to work. Then I run sudo aticonfig --initial in the terminal as recommended. Then I restarted the system leading to the problem.[/COLOR]

*I'm not sure if this was the correct subforum to post in.  Feel free to move this post to wherever it belongs.*

---

### Post by QIII on 2015-09-01
Hello!

Which release are you using?

Is this a desktop or a laptop?

Dedicated, integrated or hybrid graphics?

What model (s) of GPU?

What instructions did you follow in installing?

---

### Post by andrew257 on 2015-09-01
Using Ubuntu Gnome 15.04

This is a desktop

GPU: R9 280X

How I installed:  Downloaded proprietary driver, tried sudo sh [installation file]
Terminal says I'm missing dependencies.  I install those dependencies and try again.  This time it seems to work.  Then I run sudo aticonfig --initial in the terminal as recommended.  Then I restarted the system leading to the problem.

Link to webpage I found this at: [http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx](http://support.amd.com/en-us/kb-articles/Pages/Catalyst-Linux-Installer-Notes.aspx)

---

### Post by QIII on 2015-09-01
It might be worth your while to uninstall the driver you got from AMD's website and install the one in the Canonical repo.  It is the one that was current at the time 15.04 was released and I can say for certain it works with an R9 290X under 15.04.

I'm on my cell phone right now and details would be hard to provide.  If someone hasn't gotten back to you, I'll try to answer you after dinner tonight on the US West coast.

---

### Post by andrew257 on 2015-09-01
Unfortunately, that may be a bit tough to do when the system is frozen in the boot up screen whenever I try to turn it on.

---

### Post by QIII on 2015-09-01
Removing that driver, removing the xorg.conf and re-installing some open source packages can be done easily from the terminal in recovery mode.

You won't need to log in to the desktop.

---

### Post by andrew257 on 2015-09-01
Good news, I managed to get the system running again by repairing the packages from recovery mode!  The driver I installed even appears to be working.

---

### Post by QIII on 2015-09-01
Excellent!  If you would, please mark the thread solved so others with similar problems can find it.

There is a drop-down under "Thread Tools" for doing that.

Cheers!

---

### Post by Geoffrey_Arndt on 2015-09-01
Comment & recommendation for OP . . . IF the next kernel update breaks your graphics, . . . using the standard driver install process via System Settings>Software & Updates>Additional Drivers (tab) should correct that and stay persistent in future kernel level updates.   Changing the Windows mindset to a Linux mindset takes some time (e.g. using the distro's official source repos 1st versus various web sources (even including vendor sites)).

---


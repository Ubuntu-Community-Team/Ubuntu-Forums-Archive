---
title: "Log in screen problem"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by gj_clt on 2008-04-27
I followed the upgrade path to install 8.04. Mostly everything is O.K. however when I reach the log in screen all I see is on the right hand side of the screen. The letters UBU and part of the N is visible. In the bottom right hand corner I can only just see the user name box. I can log on. System is a P4 2.0Ghz, 2gig memory, Nvidia 6600gt, soundblaster 5.1. Would a clean install sort this?

---

### Post by southernman on 2008-04-27
You say you *can* log on?

It's a screen resolution, x, and/or graphic card problem for sure! uh duh, right!!!

Have you ever reconfigured the xserver? It's not difficult, but you can hose x if you zig instead of zag.

See this well laid out howto, right here on the forums:
[http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

Before you reconfigure x, gather all the info on your video card (drivers needed) and your monitors resolution sizes and horizontal/vertical refresh rates.

It's pretty basic and *most* of the screens have the right info already.

Enjoy

---

### Post by unbuntued on 2008-04-27
Possibly, you're having trouble with the graphics driver.
Type CTRL+ALT+BACKSPACE in the login screen. Does this get correct the screen?

---

### Post by southernman on 2008-04-27
> **unbuntued said:**
> Possibly, you're having trouble with the graphics driver.
Type CTRL+ALT+BACKSPACE in the login screen. Does this get correct the screen?Doesn't that kill the xserver? Don't think that's what were shooting for, is it?

In fact, to prevent it from happening accidentally, see this link:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html)

---

### Post by unbuntued on 2008-04-27
> **southernman said:**
> Doesn't that kill the xserver? Don't think that's what were shooting for, is it?

In fact, to prevent it from happening accidentally, see this link:
[https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html](https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/disableCtrlAltBackspace.html)
It does kill it and then restarts it.
I experienced some problem with my ATI driver: sometimes when I boot, I see a distorted login screen, the solution I used to get back to a human-readable login screen is CTRL+ALT+BACKSPACE.

---

### Post by southernman on 2008-04-27
I see. Thinking back on it, now recall doing that in my earlier days with Ubuntu and nearly shite a gold brick when it dumped me into a console. Didn't know to just do "startx"

Knock on wood, I've not had a lockup or x problem since Fiesty. Raising elephants can be strenuous work.

Of course, have not updated to hardy heron yet. Well see if the crows come home to roost or not. ;) pun intended

---

### Post by gj_clt on 2008-04-27
Thanks Southernman.
I'm printing off the instructions now and will have a go this evening. Will post back later.

---

### Post by gj_clt on 2008-04-28
Looks as if the problem is my Compaq monitor. I borrowed a Benq from a friend and it works fine. I will probably replace it although I can log on and use the system just a little odd at start up.

---

### Post by southernman on 2008-04-28
> **gj_clt said:**
> Looks as if the problem is my Compaq monitor. I borrowed a Benq from a friend and it works fine. I will probably replace it although I can log on and use the system just a little odd at start up.
What make of compaq system do you have?

Do not go throwing in the towel on this. I've read countless threads on this board with similar problems as your having. Some were more difficult to fix than others. Guess there is a 97+ % chance, this can be resolved.

If you don't know what hardware is in your computer, just post the model number of it (or you can search google and give us a link to your exact system.

---

### Post by thedoorguy on 2008-06-29
> **gj_clt said:**
> I followed the upgrade path to install 8.04. Mostly everything is O.K. however [COLOR="Blue"]when I reach the log in screen all I see is on the right hand side of the screen. The letters UBU and part of the N is visible. In the bottom right hand corner I can only just see the user name box. I can log on.[/COLOR] System is a P4 2.0Ghz, 2gig memory, Nvidia 6600gt, soundblaster 5.1. Would a clean install sort this?

I have the same problem... different equipment... same problem.

Once logged on everything including advanced effects work great.  The login screen is distorted no matter what screen resolution I set. Its hard to believe its a driver problem since it appears to affect only the login screen.

I just build the puter.  It has P4 2.2 Dual Core, 1 gig DDR2 667 Ram, on board 6.1 surround sound and built in Nvidia 7050 gpu video that shares up to 500MB ram. I'm using a Viewsonic A75f monitor.  I plugged in an HD from my old system that had 8.04 installed.  The login screen worked fine using a default driver, default screen combo in x server.  The distortion started when EnvyNG installed the correct nvidia driver monitor combo.   

Well... that's my story and I'm sticking to it. :)  Would appreciate a fix.  I hate it when things don't work right.  

Thanks.... thedoorguy aka Richard

---


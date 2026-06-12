---
title: "Screensaver problem with Hardy Heron"
date: 2008-05-12
forum: New to Ubuntu
---

### Post by Older1 on 2008-05-12
I just recently upgraded three systems to Hardy Heron from 7.10; one, an older Gateway laptop that ran 7.10 well with no issues. The other two systems are custom built desktops that also had 7.10 installed and worked very well. (I did a clean install on these two systems) Now all three systems refuse to start ANY screensaver, and also don't go into power saver mode. I've tried several of the screensaver choices, and none of them work. I can do a preview of a screensaver, but when I leave Fullscreen mode and set the time to "Regard the computer as idle after x minutes", nothing happens, no screensaver, no "Put display to sleep after x minutes", NOTHING.

I'm not new to Ubuntu, having used versions from early on; neither am I an expert, but I'm getting very frustrated about this problem.

Your help, please? :confused:

---

### Post by Older1 on 2008-05-13
Problem solved!! 
Must have been one of the last updates that did it. Anyway, the screensaver starts as expected, and the monitor goes to powersave mode at the preset time interval.

---

### Post by chamb244 on 2009-02-13
I have not been able to get screensaver to work since installing Xubuntu 8.04 some 4 or 5 months ago.  It wasn't clear from your 2nd post what it was that may have gotten things to work.  Could you specify what kind of updates you did? Or does anyone else have any advice on how to get the screensaver working?  (previews okay, but no logical combination of screensaver and/or power saving settings seems to work - no screensaver, no blank screen, no changes at all.)

thanks in advance..

---

### Post by ubiDD on 2009-02-27
I'm having the same issue; it only started in the last few days thought.  The screen darkens at the requisite time but at the moment the screensaver should be active it pops back to normal desktop.
I've tried different screensavers, all of which are included with 8.04 LTS and also updating system, also checked against compiz - nothing affects this.  Also there isn't any errors in any log, at least not anything I'm recognizing as a screensaver error.

---

### Post by chen74 on 2009-02-27
i had a similar problem with my screen saver. when when it was time to activate my monitor just turned blank. 

I changed the screen resolution and eventually solved the problem. ;)

---

### Post by jon.reeve on 2009-03-01
I'm also having this problem on Intrepid. It looks like it's this bug with compiz and gnome-screensaver. Assuming you're running compiz, you might be able to use this workaround, it worked for me at least: 

- Go into System->Preferences->Compizconfig Settings Manager (if you don't have this, you may have to install it) 
- In "General Settings," uncheck the box "Unredirect fullscreen windows" 

Anyway, the discussion about this bug is [here]("https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/278112"): 

[https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/278112](https://bugs.launchpad.net/ubuntu/+source/gnome-screensaver/+bug/278112)

---

### Post by alecz20 on 2009-08-12
> **ubiDD said:**
> I'm having the same issue; it only started in the last few days thought.  The screen darkens at the requisite time but at the moment the screensaver should be active it pops back to normal desktop.
I've tried different screensavers, all of which are included with 8.04 LTS and also updating system, also checked against compiz - nothing affects this.  Also there isn't any errors in any log, at least not anything I'm recognizing as a screensaver error.


I hav the exact same problem on 8.10 The screen dims, but it returns back to normal screen.

Interestingly this does not happen every time, only now and then.

---

### Post by mdlueck on 2009-09-24
Same thing with Ubuntu 9.04 Jaunty and compiz disabled. (Disabled via System \ Preferences \ Appearance \ Visual Effects tab \ None)

When the bug happens, the screen dims but instead of the screensaver starting, the normal display comes back.

Also when this happens, power management is also "disabled". I have my screensaver time set to 10, and power management to 20, so I would expect after 20 mins the monitor would go to sleep but it does not.

Suggestions?

---

### Post by alecz20 on 2009-10-02
Are you by any chance on a laptop?

My setup is a bit special:

Laptop connected to external Display, but no external keyboard.

So when I am done with the laptop, I close the lid. However if I move the mouse before opening the lid, I get this problem next time the screensaver should come up.

The easiest way to go around this is to lock the screen via "Ctrl + Alt + L".

After doing this the screensaver problem is fixed until next time I close the lid and open the mouse.

I think the system gets confused by the option to turn off the screen when the lid is closed and by moving the mouse at the same time.

---


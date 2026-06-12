---
title: "unity-4.20 provides unique desktop experience"
date: 2011-09-29
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by mc4man on 2011-09-29
Just finished new install &  updated - 
[https://bugs.launchpad.net/ubuntu/+source/unity/+bug/862743](https://bugs.launchpad.net/ubuntu/+source/unity/+bug/862743)

---

### Post by MacUntu on 2011-09-29
They are probably just screwing with us testers to give us a nice adrenaline shot. :P

---

### Post by Gnobody on 2011-09-29
I can confirm this problem too, w/ ATI Catalyst drivers here

---

### Post by mc4man on 2011-09-29
Might as well do another new install with todays(29) image while waiting - actually was doing a new install to see why I didn't/don't see this 'fix released' - 
[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805252](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/805252)

& was curious if the new unity would 'fix' this recent issue, appears it does, except for rotate
[https://bugs.launchpad.net/unity/+bug/861088](https://bugs.launchpad.net/unity/+bug/861088)

---

### Post by xyzzyman on 2011-09-29
Happened to me. 'unity -reset' and reboot fixed it, although I also reinstalled my nvidia driver at a recovery prompt to a graphical glitch at start up, so it was one of the two that took care of it.

EDIT: Rebooted and once again doing the same thing.

---

### Post by cwhebert on 2011-09-29
Just after the most recent update of 11.10 beta2 the background screens are offset to the lower right corner.  A third of the screen in the upper left corner is left black.  However, when I run a program is fills the screen normally.  Only blank screens are offset.  I am using an AcerOne netpc.

Any ideas?

---

### Post by s0m3f00l on 2011-09-29
I have the same issue... I don't think netbooks are very popular in the Ubuntu 11.10 crowd...

---

### Post by __lonewolf on 2011-09-29
After the update today, something fall down and go boom.  After the update I rebooted the machine and when I logged in, the desktop was shifted to the right and down.  Some apps wont' start or start but are in the gap between the unity bar and the desktop image.  Terminal is stuck right up at the upper corner.  

Things I have tried so far.
1. Tried unity --reset, didn't change anything except make the icons back to the default size on the bar.

2. Rebooted and went to a terminal.  Removed, purged and reinstalled nvidia drivers, log back in and no difference,

Good thing is now I can click on the icon and software center comes up and doesn't crash right away, but can't do much else.  

The gap between the unity bar and the edge of the desktop is about 5 inches.

Any ideas?

---

### Post by xyzzyman on 2011-09-29
[http://ubuntuforums.org/showthread.php?t=1852187](http://ubuntuforums.org/showthread.php?t=1852187)

---

### Post by collisionystm on 2011-09-29
Hit the auto adjust on your monitor

---

### Post by __lonewolf on 2011-09-29
Thanks for the link xyzzyman.  Will watch the other thread and bug thread for updates.

Thanks

---

### Post by xyzzyman on 2011-09-29
I used system monitor to kill the nautilus process, then alt-f2 for a run box and restarted nautilus, and it is now located properly after two reboots. Checked launchpad but no bug submitted. If this fix doesn't work for everyone, then you'll have to submit the bug as unfortunately mine is fixed.

---

### Post by xyzzyman on 2011-09-29
[http://ubuntuforums.org/showthread.php?t=1852187](http://ubuntuforums.org/showthread.php?t=1852187)

Can you try what kill the nautilus process and then restarting it? It's what seems to have fixed it for me. Even after updating drivers and a unity --reset.

---

### Post by __lonewolf on 2011-09-29
I tried what you did and it gets it back for the session, but as soon as I logout and login, it goes back to messed up.  Some things I noticed which are making me wonder if I need to reinstall.   

Running unity --reset show messages dbus errors that it can't find things.  At least 2 unity icon files are missing.  window borders are missing from my terminals.  Can't start firefox, cssm, etc.

When I run sudo-apt get update && sudo apt-get upgrade, it shows me 9 packages that are being held back and nothing to install.  When I run update-manager, it shows me 106 packages to be loaded, including the linux kernel 3.0.0.12.13.  Which of these do I believe?

---

### Post by cariboo on 2011-09-29
merged two threads on the same subject.

Did the search engine stop working? :) :) :)

merged another thread.

---

### Post by mc4man on 2011-09-29
The workaround in comment 12 will  pretty much restore use for the session, though it may produce a unity-panel-service crash 
(there is a fix committed already - 

Using 4.20 for a moment am disappointed to see the no blur is again, hopefully  for the moment,   transparent

4.20 has quite a # of bug fixes that would be worth checking to see if as advertised

---

### Post by Vrroom on 2011-09-30
This bug has been fixed upstream. Now we need a cherry pick fix or will have to wait for next milestone release on 4th October. 

This actually has given me the chance to try Unity 2D for longer time and I am really digging the speed :)

---

### Post by MacUntu on 2011-09-30
It has been cherry-picked and is about to be uploaded. :-)

---

### Post by xyzzyman on 2011-09-30
It's in the repo ready for download!

Changes for the versions:
Installed version: 4.20.0-0ubuntu1
Available version: 4.20.0-0ubuntu2

Version 4.20.0-0ubuntu2: 

  * Merge trunk:
    - Desktop drawn with offset (LP: #862743)

---

### Post by alphacrucis2 on 2011-09-30
When I saw this thread, I thought ok, I'll not bother installing any offered unity updates for now. Nice to see the quick response from the devs.

---


---
title: "Ubuntu Keeps Turning Itself Off"
date: 2020-06-10
forum: New to Ubuntu
---

### Post by tomblue on 2020-06-10
This is my first post here. My Windows system is so old, it’s no longer being supported. This causes problems in accessing some websites, and this is why I’m trying out ubuntu 18.04.2. It works fine for what I use online, but strange things happen that I don’t understand, and I hope someone here can help me. 
 
Once while online, the computer kept switching back to the desktop mode. I would switch it back, but after a few minutes, it would switch back again. This went on for a while, then the computer turned itself off. I was able to restart and continue on, but I can’t figure out what happened. 
 
Another time, I was offline and working on a text document, when the monitor screen started turning a light pink. This wasn’t a background color. It covered the whole screen and slowly turned a dark red and I could barely see my text document. Then the the computer turned itself off again. 
 
I thought this might be some kind of screen saver function, but I couldn’t find anything in the control panel search. I don't know my way around much in this system, and my search online only resulted in a one page intro to the basics of this system, and did not help.
 
Anybody have an idea what’s going on here? 
 
Tom

---

### Post by CelticWarrior on 2020-06-10
Welcome.

> My Windows system is so old, it’s no longer being supported. This causes problems in accessing some websites

If it's out of support it shouldn't be used in any way that implies internet connection, period. The "problems in accessing some websites" is the least of your problems. Unpatched software can be easily hacked, your personal data stolen, used and abused and your computer can be used for nefarious purposes (read criminal activities) in the net. It's therefore very dangerous for you personally and very irresponsible.

Using a current and supported release of Ubuntu, periodically updated, is the way to go if it works fine in your computer. Being "so old" the current and supported version of Windows is likely not compatible.

> the monitor screen started turning a light pink. This wasn’t a  background color. It covered the whole screen and slowly turned a dark  red and I could barely see my text document. Then the the computer  turned itself off again.

This means hardware failure. It isn't related to the OS. Or is but only to the point that the new Ubuntu is pushing the limits of the old hardware and because of that triggering failures that weren't apparent with the "old Windows". If you could run a modern and current Windows there it would likely show the some problems and perhaps sooner and harder.

In conclusion, your computer needs repairs or, better yet, a replacement. The cost of repairs, assuming it is repairable, can easily exceed the price of a new, much more energy efficient and also much faster and capable, computer.

---

### Post by tomblue on 2020-06-10
I'm aware of the danger with using my old system. I have no personal data on my computer, and everything is backed up on a remote drive. The mother board has been updated recently and runs very fast, and causes no problems.

 The ubuntu software is installed on a separate computer that is updated. My Windows computer does not turn itself off and works fine.  The only problem is the OS is Win XP, and it no longer updates the Google browser and I have a problem viewing some (very few) videos online. The ubuntu computer views online videos just fine, and has no other issues except it keeps turning itself off.

Sorry that I did not make it clear in my first post that ubuntu is on another separate computer.

---

### Post by CelticWarrior on 2020-06-11
IMO, it makes no sense posting considerations about other computers if you don't need help with those.

Nevertheless, it's still an hardware issue. You may post the hardware specifications just so we can have a better idea about what can be happening.

---

### Post by Autodave on 2020-06-11
First off, I would suggest that you switch to a lighter desktop than Ubuntu.  If your XP system was weak for XP, Ubuntu is too much for it.  I would at least drop down to Xubuntu.  There are other, lighter desktops out there as well, but I have run Xubuntu on very weak systems with no issues.

Some specs on your system would be helpful.

My guess is that either the RAM or the CPU are getting hot and shutting down.  Xubuntu will lessen the load on both of them.

---

### Post by tomblue on 2020-06-11
> **CelticWarrior said:**
> IMO, it makes no sense posting considerations about other computers if you don't need help with those.

Nevertheless, it's still an hardware issue. You may post the hardware specifications just so we can have a better idea about what can be happening.

Today I upgraded to 19.10. It will take me some time to explore the upgrade. Maybe I should start another post that's more detailed. Sorry. I'm not that experienced with software issues. I think I better find someone local to come help me out. Thank you for taking the time to respond to my not so clear questions.

---

### Post by tomblue on 2020-06-13
These are from Settings - Details. I hope these are the hardware specifications you asked for.
Memory 3.7 gib
Processor Intel Celeron CPU1007u@1.50GHZX2
Gnome 3.34.2
OS Type 64bit
Disk 256.1GB

---

### Post by CelticWarrior on 2020-06-13
OK, it's old(ish) yet new enough to support standard Ubuntu although the suggestion to use lighter variants is pertinent.
But again, the issue is hardware. Distorted colors and then unexpected shutdown suggests overheating. If this is being passively cooled (it is a typical hardware configuration of a miniPC, after all) it may be about to fail completely.

---

### Post by tomblue on 2020-06-13
> **CelticWarrior said:**
> OK, it's old(ish) yet new enough to support standard Ubuntu although the suggestion to use lighter variants is pertinent.
But again, the issue is hardware. Distorted colors and then unexpected shutdown suggests overheating. If this is being passively cooled (it is a typical hardware configuration of a miniPC, after all) it may be about to fail completely.

The cooling just might be the problem. This computer is only 2 inches tall and 7 x 7 inches square. I don't think it even has a fan, because I don't hear one. It's been running for over  an hour and a half, and hasn't shut down yet, but I'll look into getting a bigger computer that has a fan. Thank you.

---

### Post by dino99 on 2020-06-13
If you are using gnome, then install gnome-system-monitor and enable it via 'tweaks' (gnome-tweaks) to get some usefull data like temp; also glance at 'journalctl -b' output from a terminal: pay attention to the red lines (errors) and yellow ones (warnings, aka not fatal)

---

### Post by tomblue on 2020-06-13
> **dino99 said:**
> If you are using gnome, then install gnome-system-monitor and enable it via 'tweaks' (gnome-tweaks) to get some usefull data like temp; also glance at 'journalctl -b' output from a terminal: pay attention to the red lines (errors) and yellow ones (warnings, aka not fatal)

Thank you. I'll look into it.

---

### Post by tomblue on 2020-06-13
> **Autodave said:**
> First off, I would suggest that you switch to a lighter desktop than Ubuntu.  If your XP system was weak for XP, Ubuntu is too much for it.  I would at least drop down to Xubuntu.  There are other, lighter desktops out there as well, but I have run Xubuntu on very weak systems with no issues.

Some specs on your system would be helpful.

My guess is that either the RAM or the CPU are getting hot and shutting down.  Xubuntu will lessen the load on both of them.

Thank you. I think it was the cooling issue.  I'll look into the lighter desktop.

---

### Post by mmoseeker on 2020-06-19
i would suggest the xubuntu system for you. but windows xp is not too old.i am also using it now.

---

### Post by CelticWarrior on 2020-06-19
> **mmoseeker said:**
> i would suggest the xubuntu system for you. but windows xp is not too old.i am also using it now.

Windows XP has been out of support since 2014. That's 6 years without security updates. So, again > If it's out of support it shouldn't be used in any way that implies  internet connection, period. The "problems in accessing some websites"  is the least of your problems. Unpatched software can be easily hacked,  your personal data stolen, used and abused and your computer can be used  for nefarious purposes (read criminal activities) in the net. It's  therefore very dangerous for you personally and very irresponsible.


---


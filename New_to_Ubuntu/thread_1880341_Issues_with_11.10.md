---
title: "Issues with 11.10"
date: 2011-11-13
forum: New to Ubuntu
---

### Post by cyril.godart on 2011-11-13
Using Ubuntu 64bits on an Intel Core i7 desktop with NVidia Graphic Card. 

I have struggled with past 2 weeks with this latest release. At times the Ubuntu OS is almost irresponsive. I suspect that most of the issues I have with 11.10 are related to the NVidia driver. Today I came back to a dual boot Windows OS to be able to write this post. 
Symptoms that seem related to the same issue:
- Firefox or pretty much any browser freeze frequently. I thought initially the whole issue was with my network connection but there is not much traffic going on there. 
- the GUI itself freezes. 
- I have switched Nvidia drivers and from Unity to "Gnome Classic (no effect)", it improves at time but then reverts back. 
- The systems logs me out when opening some applications depending on the sessions: frequently with KeyPassX, at times with Dolphin, lately with the Dash Home on Unity and I have ceased to try to use Skype. 

Other issues I came across. While I have not experienced major issues with my sound cards so far upgrading to 11.10 deprived me from my external sound card. A post suggested to create a soft link from /var/lock to a /run/lock with I did to no avail. 

I have a lot of software installed and reinstalling completely instead of ugrading as I did would be painful. But I would be ready to jump if there was conclusive evidence that my install is corrupted. 

Any help out there?

Thanks

---

### Post by beew on 2011-11-13
Is it a laptop? Do you have Optimus enabled? 

Opps sorry, never mind.

---

### Post by cyril.godart on 2011-11-20
Somehow the driver must be stale. I followed instructions in one of these threads on the forum to install a newer version of the driver (190.06) and I have less issues, at least in Gnome Classic.

---

### Post by cyril.godart on 2011-12-14
It took actually a fresh re-install to get rid of the last issues with the driver. 
I followed the instructions from:
[http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/](http://linuxologist.com/1general/howto-fresh-ubuntu-install-without-losing-your-current-settings/)
Some part are slightly outdated (sudo dpkg --set-selections reads from stdin so you need to redirect from the file) and I would suggest for some people to save their shared font folder if you have installed some. 
Also your firefox add-ons can be lost (there must be a way to retain them).

---


---
title: "Ubuntu / Windows dual boot startup."
date: 2014-05-28
forum: New to Ubuntu
---

### Post by gordon99 on 2014-05-28
When I switch on my notebook, having recently installed Ubuntu 14.04, the first screen has 6 boot options:-
1.Ubuntu; 2. Advanced options for Ubuntu; 3. Memory test; 4. Memory test + Serial consol; 5. Windows loader; 6. Windows recovery environment.
The fact is, I rather assumed there would be just two choices, Windows or Ubuntu.
I have run both memory tests out of interest. Both gave a Pass result and frankly both tests seemed to be identical to my untrained eye.
I went into Windows recovery and all that seemed to do was tell me to insert the Windows install disk if I had a problem.
I also selected Advanced options for Ubuntu once. I cannot recall exactly what this offerred but nothing very necessary I seemed to think.
My question is- are options 2,3,4 and 6 really necessary now or might they be essential at some future time. If they are unlikely to be essential, ever, can they be removed easily or should I just learn to live with them?

Regards to all.

Gordon

---

### Post by Quarkrad on 2014-05-28
The easiest way is to download Grub Customizer from the Software Centre - you can then edit the grub screen.

---

### Post by grahammechanical on 2014-05-28
You should have seen what the boot menu looked like before Grub gave us a sub-menu, such as Advanced Options. And it is necessary because in Advanced options we can select an earlier Linux kernel. Which is useful if an upgrade to the kernel proves incompatible with a proprietary video driver that we may be using. It does happen. The Advanced Options also gives access to a Recovery mode which will load the Linux kernel and a menu which will offer these choices

Resume which will load Ubuntu with an open source video driver. Useful for when the proprietary video driver breaks the desktop.
Clean which will attempt to create space in the partition. Useful for when the partition becomes too full for Ubuntu to load.
dpkg which will repair broken packages. Useful for when we mess up with updating Ubuntu.
grub which will update the Grub boot menu's configuration files. Useful for when something  or someone (us) has messed up the boot menu.
network which will set up an connection to our router. Useful for when we have a broken system and think that it might be fixed by an update to a buggy package.
root a Linux command line from  which we can run commands to update the system (once we have a network connection0 and edit system files (if we know what we are doing) and install applications.

The alternative to not have recovery mode is to fix Ubuntu by re-installing. Sometimes that is necessary but first try recovery mode. If you think that you will never need to access that Windows Recovery partition to run Windows recovery then remove that partition and update the Grub configuration files and item 6 will be gone.

There is also a way to get rid of items 3 and 4 but we are talking about stuff that we should not mess with unless we know what we are doing and are prepared to break the OS doing it.

Regards.

---

### Post by deAthbLisS on 2014-05-29
I think this will solve your problem :)
[http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order](http://askubuntu.com/questions/100232/how-do-i-change-the-grub-boot-order)

---

### Post by stalkingwolf on 2014-05-29
one of the several Laws of Murphy (murphys law) states "you will never need it until you get rid of it."and i can attest to the truth of that law.

---

### Post by gordon99 on 2014-05-30
Thanks for the suggestions. I thought I would just change the boot selection list order but I was finding even that procedure difficult to follow so I have decided to leave things as they are. Clearly, these sorts of alterations are not designed for the average computer user.

---

### Post by sheez on 2014-05-30
I have dual setup too, but I use windows as my main OS. I altered the grub2 so that windows is on top and I built in a 3 second window to boot in to in Ubuntu if I want to. This way my pc will still boot very fast.

---


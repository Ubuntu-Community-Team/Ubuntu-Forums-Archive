---
title: "[SOLVED] After I log in, I get nothing but a blank white screen"
date: 2008-08-06
forum: New to Ubuntu
---

### Post by Raazka on 2008-08-06
I'm running Hardy on an old desktop, and for some reason, it hangs at a blank white screen (which it doesn't display normally) immediately after I log in.

I've tried reconfiguring the xserver with ```
sudo dpkg-reconfigure xserver-xorg
``` and I've also tried fixing the xserver through the recovery menu, but neither changed anything.

Please help!

---

### Post by overdrank on 2008-08-06
> **Raazka said:**
> I'm running Hardy on an old desktop, and for some reason, it hangs at a blank white screen (which it doesn't display normally) immediately after I log in.

I've tried reconfiguring the xserver with ```
sudo dpkg-reconfigure xserver-xorg
``` and I've also tried fixing the xserver through the recovery menu, but neither changed anything.

Please help!

Hi and what is the model of the graphics card?

---

### Post by abn91c on 2008-08-06
you probably have beryl or compiz enebled that your video card does not support, log in in recovery mode then uninstall them

---

### Post by endtheembargo on 2008-08-06
Have you been running hardy just fine and this happened out of the blue, or upon upgrade? It sounds like the same thing happened to me when I upgraded and I was advised to do the following;

"Reboot and when grub comes up press escape. Choose the recovery mode option. It's the second one down.

A menu will pop up, choose xfix then reboot."

It got me back into my computer just fine, but now I'm having an issue where I can't hear any sound, and my computer doesn't recognize wireless networks... Not sure that would happen to you though..

good luck

---

### Post by Raazka on 2008-08-06
Hi,

My video card is a ATI Rage 128 Pro Ultra TF, and I've been trying to find a driver for it recently. I probably should have noted this before. :)

abn91c, that's probably what's wrong, and I'll try logging in under recovery mode.

endtheembargo, my computer has been running Hardy well for a few weeks, and I think this happened after an update. I don't remember what update, though. 

Thanks!

---

### Post by Raazka on 2008-08-06
Whew!

Xfix didn't fix the problem, and I tried it a few times for good measure.

For some reason, another user account on my computer was still working, so I was able to delete everything compiz- or beryl-related, and now my computer successfully loads. 


Thanks for the help!

---


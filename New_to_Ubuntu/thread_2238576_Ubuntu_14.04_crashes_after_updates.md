---
title: "Ubuntu 14.04 crashes after updates"
date: 2014-08-08
forum: New to Ubuntu
---

### Post by wolfen10862 on 2014-08-08
Last night Ubuntu informed me that there were a lot of updates, many of them were Nvidia driver and security, so I installed them, Now today when I try to start Ubuntu, it only comes to a Black screen, I get the duel boot screen, windows vista works fine, but Ubuntu acts like windows does when it crashes.
I'm on Ubuntu 14
Emachine T5082 with a Nvidia 8400GS 2 gig of ram, 500 gig SATA hdd, duel core 3 gig processor
Please send any reply to the following email, since my  primary is on Ubuntu
<snip>

---

### Post by papibe on 2014-08-08
Hi wolfen10862.

Boot into Ubuntu, and wait about 10secs after the black screen. Then press Ctrl+Alt+F1

That should get you to a text mode console. Login as you, and once inside the text terminal run this:
```
sudo mv -iv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
```
Then reboot:
```
sudo reboot
```
Hope it helps. Let us know if that worked.
Regards.

---

### Post by wolfen10862 on 2014-08-10
That didn't work.
I wound up reloading Ubuntu, its a inconvenience at worst, not like when windows totally crashed, but now I gotta wait for all the updates I had that made it run perfect
Its the first problem I have ever even heard of with Linux though, so it might have actually been my computer because today the modem flashed because cox did something and the computer shut down all of a sudden like the power went off

---


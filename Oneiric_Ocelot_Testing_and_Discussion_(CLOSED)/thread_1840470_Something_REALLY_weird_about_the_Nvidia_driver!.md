---
title: "Something REALLY weird about the Nvidia driver!"
date: 2011-09-07
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by desire.linux on 2011-09-07
After the installation of Oneiric Beta 1 on my computer, I updated my system with the latest upgrades, rebooted, and then activated the non-free recommended driver for my Nvidia GTS 250.

When I rebooted, the fan on the video card didn't go down in RPM as it should, and I suddenly got a 2D desktop and lost all 3D features. By going back to the "additional drivers" window, it said:
**The driver is activated but not currently in use**.
When I deactivated the non-free recommend driver and rebooted, I got all the 3D features back, apparently by the Nouveau driver. (?)

Then I decided to try the free experimental Nvidia driver on the same list, which I don't know what is neither where comes from. I rebooted, but my fan was still loud, though I still had 3D.

I finally decided to deactivate the free experimental driver and try the non-free recommended one last time. And when I did that, it suddenly worked. My fan got a much lower RPM and noise, and all Nvidia features was active from its control panel. It still said:[B]
The driver is activated but not currently in use[/B]. :(
And the free experimental driver disappeared from the list and never came back!

----------

But here comes the wierd part. I had to do a complete reinstall to retest this issue.

After a fresh and new install of the Beta 1, I activated and deactivated the non-free recommended Nvidia driver several times, and when activated, I got 2D and lost 3D. When deactivated, I got 3D back.

To make it work, I have to activate and deactivate the free experimental driver once, and then activate the non-free recommended Nvidia driver. And then it works, even though it says:
**The driver is activated but not currently in use**.
And the free experimental driver disappears.

LOL! :D

Anyway, I want some feedback on this issue before I report a bug. Thanks.

NB! I use the same hardware on 10.04 LTS, and it works flawlessly. I just change HDD to test Oneiric Beta.

---

### Post by rigobot on 2011-09-07
Hi!

Try to:
- backup your /etc/X11/xorg.conf (if any)
- open a shell and do: ```
sudo nvidia-xconfig
```
- log out
- log in

cheers,
rigobot

---


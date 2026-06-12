---
title: "Ubuntu 8.10 problems"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by KazPed on 2008-09-16
Hey, i tried updating to 8.10 earlier today, after using 8.04 which was stable (just no sound). but after installing 8.10, it came to the reboot, i selected the top option from GRUB and loaded up, it came to the loading screen. but when the login was supposed to come up, i was met with a blank screen. I also tried another kernel option that i think was same as my old one from 8.04 but still a black screen. My graphics card is an ATI 2600Pro AGP. Any ideas wat caused this?

---

### Post by Dougie187 on 2008-09-16
I think since this is still an unreleased version of ubuntu you are supposed to keep questions about it to the forum specified for this version.

Mainly because you will probably just get a bunch of replies that say "You updated to an unstable version, so it might just not work for you yet."

Also, it is advised, i think its mentioned when you download it too, that you shouldn't use it on a production system. it might also say it when you try to update it. Since its strictly for testing purposes.

---

### Post by perlluver on 2008-09-16
Well first 8.10 is still alpha, secondly, you might have to reconfigure the xserver.  ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by KazPed on 2008-09-16
well i downloaded it from the updater on ubuntu. not from a site. Ill just go back to 8.04 where i was happy until its more stable i guess. thank guys, quick replies! :D

---


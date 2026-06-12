---
title: "Ubuntu 8.04 and ATI screen resolution problem..."
date: 2008-09-05
forum: New to Ubuntu
---

### Post by erdinnaya on 2008-09-05
Hi all...

I had been using version 7.10 with an on-board intel graphics accelerator, and everything about screen was perfectly fine. Then i added ATI HD3650 graphics card into motherboard but ubuntu did not boot at all. Then i could manage to boot it with the low graphics mode and i was told if i upgraded to Ubuntu 8.04, the driver problem will be fixed. So I upgraded it and now i can choose further resolutions than 800*600. BUT, now my screen looks like a 800*600 screen pathced onto blank 1024*768 wallpaper. I mean the desktop of Ubuntu is on the up-left side of the screen and the rest of the screen is occupied with pure orange background. Can anyone tell me what is the problem?..

PS: is there a way to attach screenshots to messages? Then i could easily show the situation of my screen.

Edit: ok I found the attachment screen.

---

### Post by unutbu on 2008-09-05
Have you tried:

[list]
[*]Go to System>Administration>Restricted Drivers Manager  and make sure restricted ATI drivers are enabled.
[*]
```
sudo dpkg-reconfigure xserver-xorg
```
[/list]

---

### Post by erdinnaya on 2008-09-05
I already enabled it. ATI catalyst software is also running perfectly fine. But still i have my screen like this.

---

### Post by erdinnaya on 2008-09-05
I solved the problem by chance. Just disabled any desktop effects from the appearance menu and i can now see the full screen.

---


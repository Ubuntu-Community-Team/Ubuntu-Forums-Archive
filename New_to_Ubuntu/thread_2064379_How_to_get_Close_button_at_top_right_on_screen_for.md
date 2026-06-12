---
title: "How to get Close button at top right on screen for 12.04?"
date: 2012-09-29
forum: New to Ubuntu
---

### Post by resander on 2012-09-29
I have just put Ubuntu 12.04 LTS 64-bit onto a new desktop PC dual-booting with Windows 7. 

I was using Ubuntu 10.04 LTS on my previous 32-bit PC and then I could select themes that had the close button at the top right corner of the screen. With 12.04 there are only 5 themes (Adwaita, Ambience, Radiance, High Contast and High Contrast Inverse) in the Appearance Dialog in System Settings and they all have the close button at the top-left corner.

I noticed there are more themes in the /usr/share/themes directory, e.g. Clearlooks, but these do not show in the Appearance dialog so I cannot select them. What do I need to do to see these too? Clearlooks is the theme I want, but Radiance will also do. But the close button has to be at the top right-hand corner.

Ken
P.S. I do not like/need Unity so I:
1.  installed gnome-shell from Ubuntu Software Centre
2.  Shutdown & rebooted and then selected Classic Gnome from
the login dialog. That disabled Unity and let me view a normal
menu every time following login.

---

### Post by kc1di on 2012-09-29
See post under you other thread :)

[http://ubuntuforums.org/showthread.php?t=2064385]("http://ubuntuforums.org/showthread.php?t=2064385")

---

### Post by resander on 2012-09-29
There is a command for this that I missed first time I googled... 
Enter this from the command line:

gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"

Then the minimise,maximise and close buttons will march over to the right hand side. And the setting remains after reboot.

---


---
title: "Zebronics GeForce 6200 A 256mb not detected on installation"
date: 2008-08-07
forum: New to Ubuntu
---

### Post by obscurespectre on 2008-08-07
hi.

i have browsed thru the entire forum but could not locate any soulution to my problem.

i have tried installing many diff versions of ubuntu (and other linux distros) but am always faced with the same problem. . . so i have to go back to WindowsXP :-(

the installation starts thru the livecd n shows some progress bars .... this is normal ... but soon the screen goes blank and shows an error "monitor resolution not supported, choose a diff. resolution" - or something like that.

i have been able to install ubuntu without the AGP card n it runs fine (but a bit slow graphics). the same is true on my ancient laptop. 

tried the alternate install too ..... same problem !!

below is my custom rig that i am installing to:

AMD64 2800+
Zebronics GeForce 6200a 256mb AGP
Asus K8V-MX motherboard
1GB DDR @400MHZ
Samsung 510n LCD

i even installed the latest ubuntu 8.04 n still same error.

---

### Post by obscurespectre on 2008-08-07
sorry, i forgot to add .... the installition goes thru fine all the way untill it shows "starting X" or something then the error pops-up n i have no other option to reboot n format the installation space.

sorry for the trouble

---

### Post by louieb on 2008-08-07
Probably its your display not being detected. And the refresh rate is too high. Try installing in safe graphics mode. 
Then after its installed. run
```
displayconfig-gtk
```

some other stuff to try here.
[http://ubuntuforums.org/showthread.php?t=867505](http://ubuntuforums.org/showthread.php?t=867505)

---


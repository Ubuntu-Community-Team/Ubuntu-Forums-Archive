---
title: "Help! Dual Head with GeForce7300gt"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by neurostu on 2008-06-17
I'm running Hardy Heron 32bit with the latest drivers installed via EnvyNG-gtk.  My video card is a NVidia GeForce 7300gt has a DVI out and a VGA out.  I have two Dell LCD monitors that both have 1600X1200 resolution.  I have one plugged into the VGA port and the other plugged into the DVI port.  I cannot however get the monitor on DVI port recognized.  

When I run nvidia-settings and I click "Auto Detect" only the display attached to the VGA port is detected.  

Also when I disconnect the VGA port and only have the DVI cable plugged in I cannot get anything to display on the DVI-LCD.  

Does anybody know what I have to do? It seems like there is a problem recognizing the DVI out...  

I spent the night on google trying to figure this out but I'm totally stumped...

---

### Post by NT4usB on 2008-06-17
Are you running nvidia-settings as root?
When you hook up the second monitor to DVI alone, did you try dpkg-reconfigure... to see if it comes up?
If you could get an xorg for the DVI side that way, combining them should be QED.
ed: iirc, I ran dpkg-reconfigure -phigh xserver-xorg with both monitors attached to get them recognized. Might be worth a try.

---


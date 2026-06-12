---
title: "NVIDIA drivers Ubuntu 13.04"
date: 2013-08-08
forum: New to Ubuntu
---

### Post by rPAK48D on 2013-08-08
Hello, 
My Desktop runs Windows 8 and Ubuntu 13.04 in dual boot mode but I am facing a big problem. My graphic card is: NVIDIA 8600 GT. When I enter Windows 8 everything works perfectly because I have already installed the drivers of my graphic card there. But when I enter Ubuntu 13.04 from Grub Menu, my screen goes black and appears the message: No display input. At this point there is nothing else I can do but reset my computer. I took out the graphic card of my desktop and try to enter Ubuntu without using the Nvidia graphic card. It worked, so I was able to have access to terminal and the graphical user interface of Ubuntu. But how can I install the drivers of Nvidia if I cannot enter Ubuntu using my Nvidia graphic card??
Thank you guys for your time
Vasilis

---

### Post by SweetAurora on 2013-08-08
If you only use the Nvidia card for everything, make sure the onboard graphics are disabled in the PC's BIOS. Leaving the Onboard Graphics enabled may be confusing X.Org, the Graphics manager of linux.

---

### Post by ant2 on 2013-08-08
Do you have a CD with a Live Session of Ubuntu on? If so can you boot to that, does that work OK?

You may also try the nomodeset boot option. An excellent explanation of this can be found in this thread:

[ How to set NOMODESET and other kernel boot options in grub2]("http://ubuntuforums.org/showthread.php?t=1613132")

Check out the section headed 'How to temporarily set kernel boot options on an installed OS (not wubi)' and if that works then 'How to permanently set kernel boot options on an installed OS (not wubi)'

---

### Post by rPAK48D on 2013-08-08
Finally, the problem is solved. I had to enter Ubuntu 13.04 through the option of Grub Menu --> Advanced options for Ubuntu.    That gave me access to the system (gui) so I was able to install the appropriate drivers
Thank you very much kitsuneinari78 and ant2 for your replies.

---


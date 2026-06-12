---
title: "Network icon on panel disappears after switching user"
date: 2011-09-16
forum: New to Ubuntu
---

### Post by Esot-Eric on 2011-09-16
Hey chaps, I'm using an NVIDIA card here (of which I've heard of graphical glitches after user switching) and I notice that if I switch user the network icon does not appear in the panel of the user I switched to, I am still able to connect to the internet however. I've been playing around with the switching user business trying to confirm that it was not just coincidence that when I switch user the icon goes and any other time it does not. Once (out of 6 times perhaps) the theme changed  to something I don't see on the list (though it may have been 'dust sand') and I was unable to change it back to 'new wave' even after I gave it considerable time to think about it.  All a bit concerning really, is this a problem anyone has heard of?  Edit: I'm also occasionally having a graphical glitch where the desktop will show along the top or the bottom, a bit hard to describe, I suspect this is just my computer being unable to keep up however, pulling up the system monitor seems to make the screen refresh and get rid of it.

---

### Post by Lisiano on 2011-09-16
Bear with me. I have nearly no idea why this could be happening.
Well first of, does running ```
nm-applet
``` respawn the icon?
If you are using WiFi, can you change the network you are connected to (Or create a new LAN connection with a static IP)?

---

### Post by Esot-Eric on 2011-09-16
After running nm-applet I get a response "An instance of nm-applet is already running". I'm connected via ethernet cable here.  I ran it after switching user of course. Edit: This is going to seem a silly question but I can't get it out of my mind, when I initially downloaded the ISO I did a md5sum check and it came out alright, can I be certain that I have a proper version of the OS installed?

---

### Post by wildmanne39 on 2011-09-16
Hi, welcome to the forum! if the checksum checked out then that should be ok. If your panel at the top looks like windows 95 then use this link to try and fix it, that may fix your network manager issue but I am not sure about that.
[http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html](http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html)
Thank you

---

### Post by Esot-Eric on 2011-09-16
Right, matter resolved, I had another go at searching for this problem now I knew it was called a 'Network manager' icon (I don't know what I had been calling it before) and found a fair bit of documentation on other people experiencing it, there appears to be a number of solutions for it should anyone be having the same problem. Thank you wildmanne39 for the link, I shall use that if the glitch occurs again. Very sorry for having not searched better in regards to the network icon.

---

### Post by wildmanne39 on 2011-09-16
Hi, your welcome! I am glad you got it working,  would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---


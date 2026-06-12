---
title: "No boot after updating."
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Zerxez on 2008-06-09
Hi,
I am a newb, but Hardy is now my primary OS and has been working well for me.  Last night I decided to run updates (88 of them).  It downloaded all but 33 and then told me the server was unavailable.  I tried again 4 or 5 times over the next couple hours while working on other things...same thing server is not available.  It told me I needed to reboot after installing the updates it had downloaded.  After reboot it doesn't reboot.  In fact it boots all the way to where I would expect a login screen and the give me a white X for a cursor and then tells me the my screen resolution is "very low".  My options are:  Continue (which gives me a black screen forever), and Configure:  When I select configure the only resolutions available are 640x480 and 600x800.  I can select a new driver either Nvidia or an Nvidia GeForce 8 series (I have an 8800GTX).  However after selecting that driver the machine goes to a black screen and a reboot brings me back to the "low resolution problem."  This is probably just a corrupt video driver...but how do I fix it?  Oh, I also booted in safe mode and tried to repair packages etc. It didn't help.

---

### Post by Zerxez on 2008-06-09
Ok, I figured out that my high res LCD would not support 640x480 and now have the GUI up on a different display.  However ALL hardware drivers are gone.  So I cannot connect to the internet and cannot complete the update process etc.  Can someone help me through this?

---

### Post by JoshuaRL on 2008-06-09
Could you run the following commands?
```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

```
If that doesn't work, what errors does the terminal return?

---

### Post by AndrewTheArt on 2008-06-09
I've had this sort of problem before. I recall getting the exactly same message too, about the very low resolution. The first time I booted up, I was left with absolutely no restricted drivers, which would enable my Nvidia graphics card. All I remember doing to fix the problem is rebooting after the first failure, though. Try rebooting again. How are you connecting to the Internet exactly? Are you using restricted driver(s)?

---

### Post by Zerxez on 2008-06-10
Hi,
Thank you for the help.  The brought back so many errors I couldn't count them so I just restored an image of the drive from a couple weeks ago and let it be.

---


---
title: "Synaptics Touchpad Recognized, Not Working"
date: 2014-04-02
forum: New to Ubuntu
---

### Post by Dominique_Alexi on 2014-04-02
I'm using a Toshiba S55t-A5334, just installed Ubuntu alone (I was struggling to get some version of Windows and it dual-booted, gave up).
My touchpad is recognized, when I try the xinput command I see it listed, but no matter what other commands I've run, nothing seems to get it to work.
I can hook up an external mouse and it will work.
It seems speakers are working, touchscreen display is working, internet is working, etc.

These are the commands I've tried:
xinput set-prop 12 "Device Enabled" 1
sudo modprobe -r psmouse && sudo modprobe psmouse proto=imps (when I used this, my keyboard stopped working as well)

And maybe a few others I forgot to keep track of. 
Help! I don't want to switch back to Windows but I fear I may have to....
Sorry if this is a duplicate post, I couldn't find answers anywhere. I'm quite the newbie so I have no idea if there are logs I'm supposed to attach nor how to get them....
Thanks in advance for any help!

---

### Post by bshatt1987 on 2014-04-02
Here is the Ubuntu Help Wiki about Synaptics.  You might try some things from there if you haven't already.  
[https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

---

### Post by Navneet_Kumar on 2014-04-02
yeah the above thread might help you a lot......

---

### Post by Dominique_Alexi on 2014-04-02
Hi, thanks for the response!
I did see that page, and did try what I could.
This command: "xinput --test 12" yielded no lines flying by, no nothing. When I tried the same thing using the device number for my touch display, things happened.

[COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---


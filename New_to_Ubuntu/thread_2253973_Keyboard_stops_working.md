---
title: "Keyboard stops working"
date: 2014-11-24
forum: New to Ubuntu
---

### Post by p4p00 on 2014-11-24
So seemingly randomly my keyboard stops working while in chrome or firefox.

I can ctrl+alt+f1 or f2 and log in. Then sometimes ctrl+alt+f7 will get me back to the desktop or I have to ctrl+alt+delete to restart.

I just installed Ubuntu 14.04 for the first time with little/no linux experience.

I tried and failed to use SteamOs last year but that lasted about 2 hours before I gave up on it.

What is going on here?

Edit: It just happened two mor times. The first time firefox asked me what I wanted to save and the mouse/keyboard stopped working. The second time I started a youtube video and when the adds popped up the video froze and the mouse/keyboard stopped working.

I'm going to try adblock and see if I still get the error. It just happened again when I went to click save and just hitting ctrl+alt+f2 then ctrl+alt+f7 gave me control back.

---

### Post by d4m1r on 2014-11-24
I guess it is a laptop you are using?

Specific make/model?

---

### Post by p4p00 on 2014-11-24
It is a MSI GE70 0ND-033us. The problem only seems to happen when using a browser. I played TF2 for like 3 hours and it never happened.

---

### Post by buzzingrobot on 2014-11-24
> **p4p00 said:**
> ...firefox asked me what I wanted to save and the mouse/keyboard stopped working. The second time I started a youtube video and when the adds popped up the video froze and the mouse/keyboard stopped working.


When Firefox displayed the 'Save' dialogue, were you trying to do a save, or was it completely random?

Try disabling all extensions and plugins. If that corrects the problem, re-enable them one at a time, quiting and restarting the browser each time. With  a bit of luck, you might find the culprit.

---

### Post by p4p00 on 2014-11-24
I ment share. It asked what info I wanted to share with firefox.

I will try that.

---

### Post by buzzingrobot on 2014-11-24
> **p4p00 said:**
> I ment share. It asked what info I wanted to share with firefox.



That's been an easily dismissed message at the very bottom of the Firefox window, usually just after you've installed it, when I've seen it.  It's also configurable in Firefox Preferences.

---

### Post by p4p00 on 2014-11-25
> **buzzingrobot said:**
> That's been an easily dismissed message at the very bottom of the Firefox window, usually just after you've installed it, when I've seen it.  It's also configurable in Firefox Preferences.

I just added that because I thought maybe something was triggered by it that would make the keyboard stop working. 

I still have no idea what is causing this to happen. It seems that certain web pages trigger whatever bug stops the keybard/mouse from interacting with the GUI. This one in particular triggers it consistantly.

---

### Post by p4p00 on 2014-11-25
I think I fixed it after I found the same problem posted elsewhere. 

I ran sudo apt-get install nvidia-current-updates and it rolled me back to the 304 driver from the 331.

It looks like the issue was with nvidia. Ubuntuforums.org was triggering what ever caused the keyboard/mouse to stop working but hasn't since I ran the update.

---

### Post by p4p00 on 2014-11-25
I take that back. It just froze-up again.

---

### Post by p4p00 on 2014-11-27
The issue is gone. It hasn't happened since I installed java.

---


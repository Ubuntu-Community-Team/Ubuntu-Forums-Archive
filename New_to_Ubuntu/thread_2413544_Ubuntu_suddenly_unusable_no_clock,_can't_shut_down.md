---
title: "Ubuntu suddenly unusable: no clock, can't shut down, can't access programs"
date: 2019-02-27
forum: New to Ubuntu
---

### Post by edwinek on 2019-02-27
Hi,

I generally leave my computer running and only let it switch off the displays after 30 minutes. When I come back, I switch on the monitors, press ESC (or other key) and continue working.

Sometimes when I want to resume work, part of the GUI seems gone: the time in the top bar is gone, when I click any of the icons of open applications, the windows don't appear (but the hue of the display changes slightly, changes back when I click anywhere on the background) and I can no longer shut down or restart. That option is gone from the top left menu.

I've tried switching to XFCE, but that makes no difference.

As I'm not really an experienced user, I have the feeling this is some beginner's issue, but can't figure out what I'm doing wrong. As a beginner I think: windows won't show, so maybe the window manager?

I've added a picture of the desktop as an attachment.

Anyone any idea on how to prevent this from happening?

---

### Post by NM5TF on 2019-02-28
since you posted on the Ubuntu forum, and failed to provide any other information, can we assume your OS is some version of Ubuntu ?

can you get to terminal ? if so, post the output of
 
```
inxi -F
```

do you still have a live medium that you used to install Linux from ? if so, use it to see if the malfunction persists....or use it to
reinstall whatever version of *nix you are using...

more information is much better than no information.....

tommy

---

### Post by jdeca57 on 2019-02-28
Try [Ctrl][Alt]F3 in order to get a terminal in text mode. If that doesn't work the old solution (the power switch) may be the only way to stop the system and after a restart you can consult your logs. It might be hardware.

---

### Post by edwinek on 2019-03-12
> **NM5TF said:**
> since you posted on the Ubuntu forum, and failed to provide any other information, can we assume your OS is some version of Ubuntu ?

Sorry, should have said, I'm on 18.04

---

### Post by mastablasta on 2019-03-12
looks like the GPU is not handling the power management correctly. i see you have two monitors are they both on same machine? since you have same issue on two different desktops perhaps the GPU driver does not support the wake up properly. 

what happens if you log out and log into a fresh session?

---

### Post by edwinek on 2019-03-12
It's not a wake up issue. Yesterday, for the first time, this happened when I was busy on the PC. Everything was frozen for a minute or so, then all windows disappeared and the screen became as shown in the screen shot.

---

### Post by mastablasta on 2019-03-13
please post the system specs as mentioned above by NM5TF
also post if you installed any additional graphics driver (e.g. nvidia, amdgpu-pro).

Can you switch to console when it freezes? (see jdeca57's post)

Check the system temperature using psensor: [https://wpitchoune.net/psensor/](https://wpitchoune.net/psensor/)

---


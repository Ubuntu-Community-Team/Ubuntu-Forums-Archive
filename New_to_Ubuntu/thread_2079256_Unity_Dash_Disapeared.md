---
title: "Unity Dash Disapeared"
date: 2012-11-01
forum: New to Ubuntu
---

### Post by Paul Lynch on 2012-11-01
Hi, I updated my nvidia driver to the recommended version and when I restart the desktop its missing the unity bar and the top bar (user and connectivity icons etc) has also disappeared. I presume this is an issue with the recently installed driver and I need to reinstate the original. Any advice welcome... I cant remember the shortcut key for the terminal window, that would also be helpful in the absence of the unity dash........

---

### Post by pandacookie on 2012-11-01
> **Paul Lynch said:**
>  I cant remember the shortcut key for the terminal window...

Ctrl+Alt+T

Can't help you with the rest of your problem, sorry. :(

---

### Post by Paul Lynch on 2012-11-01
Thanks, I should add that unity was working fine for a number of weeks until I installed the new nivida driver, seems to be an issue with nividia drivers and unity when I google the problem, it must be possible to roll back to the previous driver.... help

---

### Post by Paul Lynch on 2012-11-01
bump

---

### Post by NM5TF on 2012-11-01
which version of Ubuntu are you using....12.10 by any chance???

there are quite a few bugs with that distro, especially with the
Nvidia drivers....

have you tried to reset the Unity launcher???

open a terminal session  using CTRL+ALT+T

then type the following:

```
unity --reset
```

if that doesn't fix it, have you tried opening the "additional drivers"
tab in dash & selecting a different version other than the "reccommended"
version???

---

### Post by Frogs Hair on 2012-11-01
If using 12.10 use the following to reset Unity. ```
setsid unity
```

---

### Post by Paul Lynch on 2012-11-02
Issue resolved, although the unity dash has disappeared if i hover over where the settings icon should be and click, the settings window appears (like driving blind!). From there I re installed the previous driver and rebooted AOK. NVIDA is int the smoothest graphics option for this new 12.10 any ideas? is there ongoing works to improve?

---

### Post by Frogs Hair on 2012-11-02
I have been with 12.10 since beta 2 and had to experiment with the driver options because there was more than one. The Nvidia current tested driver actually had the worst performance so I am using one of the experimental drivers which works very well.

---

### Post by mtfr on 2012-11-09
I have exactly the same problem, although I'm on Radeon not Nvidia. I installed 12.10 well. Then I installed the Radeon proprietary driver, a couple of apps as well as removed another couple of apps. I guess nothing with dependencies that would harm Compiz, but can't be 100% sure (e.g. I removed Totem and Bluetooth). I worked with the OS perfectly smooth for a matter of hours.

Then when booting next time it showed: after logging in I'm only left with the wallpaper and can't do anything. Though right click shows the correct pop-up menu, and ctrl+alt+del lets me log out.

I'm desperate, I can't do anything on my computer now.

**Edit.** My specs are: AMD A10-5800K (desktop Trinity) with integrated GPU enabled, 8 GB RAM, discrete Radeon 6670 also installed, just one monitor, Ubuntu 12.10 64-bit.

---

### Post by mtfr on 2012-11-09
Alright, I just managed to fix it for myself. What I did was revert to the open source video driver. First of all, I had the fglrx-updates and I switched to the plain fglrx by opening a terminal (Ctrl+Alt+T) and running

```
sudo apt-get install fglrx
```

Then rebooted. Problem persisted so I opened again a terminal and ran

```
sudo apt-get remove fglrx
```

This removed the packages and made the switch to the open source drivers. It's disappointing that this is the only available solution (at least in my case it seems to be) as I was looking forward to playing all available games and especially the upcoming Steam cornucopia.

---


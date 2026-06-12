---
title: "Help with Screen Resolution"
date: 2008-07-08
forum: New to Ubuntu
---

### Post by Narcoleptic_Insomniac on 2008-07-08
Hello, I just upgraded my Ubuntu from Feisty to 8.04 and let me start by saying it's a beautiful addition to the Ubuntu family, however when I started it up for the first time (currently still on my first session), I had a problem with the screen resolution. I was prompted by a window telling me that my computer was running in low graphics mode, and that the resultion was in 800 by 600, when I tried to change it to 1040 by 768 or whatever the next one up is, it failed, leaving me with a screen full of static. So now I have massive windows. I attempted to change the resolution again through the preferences, however the only resolution options I had were 800 by 600 and 640 by 480. I'm using a BenQ monitor, its flat panel, I'm not sure which model it is so I couldnt tell Ubuntu what I was using, nor do I know what graphics card I had, I told Ubuntu that they were both generic. I had it running in 1040 by 768 on Feisty, so I don't know whats wrong with it now. Please help, I really don't want to re-install my operating system.

---

### Post by nkri on 2008-07-08
```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure Xorg.

Ctrl+Alt+Backspace to restart X server.

```
gksu displayconfig-gtk
```
When the window pops up, there will be a box for screen resolution; 1024x768 should be there after you reconfigure X.

Good luck!
-nkri

---

### Post by Narcoleptic_Insomniac on 2008-07-08
> **nkri said:**
> ```
sudo dpkg-reconfigure xserver-xorg
```
to reconfigure Xorg.

Ctrl+Alt+Backspace to restart X server.

```
gksu displayconfig-gtk
```
When the window pops up, there will be a box for screen resolution; 1024x768 should be there after you reconfigure X.

Good luck!
-nkri

Thanks for the help, I tried restarting my computer (which I should have done to begin with) and it put back to its higher resolution.

---

### Post by nkri on 2008-07-08
Ah, ok.  I was assuming you already tried that;).

---


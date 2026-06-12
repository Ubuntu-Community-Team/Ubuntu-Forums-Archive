---
title: "Dual Monitor Issue"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by john.hall on 2008-09-14
I'm having some trouble getting my dual monitors to work in Ubuntu.  I have one DVI and one VGA (connected via an adapter) on an NVidia 9600 GT.  

I've had trouble with the drivers for this card before, but as far as I can tell, I have them working fine now.  I have the 171.05 drivers installed (downloaded from the NVidia FTP site).

When I set one of my monitors to "TwinView" and try to open a Firefox window, everything gets incredibly slow.  I can't even tell that it's doing something most of the time.  I end up using Ctrl-Alt-F2 to restart gdm.

By the way, what is the usual dual monitor setup in Ubuntu?  I know in Windows by default it has the taskbar on one monitor, and you can maximize a window and it will only take up one screen.  TwinView actually stretches everything across two monitors.  This is one of those rare instances where I like the Windows way better.  How can I make it be like that?

Thanks.

---

### Post by chuckmanbob on 2008-10-24
yeah i have the same problem it all gets stupidly slow i will try to post it again and get back to you

---

### Post by /////// on 2008-10-24
Use Seperate X screens

---

### Post by john.hall on 2008-10-24
> **/////// said:**
> Use Seperate X screens

When I do, odd things start happening.  Like now I don't have the bar with all the open applications or the workspace switcher.  I can't click and drag on the desktop.

When I first set it to separate X screens (and just used ctrl-alt-backspace) to restart the X server, I had the bar at the bottom and the top bar on both screens.  I still couldn't click and drag on the desktop.  When I restarted the machine completely, I lost the bottom bar on both screens and the top bar on the new screen.

---

### Post by choboja on 2008-10-25
Hmmm, I have a similar problem when I use the generic kernel?
If I boot into the 386 kernel my desktop(s) behave fine (but I have lots of other issues), but if I boot into the generic kernel I get that behaviour - Panel icons only appear on one screen and none appear clickable and desktop icons either don't work or cause the grey-out shortly after running.
[using 2.6.24-21-386]

---

### Post by /////// on 2008-10-25
> **john.hall said:**
> When I do, odd things start happening.  Like now I don't have the bar with all the open applications or the workspace switcher.  I can't click and drag on the desktop.

When I first set it to separate X screens (and just used ctrl-alt-backspace) to restart the X server, I had the bar at the bottom and the top bar on both screens.  I still couldn't click and drag on the desktop.  When I restarted the machine completely, I lost the bottom bar on both screens and the top bar on the new screen.

Uhh what happens if you enable Xinerama with Seperate X screens?

---

### Post by john.hall on 2008-10-25
> **/////// said:**
> Uhh what happens if you enable Xinerama with Seperate X screens?

The odd occurrences seem to go away.  However, I'm not sure if this is what I'm looking for.  It stretches the wallpaper across both screens (and vertically as well for some reason), etc.  That might be OK if they were the same size/resolution, but unfortunately they aren't.

If the separate X screens (without Xinerama) worked, I think I would be able to do everything except maybe drag a window from one screen to the other.  I'm not sure, as I haven't really had a chance to check it out in detail.

Should I file a bug report or something?

---

### Post by /////// on 2008-10-25
zzz I'm not sure, perhaps you should try re-installing the driver for your video card...

---

### Post by nick_h on 2008-10-26
I am using two monitors from the same nvidia card using TwinView.

I enabled it all from System->Adminstration->NVIDIA X Server Settings

To install it type:
```
sudo apt-get install nvidia-settings
```

You need to look in the X server display configuration section.

I get the wallpaper stretching across the screens (not ideal), but windows maximise to one screen only.

---

### Post by choboja on 2008-10-27
I had a system running the generic kernel, but was using the nvidia drivers built for the 386 kernel. This seemed to work ok up to a point and I would be left with a non-responsive desktop. Resetting the graphics server just cleared my whole desktop. The nvidia site provide an install script that will do the recompile for you. My desktop is now working again!

---


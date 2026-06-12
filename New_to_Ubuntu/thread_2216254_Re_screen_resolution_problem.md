---
title: "Re: screen resolution problem"
date: 2014-04-10
forum: New to Ubuntu
---

### Post by Devin_Carpenter on 2014-04-10
I'm also having a problem with the resolution in Lubuntu. I'm using an HDMI to view the screen on a 1366*768 native resolution TV, and yet when I select the 1366*768 resolution in the Display Settings it doesn't fit the screen. I can't view the lower taskbar at all in that resolution, but the when I change to 1920*1080 it fits well, but it still looks bad because it's not the screens native resolution. Any way to resolve this?

---

### Post by sandyd on 2014-04-10
I have moved your post to a separate thread.

---

### Post by Devin_Carpenter on 2014-04-14
Thank you. Is there anybody that can think of the reason behind this happening, and how to fix it?

I have used the xrandr to try and change the resolutions and create new resolution settings but I haven't had any luck.

---

### Post by QIII on 2014-04-14
Hello!

It would be helpful to others if you could post your machine's specs, particularly the GPU and whether you are using a proprietary driver.

Cheers!

---

### Post by Devin_Carpenter on 2014-04-14
> **QIII said:**
> Hello!

It would be helpful to others if you could post your machine's specs, particularly the GPU and whether you are using a proprietary driver.

Cheers!


I am not using any proprietary drivers that I know of, I'm not entirely sure on what they are either. I don't think Lubuntu comes with them, nor have I downloaded them..I think.

CPU: 8x intel I7-2675QM @ 2.2 GHZ
RAM: 6gb DDR3
GPU: AMD Radeon 6490M
OS: LXDE Ubuntu 13.10

---

### Post by trag on 2014-04-14
your tv's native resolution is 1366x768  while in VGA mode. your TV can receive only a limited number different resolutions under HDMI,and your pc can only push out a limited number of different resolutions under HDMI.Because there is no common resolution that your pc/tv can share your will experience overscan on your monitor. If using a VGA cable is not an option for your setup than I recommend adding  a VGA/HDMI adapter to the HDMI cable.The sound will still be transmitted via HDMI but the video signal will be captured and converted to VGA before making it to your tv. Go to your tv's settings and have it receive via VGA instead if HDMI and you will then get your full native resolution of 1366x768.

---

### Post by SeijiSensei on 2014-04-15
What kind of TV is it?

I've used Sonys, LGs and Samsungs, and they all have an option for "full-pixel" displays with HDMI that turn off the normal overscan used for television signals.  Take a look in the TV's manual to see what options are available to you.

I have one laptop with a 1366x768 display and a ATI Radeon 6770M.  On that machine I have the proprietary driver installed (via the "Additional Drivers" application in Ubuntu), though I suspect that isn't mandatory in this case.  I can go into the display settings and set the TV to a different resolution like 1280x720 while the laptop stays at 1366x768.  Sometimes this works better if you disable the laptop display entirely in the display settings applet.

---

### Post by Devin_Carpenter on 2014-04-19
> **trag said:**
> your tv's native resolution is 1366x768  while in VGA mode. your TV can receive only a limited number different resolutions under HDMI,and your pc can only push out a limited number of different resolutions under HDMI.Because there is no common resolution that your pc/tv can share your will experience overscan on your monitor. If using a VGA cable is not an option for your setup than I recommend adding  a VGA/HDMI adapter to the HDMI cable.The sound will still be transmitted via HDMI but the video signal will be captured and converted to VGA before making it to your tv. Go to your tv's settings and have it receive via VGA instead if HDMI and you will then get your full native resolution of 1366x768.

The TV has the option for VGA yes but I would have to buy the converter like you are saying. If any built in options cannot fix it then I will try that route.

Thank you, and I'll post what happens if I have to use VGA to fix it.

> **SeijiSensei said:**
> What kind of TV is it?

I've used Sonys, LGs and Samsungs, and they all have an option for "full-pixel" displays with HDMI that turn off the normal overscan used for television signals. Take a look in the TV's manual to see what options are available to you.

I have one laptop with a 1366x768 display and a ATI Radeon 6770M. On that machine I have the proprietary driver installed (via the "Additional Drivers" application in Ubuntu), though I suspect that isn't mandatory in this case. I can go into the display settings and set the TV to a different resolution like 1280x720 while the laptop stays at 1366x768. Sometimes this works better if you disable the laptop display entirely in the display settings applet.

The TV is a Westinghouse EW32S5KW.

I've tried the aspect buttons on the remote and the options it has don't fit right for either my native resolution 1366x768 nor 1920x1080.

I also cannot find any options in the manual for changing the resolution, other than the ratio.

---


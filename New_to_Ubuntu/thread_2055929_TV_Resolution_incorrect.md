---
title: "TV Resolution incorrect"
date: 2012-09-10
forum: New to Ubuntu
---

### Post by smartalick on 2012-09-10
Hi all. I'm new to Linux and Ubuntu - I have installed recently and so far everything has been brilliant with one small exception.  I have plugged in my TV (Im chuffed that this works straight away without other software so far) but it seems to think that the TV screen is a 95" when it is smaller - I cant find the tape measure to see how big it really is ATM. So all the edges of the screen are cut off.

Does anyone have any advise on how to change this - I have played around with the resolution on both the computer and TV but to no avail

Thanks very much in advance

---

### Post by mcduck on 2012-09-10
The physical size of the TV is meaningless, it's just the resolution that matters with displays.

Anyway, your problem is most likely caused by [overscan]("http://en.wikipedia.org/wiki/Overscan"). If your TV has a specific picture mode for PC or game consoles, try using that. (ot could also be named as pixel-per-pixel or something similar, depending on TV's manufacturer and model).

If there isn't such option, then depending on your graphics card it might have an option for compensating for overscan. At least nVidia's proprietary drivers allow you to do that.

---

### Post by sandyd on 2012-09-10
Go into the terminal (Unity Dash -> type in "terminal")
and post the output of
```

xrandr

```

---

### Post by smartalick on 2012-09-10
The screen is attached through the HDMI. there is a PC option but my computeer screen needs that cable

The xrandr results:

xrandr
Screen 0: minimum 320 x 200, current 3360 x 1284, maximum 8192 x 8192
HDMI-0 connected 1920x1080+1440+0 (normal left inverted right x axis y axis) 708mm x 398mm
   1920x1080i     25.0*+   30.0  
   1280x720       50.0  
   720x576        50.0  
   720x480        59.9  
DVI-0 disconnected (normal left inverted right x axis y axis)
VGA-0 connected 1440x900+0+384 (normal left inverted right x axis y axis) 410mm x 257mm
   1440x900       60.1*+   75.0  
   1400x1050      74.9  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x921       76.0  
   1280x800       74.9  
   1152x864       75.0  
   1280x720       60.0  
   1024x768       75.1     70.1     60.0  
   832x624        74.6  
   800x600        72.2     75.0     60.3     56.2  
   640x480        72.8     75.0     66.7     60.0  
   720x400        70.1  


Cheers

---

### Post by sandyd on 2012-09-10
Current resolution is 1080p/i.

What drivers are you using?

If you are using the ati/nvidia drivers installed from the Hard Ware Drivers window, you can adjust the overscan/underscan for the monitor (you want to reduce the overscan right now) from either Nvidia Settings or ATI Catalyst.

---

### Post by smartalick on 2012-09-10
Im not sure - didnt buy it myself and doesnt say. Its a Toshiba and it is HD ready so should imagine that 1080 would be fine??

When changing down to  it still doesnt change much but makes everything bigger

---

### Post by mcduck on 2012-09-10
> **smartalick said:**
> Im not sure - didnt buy it myself and doesnt say. Its a Toshiba and it is HD ready so should imagine that 1080 would be fine??

When changing down to  it still doesnt change much but makes everything bigger

HD-Ready means support for 720p resolution (1280x720), although the TV might be able to handle 1080i/p. Anyway, the most common native resolution for HD-Ready televisions is 1366x768, so try that one (or 1360x768 if the former one isn't available).

---

### Post by smartalick on 2012-09-10
Sorry to be thick but where do I find the graphic drivers in Ubuntu - I havent added anything on this so it was what come with the package I should Imagine

---

### Post by smartalick on 2012-09-10
> **mcduck said:**
> HD-Ready means support for 720p resolution (1280x720), although the TV might be able to handle 1080i/p. Anyway, the most common native resolution for HD-Ready televisions is 1366x768, so try that one (or 1360x768 if the former one isn't available).

I have tried changing the resolution but 1080 is the only one that comes close to fitting, I think Im with sandyd in thinking its in the overscan - not that I know what I am doing here but it would be nice to go into the driver setting and take a look as the only adjustment I have at the moment is in setting -> display

---

### Post by mips on 2012-09-10
Full make & model of the tv?

---

### Post by mcduck on 2012-09-10
> **smartalick said:**
> I have tried changing the resolution but 1080 is the only one that comes close to fitting, I think Im with sandyd in thinking its in the overscan - not that I know what I am doing here but it would be nice to go into the driver setting and take a look as the only adjustment I have at the moment is in setting -> display

Sure, the problem with parts of the image going outside f the display area definitely is becausde of overscan.

However using the native resolution would give you the best image quality, as any other resolution will have to be scaled to fit the physical pixels of the display panel. Of course how important that is it depends on what you are using the TV for, if you are just watching movies or playing some games then using a different resolution should be quite OK, but if you plan on using the TV as an actual display for desktop applications you might find the image way too blurry with any other than the native resolution.

---

### Post by smartalick on 2012-09-11
> **mips said:**
> Full make & model of the tv?

I have attached a pic of the details on the back

---

### Post by SeijiSensei on 2012-09-11
Does the TV itself has a sizing option like "widescreen" versus "normal" or "standard"?  Perhaps you have the TV configured to upscale the image when it should not be.  If I connect a computer to my Sony Bravia and choose the "zoom" option, it will make the image too large to fit the screen.  I have to choose a different option, "full" in my case, to make it fit properly.

In addition the TV may have settings that apply to computer inputs.  Bravias have a "full pixel" setting that make the TV have the same display characteristics as a monitor.  

Browse around the TV's settings and see what you find.

---

### Post by mips on 2012-09-11
> **smartalick said:**
> I have attached a pic of the details on the back

Ok it's a Toshiba 32WLT66 and it has a native resolution of 1366x768 pixels. There's a manual [here]("http://www.scribd.com/doc/39812370/32WLT66").

You need to set it up on your PC for 1366x768 resolution.

What gpu/gfx card does your computer have (Make & model)?  The command 'lspci' or 'lspci -v' in a terminal will give us this information so post it here.

---


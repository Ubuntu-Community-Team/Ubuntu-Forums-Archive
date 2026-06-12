---
title: "HDMI output to 32inch LCD TV goes off edges"
date: 2014-03-31
forum: New to Ubuntu
---

### Post by angel5 on 2014-03-31
Hello, Ive been using Ubuntu for a few days now on my Dell Inspiron N5050. I have an Emerson 32" LCD HDTV connected via HDMI and the image on the TV is outside the screen edges. I cant see the top toolbar and only half the launcher is visible when its active on both screens. Its frustrating to have to resize every window to fit exactly and still not see the back or exit buttons! Can somebody point me in the right direction please??

I read about xrandr but im not sure what to change to get the image to fit correctly. this is current settings:



*angel@angel-Inspiron-N5050:~$ xrandr*
*Screen 0: minimum 320 x 200, current 2646 x 768, maximum 32767 x 32767*
*LVDS1 connected primary 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm*
*   1366x768       60.0*+   40.0  *
*   1360x768       59.8     60.0  *
*   1024x768       60.0  *
*   800x600        60.3     56.2  *
*   640x480        59.9  *
*VGA1 disconnected (normal left inverted right x axis y axis)*
*HDMI1 connected 1280x720+1366+0 (normal left inverted right x axis y axis) 16mm x 9mm*
*   1920x1080      60.0 +   59.9     30.0     24.0     30.0     24.0  *
*   1920x1080i     60.1     60.0  *
*   1280x720       60.0*    59.9  *
*   1440x480i      60.1     60.1  *
*   720x480        60.0     59.9  *
*   640x480        60.0     59.9  *
*DP1 disconnected (normal left inverted right x axis y axis)*
*VIRTUAL1 disconnected (normal left inverted right x axis y axis)*
*angel@angel-Inspiron-N5050:~$ *

Any help is greatly appreciated!

---

### Post by mcduck on 2014-03-31
Sounds like overscan. Check your TV's settings, most likely there is a picture mode made for PC or gaming use, or called "pixel-per-pixel", "just scan" or something like that. Or simply an option to switch off overscan. That should fix the problem.

If not (which would be quite rare actually), your graphics card's options may have options for it but in that case you will loose picture quality (as the TV isn't rendering the picture as it is but is doing some scaling) and will also have to mess with the settings when switching between the TV and monitors.

Xrandr would be the way to go only if fixing the problem on TV's end is not possible, and the graphics cardd river you use doesn't give you the option.

---

### Post by angel5 on 2014-03-31
After reading your response, I tried going through the settings manually and there was an option that said PC-Settings but I couldn't select it for some reason. Maybe the TV software needs to be updated... I'm not sure where the settings for the graphics card might be either, Xrandr seems like a good option but I've learned to be careful when using the command prompt. I'm eager to learn and in my curiosity, I've had to re-install Ubuntu twice since I originally replaced Windows. Which I also managed to render completely useless on my HD by exploring more than I know. I guess what i'm trying to say is I am more than willing to use Xrandr to fix the issue. I just don't know how to interpret the command options well enough to do it on my own, can you help me?

---

### Post by mcduck on 2014-03-31
the "PC settings" in TV settings might only be available when using s specific connector on the TV (if it has a VGA D-SUB, that's the most likely one). However even having that option proves the TV is capable of pixel-per-pixel, so it's quite likely that you'd have an option to enable it even with the other conenctors.

I'd still recommend using xrandr only as the last resort, you'll get a bad quality as the TV will scale the picture from your PC up and part of the resolution gets wasted for overscan (same as with overscan compensation from graphics driver). It really is an issue on the TV end and trying to fix it elsewhere will just give you a workaround with less than optimal results.

Edit. I recommend checking your TV's manual, or if you can give the exact model number I might be able to find one online to check what's available.

---

### Post by newb85 on 2014-03-31
Sounds to me like it's a simple matter of adjusting the output of the graphics card to match the resolution of the tv.   The method would carry depending on your graphics card and driver. Please give the output of
[Code] sudo lshw -c video [code]

---

### Post by trag on 2014-03-31
Had same problem,pc output resolutions did not match compatible tv resolutions while under hdmi. after exploring all potential all software solutions I abandoned the hdmi only solution and went to a hdmi to vga converter. my tv supports more vga resolutions than hdmi and with this adapter the problem is solved and my pc/tv have settled on a pleasing  1368x760 resolution which is higher than my tv was willing to go under hdmi only.

---


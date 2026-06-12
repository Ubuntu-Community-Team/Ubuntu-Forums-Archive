---
title: "hdmi link up to monitor - no sound"
date: 2012-09-09
forum: New to Ubuntu
---

### Post by kabukiM0n0 on 2012-09-09
Hey guys. 
I just tried liking up my Aspire One Netbook which is running Gnome fallback (Ubuntu 12.04) to a View Sonic television, which can also be used as a monitor. 

At first I thought HDMI might not support sound, but of course it does as it's the only cable I use to connect to my xbox. 
Anyway, I manage to get the screen output on the television but there is no sound. I tried plugging the (red/white) audio cables into my laptop but that does nothing either. 

Is there any previous configuration that has to be done to enable sound for the HDMI cable in Linux? 

Any help is hugely appreciated!

This might help to identify the problem. 

typing this command
```
sudo xrandr --verbose
```

I get this

```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 600, current 1024 x 600, maximum 1024 x 600
default connected 1024x600+0+0 (0x138) normal (normal) 0mm x 0mm
	Identifier: 0x137
	Timestamp:  850764
	Subpixel:   horizontal rgb
	Clones:    
	CRTC:       0
	CRTCs:      0
	Transform:  1.000000 0.000000 0.000000
	            0.000000 1.000000 0.000000
	            0.000000 0.000000 1.000000
	           filter: 
  1024x600 (0x138)    0.0MHz *current
        h: width  1024 start    0 end    0 total 1024 skew    0 clock    0.0KHz
        v: height  600 start    0 end    0 total  600           clock    0.0Hz

```

---

### Post by newb85 on 2012-09-09
You need to select the correct output in the "Sound Settings..." dialog.  (Sorry, I'm not sure how to get to it in Fallback, but It's probably under "Preferences".)

Under the "Output" tab, there should be an option to Play sound through "HDMI/Display Port".  If it's not there, try rebooting your machine.

---

### Post by kabukiM0n0 on 2012-09-09
Nothing appears in sound settings :/ even though rebooting did fix the screen resolution, nothing changed in reference to sound. see attachment.

---

### Post by lu15 on 2012-09-09
I have this problem too.

---

### Post by newb85 on 2012-09-09
Sounds to me like a driver issue.  Please give more details about your hardware.  Someone with successful experience with similar hardware can chime in.

---

### Post by kabukiM0n0 on 2012-09-09
Okay, I figured it out. I had to install the drm Driver for the Intel GMA500. And then change manually the 'standard' sound to HDMI surround-sound output, which is right at the bottom where it says *connector*. resolution is all over the shop, but that's a different story. 

Thank you

---


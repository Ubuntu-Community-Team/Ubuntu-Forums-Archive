---
title: "Setting correct resolution for TV"
date: 2012-06-14
forum: New to Ubuntu
---

### Post by pienose on 2012-06-14
Okay so I have a computer connected via VGA to a Toshiba HDTV

I cannot get the correct resolution. 

Video card is a GeForce 9800 GTX.

Nvidia X Server settings allows me to set the resolution to 1360x768 which leaves me with black boarders on either side. Every time I restart the computer the resolution is set back to 1024x768. 

xrandr gives me-
```
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1360 x 768, maximum 1360 x 768
default connected 1360x768+0+0 0mm x 0mm
   1360x768       50.0*    52.0  
   1024x768       51.0  
   800x600        53.0     54.0     55.0  
   680x384        56.0     57.0  
   640x480        58.0  
   512x384        59.0  
   400x300        60.0  
   320x240        61.0  
  1984x1080_60.00 (0x17a)  178.2MHz
        h: width  1984 start 2112 end 2320 total 2656 skew    0 clock   67.1KHz
        v: height 1080 start 1083 end 1093 total 1120           clock   59.9Hz
```

I've tried a bunch of stuff, nothing seems to work! Help us out :)

---

### Post by papibe on 2012-06-14
Hi pienose.

Could you restart your computer with the TV connected, and then post the content of these files?
```
/etc/X11/xorg.conf

/var/log/Xorg.0.log
```
Please paste them separately here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the links here.

Regards.

---

### Post by pienose on 2012-06-14
[http://paste.ubuntu.com/1041034/](http://paste.ubuntu.com/1041034/)

[http://paste.ubuntu.com/1041039/](http://paste.ubuntu.com/1041039/)

Thanks for the reply!

---

### Post by papibe on 2012-06-14
```
[    23.912] (WW) NVIDIA(GPU-0): Unable to read EDID for display device CRT-0
```
This is a common error these days: a modern monitor or HDTV, that doesn't report correctly its resolution and timings (EDID) over an analog connection.

A few ideas:

[LIST]
[*]Usually pure digital connections have less errors (like HDMI).

[*]If you have a Windows machine available, it would be possible to get the EDID data using Windows.

[*]There may be other users with the same problem, and may be some of them posted the EDID data somewhere in another forum.

[*]There may be some technical information on the TV manufacture site.
[/LIST]

I hope that helps a little.
Regards.

---


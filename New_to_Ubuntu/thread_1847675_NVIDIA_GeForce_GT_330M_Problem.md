---
title: "NVIDIA GeForce GT 330M Problem"
date: 2011-09-21
forum: New to Ubuntu
---

### Post by technosysind on 2011-09-21
I have an NVIDIA GeForce GT 330M in my laptop and I'm having some problem with the drivers. It says [COLOR=Red]**"THIS DRIVER IS ACTIVATED BUT NOT CURRENTLY IN USE"**[/COLOR]

Please help me get this work properly.
I'm attaching a screenshot of this also

Thanx

---

### Post by realzippy on 2011-09-21
please show

```
lspci | grep VGA
```

---

### Post by technosysind on 2011-09-21
It says 
> 02:00.0 VGA compatible controller: nVidia Corporation GT216 [GeForce GT 330M] (rev a2)


What do I do next??

---

### Post by realzippy on 2011-09-21
post xorg.conf content..

```
cat /etc/X11/xorg.conf
```

---

### Post by technosysind on 2011-09-21
> 
Section "Device"
 Identifier    "Default Device"
 Option    "NoLogo"    "True"
EndSection



I did not understand?

---

### Post by searchfgold6789 on 2011-09-21
Same problem here with the GeForce FX 5200. Desktop effects can be activated and games run smoothly. But in 11.04 the problem is the same, driver is not activated but is currently in use. :S

---

### Post by realzippy on 2011-09-21
```
Section "Device"
Identifier "Default Device"
Option "NoLogo" "True"
EndSection
```

Was this the whole output?

---

### Post by technosysind on 2011-09-21
Yes, This was the whole output !!

---

### Post by realzippy on 2011-09-21
Had a quick look at your other posts...

[http://ubuntuforums.org/showthread.php?t=1847091](http://ubuntuforums.org/showthread.php?t=1847091)

..here you attached screenshots which clearly show that your nvidia driver is working,since you run compiz...?

Note that "drivers activated but not in use" maybe the old jockey bug;
just ignore it.


To be sure you could install glxspheres...

```
sudo add-apt-repository ppa:bumblebee/stable
sudo apt-get update
sudo apt-get install virtualgl
```
then run:
```
glxspheres
```

what does it say?

---

### Post by technosysind on 2011-09-21
It says 
> 
Polygons in scene: 62464
Visual ID of window: 0x27
Context is Direct
OpenGL Renderer: GeForce GT 330M/PCI/SSE2
389.025533 frames/sec - 434.152494 Mpixels/sec
362.921174 frames/sec - 397.783908 Mpixels/sec
407.909652 frames/sec - 400.043522 Mpixels/sec
416.754427 frames/sec - 408.717734 Mpixels/sec
415.527933 frames/sec - 407.514893 Mpixels/sec
416.873443 frames/sec - 408.834456 Mpixels/sec
354.946734 frames/sec - 383.248899 Mpixels/sec
411.108671 frames/sec - 403.180852 Mpixels/sec
421.680344 frames/sec - 413.548661 Mpixels/sec
426.898321 frames/sec - 418.666014 Mpixels/sec
385.745063 frames/sec - 378.306355 Mpixels/sec
418.859941 frames/sec - 410.782646 Mpixels/sec
360.995598 frames/sec - 354.034159 Mpixels/sec
382.401398 frames/sec - 375.027169 Mpixels/sec
419.354476 frames/sec - 411.267645 Mpixels/sec
422.432671 frames/sec - 414.286480 Mpixels/sec
377.119312 frames/sec - 369.846943 Mpixels/sec
359.465676 frames/sec - 352.533740 Mpixels/sec

and also it opens a graphical window. I'm attaching the screenshot of this graphic

---

### Post by technosysind on 2011-09-21
Does the above output mean that everything is working fine??
No Need to worry??

---

### Post by realzippy on 2011-09-21
Exactly.
```
Context is Direct
OpenGL Renderer: GeForce GT 330M/PCI/SSE2
```

..means,3D rendering is direct (hardware) on your 330M.
In your case it is the jockey bug,ignore it.
As mentioned,if you can spin the compiz cube (or cylinder/whatever),then
your nvidia-driver is working.

....
Offtopic,but nice:

when using the cube,try an equirectangular skydome image as backround
(eg: [http://www.flickr.com/groups/equirectangular/pool/](http://www.flickr.com/groups/equirectangular/pool/)  )
..and set skydome to "animated"   ;)

---

### Post by technosysind on 2011-09-21
I've already done that and it looks beautiful. Thank you very much for your help my friend :)

---

### Post by technosysind on 2011-09-21
Can I ask you something? I have posted 51 beans now. How will my control panel enable? Do I have to contact the administrator or will it happen itself?

Thanx again

---

### Post by realzippy on 2011-09-21
There is a script running on the forums,which updates user data every hour.
Maybe you have to log out/in then,dunno.
Little patience...
Please set thread as solved then...(threadtools)
Have fun!

---

### Post by technosysind on 2011-09-21
Alright:) Thanx a lot

---


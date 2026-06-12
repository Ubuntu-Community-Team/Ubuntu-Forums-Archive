---
title: "Yet Another Performance Issue..."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by Ajantis on 2008-07-18
First of all hello everyone :) .

I have been using Ubuntu/Kubuntu for more or less 1-1,5 year and I really love it. It's so much different than XP. It's a great feeling when you use something else than just an ordinary Windows :) .

Anyway, I would be really grateful if somebody could give me a hand with my problem.
My specs are:
Celeron 2000
768MB RAM
GF 6800 256 MB
40 GB HDD

For sure not a high-end machine, but Ubuntu should work. And it works. Slow. The most annoying thing is the delay after opening a program or after clicking Tools/History/Edit in Firefox or any other applications. I tried to trim the system as much as I can, but with no results. Compiz off, no memory consuming processes. I use proprietary drivers for GeForce. I have also removed all unnecessary packages and turned off unused system processes.

I tried changing swappiness to anything from 10 to 90, no results. Unfortunately, I realized my HDD all have DMA disabled
```
/dev/sda6:
 IO_support    =  0 (default)
16-bit)
 HDIO_GET_UNMASKINTR failed: Inappropriate ioctl for device
 HDIO_GET_DMA failed: Inappropriate ioctl for device
 HDIO_GET_KEEPSETTINGS failed: Inappropriate ioctl for device
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 5005/255/63, sectors = 8257347, start = 49335678
```
No matter what I do, I just can't speed up anything.

I checked some tutorials on increasing Ubuntu performance, none of them helped. I'm pretty desperate. I just love Linux, but working on second OS (XP Prof) seems so much faster...

---

### Post by Bachstelze on 2008-07-18
Please paste output of [font="Courier New"]glxinfo | grep -i direct[/font].

Also, with the new drivers used by Ubuntu, DMA is always on, so you shouldn't worry about that.

---

### Post by Ajantis on 2008-07-18
```
ajan@NCR:~$ glxinfo | grep -i direct.
direct rendering: Yes
```

---

### Post by Bachstelze on 2008-07-18
Then maybe your problem is precisely caused by the nvidia drivers, which seem to have vey bad 2D rendering performance on some systems. a good way to objectively test that would be to use [gtkperf](http://gtkperf.sourceforge.net/).

---

### Post by Ajantis on 2008-07-18
Indeed, I remember **serious** gfx problems with my ATI card. GF seems to be a bit better, definitely not as fast as on XP though.

Anyway, here are the results you asked for
```
GtkPerf 0.40 - Starting testing: Fri Jul 18 21:59:48 2008

GtkEntry - time:  0.19
GtkComboBox - time:  5.17
GtkComboBoxEntry - time:  4.44
GtkSpinButton - time:  0.99
GtkProgressBar - time:  0.71
GtkToggleButton - time:  1.49
GtkCheckButton - time:  1.48
GtkRadioButton - time:  2.02
GtkTextView - Add text - time:  1.92
GtkTextView - Scroll - time:  1.56
GtkDrawingArea - Lines - time:  0.82
GtkDrawingArea - Circles - time:  1.10
GtkDrawingArea - Text - time:  5.04
GtkDrawingArea - Pixbufs - time:  0.75
 --- 
Total time: 27.70


```

---

### Post by Bachstelze on 2008-07-18
That is indeed *very* slow. I get 33.25 on my EeePC 701 and 10.something on my desktop (Athlon 64 FX-62, 2 GB of RAM, GeForce 8600 GT).

How did you install your nvidia drivers ?

---

### Post by Ajantis on 2008-07-18
After installing clean Kubuntu 8.04 I was prompted to use proprietary drivers, they were automatically downloaded and installed. From my adventures with ATI drivers I did not want to risk using open drivers.

---


---
title: "Finding out the vertical refresh and horizontal sync rates..."
date: 2008-05-02
forum: New to Ubuntu
---

### Post by khr on 2008-05-02
Does there exist a program to find out the vertical refresh rate and the horizontal sync rate?

---

### Post by perlluver on 2008-05-02
Most newer monitors will tell you waht they are, when you open up the settings for the monitor.

---

### Post by khr on 2008-05-02
> **perlluver said:**
> Most newer monitors will tell you waht they are, when you open up the settings for the monitor.

And how do you do that? :)
BIOS?

---

### Post by perlluver on 2008-05-02
> **khr said:**
> And how do you do that? :)
BIOS?

If you have a wheel, or menu button on your monitor itself, you should be able to press that, and it will bring up the menu, where you would fix your picture and move it.  It shoud be in there usually on top, of that little pop up screen.

---

### Post by khr on 2008-05-02
> **perlluver said:**
> If you have a wheel, or menu button on your monitor itself, you should be able to press that, and it will bring up the menu, where you would fix your picture and move it.  It shoud be in there usually on top, of that little pop up screen.

Im not using a monitor.
Does actually laptop screens have a vertical refresh or horizontal sync rate?

---

### Post by perlluver on 2008-05-02
> **khr said:**
> Im not using a monitor.
Does actually laptop screens have a vertical refresh or horizontal sync rate?

I'm not sure of that, I believe they do, but I have never owned a laptop, therfore I am not sure how to check what it would be.

---

### Post by sailor2001 on 2008-05-02
/usr/share/applications/screen & graffics    Check in there ...

---

### Post by khr on 2008-05-02
> **sailor2001 said:**
> /usr/share/applications/screen & graffics    Check in there ...

That helped, thanks!

The model was set on plug 'n' play which is:
HorizSync: 28.0 - 33.0
VertRefresh: 43 - 72

Just incase its wrong, i wrote down the HorizSync and the VertRefresh for the 1280 x 800 LCD model...

Anyway, i've a question to this:
Can i trust it?

---

### Post by unutbu on 2008-05-02
Run 
```
% xvidtune -show


```

You should get something like

```
"1680x1050"   146.25   1680 1784 1960 2240   1050 1053 1059 1089 -hsync +vsync
```

146.25 is the pixel_clock_freq (in MHz),
2240 is the the h_field_len,
1089 is the v_field_len.

Then, according to [http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline),
the refresh rate (rr) is given by the formula
```

rr = pixel_clock_freq / (h_field_len * v_field_len)

```
In the above case,

rr = 146.25 * 10^6 / (2240*1089) = 59.9 Hz.

rr is also called the Vertical refresh rate.

The horizontal sync rate (hsr) (I'm guessing) is given by

```
hsr = pixel_clock_freq / h_field_len
```

So in the case above, it equals

hsr = 146.25 * 10^6 / 2240 = 65.3 KHz.

These numbers match (to within 0.1) what my monitor tells me the values are.

---

### Post by Zralou on 2008-05-02
When I had to manually edit my xorg.conf file to adjust the monitor, I went to this site to get the specs: [http://www.monitorworld.com/]("http://www.monitorworld.com/")

Don't know if it would work for a laptop tho'.

Sara Lou

---

### Post by Digger78 on 2008-05-02
I dunno if this will work on a laptop but to find what your screen is capable of do the following in a terminal (black text only)

```
sudo apt-get install xresprobe   [COLOR="Red"]*this may already be installed[/COLOR]
```

```
sudo ddcprobe | grep monitorrange
```

If it work it will display something like
```
monitorrange: 30-61, 56-75
```

30-61 would be the horizontal sync range (HorizSync)

56-75 would be the vertical refresh range (VertRefresh)

---

### Post by khr on 2008-05-02
> **unutbu said:**
> Run 
```
% xvidtune -show


```

You should get something like

```
"1680x1050"   146.25   1680 1784 1960 2240   1050 1053 1059 1089 -hsync +vsync
```

146.25 is the pixel_clock_freq (in MHz),
2240 is the the h_field_len,
1089 is the v_field_len.

Then, according to [http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline),
the refresh rate (rr) is given by the formula
```

rr = pixel_clock_freq / (h_field_len * v_field_len)

```
In the above case,

rr = 146.25 * 10^6 / (2240*1089) = 59.9 Hz.

rr is also called the Vertical refresh rate.

The horizontal sync rate (hsr) (I'm guessing) is given by

```
hsr = pixel_clock_freq / h_field_len
```

So in the case above, it equals

hsr = 146.25 * 10^6 / 2240 = 65.3 KHz.

These numbers match (to within 0.1) what my monitor tells me the values are.

When i try "xvidtune -show", i just get this:

Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Unable to query video extension version 

When i search for XFree86-VidModeExtension in Synaptic Package Manager i just get libxxf86vm1, libxxf86vm1-dbg, and libxxf86vm-dev.
I've tried installing all of them but the result is the same.

Anyway, thanks for your help, but could you help me with this?

---

### Post by khr on 2008-05-02
Zralou, it doesnt work for my laptop, thanks anyways.

Digger78, am i supposed to type in: "sudo ddcprobe" first, then "grep monitorrange"? Anyway, i tried sudo ddcprobe it returns atleast 10 lines with resolutions and at the end there are some info about my video card and screen or something. I've looked carefully through it and there's nothing that could be the horizSync or VertRefresh rates.

When i enter "grep monitorrange" it just starts on a new empty line and blinks. It obviously doesn't work on laptops...

Anyway thanks for your help!

---

### Post by unutbu on 2008-05-02
Try

```
sudo apt-get install xvidtune
```

---

### Post by khr on 2008-05-02
> **unutbu said:**
> Try

```
sudo apt-get install xvidtune
```

It returns:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package xvidtune is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  x11-xserver-utils
E: Package xvidtune has no installation candidate

By the way, x11-xserver-utils is already installed.(In synaptic)

---

### Post by unutbu on 2008-05-02
Edit: Please see if you have xserver-xorg-core-dbg installed.

Hm. Please try

```
grep VidMode /var/log/Xorg.0.log
ls -l /usr/lib/xorg/modules/extensions

```

You should see
```

% grep VidMode /var/log/Xorg.0.log
(II) Loading extension XFree86-VidModeExtension

```
and
```
  /usr/lib/xorg/modules/extensions:
  total used in directory 3088 available 260901196
 ...
  -rw-r--r-- 1 root root  148535 2008-01-18 18:18 libextmod.so

```

If you're not seeing these things, then it appears Hardy ships xserver-xorg-core without libextmod.so.
I don't know. You're machine's behaviour is not like mine (running Gutsy). Short of compiling X yourself (cringe) I don't know what to tell you.

---

### Post by khr on 2008-05-02
For "grep VidMode /var/log/Xorg.0.log" i get:
```

(II) Loading extension XFree86-VidModeExtension

```

And for "ls -l /usr/lib/xorg/modules/extensions" i get:
```

total 3064
-rw-r--r-- 1 root root   18824 2008-04-15 19:41 libdbe.so
-rw-r--r-- 1 root root   40629 2008-04-15 19:41 libdri.so
-rw-r--r-- 1 root root  151354 2008-04-15 19:41 libextmod.so
-rw-r--r-- 1 root root 2409784 2008-04-15 19:41 libGLcore.so
-rw-r--r-- 1 root root  429290 2008-04-15 19:41 libglx.so
-rw-r--r-- 1 root root   27976 2008-04-15 19:41 librecord.so
-rw-r--r-- 1 root root   39783 2008-04-15 19:41 libxtrap.so

```

Yes, I'm using Hardy.
edit: xserver-xorg-core-dbg is not installed, i'll install it now...

---

### Post by Digger78 on 2008-05-02
> **khr said:**
> Zralou, it doesnt work for my laptop, thanks anyways.

Digger78, am i supposed to type in: "sudo ddcprobe" first, then "grep monitorrange"? Anyway, i tried sudo ddcprobe it returns atleast 10 lines with resolutions and at the end there are some info about my video card and screen or something. I've looked carefully through it and there's nothing that could be the horizSync or VertRefresh rates.

When i enter "grep monitorrange" it just starts on a new empty line and blinks. It obviously doesn't work on laptops...

Anyway thanks for your help!

the **| grep monitorrange** cuts down the output to just the monitorrange line, so type the whole line then hit enter.

---

### Post by unutbu on 2008-05-02
Does your /etc/X11/xorg.conf say anything about VidModeExtension?

```
Option "DisableVidModeExtension"
```
perhaps?

I'm getting this from:
[http://lists.apple.com/archives/darwinos-users/2002/Oct/msg00084.html](http://lists.apple.com/archives/darwinos-users/2002/Oct/msg00084.html)

---

### Post by wermeulen on 2008-05-02
Hey, give ddcprobe another try--it works for me! Though I'm using a LCD screen on DVI output.

Type the following *exactly* as it appears (or copy & paste) into a terminal. Or just run "sudo ddcprobe" and post the output here :)
```
sudo ddcprobe | grep range
```
In my case, I get:
```
wermeulen@home:~$ sudo ddcprobe | grep range
monitorrange: **30-83, 56-76**

```
The monitorrange gives you first the Horizontal Frequency in kHz (30-83 in this case) and second the Vertical refresh rate in Hz (56-76). For the record, these match the factory documented ranges for my LCD screen.

BTW, to get a modeline for a resolution use gtf. For example to get modeline for 1024 x 768 at 60 Hz, type:
```
gtf 1024 768 60
```

---

### Post by khr on 2008-05-02
Digger78, when it try "sudo ddcprobe | grep monitorrange" nothing happens.
It just asks for my password then nothing happens.
Thanks anyways.

> Does your /etc/X11/xorg.conf say anything about VidModeExtension?
No it doesn't.

Option "DisableVidModeExtension" just returns:
```
bash: Option: command not found
```

---

### Post by unutbu on 2008-05-02
I'm pretty sure this will come up donuts, but anyway, try:

```
grep VidMode /etc/X11/xorg.conf
```

Wermeulen, thanks for pointing out gtf; I didn't know I had that! The problem with it, however, is that *you* have to supply the refresh rate. I think the OP wants to find out the actual refresh rate. xvidtune is the usual tool for querying the X server to find out the actual modeline it is using.

---

### Post by khr on 2008-05-02
> **wermeulen said:**
> Hey, give ddcprobe another try--it works for me! Though I'm using a LCD screen on DVI output.

Type the following *exactly* as it appears (or copy & paste) into a terminal. Or just run "sudo ddcprobe" and post the output here :)
```
sudo ddcprobe | grep range
```
In my case, I get:
```
wermeulen@home:~$ sudo ddcprobe | grep range
monitorrange: **30-83, 56-76**

```
The monitorrange gives you first the Horizontal Frequency in kHz (30-83 in this case) and second the Vertical refresh rate in Hz (56-76). For the record, these match the factory documented ranges for my LCD screen.

BTW, to get a modeline for a resolution use gtf. For example to get modeline for 1024 x 768 at 60 Hz, type:
```
gtf 1024 768 60
```

"sudo ddcprobe | grep range" returns nothing while "sudo ddcprobe" returns:

vbe: VESA 3.0 detected.
oem: ATI ATOMBIOS
vendor: (C) 1988-2005, ATI Technologies Inc.
product: M56P 01.00
memory: 16384kb
mode: 640x400x256
mode: 640x480x256
mode: 800x600x256
mode: 1024x768x256
mode: 1280x1024x256
mode: 132x25 (text)
mode: 132x43 (text)
mode: 640x480x32k
mode: 640x480x64k
mode: 640x480x16m
mode: 800x600x32k
mode: 800x600x64k
mode: 800x600x16m
mode: 1024x768x32k
mode: 1024x768x64k
mode: 1024x768x16m
mode: 1280x1024x32k
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 320x200x32k
mode: 320x200x64k
mode: 320x200x16m
mode: 1600x1200x256
mode: 1600x1200x32k
mode: 1600x1200x64k
edid: 
edid: 1 3
id: 1974
eisa: AUO1974
serial: 00000000
manufacture: 1 2005
input: analog signal.
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
dtiming: 1280x800@59
monitorid: AUO
monitorid: B154EW01 V9

It probably won't work because I'm using my laptop-screen.

---

### Post by khr on 2008-05-02
> **unutbu said:**
> I'm pretty sure this will come up donuts, but anyway, try:

```
grep VidMode /etc/X11/xorg.conf
```

It just returns flying donuts.

---

### Post by unutbu on 2008-05-02
```
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
**dtiming: 1280x800@59**
monitorid: AUO
monitorid: B154EW01 V9

```
I'm not familiar with ddcprobe, but it looks like 59Hz your refresh rate.

---

### Post by wermeulen on 2008-05-02
> **unutbu said:**
> ```
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
**dtiming: 1280x800@59**
monitorid: AUO
monitorid: B154EW01 V9

```
I'm not familiar with ddcprobe, but it looks like 59Hz your refresh rate.

Second that, but know that I stop and think about it ... you are using a laptop screen, so in almost all cases these run at 60hz fixed :) No use thinking about it, just use 60Hz for refresh rate. (ddcprobe can be a little bit off with timings, no matter.)

Some laptop screens support either 60Hz or 75Hz, but even in those cases I believe 60Hz is factory recommended.

---

### Post by khr on 2008-05-02
> **unutbu said:**
> ```
screensize: 33 21
gamma: 2.200000
dpms: RGB, no active off, no suspend, no standby
**dtiming: 1280x800@59**
monitorid: AUO
monitorid: B154EW01 V9

```
I'm not familiar with ddcprobe, but it looks like 59Hz your refresh rate.

Yeah it really is!
Then we just need the HorizSync.

---

### Post by wermeulen on 2008-05-02
> **khr said:**
> Yeah it really is!
Then we just need the HorizSync.

```
wermeulen@home:~$ gtf 1280 1024 60

  # 1280x1024 @ 60.00 Hz (GTF) hsync: 63.60 kHz; pclk: 108.88 MHz
  Modeline "1280x1024_60.00"  108.88  1280 1360 1496 1712  1024 1025 1028 1060  -HSync +Vsync

```

There you go! Just run gtf with desired widht x depth at 60Hz and you get the hsync in the first line.

---

### Post by unutbu on 2008-05-02
```
% gtf 1280 800 59

  # 1280x800 @ 59.00 Hz (GTF) **hsync: 48.85 kHz**; pclk: 82.07 MHz
  Modeline "1280x800_59.00"  82.07  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync

% gtf 1280 800 60

  # 1280x800 @ 60.00 Hz (GTF) **hsync: 49.68 kHz**; pclk: 83.46 MHz
  Modeline "1280x800_60.00"  83.46  1280 1344 1480 1680  800 801 804 828  -HSync +Vsync
```

I agree except that khr's screen res is 1280x800.

---

### Post by Digger78 on 2008-05-02
> **khr said:**
> Yeah it really is!
Then we just need the HorizSync.

Are you looking for these so that you can get a higher resolution on your laptop?

if so just edit your etc/X11/xorg.conf

```
Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   [B]HorizSync 28-72
   VertRefresh 43-60[/B]
EndSection

```

and 

```
Section "Screen"
   Identifier   "Default Screen"
   Device      "Generic Video Card"
   Monitor      "Generic Monitor"
   DefaultDepth   24
   SubSection "Display"
      **Modes      "1280x800"**
   EndSubSection
EndSection
```

---

### Post by khr on 2008-05-02
Success!!!!

I thank everybody who've posted in this thread and helped me!
I've had this problem since i used Gutsy and had problem changing my resolution to 1280x800... But finally i got help from you guys!

Thank you very much!

Cheers!

PS: I think my refresh rate is 65 Hz since you guys got me to remember that i once used a program to find my refresh rate and the result was 65 Hz.
Also, is there actually any difference from using the wrong refresh rate?

Edit: No, I'm just looking for the vertical refresh and horizontal sync rates to fine-tune my settings. :)
Edit2: Unutbu, is it correct if my horizsync is 54.01 kHz?

---

### Post by unutbu on 2008-05-02
Be careful not to drive your monitor at a refresh rate which is outside the manufacturer's specs. I've been told (but never tried) it can result in a broken monitor.

---

### Post by Fedz on 2008-05-02
The refresh rate is is basically a current rate frequency to your monitor otherwise you'll have a wrong current rate frequency and the video card sends the wrong current rate frequency to the monitor which the monitor can't hear - so you get out of range signal :)

Upto 65 is a standard range for monitors on default :)

---

### Post by khr on 2008-05-02
One last question:

Is vertical sync rate and vertical refresh rate the same?

---

### Post by wermeulen on 2008-05-02
> **khr said:**
> One last question:

Is vertical sync rate and vertical refresh rate the same?

Short: no

Vertical refresh rate is how many times per second the screen is redrawn, top to bottom. Vertical sync (without the rate) applies to CRT monitors (them big old screens :-)) and it means the pixel data in memory should only be changed when the ray that draws all the pixels on the screen is at the bottom of the screen. When the ray sweeps back up to the top of the screen to start redrawing the screen again, if you then change the pixel data in memory you wouldn't see it and as such the screen wouldn't flicker. Don't know if this applies to LCD monitors though.

---

### Post by Fedz on 2008-05-02
No not the same by any means.

H is a range (frequency)

V is a refresh range rate.

The can and are different.

---

### Post by khr on 2008-05-02
Thanks guys...
Anyway, do laptops have vertical sync?

If they do how do i find it out?
I'm guessing that we can find it out with the "gtf 1280 800 65" results:
```
 # 1280x800 @ 65.00 Hz (GTF) hsync: 54.01 kHz; pclk: 91.61 MHz
  Modeline "1280x800_65.00"  91.61  1280 1352 1488 1696  800 801 804 831  -HSync +Vsync
```
But where is the Vsync?

---

### Post by unutbu on 2008-05-02
I think manually changing modelines is no longer the kosher way of configuring X. Check out

[http://en.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/](http://en.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/)

> This HOWTO is effectively obsolete. Current (4.0.1 and up) versions of XFree86 compute optimal modelines from the resolution you specify in the Modes section of your X configuration file.

---

### Post by wermeulen on 2008-05-02
> **unutbu said:**
> I think manually changing modelines is no longer the kosher way of configuring X. Check out

[http://en.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/](http://en.tldp.org/HOWTO/XFree86-Video-Timings-HOWTO/)




[http://en.wikipedia.org/wiki/XFree86_Modeline](http://en.wikipedia.org/wiki/XFree86_Modeline)
[http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)

Hey, unutbu is fast... Beat me to those links, which I was about to post :)

---


---
title: "DVB/TV tuner in VLC?"
date: 2008-10-08
forum: New to Ubuntu
---

### Post by sacredsunder on 2008-10-08
I have an old ATI TV WONDER PRO that I am trying to get to work. Previously in Windows I have used Dscaler and it worked fine. In Ubuntu if I check $ lspci -vnn my card shows up, but I don't have a directory in /dev/ called /dbv/adapter0/ and I'm just wondering how do I set up my card to work with that?:confused: I'm trying to avoid myth tv, and I think I might be able to get it to work in VLC because it has the option to play DBV.

Any help is greatly appreciated!:):)

---

### Post by Jose Catre-Vandis on 2008-10-08
Can you output the following:

lspci -v

and

dmesg  (after boot-up)

and post back to this thread?

---

### Post by sacredsunder on 2008-10-15
> **Jose Catre-Vandis said:**
> Can you output the following:

lspci -v

and

dmesg  (after boot-up)

and post back to this thread?

Sorry it took me so long to reply, got a little busy. I attached the lspci as a text file but the dmesg was too big to attach. Were these the lines you were looking for?

[   44.478106] cx88[0]: subsystem: 1002:00f8, board: ATI TV Wonder Pro [card=4,autodetected]
[   44.478108] cx88[0]: TV tuner type 44, Radio tuner type -1
[   44.626383] cx88[0]/0: found at 0000:03:06.0, rev: 5, irq: 21, latency: 32, mmio: 0xfb000000
[   44.653143] tuner 1-0043: chip found @ 0x86 (cx88[0])
[   44.653160] tda9887 1-0043: tda988[5/6/7] found @ 0x43 (tuner)
[   44.653162] tuner 1-0043: type set to tda9887
[   44.655176] All bytes are equal. It is not a TEA5767
[   44.655177] tuner 1-0060: chip found @ 0xc0 (cx88[0])
[   44.655185] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   44.655187] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   44.655189] tuner-simple 1-0060: type set to 44 (Philips 4 in 1 (ATI TV Wonder Pro/Conexant))
[   44.655191] tuner 1-0060: type set to Philips 4 in 1 (ATI
[   44.661718] cx88[0]/0: registered device video0 [v4l2]
[   44.661733] cx88[0]/0: registered device vbi0

---

### Post by Jose Catre-Vandis on 2008-10-15
OK, I think this is what may be needed:

run this code in a terminal:
```
sudo modprobe cx88xx
```

For this to work everytime, add the line cx88_dvb to your /etc/modules file:
```
sudo nano /etc/modules

add cx88_dvb to bottom of list

CTRL+X, then Y, then Enter
```

Analog:
```
sudo apt-get install tvtime
```
Run tvtime (Applications>Sound & Video>TvTime)
hopefully it will present a menu from which you can start to scan for channels - be patient. If all goes well, you have analog tv working.

---

### Post by sacredsunder on 2008-10-15
Thanks, it works, but I have a question. Every time I shut down TVtime, when I start it again, none of the channels or picture settings are saved. Also I have black space in the top and left of the screen and I can't figure out how to fix that.

---

### Post by sacredsunder on 2008-10-15
> **sacredsunder said:**
> Thanks, it works, but I have a question. Every time I shut down TVtime, when I start it again, none of the channels or picture settings are saved. Also I have black space in the top and left of the screen and I can't figure out how to fix that.

Ok... now I have more problems. After I restarted the computer It wont load at all. I get this error when I try to run it from console

Running tvtime 1.0.2.
Reading configuration from /etc/tvtime/tvtime.xml
I/O warning : failed to load external entity "/home/sacredsunder/.tvtime/tvtime.xml"
I/O error : Permission denied
I/O error : Permission denied
Cannot change owner of /home/sacredsunder/.tvtime/tvtime.xml: Permission denied.
xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver.  If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

---

### Post by Jose Catre-Vandis on 2008-10-16
Yeah, it sometimes happens that tvtime puts stuff in your home directory then makes it read-only (or gives it root permissions)

```
sudo chmod -R 777 /home/sacredsunder/.tvtime
```

to give full read / write permissions to everybody for the .tvtime directory

Also, check the tvtime website for advice on the overlay issue, there is a fix on there for this issue, if memory serves me right

---

### Post by sacredsunder on 2008-10-17
> **Jose Catre-Vandis said:**
> Yeah, it sometimes happens that tvtime puts stuff in your home directory then makes it read-only (or gives it root permissions)

```
sudo chmod -R 777 /home/sacredsunder/.tvtime
```

to give full read / write permissions to everybody for the .tvtime directory

Also, check the tvtime website for advice on the overlay issue, there is a fix on there for this issue, if memory serves me right

That got rid of the permission errors, but I still have this error

xvoutput: No XVIDEO port found which supports YUY2 images.

*** tvtime requires hardware YUY2 overlay support from your video card
*** driver. If you are using an older NVIDIA card (TNT2), then
*** this capability is only available with their binary drivers.
*** For some ATI cards, this feature may be found in the experimental
*** GATOS drivers: [http://gatos.souceforge.net/](http://gatos.souceforge.net/)
*** If unsure, please check with your distribution to see if your
*** X driver supports hardware overlay surfaces.

I am using the ati proprietary driver

---

### Post by Jose Catre-Vandis on 2008-10-18
As suggested try following the advice here:

[http://tvtime.sourceforge.net/problems.html#fgloverlay](http://tvtime.sourceforge.net/problems.html#fgloverlay)

---

### Post by sacredsunder on 2008-10-18
I don't have the file they are talking about. It kinda looks like xorg.conf, so I put those values under 


```
Section "Device"
	Identifier	"Configured Video Device"
	Driver		"fglrx"
	Option		"VideoOverlay"	"on"
	Option		"OpenGLOverlay"	"off"
```

I had to put in the VideoOverlay and OpenGLOverlay, they weren't there already. I still get the error.

---

### Post by Jose Catre-Vandis on 2008-10-18
You got it, it should go in /etc/X11/xorg.conf in the Device section. I guess you have restarted X?

Reached the end of my knowledge here, you have done everything I would do to get such a card working. 

Done a bit of research, try replacing cx88xx with **cx2388x or cx8800** this seems to be the latest incarnation, and describes your ATi card as you list in your dmesg as No. 4.

---


---
title: "HOW-TO: Flyvideo3000 saa7134, tv and radio viewing"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by humanity_to_others on 2005-10-15
Learn your card number from this page: [http://linux.bytesex.org/](http://linux.bytesex.org/) or [http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)
For Flyvideo 3000 number is 2 ```
sudo gedit /etc/modules
```add the line```
saa7134 card=2
```and I use tvtime for viewing you can get it with synaptic and after next reboot for channel scanning : ```
tvtime-scanner
``` 

If you want to use mplayer for viewing first install it with fonts and codecs (mplayer-386 mplayer-fonts w32codecs) then edit config file,```
gedit .mplayer/config
``` add the following line:```
tv=driver=v4l2:device=/dev/video0:fps=25:chanlist=etc:norm=pal:
audiorate=32000:adevice=/dev/dsp1:input=0:amode=1:normid=4
```and```
mplayer tv://
``` 

For recording install mencoder for your processor (-586 -k7 -k6) and edit config file:```
gedit .mplayer/mencoder
```
add this line: ```
tv=driver=v4l2:device=/dev/video0:fps=25:norm=pal:amode=1:
width=640:height=480
```and recording command:
```
mencoder tv:// -ovc lavc -oac mp3lame
```

For radio listening and recording gnomeradio is well enough, first download it:
```
wget -c http://www.wh-hms.uni-ulm.de/~mfcn/gnomeradio/packages/gnomeradio_1.6-1_i386.deb
```
then install:```
sudo dpkg -i gnomeradio_1.6-1_i386.deb
```I also changed default device from /dev/radio to /dev/radio0 in settings.

---

### Post by abena on 2007-04-26
[COLOR="DarkRed"][I]Hi, I have a big dude, I did all here and I still don't have input signal on my tvtime... what do I suppose to have on my modules file, 'cause actually I just have that line (saa7134 card = 2)

Thanks![/I][/COLOR]

---

### Post by intact on 2009-09-03
Hi, 
Im trying to get the remote control working (flyview 3000), but havent found much info, any idea how to get it done?

Greets

---

### Post by Vortex_nc on 2010-05-01
Hey guys

I have this TV card aswell. My problem is with gnomeradio. It wants to listen on dig1. I don't have any digital inputs. how do I configure it to listen on line-in? The setup menu doesn't have the option. I have an Intel G945gm motherboard

---


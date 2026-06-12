---
title: "[SOLVED] Problem with tvtime"
date: 2008-09-26
forum: New to Ubuntu
---

### Post by WitchCraft on 2008-09-26
I installed tvtime, and wanted to watch TV over my Pinnacle PCTV 150e USB device.

Now it doesn't work when i start tvtime.
I figured this is because tvtime looks at /dev/video0, and there is my integrated Chicony webcam.

so i started it with: tvtime --device /dev/video1
Now I have the pictures,, but I don't have any sound...

I read somewhare that you need to press the right arrow to increase the volume, and when I did so, I saw "volume 0", but pressing the right arrow repeatedly or staying on it does not increase the volume...

What is wrong?
(volume is on, i can listen to music using vlc or totem or mplayer)

Here a listing for my devices:
```

:~# lsusb
Bus 006 Device 005: ID 2304:0208 Pinnacle Systems, Inc. [hex] Pinnacle Studio PCTV USB2
Bus 006 Device 003: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 006 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

:~# ls /dev/vid*
/dev/video0  /dev/video1

:~# ls /dev/dsp*
/dev/dsp  /dev/dsp2




:/dev# ls
audio      ptybf  ptyqd  ptyvb  ram3        tty58  ttye4  ttyse  ttyxc
audio2     ptyc0  ptyqe  ptyvc  ram4        tty59  ttye5  ttysf  ttyxd
bus        ptyc1  ptyqf  ptyvd  ram5        tty6   ttye6  ttyt0  ttyxe
cdrom      ptyc2  ptyr0  ptyve  ram6        tty60  ttye7  ttyt1  ttyxf
cdrw       ptyc3  ptyr1  ptyvf  ram7        tty61  ttye8  ttyt2  ttyy0
console    ptyc4  ptyr2  ptyw0  ram8        tty62  ttye9  ttyt3  ttyy1
core       ptyc5  ptyr3  ptyw1  ram9        tty63  ttyea  ttyt4  ttyy2
disk       ptyc6  ptyr4  ptyw2  random      tty7   ttyeb  ttyt5  ttyy3
dri        ptyc7  ptyr5  ptyw3  rtc         tty8   ttyec  ttyt6  ttyy4
dsp        ptyc8  ptyr6  ptyw4  sda         tty9   ttyed  ttyt7  ttyy5
dsp2       ptyc9  ptyr7  ptyw5  sda1        ttya0  ttyee  ttyt8  ttyy6
dvd        ptyca  ptyr8  ptyw6  sda2        ttya1  ttyef  ttyt9  ttyy7
dvdrw      ptycb  ptyr9  ptyw7  sda3        ttya2  ttyp0  ttyta  ttyy8
fd         ptycc  ptyra  ptyw8  sequencer   ttya3  ttyp1  ttytb  ttyy9
full       ptycd  ptyrb  ptyw9  sequencer2  ttya4  ttyp2  ttytc  ttyya
fuse       ptyce  ptyrc  ptywa  sg0         ttya5  ttyp3  ttytd  ttyyb
hda        ptycf  ptyrd  ptywb  shm         ttya6  ttyp4  ttyte  ttyyc
hpet       ptyd0  ptyre  ptywc  snapshot    ttya7  ttyp5  ttytf  ttyyd
initctl    ptyd1  ptyrf  ptywd  snd         ttya8  ttyp6  ttyu0  ttyye
input      ptyd2  ptys0  ptywe  sndstat     ttya9  ttyp7  ttyu1  ttyyf
kmem       ptyd3  ptys1  ptywf  stderr      ttyaa  ttyp8  ttyu2  ttyz0
kmsg       ptyd4  ptys2  ptyx0  stdin       ttyab  ttyp9  ttyu3  ttyz1
log        ptyd5  ptys3  ptyx1  stdout      ttyac  ttypa  ttyu4  ttyz2
loop0      ptyd6  ptys4  ptyx2  tty         ttyad  ttypb  ttyu5  ttyz3
loop1      ptyd7  ptys5  ptyx3  tty0        ttyae  ttypc  ttyu6  ttyz4
loop2      ptyd8  ptys6  ptyx4  tty1        ttyaf  ttypd  ttyu7  ttyz5
loop3      ptyd9  ptys7  ptyx5  tty10       ttyb0  ttype  ttyu8  ttyz6
loop4      ptyda  ptys8  ptyx6  tty11       ttyb1  ttypf  ttyu9  ttyz7
loop5      ptydb  ptys9  ptyx7  tty12       ttyb2  ttyq0  ttyua  ttyz8
loop6      ptydc  ptysa  ptyx8  tty13       ttyb3  ttyq1  ttyub  ttyz9
loop7      ptydd  ptysb  ptyx9  tty14       ttyb4  ttyq2  ttyuc  ttyza
MAKEDEV    ptyde  ptysc  ptyxa  tty15       ttyb5  ttyq3  ttyud  ttyzb
mcelog     ptydf  ptysd  ptyxb  tty16       ttyb6  ttyq4  ttyue  ttyzc
mem        ptye0  ptyse  ptyxc  tty17       ttyb7  ttyq5  ttyuf  ttyzd
mixer      ptye1  ptysf  ptyxd  tty18       ttyb8  ttyq6  ttyv0  ttyze
mixer1     ptye2  ptyt0  ptyxe  tty19       ttyb9  ttyq7  ttyv1  ttyzf
mixer2     ptye3  ptyt1  ptyxf  tty2        ttyba  ttyq8  ttyv2  urandom
net        ptye4  ptyt2  ptyy0  tty20       ttybb  ttyq9  ttyv3  usbdev1.1_ep00
null       ptye5  ptyt3  ptyy1  tty21       ttybc  ttyqa  ttyv4  usbdev1.1_ep81
nvidia0    ptye6  ptyt4  ptyy2  tty22       ttybd  ttyqb  ttyv5  usbdev2.1_ep00
nvidiactl  ptye7  ptyt5  ptyy3  tty23       ttybe  ttyqc  ttyv6  usbdev2.1_ep81
oldmem     ptye8  ptyt6  ptyy4  tty24       ttybf  ttyqd  ttyv7  usbdev3.1_ep00
port       ptye9  ptyt7  ptyy5  tty25       ttyc0  ttyqe  ttyv8  usbdev3.1_ep81
ppp        ptyea  ptyt8  ptyy6  tty26       ttyc1  ttyqf  ttyv9  usbdev4.1_ep00
psaux      ptyeb  ptyt9  ptyy7  tty27       ttyc2  ttyr0  ttyva  usbdev4.1_ep81
ptmx       ptyec  ptyta  ptyy8  tty28       ttyc3  ttyr1  ttyvb  usbdev5.1_ep00
pts        ptyed  ptytb  ptyy9  tty29       ttyc4  ttyr2  ttyvc  usbdev5.1_ep81
ptya0      ptyee  ptytc  ptyya  tty3        ttyc5  ttyr3  ttyvd  usbdev6.1_ep00
ptya1      ptyef  ptytd  ptyyb  tty30       ttyc6  ttyr4  ttyve  usbdev6.1_ep81
ptya2      ptyp0  ptyte  ptyyc  tty31       ttyc7  ttyr5  ttyvf  usbdev6.3_ep00
ptya3      ptyp1  ptytf  ptyyd  tty32       ttyc8  ttyr6  ttyw0  usbdev6.3_ep83
ptya4      ptyp2  ptyu0  ptyye  tty33       ttyc9  ttyr7  ttyw1  usbdev6.5_ep00
ptya5      ptyp3  ptyu1  ptyyf  tty34       ttyca  ttyr8  ttyw2  usbdev6.5_ep81
ptya6      ptyp4  ptyu2  ptyz0  tty35       ttycb  ttyr9  ttyw3  usbdev6.5_ep82
ptya7      ptyp5  ptyu3  ptyz1  tty36       ttycc  ttyra  ttyw4  usbdev6.5_ep84
ptya8      ptyp6  ptyu4  ptyz2  tty37       ttycd  ttyrb  ttyw5  vbi0
ptya9      ptyp7  ptyu5  ptyz3  tty38       ttyce  ttyrc  ttyw6  vcs
ptyaa      ptyp8  ptyu6  ptyz4  tty39       ttycf  ttyrd  ttyw7  vcs1
ptyab      ptyp9  ptyu7  ptyz5  tty4        ttyd0  ttyre  ttyw8  vcs2
ptyac      ptypa  ptyu8  ptyz6  tty40       ttyd1  ttyrf  ttyw9  vcs3
ptyad      ptypb  ptyu9  ptyz7  tty41       ttyd2  ttys0  ttywa  vcs4
ptyae      ptypc  ptyua  ptyz8  tty42       ttyd3  ttyS0  ttywb  vcs5
ptyaf      ptypd  ptyub  ptyz9  tty43       ttyd4  ttys1  ttywc  vcs6
ptyb0      ptype  ptyuc  ptyza  tty44       ttyd5  ttyS1  ttywd  vcs7
ptyb1      ptypf  ptyud  ptyzb  tty45       ttyd6  ttys2  ttywe  vcs8
ptyb2      ptyq0  ptyue  ptyzc  tty46       ttyd7  ttyS2  ttywf  vcsa
ptyb3      ptyq1  ptyuf  ptyzd  tty47       ttyd8  ttys3  ttyx0  vcsa1
ptyb4      ptyq2  ptyv0  ptyze  tty48       ttyd9  ttyS3  ttyx1  vcsa2
ptyb5      ptyq3  ptyv1  ptyzf  tty49       ttyda  ttys4  ttyx2  vcsa3
ptyb6      ptyq4  ptyv2  ram0   tty5        ttydb  ttys5  ttyx3  vcsa4
ptyb7      ptyq5  ptyv3  ram1   tty50       ttydc  ttys6  ttyx4  vcsa5
ptyb8      ptyq6  ptyv4  ram10  tty51       ttydd  ttys7  ttyx5  vcsa6
ptyb9      ptyq7  ptyv5  ram11  tty52       ttyde  ttys8  ttyx6  vcsa7
ptyba      ptyq8  ptyv6  ram12  tty53       ttydf  ttys9  ttyx7  vcsa8
ptybb      ptyq9  ptyv7  ram13  tty54       ttye0  ttysa  ttyx8  video0
ptybc      ptyqa  ptyv8  ram14  tty55       ttye1  ttysb  ttyx9  video1
ptybd      ptyqb  ptyv9  ram15  tty56       ttye2  ttysc  ttyxa  xconsole
ptybe      ptyqc  ptyva  ram2   tty57       ttye3  ttysd  ttyxb  zero


:~# cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf8600000 irq 16
 1 [HDMI           ]: HDA-Intel - HDA ATI HDMI
                      HDA ATI HDMI at 0xf8010000 irq 19
 2 [PAL            ]: USB-Audio - PCTV USB2 PAL
                      Pinnacle Systems GmbH PCTV USB2 PAL at usb-0000:00:13.5-2, high speed


```

---

### Post by WitchCraft on 2008-09-26
OK, i was able to solve the problem:

sudo apt-get install sox libsox-fmt-all

```

#!/bin/sh
#-q
# sudo apt-get install sox libsox-fmt-all
#
# start-tv.sh
#
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp2 -t ossdsp -w -r 32000 /dev/dsp &
soxpid=$!
sleep 0.5
tvtime --device /dev/video1
kill $soxpid

```


For default installation:
```

#!/bin/sh
#-q
# sudo apt-get install sox libsox-fmt-all
#
# start-tv.sh
#
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
soxpid=$!
sleep 0.5
tvtime --device /dev/video0
kill $soxpid

```

---

### Post by megamania on 2008-10-15
> **WitchCraft said:**
> OK, i was able to solve the problem:

I had been looking for a solution for a LONG time!

I'm using a Hauppauge 1100, and although I had sound with TVtime it had a big delay (over 1 second).
I tried several solutions, without success - until now.

I can finally say bye-bye to mplayer for watching TV!

**Thank you!**

---

### Post by megamania on 2008-10-18
> **megamania said:**
> 
I can finally say bye-bye to mplayer for watching TV!

I spoke too early!

While TVtime works perfectly and has a far better quality than mplayer, when using this script it interferes with pulseaudio (I think) and I'm not able to get any sound from other programs until I close TVtime.

Does anybody know how to fix it?

EDIT:
[http://ubuntuforums.org/showthread.php?t=723618](http://ubuntuforums.org/showthread.php?t=723618)
this solution appears to work: just add the command padsp before the "sox" command:
```
padsp sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
```

---

### Post by orion2087 on 2008-11-04
Very nice solution. I noticed the volume was way too high with my AVermedia MCE1500, so I cut it down to 10% by adding a -v to sox:

```
padsp sox -v -0.1 -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000
```

Sadly, I've got another problem where the audio is behind the video after a little bit of playing time. I hear little skips here and there.

---

### Post by WitchCraft on 2008-12-11
> **orion2087 said:**
> Very nice solution. I noticed the volume was way too high with my AVermedia MCE1500, so I cut it down to 10% by adding a -v to sox:

```
padsp sox -v -0.1 -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000
```

Sadly, I've got another problem where the audio is behind the video after a little bit of playing time. I hear little skips here and there.

Interesting.
I don't have this problem, maybe you should use ALSA instead of pulseaudio.
ALSA usually **solves** [COLOR="Red"][SIZE="3"]AL[/SIZE][/COLOR]L [COLOR="Red"][SIZE="3"]S[/SIZE][/COLOR]ORTS OF [COLOR="Red"][SIZE="3"]A[/SIZE][/COLOR]NNOYANCES. ):P

---


---
title: "No sound, Ubuntu 12.04"
date: 2013-05-01
forum: New to Ubuntu
---

### Post by 007casper on 2013-05-01
I tried so many things, I just cant make it work.

OS ubuntu 12.04

it stopped working after I installed an additional old hard drive.  I disconnected the old hard drive, and tried so many different things for sound to work again.

It just doesnt work.

tried this
> sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get install alsa-base
sudo apt-get install pulseaudio
sudo alsa force-reload
reboot


???

---

### Post by 007casper on 2013-05-03
bump

---

### Post by Isamu715 on 2013-05-03
Run:
```
alsamixer
```
and see if channels are not muted. Or alternatively:
```

amixer sset Master unmute 
```

---

### Post by 007casper on 2013-05-04
tried that

no luck.  I tried so many things... it just doesnt work.

alsa mixer master at 100

amixer sset Master unmute> 
Simple mixer control 'Master',0
  Capabilities: pvolume pvolume-joined pswitch pswitch-joined penum
  Playback channels: Mono
  Limits: Playback 0 - 39
  Mono: Playback 24 [62%] [-22.50dB] [on]

---

### Post by claracc on 2013-05-04
Could you try, in this order:```
[CODE][CODE]killall pulseaudio
sudo alsa force-reload
pulseaudio -D
```[/CODE][/CODE]

Also, you can try to kill and restart pulseaudio:
```
pulseaudio -vvv
```

Anycase, it would be desirable to know what sound card you have:
```
aplay -l
```

---

### Post by 007casper on 2013-05-05
pulseaudio -vvv> 
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
D: [pulseaudio] core-rtclock.c: Timer slack is set to 50 us.
D: [pulseaudio] core-util.c: RealtimeKit worked.
I: [pulseaudio] core-util.c: Successfully gained nice level -11.
I: [pulseaudio] main.c: This is PulseAudio 2.0
D: [pulseaudio] main.c: Compilation host: x86_64-pc-linux-gnu
D: [pulseaudio] main.c: Compilation CFLAGS: -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -g -O2 -fstack-protector --param=ssp-buffer-size=4 -Wformat -Wformat-security -Werror=format-security -Wall -W -Wextra -pipe -Wno-long-long -Wvla -Wno-overlength-strings -Wunsafe-loop-optimizations -Wundef -Wformat=2 -Wlogical-op -Wsign-compare -Wmissing-include-dirs -Wformat-nonliteral -Wpointer-arith -Winit-self -Wdeclaration-after-statement -Wfloat-equal -Wmissing-prototypes -Wredundant-decls -Wmissing-declarations -Wmissing-noreturn -Wshadow -Wendif-labels -Wcast-align -Wstrict-aliasing -Wwrite-strings -Wno-unused-parameter -ffast-math -Wp,-D_FORTIFY_SOURCE=2 -fno-common -fdiagnostics-show-option
D: [pulseaudio] main.c: Running on host: Linux x86_64 3.2.0-41-generic #66-Ubuntu SMP Thu Apr 25 03:27:11 UTC 2013
D: [pulseaudio] main.c: Found 4 CPUs.
I: [pulseaudio] main.c: Page size is 4096 bytes
D: [pulseaudio] main.c: Compiled with Valgrind support: no
D: [pulseaudio] main.c: Running in valgrind mode: no
D: [pulseaudio] main.c: Running in VM: no
D: [pulseaudio] main.c: Optimized build: yes
D: [pulseaudio] main.c: FASTPATH defined, only fast path asserts disabled.
I: [pulseaudio] main.c: Machine ID is e02a3f17414f7361a896752f00000006.
I: [pulseaudio] main.c: Session ID is e02a3f17414f7361a896752f00000006-1367466993.765584-19738657.
I: [pulseaudio] main.c: Using runtime directory /home/candy/.pulse/e02a3f17414f7361a896752f00000006-runtime.
I: [pulseaudio] main.c: Using state directory /home/candy/.pulse.
I: [pulseaudio] main.c: Using modules directory /usr/lib/pulse-2.0/modules.
I: [pulseaudio] main.c: Running in system mode: no
E: [pulseaudio] pid.c: Daemon already running.
E: [pulseaudio] main.c: pa_pid_file_create() failed.

since I got operation not permited. 
I: [pulseaudio] main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: [pulseaudio] main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted

I tried it with root... I can post it here but it is long, and it just hangs in terminal.

aplay -l> 
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: AD198x Analog [AD198x Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: AD198x Digital [AD198x Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 7: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 8: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: NVidia [HDA NVidia], device 9: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

no luck - sound still doesnt work...

---

### Post by MrSteve on 2013-05-06
on my system (12.04 LTS) i have usb attached speakers and have to go to sound settings and mark/click the usb speakers in the menu for them to work

you could also try 
in a terminal write

sudo gnome-control-center

press enter then enter your password and change sound settings from there ...

---

### Post by 007casper on 2013-05-06
my speakers are connected to speaker jack.  I am not using usb for sound.

I did sudo gnome-control-center for input and output, I dont see anything listed for input, and output.  I get nothing.

I dont really know what had happen... I have a feeling connecting old hard drive somehow corrupted sound drivers.  It used to work.  I cant figure out how to fix it.

???

---

### Post by 007casper on 2013-05-07
bump

---

### Post by 007casper on 2013-05-07
seriously - anybody ???

There is no way to fix this besides reloading the whole OS

---

### Post by Lightning Dragon on 2013-05-07
Hi,

I don't think connecting an old hard drive would have caused this unless while you were connecting it you accidentally unplugged something/damaged something on your board. To me it sounds like pulseaudio is either broken or not installed. Could you post the output of

lspci

And also could  you tell me the exact output of

alsamixer

What does it say? "oo" or "mm"? Next, see if the following can help you;

[http://askubuntu.com/questions/144609/pulseaudio-does-not-start-after-logout-and-login-again](http://askubuntu.com/questions/144609/pulseaudio-does-not-start-after-logout-and-login-again)

But it might be your default.pa file that is broken. Luckily I found someone online who posted his file that might work. Could you try this and report back if it was a success or not?

[http://askubuntu.com/questions/225444/how-to-make-pulseaudio-work-again](http://askubuntu.com/questions/225444/how-to-make-pulseaudio-work-again)

Hope it helps!

---

### Post by 007casper on 2013-05-11
lspci

> 00:00.0 Host bridge: Intel Corporation 4 Series Chipset DRAM Controller (rev 03)
00:02.0 VGA compatible controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation 4 Series Chipset Integrated Graphics Controller (rev 03)
00:03.0 Communication controller: Intel Corporation 4 Series Chipset HECI Controller (rev 03)
00:03.2 IDE interface: Intel Corporation 4 Series Chipset PT IDER Controller (rev 03)
00:03.3 Serial controller: Intel Corporation 4 Series Chipset Serial KT Controller (rev 03)
00:19.0 Ethernet controller: Intel Corporation 82567LM-3 Gigabit Network Connection (rev 02)
00:1a.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #5 (rev 02)
00:1a.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #6 (rev 02)
00:1a.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 1 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801JD/DO (ICH10 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB controller: Intel Corporation 82801JD/DO (ICH10 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev a2)
00:1f.0 ISA bridge: Intel Corporation 82801JDO (ICH10DO) LPC Interface Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 4-port SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801JD/DO (ICH10 Family) SMBus Controller (rev 02)
00:1f.5 IDE interface: Intel Corporation 82801JD/DO (ICH10 Family) 2-port SATA IDE Controller (rev 02)
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [ION] (rev a2)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)


alsamixer
> 
master "00" at 100
headphone "00" - empty
PCM no "00" or "mm" at 100<>100
front "00" 100<>100
front mi "mm" 0<>0
front mi no "00" or "mm" 0<>0
surround "00" at 100<>100
center "00" at 100
LFE "00" at 100
Line "mm" 0<>0
Line In no "00" or "mm" 0<>0
CD "mm" 0<>0

front mic bo 0<>0
line-in boos 0<>0
Mic Boost 22<>22
Capture 42<>42
capture 1 39<>39
Digital 24<>24
Input Source Mic nothing
Input Source Front mic nothing


---

### Post by 007casper on 2013-05-11
/etc/pulse$ ls -al
total 36
drwxr-xr-x   2 root root  4096 May  1 20:51 .
drwxr-xr-x 156 root root 12288 May 11 04:21 ..
-rw-r--r--   1 root root  1269 May 31  2012 client.conf
-rw-r--r--   1 root root  2317 May 28  2012 daemon.conf
-rw-r--r--   1 root root  5668 May 28  2012 default.pa
-rw-r--r--   1 root root  2284 May 28  2012 system.pa

it still doesnt work.  I wondered if it is a permission issue.  I also tried the links provided.

thank you so much

---

### Post by 007casper on 2013-05-11
through terminal I launced gstreamer... I tried different output plugins and click on pipeline test.  The test never finishes.

It says testing pipeline... testing - click Ok to finish.  No status or confirmation of the test.  The sound still doesnt work. 

I left the computer on overnight with the test.  After ten hours the test is still going on... ???

still no sound

gstreamer-properties
> 

(gstreamer-properties:17692): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:17692): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
gstreamer-properties-Message: Skipping unavailable plugin 'artsdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'esdsink'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosink'
gstreamer-properties-Message: Skipping unavailable plugin 'glimagesink'
gstreamer-properties-Message: Skipping unavailable plugin 'sdlvideosink'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lmjpegsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'qcamsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'v4lsrc'
gstreamer-properties-Message: Skipping unavailable plugin 'esdmon'
gstreamer-properties-Message: Skipping unavailable plugin 'sunaudiosrc'


---

### Post by nsync on 2013-05-11
wait, i think reinstalling or repairing might help.

---

### Post by 007casper on 2013-05-12
I tried to reinstall so many times. It just didnt work.  Unless, I am doing it wrong. I think I need to back up and reinstall the OS.

---

### Post by Archit88 on 2013-05-12
> **007casper said:**
> seriously - anybody ???

There is no way to fix this besides reloading the whole OS

this sounds funny but when u log in see on left hand side that your audio is muted. happened with me few days ago  ..

---

### Post by catraeus on 2013-06-29
How 'bout some basics ...

```

00:1b.0 Audio device: Intel Corporation 82801JD/DO (ICH10 Family) HD Audio Controller (rev 02)
02:00.1 Audio device: NVIDIA Corporation High Definition Audio Controller (rev a1)

```

shows two devices.  The Intel controller is a motherboard digital audio port that shows up just from the chipset and the NVIDIA is a built-in that comes along for the ride in most video controller.  The Intel is your actual player, so if you can configure with the GUI sound controller, then definitely choose the Intel.

Next, try aplay -l to see what ALSA believes is your sound environment.  Pulse is a server that rides on top of ALSA.  you might have to do ```
sudo apt-get install alsa-base alsa-utils
```

---

### Post by napzilla2 on 2013-12-03
I'm not sure why or how this worked, but I had the same problem in 12.04 and 13.10, and removing the following filed worked (I moved it to a temporary folder rather than deleting it, just in case):
<code>sudo mv /opt/majesty-gold/lib/lib1/libvorbis.so.0 temp/</code>

---


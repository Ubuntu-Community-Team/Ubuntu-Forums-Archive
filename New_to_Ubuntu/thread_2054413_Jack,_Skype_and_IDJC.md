---
title: "Jack, Skype and IDJC"
date: 2012-09-07
forum: New to Ubuntu
---

### Post by fractalman on 2012-09-07
I'm trying to set up jack so i can have the audio from skype go through IDJC and then out to the internet but i'm struggling to configure everything, i have spent the last 3 days googling, reading guides but nothing seems to be working, i'm finding the whole thing confusing and it's giving me a headache so if anyone can guide me through then it would much appreciated.

I have tried the guides on the IDJC homepage

I am using ubuntu 11.04 natty (32bit) i have 2.5g ram @3200hz with the motherboard audio

```

phi@BLACK47:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
phi@BLACK47:~$ arecord -l
**** List of CAPTURE Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 2: ALC888 Analog [ALC888 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


```

i have edited limits.conf and added the line

```

@audio          -       rtprio          99

```

I have tried creating a file named  *~/.asoundrc *in my home directory and put the following in it

```

# VoIP plugin for the IDJC default profile. pcm.idjcvoip {    type plug    slave.pcm {       type jack       playback_ports {          0 idjc_default:voip_in_l          1 idjc_default:voip_in_r       }       capture_ports {          0 idjc_default:voip_out_l          1 idjc_default:voip_out_r       }    } }  

```

i have also tried editing the alsa.conf file as well

jackd -d alsa gives the following output when i try and start jack

```

phi@BLACK47:~$ jackd -d alsa
jackdmp 1.9.7
Copyright 2001-2005 Paul Davis and others.
Copyright 2004-2010 Grame.
jackdmp comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
Cannot create thread 1 Operation not permitted
Cannot create thread 1 Operation not permitted
JACK server starting in realtime mode with priority 10
Cannot lock down memory area (Cannot allocate memory)
control device hw:0
control device hw:0
audio_reservation_init
Acquire audio card Audio0
creating alsa driver ... hw:0|hw:0|1024|2|48000|0|0|nomon|swmeter|-|32bit
control device hw:0
Using ALSA driver HDA-Intel running on card 0 - HDA NVidia at 0xfe028000 irq 23
configuring for 48000Hz, period = 1024 frames (21.3 ms), buffer = 2 periods
ALSA: final selected sample format for capture: 32bit integer little-endian
ALSA: use 2 periods for capture
ALSA: final selected sample format for playback: 32bit integer little-endian
ALSA: use 2 periods for playback
Cannot use real-time scheduling (RR/10)(1: Operation not permitted)
AcquireSelfRealTime error


```

if i start IDJC first then jack starts ok,  

when i open the settings tab on Jackqt  the interface option is greyed out and i cannot select hw:0

i have tried installing packages to play pulseaudio through jack but nothing seems to be working, none of the jack sinks are showing up anywhere,  when i open skype and look at the audio devices, the only option is pulse audio

i really would appreciate some help getting this going

---

### Post by fractalman on 2012-09-07
I have managed to get skype to show idjcvoip in the sound devices section, but when i click the button in IDJC to bring in voip all i am getting is a load of hissing,  skype is now giving me about 30 devices to choose from but none of them seem to be connecting properly with jack or IDJC



i have also been using ubuntu studio to try stuff out before breaking my main install of 11:04,  when i select idjcvoip in the skype sound devices selection  the whole pc starts really lagging and i have to kill skype with the system monitor, which also keeps not responding,  if i choose any other sound device like alsa_input or jack_capture1  then everything still works fine but i still get no sound through IDJC

these are all the connections i have in qjackctl in natty but when i looked in studio there were 8 more system devices on the left  - see attachment

---

### Post by fractalman on 2012-09-08
Bump!


I have been trying everything i have found online but still no joy,

if i select jack or alsa devices in skype then all i get is skype saying playback problem, if i try voipidjc as the idjc homepage suggests then my system freezes and i have to kill skype before i can do anything

the jack sinks are showing in the connection manager for jack with pulseaudio but again all i get is playback problem from skype,


does anyone know how to get skype audio through idjc?


 i was thinking about trying it this way but it would mean having to install a later distro
and i really don't want to have to fiddle with unity just so i can use claudia and gladish

[http://www.penguinproducer.com/2012/01/streaming-podcast-with-skype-workflow/](http://www.penguinproducer.com/2012/01/streaming-podcast-with-skype-workflow/)

---

### Post by StephenF on 2012-09-09
The guides on the IDJC homepage are for the latest version of IDJC.

What you want is the source code for the _version you are using_ from sourceforge.net then point your web browser at doc/index.html. There you will find the correct .asoundrc for your particular version.

---

### Post by fractalman on 2012-09-09
Thank you, i shall try that for natty but yesterday i installed a copy of ubuntu studio 12:04 and the instructions on the idjc homepage do not work for that either,  so i have posted in the studio forums about that as well

---

### Post by fractalman on 2012-09-09
Well the idjc packages on sourceforge are not marked according to distro releases, so i tried the one that was modified 2011-04-06  as i am using natty (11:04)

```

phi@BLACK47:~$ cd idjc-0.8.5
phi@BLACK47:~/idjc-0.8.5$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for a Python interpreter with version >= 2.6... python
checking for python... /usr/bin/python
checking for python version... 2.7
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.7/dist-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.7/dist-packages
checking for style of include used by make... GNU
checking for gcc... gcc
checking whether the C compiler works... yes
checking for C compiler default output file name... a.out
checking for suffix of executables... 
checking whether we are cross compiling... no
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking dependency style of gcc... gcc3
checking whether gcc and cc understand -c and -o together... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for LIBJACK... no
configure: error: Package requirements (jack >= 0.98.0) were not met:

No package 'jack' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables LIBJACK_CFLAGS
and LIBJACK_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
phi@BLACK47:~/idjc-0.8.5$ make
make: *** No targets specified and no makefile found. Stop.
phi@BLACK47:~/idjc-0.8.5$ 


```> 
Package requirements (jack >= 0.98.0) were not met:


i cannot find this package, i have checked sourceforge, all other websites with references to this package are from 2004.

  i have jack, jack2,jackqctl and a few others already installed

---


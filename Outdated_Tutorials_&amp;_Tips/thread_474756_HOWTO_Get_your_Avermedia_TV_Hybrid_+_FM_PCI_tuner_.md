---
title: "HOWTO: Get your Avermedia TV Hybrid + FM PCI tuner to work"
date: 2007-06-15
forum: Outdated Tutorials &amp; Tips
---

### Post by Gruelius on 2007-06-15
Hey all,
Feisty's kernel comes with the correct bits and pieces, you just need to tell it what type of card it is.

One friend told me that his worked automatically so to make sure you need to fiddle around type in "dmesg | grep saa" and if you see this you need to do the following steps
```
[   39.847928] saa7130/34: v4l2 driver version 0.2.14 loaded
[   39.848432] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 21, latency: 32, mmio: 0xe8002000
[   39.848437] saa7133[0]: subsystem: 1461:2c00, board: UNKNOWN/GENERIC [card=0,autodetected]

```
If you see this then why are you looking at this guide!
```
[  555.864000] saa7130/34: v4l2 driver version 0.2.14 loaded
[  555.864000] saa7133[0]: found at 0000:01:05.0, rev: 209, irq: 21, latency: 32, mmio: 0xe8002000
[  555.864000] saa7133[0]: subsystem: 1461:2c00, board: AVerMedia TV Hybrid A16AR [card=99,insmod option]
```

[SIZE="4"]**Getting it to work**[/SIZE]

To make sure you have a A16AR type in "lspci -v" and you should see:
```
01:05.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device 2c00
        Flags: bus master, medium devsel, latency 32, IRQ 21
        Memory at e8002000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>
```

Then type ```
Sudo rmmod saa7134_alsa saa7134-dvb saa7134
```. If you cant close them type in ```
fuser -v /dev/snd/* /dev/dsp/*
``` and then ```
killall -9 <process names>
```

Now you need to load the correct modules
```
modprobe saa7134 card=99
modprobe saa7134_alsa
modprobe saa7134-dvb
```


If this all works for you tell ubuntu to automatically use the new options for saa7134
```
Cd /etc/modprobe.d/
sudo echo "options saa7134 card=99" >> options
```

---

### Post by Gruelius on 2007-06-18
To make sure that it works after boot up type these commands
```
Cd /etc/modprobe.d/
sudo echo "options saa7134 card=99" >> options
```

---

### Post by Enverex on 2007-06-18
Argh damnit. Saw this thread and finally thought my Tuner was going to work, didn't notice the PCI in the title though. FYI the USB one is still a brick.

---

### Post by fivosz on 2008-03-05
Well it's been a while but i 'll try to open this discussion again ;)

My system recognise's the card correctly and everything seems fine...
I 'm using tvtime but i've the same problems with other TV-apps

[SIZE="4"]The problem[/SIZE]

I can see picture(no sound) by adjusting the input to composite, but the source from which comes the freq that i 'm watching is an air antenna :S. When i adjust the input to television(the source i should be using, so i could change through channels and have sound) i simply get a blue screen.
any ideas?

also my "lspci -v" returns this

> 02:07.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
        Subsystem: Avermedia Technologies Inc Unknown device 2c00
        Flags: bus master, medium devsel, latency 64, IRQ 19
        Memory at feaef800 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

note the latency and IRQ...

please help i'm trying to make it over a year now and it's the only reason i 'm keeping XP on my desktop :(

---


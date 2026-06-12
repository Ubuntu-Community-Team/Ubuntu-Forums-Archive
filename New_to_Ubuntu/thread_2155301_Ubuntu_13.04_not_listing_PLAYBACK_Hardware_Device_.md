---
title: "Ubuntu 13.04 not listing PLAYBACK Hardware Device - no sound"
date: 2013-06-17
forum: New to Ubuntu
---

### Post by HavingFun on 2013-06-17
I have an Emachines (PC) T5010.  Upgraded  to 13.04 and lost sound.  I completed all steps of the Ubuntu sound  troubleshooting guide here:  [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

One thing that stood out:  When executing this tip


sudo aplay -l
I think the output of that command should look something like this: 

**** List of PLAYBACK Hardware Devices **** card 0: Intel [HDA Intel],  device 0: ALC861VD Analog [ALC861VD Analog]   Subdevices: 0/1    Subdevice #0: subdevice #0

I only received this:
**** List of PLAYBACK Hardware Devices ****


Didn't list the card.  But when I execute this:  lspci -v | grep -A7 -i "audio", 

I do get -

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
    Subsystem: Gateway, Inc. Device 4040
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at b01c0000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6  Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])

I'm new with ubuntu and any help would be very much appreciated!!!

---

### Post by zero2xiii on 2013-06-18
Hay,

Please start here:[http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446](http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446)
[URL="http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446The"]
[/URL]The very first thing you should do is format your posts correctly.

Then there is a heading for sound debugging, please see that link for more detail and supply us more information.
Some useful output would include a list of the computer hardware, the current operating system, kernel and architecture, along with some other data you will get from that link.

That threat is made by me to help people learn how to format posts correctly and supply some of the basic information we need to assist you.

Cheers and thank you

---

### Post by HavingFun on 2013-06-27
> **zero2xiii said:**
> Hay,
[URL="http://ubuntuforums.org/showthread.php?t=2140012&p=12623446#post12623446The"]
[/URL]The very first thing you should do is format your posts correctly.



Thanks for the heads up.  

Ubuntu is not listing the sound card.  

aplay -l

```
**** List of PLAYBACK Hardware Devices ****
```

Some system info:

uname -a
```
Linux emachine-desktop 3.8.0-25-generic #37-Ubuntu SMP Thu Jun 6 20:47:30 UTC 2013 i686 i686 i686 GNU/Linux
```


lsb_release -a
```
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring
```



ps -ef | grep pulseaudio
```
emachine  3149     1  0 08:16 ?        00:00:00 /usr/bin/pulseaudio --start --log-target=syslog
emachine  3193  3043  0 08:21 pts/1    00:00:00 grep --color=auto pulseaudio

```

In this case, 3149 process is pulse audio and is taking Very High Priority
3043 process is bash.  

I'm assuming the "?" means I have a Pulseaudio problem?  But I haven't been able to get further.  Any help appreciated.

---


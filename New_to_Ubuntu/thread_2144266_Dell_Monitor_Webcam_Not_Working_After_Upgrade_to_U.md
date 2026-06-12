---
title: "Dell Monitor Webcam Not Working After Upgrade to Ubuntu 13.04"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by nicraz on 2013-05-11
Hi guys, 

A few days ago I decided to upgrade to Raring Tail once I was prompted to do so on my computer. I noticed I'm having a few issues, first HDMI audio wasn't working but I was able to fix it. The second issue that I can't seem to fix permanently is for the integrated webcam on my Dell SX2210B 21.5" monitor to work properly. The thing is that it's off and on. I tried installing the PPA for libv4l v4l-utils and it seemed to work but after fixing the HDMI issue today the webcam isn't working at all. 

The webcam is not detected by Skype, Cheese or [http://www.testwebcam.com/](http://www.testwebcam.com/). I also tried [this]("http://ubuntuforums.org/archive/index.php/t-1703909.html") but I get this error *'video for linux 2 (v4l2) cannot identify device '/dev/video0'*

I'm including this info in case it's helpful:

```
lsusb

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 046d:c52e Logitech, Inc. 
Bus 002 Device 003: ID 0424:2512 Standard Microsystems Corp. USB 2.0 Hub
Bus 002 Device 004: ID 05e3:0729 Genesys Logic, Inc. 
Bus 002 Device 005: ID 05a9:264b OmniVision Technologies, Inc. Monitor Webcam
Bus 002 Device 006: ID 0424:2514 Standard Microsystems Corp. USB 2.0 Hub
```


```
lsmod | grep video

uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
videobuf2_core         39161  1 uvcvideo
videodev               95806  2 uvcvideo,videobuf2_core
video                  18894  1 i915
```

**Processor**: Intel® Core&#8482; i5-2320 CPU @ 3.00GHz × 4 
**Graphics**: Intel® Sandybridge Desktop x86/MMX/SSE2

Thank you in advance.

EDIT to Add: I upgraded from Ubuntu 12.10 to 13.04.

---

### Post by nicraz on 2013-05-13
Anybody? :(

---

### Post by sloan31 on 2013-05-15
I'm having the same exact issue...I'll report back here if I find anything out.

EDIT:
I just found this bug report Bug #1168430
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1168430](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1168430)

Looks like that patch only fixed it for a specific model of webcam so I submitted another bug report for my model...Bug #1180409

---

### Post by nicraz on 2013-05-19
Thanks sloan31! I had forgotten about the issue and I know the system prompted me to update a few days ago. I checked today and it seems to be working. I'm not sure if it's going to be an on and off issue. I'll have to test every day for the next few days. I also removed Everpad yesterday because it kept on crashing. Not sure if that would have any effect on the webcam.

---

### Post by nicraz on 2013-05-20
Update: No, it's not entirely fixed. The problem comes and goes. One day it works, another day it doesn't and I don't know what's the cause of the issue :(

---

### Post by sloan31 on 2013-05-20
Do you have the exact same model number I have?
ID 05a9:2643 OmniVision Technologies, Inc. Monitor Webcam

If not, you need to file a bug report for your model number.  If you do have the same one, the patch has been sent upstream but not available yet via kernel update.

In the meantime, you can resolve this by specifying a quirk to the module like this.
sudo modprobe -r uvcvideo
sudo modprobe uvcvideo quirks=64

If 64 doesn't work for you, try 16 or 32. In ubuntu 13.04, quirks=64 worked for me...but in Mint 15 quirks=16 is what worked.

---

### Post by giuliocoluccia on 2013-05-21
Hi,
try with this
[http://ubuntuforums.org/showthread.php?t=2145996](http://ubuntuforums.org/showthread.php?t=2145996)

---

### Post by sloan31 on 2013-05-21
> **giuliocoluccia said:**
> Hi,
try with this
[http://ubuntuforums.org/showthread.php?t=2145996](http://ubuntuforums.org/showthread.php?t=2145996)

You had to go all the way to quirks=256 for it to work? Or had you not tried other numbers?

---

### Post by giuliocoluccia on 2013-05-21
No, I knew what value to use. In fact, if you look at the output of dmesg, there was a failure (the GET_DEF(PROBE) stuff) in a check. And looking at the uvcvideo FAQ, [http://www.ideasonboard.org/uvc/faq/](http://www.ideasonboard.org/uvc/faq/) scroll down a little bit, you can see that 0x100 is the value of quirks to avoid that check.

---

### Post by sloan31 on 2013-05-21
> **giuliocoluccia said:**
> No, I knew what value to use. In fact, if you look at the output of dmesg, there was a failure (the GET_DEF(PROBE) stuff) in a check. And looking at the uvcvideo FAQ, [http://www.ideasonboard.org/uvc/faq/](http://www.ideasonboard.org/uvc/faq/) scroll down a little bit, you can see that 0x100 is the value of quirks to avoid that check.

Cool, thanks.  I had to use one value with ubuntu and a different one with mint...now i can just use 256 for both.

---


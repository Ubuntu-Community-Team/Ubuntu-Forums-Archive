---
title: "UB445-U and cx231xx not working"
date: 2013-11-24
forum: New to Ubuntu
---

### Post by bigwolf227 on 2013-11-24
Hello, 

I just installed Kubuntu 13.10 and upgraded the kernel to 3.12.1 because I read that this kernel supports the KWorld UB445-U usb tv tuner. I have searched Google and other forums for answers, but I have come up with nothing. 
I have several questions that I hope someone can help me with. 

Right now, I have to manually type, sudo modprobe cx231xx, to get the the drivers loaded.
lsmod reports that the drivers are loaded:
cx231xx               167216  0 
videobuf_vmalloc       13560  1 cx231xx
cx2341x                28230  1 cx231xx
rc_core                28084  1 cx231xx


v4l2_common            15652  2 cx2341x,cx231xx
videobuf_core          25993  2 cx231xx,videobuf_vmalloc
videodev              134044  3 cx2341x,cx231xx,v4l2_common

How do I get the kernel to load the cx231xx drivers when the system boots?

Here's what dmesg reports about my tv tuner:
[    1.387596] usb 1-1: New USB device found, idVendor=1b80, idProduct=e43f
[    1.387597] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.387599] usb 1-1: Product: Polaris AV Capture
[    1.387600] usb 1-1: Manufacturer: Conexant Corporation
[    1.387601] usb 1-1: SerialNumber: 0000000000

What does that mean and how do I access the Polaris AV Capture card?

/dev doesn't show that there is a video0 device on my system.
How do I set up linux to open the video0 device so I can watch tv?

I read something in a post that intrigued me, but I haven't been able to find any more details. Basically, the post was about there bieng a cx231xx.conf file in /etc/modprobe.d directory. What is the format for this file? Is there a template somewhere that I can copy for use in this file?

Thank you all for your support. 

Tim
:confused:

---

### Post by sandyd on 2013-11-24
> **bigwolf227 said:**
> Hello, 

I just installed Kubuntu 13.10 and upgraded the kernel to 3.12.1 because I read that this kernel supports the KWorld UB445-U usb tv tuner. I have searched Google and other forums for answers, but I have come up with nothing. 
I have several questions that I hope someone can help me with. 

Right now, I have to manually type, sudo modprobe cx231xx, to get the the drivers loaded.
lsmod reports that the drivers are loaded:
cx231xx               167216  0 
videobuf_vmalloc       13560  1 cx231xx
cx2341x                28230  1 cx231xx
rc_core                28084  1 cx231xx
v4l2_common            15652  2 cx2341x,cx231xx
videobuf_core          25993  2 cx231xx,videobuf_vmalloc
videodev              134044  3 cx2341x,cx231xx,v4l2_common

How do I get the kernel to load the cx231xx drivers when the system boots?

Here's what dmesg reports about my tv tuner:
[    1.387596] usb 1-1: New USB device found, idVendor=1b80, idProduct=e43f
[    1.387597] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.387599] usb 1-1: Product: Polaris AV Capture
[    1.387600] usb 1-1: Manufacturer: Conexant Corporation
[    1.387601] usb 1-1: SerialNumber: 0000000000

What does that mean and how do I access the Polaris AV Capture card?

/dev doesn't show that there is a video0 device on my system.
How do I set up linux to open the video0 device so I can watch tv?

Thank you all for your support. 

Tim
:confused:

**Add the module to /etc/modules, which will load on bootup**
```

sudo sh -c 'echo "cx231xx" >> /etc/modules'
```

**Update Initramfs**
```

sudo update-initramfs -u
```

---

### Post by bigwolf227 on 2013-11-24
Thank you, sandyd. The drivers loaded when I rebooted linux! 
:p

---


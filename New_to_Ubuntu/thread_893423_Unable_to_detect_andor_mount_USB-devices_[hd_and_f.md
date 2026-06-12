---
title: "Unable to detect and/or mount USB-devices [hd and flash memory]"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by undread on 2008-08-18
I would need help with the problem mentioned in the title.

When I connect the USB-devices (in this case a Kingston USB-flash memory and two external hard rives [LaCie and Buffalo]) nothing happens. Before I have been able to use them successfully with the same laptop and (propably) same version of Ubuntu. After not having used the machine for a while, now I cannot even find the devices with any commands I know of so that I could mount them manually. All still work with other computers /OS (with Windows XP). I have not tried them out with another machine with Ubuntu, but I suspect the problem lies with my OS or hardware. The laptop has also hardware problems (an almost completely defunct graphics card), but I do not see how it would relate to my problems with the USB-devices or ports.

My questions are:

1. How can I check if the devices actually show up as I have not been able to locate them? If I manage to find the devices it should be easy to manually mount them.

2. If they do not show up is there a way to locate the problem? [e.g. if there is a problem with the USB-ports...]

Thank you in advance, whomever is able to help me, if not to solve then at least to understand the problem.

---

### Post by dustman on 2008-08-18
maybe this'll help ;) : [http://ubuntuforums.org/showthread.php?t=669338](http://ubuntuforums.org/showthread.php?t=669338)

---

### Post by undread on 2008-08-18
Well the thread was so confused it was hard to follow, but at least it did not solve for me the problem of locating the devices. When typing the dmesg command for example I get an endless list that looks like this

```
[ 6202.995110] gspca: probe of 5-8:1.0 failed with error -5
[ 6202.995251] usb 5-8: USB disconnect, address 108
[ 6203.122465] usb 5-8: new high speed USB device using ehci_hcd and address 109
[ 6203.278441] usb 5-8: configuration #1 chosen from 1 choice
[ 6203.278975] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[ 6203.500734] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[ 6203.500762] gspca: probe of 5-8:1.0 failed with error -5
[ 6203.500901] usb 5-8: USB disconnect, address 109
[ 6203.638315] usb 5-8: new high speed USB device using ehci_hcd and address 110
[ 6203.794358] usb 5-8: configuration #1 chosen from 1 choice
[ 6203.795202] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[ 6204.015679] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[ 6204.015725] gspca: probe of 5-8:1.0 failed with error -5
[ 6204.015959] usb 5-8: USB disconnect, address 110
[ 6204.146444] usb 5-8: new high speed USB device using ehci_hcd and address 111
[ 6204.302562] usb 5-8: configuration #1 chosen from 1 choice
[ 6204.303058] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[ 6204.524865] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[ 6204.524909] gspca: probe of 5-8:1.0 failed with error -5
[ 6204.525139] usb 5-8: USB disconnect, address 111
[ 6204.679342] usb 5-8: new high speed USB device using ehci_hcd and address 112
```

Is there a way to read the dmesg -output a screen at a time, because the part of the output shown above repeats itself so often that the beginning is no longer shown in the console?

---

### Post by dustman on 2008-08-18
that thread was confusing to me also :) with all those bumps...i don't know how to get dmesg to output just a screen of messages at a time, but you could try "dmesg | tail" to see just the end of it (which is practically useless since you want to see the beginning of the messages :lolflag: ). A solution would be to redirect the output of dmesg to a text file:
```
dmesg >> log.txt
``` then just open the file with a text editor.

 In the thread i told you about, the name of the device was pretty clearly stated, so i just guessed it :D. You seem to have somekind of error message. When i'll get home, i'll give it a little more time and try to get to the bottom of this.

Best regards!

Radu

---

### Post by undread on 2008-08-18
Thanks for the quick replies and the efforts. Even when using dmesg to create a log file the endless error message gets repeated so often that the log actually does not contain the beginning, but only the same error over and over. 

The log begins in the middle with the same thing I posted above.

```
inux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[ 7818.426283] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[ 7818.426322] gspca: probe of 5-8:1.0 failed with error -5
[ 7818.426467] usb 5-8: USB disconnect, address 78
[ 7818.576893] usb 5-8: new high speed USB device using ehci_hcd and address 79
[ 7818.732928] usb 5-8: configuration #1 chosen from 1 choice
[ 7818.733461] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: USB GSPCA camera found.(VC0321) 
[ 7818.954195] /build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c: Failed to configure camera
[ 7818.954225] gspca: probe of 5-8:1.0 failed with error -5
[ 7818.954362] usb 5-8: USB disconnect, address 79
```

I guess what I'd need is the opposite of |tail to see the interesting bit. I don't know much of the inner workings of Ubuntu, but it seems problematic that the dmesg-log can be "flooded" so that it does not show all relevant information. I hope there is a way around that.

I also tried using lsusb in the console. It results in no output at all. I don't know if I'm using the command in a wrong way, or there are more problems than I hoped for.

---

### Post by dustman on 2008-08-18
if you write : "dmesg >> log.txt" it's impossible not to have the first messages. After you've first created the file, you can just append data to it, but using : "dmesg > log.txt" (so, not >>, but >). 

As i see it, there might be a bug with the "/build/buildd/linux-ubuntu-modules-2.6.24-2.6.24/debian/build/build-generic/media/gspcav1/gspca_core.c" file. Are you using a "home brewed" kernel? I mean, did you compile your kernel yourself of just used the kernel ubuntu came with (fresh install/update)?

---

### Post by undread on 2008-08-18
It is the kernel from the normal update.

Using (to create a fresh log I changed its name too...)
```
dmesg >> dmesglog.txt
```

produces a log file that does not contain the initial lines. What I notice though is that numbers run all the time higher.

```

[ 9342.882505] gspca: probe of 5-8:1.0 failed with error -5
[ 9342.882723] usb 5-8: USB disconnect, address 7
```

compared to

```
[ 6202.995110] gspca: probe of 5-8:1.0 failed with error -5
[ 6202.995251] usb 5-8: USB disconnect, address 108

```

from the first part I posted.

Besides the point: should not using the **lsusb** command in the console produce some kind of output? (cf. my earlier post)

---

### Post by decoherence on 2008-08-18
with the drive unplugged, open a terminal and type

sudo udevmonitor > output.txt

now plug the drive in and give udev a few seconds to try and work things out. when it stops spitting out information (or is obviously in a loop-of-death) press Ctrl C. Now copy/paste the contents of the file output.txt, which should be in your home folder, to this thread.

---

### Post by undread on 2008-08-18
the command **sudo udevmonitor > output.txt** results in ```
bind failed: Address already in use
```

as it does when changing the name of the log file or just using **sudo udevmonitor**

---

### Post by dustman on 2008-08-18
did you unplug your device? as stated in decoherence's post...

---

### Post by undread on 2008-08-18
Yes I did. Plugged or unplugged it always gives the 'bind failed' message.

---

### Post by undread on 2008-08-18
The error message was obviously related to a webcam problem. 

[http://ubuntuforums.org/showthread.php?t=322218&page=5]("http://ubuntuforums.org/showthread.php?t=322218&page=5")
[http://backports.ubuntuforums.com/showthread.php?t=121125&page=103]("http://backports.ubuntuforums.com/showthread.php?t=121125&page=103")

I blacklisted gpsca and rebooted. Now the message has disappeared (**dmesg** works as does **lsusb**). The computer also automounts the USB-devices. 

Problem solved for now, but it is interesting to note that in my case a failure with the webcam (it worked before) or its driver causes an infinite loop that floods the log, slows down booting and prevents the use of the USB devices. Maybe there is a fix to that too, but I rather have my hard drives than the webcam working

Thanks for the help anyway.

---


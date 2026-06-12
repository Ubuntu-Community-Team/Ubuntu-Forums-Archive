---
title: "USB hub ignored"
date: 2013-02-05
forum: New to Ubuntu
---

### Post by Paper Pusher on 2013-02-05
I have a desktop PC running Ubuntu 12.4-64 lts dte. All patches are up to date. Because I have so many USB peripherials I am using a USB hub. 

Yesterday a new problem arose. My system has started to not recognize the hub. It insists on having me plug in my USB pheripherials directly. 

What is going on? The hub used to work just fine. I have tried three different USB hubs, two powered and one non powered. They all exhibit the same symptom.

---

### Post by Paper Pusher on 2013-02-05
I have tried using a USB hub on 4 different desktop computers running Ubuntu and have faced a problem.

Three computers (2 are 64-bit, 1 is 32-bit) with recent updates from Ubuntu Software Center did not recorgnize the USB hub. One computer that has not been updated in a few months recognized the USB hub and allowed it to work. I have tested each USB port on the computers and they seem to be working fine. Only when I plug the USB hub into any one of the USB ports, the hub is unable to connect.

At this point I do not know which software update is preventing the computer from recognizing the USB hub, but I would like to know if there is any way to fix this problem.

Does anyone know of solution to this problem?

---

### Post by |{urse on 2013-02-05
What model and manufacture is it?

---

### Post by Paper Pusher on 2013-02-05
> **|{urse said:**
> What model and manufacture is it?

I have 3 USB hubs. 

1. Rosewill 7 port hubs (powered)
2. Rosewill RHB 330 - 7 port hubs (powered)
3. A squid type with 7 port hubs (powered)

I have tested 4 computers. They all have Ubuntu 12.4 Desktop Edition installed. 

Three did not recognize the USB hub. They were all up to date from the Update Manager:
1. HP AMD Athlon Dual Core 4850e- 64-bit
2. Homebuilt Micro with ITX Foxcon Motherboard- Dual Core Atom - 32-bit
3. Homebuilt ATX Desktop AMD Dual Core- 64-bit

One computer that worked WAS NOT up to date from the Update Manager.
1. HP Paviliion 700- Single Core- 64-bit

---

### Post by DuckHook on 2013-02-05
It is possible that an update broke a driver/module/kernel parameter that allowed older versions to see hubs but not newer versions. This happens more often than anyone likes. If so, you can and should file a bug report so that the developers can be made aware of it. It would be interesting to see what the differences are between new and old installs. If you have the time and the inclination, try the following commands on both your new and old OSes with different hubs being plugged in:

```
lsusb
```Then do:

```
dmesg | tail
```...immediately after plugging in to both a working and nonworking OS to see what respective kernel messages are being generated. Include these in your bug report.

As for solving your immediate problem, you may wish to ask one of the forums admins to move your thread to hardware, where they have more experience with this sort of thing.

---

### Post by Paper Pusher on 2013-02-05
I'm not sure what all this measn but I did what you asked me to do.  How do I file a bug against Ubuntu?

Below is no USB hub installed.

~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. Serial-ATA bridge
Bus 001 Device 007: ID 046d:082d Logitech, Inc. 
Bus 001 Device 008: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 047d:1020 Kensington Expert Mouse Trackball
Bus 002 Device 003: ID 0763:201d Midiman M-Audio Producer
Bus 002 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 010: ID 045e:075c Microsoft Corp. 
axel@axel-NC890AA-ABA-a6803w:~$ dmesg | tail
[27926.224060] usb 2-5: device descriptor read/64, error -62
[27926.512058] usb 2-5: device descriptor read/64, error -62
[27926.792064] usb 2-5: new full-speed USB device number 8 using ohci_hcd
[27927.200035] usb 2-5: device not accepting address 8, error -62
[27927.376064] usb 2-5: new full-speed USB device number 9 using ohci_hcd
[27927.784045] usb 2-5: device not accepting address 9, error -62
[27927.784082] hub 2-0:1.0: unable to enumerate USB device on port 5
[27974.188065] usb 2-5: new full-speed USB device number 10 using ohci_hcd
[27974.491922] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 X3 Mouse as /devices/pci0000:00/0000:00:02.0/usb2/2-5/2-5:1.0/input/input16
[27974.492448] generic-usb 0003:045E:075C.0005: input,hidraw3: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae SideWinder\xffffffe2\xffffff84\xffffffa2\xffffff84\xffffffa2 X3 Mouse] on usb-0000:00:02.0-5/input0

---

### Post by Paper Pusher on 2013-02-05
Below is a USB hub installed on a computer that is up to date and does not recognize the hub.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 1bcf:0c31 Sunplus Innovation Technology Inc. Serial-ATA bridge
Bus 001 Device 014: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 015: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 008: ID 0bda:0151 Realtek Semiconductor Corp. Mass Storage Device (Multicard Reader)
Bus 002 Device 002: ID 047d:1020 Kensington Expert Mouse Trackball
Bus 002 Device 003: ID 0763:201d Midiman M-Audio Producer
Bus 002 Device 004: ID 04d9:1603 Holtek Semiconductor, Inc. Keyboard
Bus 002 Device 010: ID 045e:075c Microsoft Corp. 
Bus 001 Device 016: ID 046d:082d Logitech, Inc. 
axel@axel-NC890AA-ABA-a6803w:~$ dmesg | tail
[44071.429188] usb 1-6.4.1: USB disconnect, device number 16
[44071.704061] usb 1-6: new high-speed USB device number 17 using ehci_hcd
[44071.842973] hub 1-6:1.0: USB hub found
[44071.844498] hub 1-6:1.0: 4 ports detected
[44072.116381] usb 1-6.4: new high-speed USB device number 18 using ehci_hcd
[44072.210067] hub 1-6.4:1.0: USB hub found
[44072.210368] hub 1-6.4:1.0: 4 ports detected
[44072.480387] usb 1-6.4.1: new high-speed USB device number 19 using ehci_hcd
[44072.575527] uvcvideo: Found UVC 1.00 device HD Pro Webcam C920 (046d:082d)
[44072.580257] input: HD Pro Webcam C920 as /devices/pci0000:00/0000:00:02.1/usb1/1-6/1-6.4/1-6.4.1/1-6.4.1:1.0/input/input19

---

### Post by Paper Pusher on 2013-02-05
This is a computer that does recognize USB hubs.  Below is no USB hub installed.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e6:0325 SCM Microsystems, Inc. eUSB ORCA Quad Reader
firstpres@First-Pres-Desktop:~$ dmesg | tail
[   27.354711] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  173.14.35  Fri Jun  8 00:07:59 PDT 2012
[   27.601043] init: plymouth-upstart-bridge main process (791) killed by TERM signal
[   27.766011] vesafb: mode is 2048x1536x32, linelength=8192, pages=0
[   27.766015] vesafb: scrolling: redraw
[   27.766018] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[   27.768508] vesafb: framebuffer at 0xc0000000, mapped to 0xffffc90011300000, using 12288k, total 12288k
[   27.768942] Console: switching to colour frame buffer device 256x96
[   27.769005] fb0: VESA VGA frame buffer device
[   27.794152] init: plymouth-splash main process (1217) terminated with status 1
[   35.120028] eth0: no IPv6 routers present

---

### Post by Paper Pusher on 2013-02-05
This is a computer that does recognize USB hubs.  Below is with a USB hub installed.

lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 04e6:0325 SCM Microsystems, Inc. eUSB ORCA Quad Reader
Bus 001 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 004: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
firstpres@First-Pres-Desktop:~$ dmesg | tail
[   27.768942] Console: switching to colour frame buffer device 256x96
[   27.769005] fb0: VESA VGA frame buffer device
[   27.794152] init: plymouth-splash main process (1217) terminated with status 1
[   35.120028] eth0: no IPv6 routers present
[  469.168020] usb 1-7: new high-speed USB device number 3 using ehci_hcd
[  469.301613] hub 1-7:1.0: USB hub found
[  469.301944] hub 1-7:1.0: 4 ports detected
[  469.572332] usb 1-7.4: new high-speed USB device number 4 using ehci_hcd
[  469.665807] hub 1-7.4:1.0: USB hub found
[  469.666075] hub 1-7.4:1.0: 4 ports detected

---

### Post by DuckHook on 2013-02-06
I don't want to mislead you. I'm not a hardware expert and don't know much about USB subsystems, but here is what I can make out. Ubuntu does see your hub even on your new installs. They are the 4th and 5th lines from lsusb: Genesys Logic 4-Port HUB. So, if your USB devices are not being recognized, it isn't because the OS doesn't see the HUB. To my knowledge, USB is not something that is driver dependent, but I'm not sure. dmesg also shows the hub being detected and further recognized an HD Pro Webcam. Did you plug that into the hub?

To report a bug, you need to register with [launchpad]("https://launchpad.net/") and then submit your report, which includes a detailed accounting of your experience as well as such output as you've already produced. The developers there may ask for further info, but will provide you with instructions for getting it.

It's after midnight here, so I won't be responding further till tomorrow. Given that it isn't a critical problem, hope you can wait or perhaps someone else will jump in.

---

### Post by DuckHook on 2013-02-06
After re-reading your posts with a fresh mind, it looks like your system is seeing your 7-port hubs as only 4-ports. This may be at least part of the problem. Now, the old OS does the same thing: "[ 469.301944] hub 1-7:1.0: 4 ports detected" but somehow is able to see your devices whereas the new OS does not.

Do all of your ports work? Have you tried plugging in your devices to different ports on the hubs? Did you plug into different ports when testing the old OS vs the new?

This doesn't solve the problem of why your system doesn't recognize 7 ports, but it might get some ports working.

It's hard to find references to your hub using google, but I found [this]("http://www.raspberrypi.org/phpBB3/viewtopic.php?f=46&t=12625"). It's a raspberry pi thread, but since the pi runs Linux, it should have some bearing. On this thread, the poster mentions that dmesg on his system shows the hub as a "Terminus Technology Inc. FE 2.1 7-port Hub". Since you don't know the chipset of your models, it's impossible to tell if this is dead accurate, but at least his hub is recognized as 7 ports. There also appear to be a number of different models from Rosewill which only muddies things further.

I don't know what else to tell you from here. As noted previously, the gurus inhabiting the HW forum may be better able to help. You can also tap Rosewill support on their own site, but since they specifically exclude Linux from supported OSes, you may not get too far with them.

---

### Post by Paper Pusher on 2013-02-06
Thank you, Duckhook for all your advice. 

Because the USB hub works on the computer that has not been updated but it fails on the computers that have been fully updated I think its a problem caused by an update. I tried to report a bug on Ubuntu but failed. It is simply too difficult to file a bug on Ubuntu. I hope that someone else is more knowledgeable and can file the bug. Prior posts in this thread show all information you identified is relavent.

Paper Pusher

---

### Post by DuckHook on 2013-02-06
> **Paper Pusher said:**
> ...I hope that someone else is more knowledgeable and can file the bug.

As I mentioned, bugs need to be filed in Launchpad, not Ubuntu. It's fine if you don't file the bug. However, no one else can either because we can't duplicate the problem, which is what the developers need if they are going to address it.

At this point, I would still suggest that you try the manufacturer. Although Linux is not technically supported, they may still be able to help you.

Good luck!

---

### Post by DuckHook on 2013-02-06
Have been doing some USB self-educating, going through some of the old threads and generally googling/wikipediaing. Here's what I've gathered (in a rough semi-educated way):

The USB subsystem is even more complex than I thought (and I was expecting high levels of complexity already). Some powered hubs are not as well-powered as they claim--it depends not only on the wattage of their power supply but the effectiveness of their internal power distribution. Many people have run into problems plugging high-draw devices into USB hubs. Even though the hub is supposedly powered, it does not provide sufficient power for the device in question. I have a joystick/throttle duo with all sorts of pretty LEDs that falls into this category. I burned out a lowly hub with this duo. Didn't fully understand before, but now I understand a little better why.

OSes actually query hubs to see if they can support a threshold level of service. If the OS judges the hub to be insufficiently powered or otherwise unreliable (I have no idea how this is done), then it won't use the connection. This is a safety feature designed to safeguard data. The last thing you want to be doing is writing data to an unreliable USB stick/drive, so this makes a certain sense. Different OSes have different query methods and different thresholds. Therefore, a USB hub may pass the test on one OS but not on another.

This might account for how your *lsusb* and *dmesg* queries returned recognition of a hub, but the OS nonetheless refused to connect. Also, either the hub is non-standard or there's a bug in the OS which prevents it from recognizing the hub as a 7-port. The old version of Ubuntu may have had a higher tolerance for non-optimal connection whereas the new version has low tolerance. This is all sheerest guess and golly but I've no better explanation that accounts for all the facts.

Irrespective of above, there are some valid conclusions that can be drawn. First of all, an unpowered 7-port hub is just bad news. Don't use it. The tiny little 500mA power supply coming from your computer's usb port is simply not sufficient to power a 7-port hub and the OS is doing you a favour not allowing you to use it. Even if you somehow get it recognized, you risk data loss and corrupted files trying to transfer anything from or to it. Your two powered hubs come from the same manufacturer. Others have had problems with this brand of hub, but I don't know if that means anything because someone or other will have had problems with every piece of equipment ever manufactured. I have no idea what the specs are on your hubs but you should check the rating of the power supply. Since the USB standard is 500mA per port, seven ports equals 3.5 Amps plus overhead to run the hub. If your power supply is not around 4 Amps at 5 volts, or another combination that equals 20 watts, then your hub is underpowered and you may run into problems irrespective of what OS you are using.

You can try a different hub or a different OS. Don't know if the other flavours of 'buntu will behave differently. You might also want to try base Debian, Fedora, Gentoo or Slackware. The number of alternate Linux distros must number into the dozens, but the nice thing about Linux is you can download everything and try it out at leisure and at absolutely no cash outlay.

I know that your problem still remains, but I appreciated the opportunity to have learned more about USB. Good luck!

---

### Post by Paper Pusher on 2013-02-07
Thank you for the detailed explanation of USB technology. You are describing a lot that I did know. From my perspective the situation is very straight forward

[LIST=1]
[*]I have three USB hubs which used to work on my Ubuntu 12.04 computers
[*]They no longer work on my up to date Ubuntu 12.4 computers.
[*]The hubs still work on the Ubuntu 12.04 computer whihc is out of date (beacause it was in storage).
[/LIST]

That tells me that you are quite correct in your earlier post. An update to Ubuntu broke the USB support on my hubs. I have followed your advice and done the following: 

[LIST=1]
[*]I have registered on the launch pad website.
[*]I have explored the launch pad website on how to submit a bug, but have been unable to do so.
[*]I am stuck and I don't know how to go any further. I will have to depend on other people reporting the bug and fixing it.
[/LIST]

---

### Post by DuckHook on 2013-02-07
> **Paper Pusher said:**
> ..,I am stuck and I don't know how to go any further.

...well, I suspect that we can find a way forward...

> They no longer work on my up to date Ubuntu 12.4 computers.

I don't know what you are referring to here because there is no 12.4: there is 12.04, which is LTS, and then there is 12.10, which is the latest upgrade. I suspect that your problems arose after you *upgraded* to 12.10. Therefore, to move forward, you can:

1. Revert to 12.04 which has proven to work for you. Since it is LTS, it will be supported to 2017, which should give you lots of time to explore alternatives. If my understanding is not correct and you are still at 12.04, then, as I've suggested earlier, you can try,

2. Revert to 11.10 which is still supported for a few more months and which would presumably not have whatever update broke your usage.

3. Using Kubuntu, Xubuntu or Lubuntu, all runnable from a LiveCD/DVD so that you can try them out first (and test your hub) before actually installing,

4. Using Debian, Fedora, Gentoo, or any of a dozen other distros,

5. Contacting your hub manufacturer to see if they can offer any easy workaround,

6. Trying a different powered hub.

7. Post to the hardware forum, (or ask this thread to be moved there) where actual hardware gurus visit.

It is perfectly understandable that you not file bug reports. I imagine that most people don't. A bug report is no guarantee of a fix anyways. It's just an alert to the developers and what we members of the community try to do to continually improve the product, but it is not obligatory. If you want to still do so, then [here]("https://bugs.launchpad.net/") is the link to launchpad bug report filing. In the final analysis, if these exact hubs are indispensable to you and none of the seven options above work, then I suppose you will have to make a decision between living with the drawback of plugging your devices in directly, or sticking with Windows only. Sorry I can't be of further help.

---

### Post by Paper Pusher on 2013-02-10
Thank you very much for all the help.  The problem has gone away.  One of the recent updates must have fixed the problem that arose.  My USB hub works fine now.

---


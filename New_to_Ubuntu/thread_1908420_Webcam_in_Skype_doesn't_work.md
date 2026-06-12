---
title: "Webcam in Skype doesn't work"
date: 2012-01-13
forum: New to Ubuntu
---

### Post by DocSeaLion on 2012-01-13
Hi Community,
 
I am a fresh guy in ubuntu. I have ubuntu 11.10 on Acer Aspire one netbook. But I've recently got a sudden bug: inbuilt webcam has disappeared from Skype showing "No Devices Found" though it worked before.
 
lsusb gives just
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
 
How could I return it back to operate?
 
Thank you in advance.

---

### Post by cogier on 2012-01-13
Try going to the Software Centre and then Remove Skype and then reinstall it.

No guarantees but it can't hurt to try.

---

### Post by DocSeaLion on 2012-01-13
Thank you for the suggestion. I will try this night. Maybe it is also worth to install cheese and check camera detection on it? I have concern that everybody who had similar problem detected their cams with "lsusb" command. But I cannot do that (At least I do not see anything looking as a webcam in the list responding to that command - please see my first post).

---

### Post by Drowz0r on 2012-01-13
My webcam would work in the preview (test thing) but wouldn't work when doing a video call. It was a widely used Logitech cam that worked in windows fine.

I tried a different webcam and everything worked. Not sure why. Do you have another webcam you can try at all? Just a thought.

---

### Post by DocSeaLion on 2012-01-13
I do have other webcam but I want to use inbuilt webcam. Skype reinstallation doesn't work... Eh.

---

### Post by DocSeaLion on 2012-01-13
Even Cheese does not detect my webcam... How could I check if it works or not physically... Please help, thank you

---

### Post by Drowz0r on 2012-01-15
> **DocSeaLion said:**
> Even Cheese does not detect my webcam... How could I check if it works or not physically... Please help, thank you

Yeah I had the same thing. Well, sorta.

Skype would show webcam but only in the test area. Cheese would show webcam but all the effects would screw it up. Websites like chatroutlette for example would not show my webcam.

Changed the webcam and it worked perfectly. I tried for ages to get it working. Re-installed flash as some things rendered in flash. Tried drivers but no joy. Reinstalled all sorts of applications.

I've found better performance downloading skype from the skype site and selecting the 11.04 version rather than using the software centre version though - if that helps.

---

### Post by Carterclan on 2012-01-15
If your Webcam does not work in Cheese it is likely that it wont work at all in Linux.

It is not unusual for a webcam to work in cheese and other applications but not in Skype, if that is the case then you need to follow the instructions found in this inserted link.

[http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html](http://www.ubunturoot.com/2010/05/how-to-fix-webcam-problem-in-skype.html)

---

### Post by madvinegar on 2012-01-15
wrong post.

---

### Post by resander on 2012-01-15
I also had a hard time getting sound and video for Skype....

First the inbuilt camera on a Fujitsu Biblo netbook showed the image upside down. The following commands issued from the command line solves that problem:

export LIBV4LCONTROL_FLAGS=3
LD_PRELOAD=/usr/lib/libv4lcompat.so skype

but the quality of the inbuilt camera was poor so I bought a USB Logitech C310 webcam. That worked fine out of the box, but it was necessary to goto Skype Video Options (of the Skype program - click light blue circle with an S in it at bottom left, then Options, then Video Devices) and select the USB camera as current camera via the drop down list headed Select webcam: in the Video Devices dialog. There is a similar dropdown list in Cheese->Edit->Preferences dialog.

The Logitech USB camera has an inbuilt microphone. The Skype program defaults to the inbuilt mic of the laptop/netbook (if there is one) or a pink-plug mic. To capture sound from the USB camera Skype needs to be told via sound preferences in Ubuntu:

System->Preferences->Sound->Input-Tab

A Sound Preferences dialog pops up. In my case the 'Connector:' input field was 'Analogue Microphone'. Then select the USB camera from the list of radio buttons headed 'Choose a device for sound input:'. In my case the radio button choice is '081b Analog Mono'. The 081b is part of the USB identifier of the webcam shown in the lsusb command.

Don't know if any of the above would apply though...

I am using the latest Skype for Linux 2.2.beta and Ububtu 10.04.03 LTS.

Ken

---

### Post by mastablasta on 2012-01-15
> **DocSeaLion said:**
> Even Cheese does not detect my webcam... How could I check if it works or not physically... Please help, thank you
in terminal:
gstreamer-properties


there you can switch various linux video drivers.

the ld preload command given above is also worth a try. 
[http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux](http://superuser.com/questions/85500/webcam-problem-with-skype-on-linux)

additionally - when you unintsall skype did you also remove the hidden ./skype directory in home folder? if not try again and remove that one. also you can try using the .deb file found at sykpe.com.

---


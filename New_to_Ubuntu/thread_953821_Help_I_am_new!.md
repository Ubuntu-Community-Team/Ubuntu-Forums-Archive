---
title: "Help I am new!"
date: 2008-10-20
forum: New to Ubuntu
---

### Post by Legebriwen on 2008-10-20
Hi. I am new to using Ubuntu and I am finding things very confusing. I am not very technical with computers and would like some help getting my LaPazz graphic tablet to work. It is the model WP5540, I have tried lots of different things to get it work and don't know what to do. If anyone can help me to get this to work it would be great.:)

---

### Post by Legebriwen on 2008-10-20
Hi. I am new to using Ubuntu and finding it very confusing. I am not very technical when it comes to computers. I am trying to get my LaPazz graphic tablet to work it is the WP5540. My laptop is a HP Pavilion DV2000 (Bought in the UK). I have tried lots of different things to get it to work and none have so far. If anyone can help me to get it to work that would be fantastic. :)

---

### Post by Elfy on 2008-10-20
Hi and welcome to the forums - to start with we cna see if the device is recognised, make sure the tablet is plugged in. Now open a terminal from the accessories menu - paste this command in and enter

```
cat /sys/bus/usb/devices/*/product
```

It should output all the usb devices attached, please paste that into a new post.

This has a thread now.

---

### Post by Elfy on 2008-10-20
I just posted in the other for you - it says this

> **forestpixie said:**
> Hi and welcome to the forums - to start with we cna see if the device is recognised, make sure the tablet is plugged in. Now open a terminal from the accessories menu - paste this command in and enter

```
cat /sys/bus/usb/devices/*/product
```

It should output all the usb devices attached, please paste that into a new post.

Please don't use titles like that in future - most people here have a problem and need help :)

---

### Post by overdrank on 2008-10-21
Post merged to new thread  Welcome. :)

---

### Post by Legebriwen on 2008-10-21
Hi thank you for replying I typed in the command and this is what has come up. The tablet is showing.

Fingerprint Sensor
HP Integrated Module
Tablet WP5540U
SideWinder? Mouse
HP Webcam
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
UHCI Host Controller
EHCI Host Controller
EHCI Host Controller

---

### Post by Elfy on 2008-10-21
Ok well I willing to try and help - never used a tablet, nor attempted to make one work.

Can you first open sysnaptic and look for xorg - we need to know which version you have installed - screenshot gives mine

Itis quite complicated to do it seems, but nevertheless - it is only following instructions (for both of us)

---

### Post by Elfy on 2008-10-21
Once you've done that - if the xorg version is 1:7.3 as mine is then look here - there is a lot of information in the page, take it slowly as you work through the steps. If you get a problem or are unsure stop and ask the question.

[https://help.ubuntu.com/community/TabletSetupWizardpenHardy173](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173)

If not then here
[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

One other small thing - use the report button on the first post, ask a mod to rename the thread to something more descriptive - people use titles to search for threads :)

---

### Post by Legebriwen on 2008-10-22
Hi again. I have tried both of those ways and no luck.:(. I do have the same version as you with xorg.

---

### Post by Elfy on 2008-10-23
Can you run this from a terminal and post the output please

```
cat /etc/X11/xorg.conf
```

---

### Post by hyper_ch on 2008-10-23
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by Legebriwen on 2008-11-01
Hi. 

I am so sorry it has taken me so long to reply it has been a manic week. I have typed the command in and this is what has come up, I have added the pen in however it still does not work. Sorry this is not displayed properly, i am not sure how to do it and can't do the [code][code] thing.


Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"gb"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "InputDevice"
        Identifier      "WizardPen Tablet"
        Option          "Name" "UC-LOGIC Tablet W5540U"
        Option          "SendCoreEvents"        "true"
        Driver          "wizardpen"
        Option          "TopX"          "2199"
        Option          "TopY"          "3598"
        Option          "BottomX"       "30325"
        Option          "BottomY"       "29278"
        Option          "MaxX"          "30325"
        Option          "MaxY"          "29278"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"		"/dev/psaux"
	Option		"Protocol"		"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Synaptics Touchpad"
        InputDevice     "WizardPen Tablet" "SendCoreEvents"
EndSection

---

### Post by HittingSmoke on 2008-11-01
> Hi. 

I am so sorry it has taken me so long to reply it has been a manic week. I have typed the command in and this is what has come up, I have added the pen in however it still does not work. Sorry this is not displayed properly, i am not sure how to do it and can't do the [code][code] thing.

If you highlight your pasted code then hit the # button in the bar above the text box it will wrap code tags around your highlighted text :)

---

### Post by Legebriwen on 2008-11-02
> **HittingSmoke said:**
> If you highlight your pasted code then hit the # button in the bar above the text box it will wrap code tags around your highlighted text :)

Thankyou very much I will remember that. :)

---

### Post by Elfy on 2008-11-02
So you had no problems running the .configure and make install and the driver was installed correctly?

It might be that you need to calibrate it then [https://help.ubuntu.com/community/TabletSetupWizardpenHardy173#Calibration](https://help.ubuntu.com/community/TabletSetupWizardpenHardy173#Calibration)

Please run these from a terminal - use code tags please, if in doubt you just need to type them in one at the beginning one at the end

```
cat /var/log/Xorg.0.log |grep err
dmesg |grep error
```

---


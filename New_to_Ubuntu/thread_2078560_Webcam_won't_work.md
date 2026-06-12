---
title: "Webcam won't work"
date: 2012-10-31
forum: New to Ubuntu
---

### Post by Kev261266 on 2012-10-31
Hi,

I have a generic webcam, the only details I have are "USB 2.0 PC Camera (SN9C201 & 202)" 

I had a look round the forums and the consensus seems to be download "cheese" and see if it works there, well I did and it does. But it won't seem to work on anything else.

Any ideas??

---

### Post by NikTh on 2012-10-31
Hi , 
[quote="Kev261266"]But it won't seem to work on anything else.[/quote]
when you say anything else ? Do you mean Skype ? 


[LIST]
[*] Open a terminal (CTRL+ALT+T) and provide some more info.
[/LIST]
 Give the results of bellow commands 
```
lsb_release -rcd ; uname -r
lsusb
```Put the results between these brackets **[noparse]```
here
```[/noparse]** to be easier to read.


[LIST]
[*] Also perform a test.
[/LIST]
 ```
gstreamer-properties
```and at the opened window goto "Video" > "Default Input" and click "Test". If your WebCam works there, the problem is not your WebCam or Ubuntu , but the program where the WebCam not works.

Thanks

---

### Post by Kev261266 on 2012-10-31
Hi,

Here's the results:

```
lsb_release -rcd ; uname -r
```Gives the following:

```

Description:    Ubuntu 12.10
Release:    12.10
Codename:    quantal
3.5.0-17-generic

```and

```
lsusb
```gives this:

```
Bus 001 Device 003: ID 0bc2:3000 Seagate RSS LLC 
Bus 002 Device 004: ID 0c45:628f Microdia PC Camera with Microphone (SN9C202 + OV9650)
Bus 002 Device 002: ID 148f:2070 Ralink Technology, Corp. RT2070 Wireless Adapter
Bus 002 Device 003: ID 0644:0200 TEAC Corp. All-In-One Multi-Card Reader CA200/B/S
Bus 004 Device 002: ID 413c:1003 Dell Computer Corp. Keyboard Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 413c:2010 Dell Computer Corp. Keyboard
Bus 004 Device 004: ID 056a:0062 Wacom Co., Ltd Volito2 4x5
```So I see that it is recognising the webcam.

Running the test did show the cam as working but slow and blurry, and gave the following results in the terminal:

```
(gstreamer-properties:6079): Gtk-WARNING **: Unknown property: GtkDialog.has-separator

(gstreamer-properties:6079): Gtk-WARNING **: Unknown property: GtkDialog.has-separator
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
```So maybe it's the site I was using that was not working (it did however work in WinXP)

---

### Post by NikTh on 2012-10-31
[quote="[Kev261266]("http://ubuntuforums.org/member.php?u=1747338")"]So maybe it's the site I was using that was not working[/quote] 

Yeap. Probably the site wants Windows code or something ? I don't know , but as you see the WebCam working. Both cheese and this gstreamer-properties test can verify that your WebCam recognized properly from Linux(Ubuntu) and works well.

---

### Post by Kev261266 on 2012-11-01
From further research it seems to be something to do with Adobe Flash Player. Do you know where I would add/allow a site in the settings manager?

Cheers.

Kev.

---


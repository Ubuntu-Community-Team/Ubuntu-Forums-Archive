---
title: "need help on motion software."
date: 2013-12-09
forum: New to Ubuntu
---

### Post by akashdeepmitthu on 2013-12-09
I had installed motion software and configured it according to the advice on the forum. I am using logitech c210 webcam. My webcam has been detected by the system but when I am running motion I am getting some error. Then I checked the output of "demesg"  command. I got following:
```
[COLOR=#8B8B8B][FONT=Monaco][5.790301] Linux video capture interface: v2.00[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][6.213422] uvcvideo: Found UVC 1.00 device. <unnamed> (046d:0819)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][6.610378] input: UVC camera (046d:0819)  as  /devices/platform/bcm2708_usb/usb1/1-1/1-1.2/1-1.2:1.0/input/input2 [/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][6.856060] usbcore: registered new interface driver uvcvideo[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][6.996478] USB Video Class driver (1.1.1)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 7.796439] usbcore:  registered new interface driver snd-usb-audio[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][10.301633] EXT4-fs (mmcblk0p2): re-mounted.Opts : (null) [/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][10.822316] EXT4-fs (mmcblk0p2): re-mounted.Opts : (null)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 23.426901] Adding 102396k swp on /var/swap. Priority:-1 extents:1 across:102396k SS[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 26.301843] uvcvideo: Failed to query (SET_CUR) UVC control 3 on unit 2: -110  (exp.2)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 26.601848] uvcvideo: Failed to query (SET_CUR) UVC control 7 on unit 2: -110  (exp.2)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 26.601848] uvcvideo: Failed to query (SET_CUR) UVC control 2 on unit 2: -110  (exp.2)[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 32.931814] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][ 37.931908] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][43.941808]uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][48.841809] uvcvideo: Failed to set UVC probe control : -110 (exp. 26).[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][540.830427] uvcvideo: Failed to set UVC probe control : -71 (exp. 26).[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][541.059081] usb1-1.2: USB disconnected, device number 4.[/FONT][/COLOR]
[COLOR=#8B8B8B][FONT=Monaco][544.621932] usb 1-1.2: new low-speed USB device number 6 using dwc_otg.[/FONT][/COLOR]
```

---

### Post by papibe on 2013-12-09
Hi akashdeepmitthu. Welcome to the forum ):P

What version of Ubuntu are you using? Regular desktop? Minimal? Server?

Regards.

---


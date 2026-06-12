---
title: "use card=&lt;n&gt; insmod option???"
date: 2013-05-04
forum: New to Ubuntu
---

### Post by white123 on 2013-05-04
hi there, I'm installing dvb-t card and with dsmesg I got this

```
20.219636] em28xx #0: found i2c device @ 0xa0 [eeprom]
[   20.237137] em28xx #0: found i2c device @ 0xb8 [tvp5150a]
[   20.279645] em28xx #0: found i2c device @ 0xc2 [tuner (analog)]
[   20.297516] em28xx #0: Your board has no unique USB ID and thus need a hint to be detected.
[   20.297730] em28xx #0: You may try to use card=<n> insmod option to workaround that.
[   20.297916] em28xx #0: Please send an email with this log to:
[   20.298051] em28xx #0:     V4L Mailing List <linux-media@vger.kernel.org>
[   20.298216] em28xx #0: Board eeprom hash is 0xa4e09589
[   20.298353] em28xx #0: Board i2c devicelist hash is 0xa49b008f
[   20.298502] em28xx #0: Here is a list of valid choices for the card=<n> insmod option:
...
[   20.309060] em28xx #0:     card=18 -> Hauppauge WinTV HVR 900 (R2)
[   20.312120] em28xx #0:     card=19 -> EM2860/SAA711X Reference Design
[   20.315136] em28xx #0:     card=20 -> AMD ATI TV Wonder HD 600
...
[   20.361444] em28xx #0:     card=72 -> Gadmei UTV330+
[   20.361449] em28xx #0:     card=73 -> Reddo DVB-C USB TV Box
[   20.367046] em28xx #0: Config register raw data: 0x58
[   20.377630] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   20.377703] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   20.452288] em28xx #0: AC97 vendor ID = 0xffffffff
[   20.452863] em28xx #0: AC97 features = 0x6a90
[   20.452872] em28xx #0: Empia 202 AC97 audio processor detected
[   20.493515] em28xx #0: v4l2 driver version 0.1.2
[   20.542834] em28xx #0: V4L2 video device registered
```

my choice is card=20 but how to You may try to use card=<n> insmod option to workaround that? I have no clue,, thank you!

---

### Post by white123 on 2013-05-04
ok, I edited file alsa-base.conf in /etc/modprobe.d

added line

options em28xx card=20

now it looks ok, card even blinked with blue LED on it but VLC don't play from it and other programs like W_SCAN or ME TV don't see the card.

there is grep dmsg, what can be the problem?

```
 26.448536] em28xx #0: i2c eeprom f0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
[   26.448572] em28xx #0: EEPROM ID= 0x9567eb1a, EEPROM hash = 0xa4e09589
[   26.448578] em28xx #0: EEPROM info:
[   26.448583] em28xx #0:    AC97 audio (5 sample rates)
[   26.448589] em28xx #0:    USB Remote wakeup capable
[   26.448595] em28xx #0:    500mA max power
[   26.448602] em28xx #0:    Table at 0x04, strings=0x226a, 0x0000, 0x0000
[   26.449313] em28xx #0: Identified as AMD ATI TV Wonder HD 600 (card=20)
[   26.530787] tvp5150 2-005c: chip found @ 0xb8 (em28xx #0)
[   26.587197] tuner 2-0061: chip found @ 0xc2 (em28xx #0)
[   29.064392] input: em28xx IR (em28xx #0) as /devices/pci0000:00/0000:00:1d.7/usb1/1-1/input/input11
[   29.065635] em28xx #0: Config register raw data: 0x58
[   29.066587] em28xx #0: AC97 vendor ID = 0xffffffff
[   29.067029] em28xx #0: AC97 features = 0x6a90
[   29.067036] em28xx #0: Empia 202 AC97 audio processor detected
[   29.301962] em28xx #0: v4l2 driver version 0.1.2
[   29.390532] em28xx #0: V4L2 video device registered as /dev/video1
[   29.390541] em28xx #0: V4L2 VBI device registered as /dev/vbi0
[   29.405155] em28xx audio device (eb1a:2881): interface 1, class 1
[   29.405189] em28xx audio device (eb1a:2881): interface 2, class 1
[   29.405302] usbcore: registered new interface driver em28xx
[   29.405312] em28xx driver loaded
[   29.784358] em28xx #0/2: dvb frontend not attached. Can't attach xc3028


```

---


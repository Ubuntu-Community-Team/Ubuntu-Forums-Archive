---
title: "How to install this Prodikeys PC-MIDI HID Driver?"
date: 2019-11-29
forum: New to Ubuntu
---

### Post by mika3 on 2019-11-29
Hi, I have an old Creative Prodikeys DM -keyboard which works well as keyboard, but midi (piano) keys don't work with Ubuntu out of box. I am moving my homestudio from Windows to Ubuntu (Reaper DAW). 

I found drivers for Prodikeys from here: [http://prodikeys.princefolk.co.uk/](http://prodikeys.princefolk.co.uk/) but didn't succeed with installation.

I also found "HID: Prodikeys PC-MIDI HID Driver" from here, but I don't have a clue how to install this: 
[https://gitlab-beta.engr.illinois.edu/ejclark2/linux/commit/3a370ca1dcf8c80aff7a0a21d6b0f50ca2a151e9](https://gitlab-beta.engr.illinois.edu/ejclark2/linux/commit/3a370ca1dcf8c80aff7a0a21d6b0f50ca2a151e9)
Any tips? Thank you!

---

### Post by Holger_Gehrke on 2019-11-30
Do you have the older version with PS/2 interface ? Then you're probably out of luck. The driver you're linking to is for the newer version connected through USB. It should already be installed by default as '/lib/modules/$(uname -r)/kernel/drivers/hid/hid-prodikeys.ko'. The only thing missing is the app to set up some things which is included in source code in the archive on sourceforge (which is linked on the prodikeys.princefolk.co.uk page).

Holger

---

### Post by mika3 on 2019-11-30
> **Holger_Gehrke said:**
> Do you have the older version with PS/2 interface ? Then you're probably out of luck. The driver you're linking to is for the newer version connected through USB. It should already be installed by default as '/lib/modules/$(uname -r)/kernel/drivers/hid/hid-prodikeys.ko'. The only thing missing is the app to set up some things which is included in source code in the archive on sourceforge (which is linked on the prodikeys.princefolk.co.uk page).

Holger

Hi Holger,

unfortunately I have an older version with PS/2. I was hoping that same driver would work, but didn't understand that it was only for usb interface. So I'll just go and buy a good and small Midi keyboard.

Thank you for your answer, it was very helpful!

-Mika-

---

### Post by dragon-788 on 2020-05-13
You probably already have your USB MIDI device in hand, but there is a way to convert a PS/2 to USB via Arduino.

[https://linuxmusicians.com/viewtopic.php?p=107896&sid=c2c9c6df9dda58803265d6965dc7972a#p107896](https://linuxmusicians.com/viewtopic.php?p=107896&sid=c2c9c6df9dda58803265d6965dc7972a#p107896)

And there is a built in kernel driver for the USB version of the keyboard.

[https://github.com/torvalds/linux/blob/master/drivers/hid/hid-prodikeys.c](https://github.com/torvalds/linux/blob/master/drivers/hid/hid-prodikeys.c)

---


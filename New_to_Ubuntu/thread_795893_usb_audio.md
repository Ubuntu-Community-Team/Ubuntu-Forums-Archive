---
title: "usb audio"
date: 2008-05-15
forum: New to Ubuntu
---

### Post by Bigadada_saba on 2008-05-15
My speakers on the laptop arn't working so i bought  the logitech note book speakers  when i plug them in i hair the logon chimes but when i play  music or video i don't heer any thing can someone help me with this problem  im running 8.04

---

### Post by lonestar32 on 2008-05-16
It might have something to do with pulseaudio.  It allows for different streams of audio to be directed to different devices.  In order to control pulseaudio, you'll need to install PulseAudio Device Chooser.

Once it is installed, you'll need to start it - from Applications - Sound & Video - PulseAudio Device Chooser.

Then there will be a new icon in the top right, click that, and the drop down menu will have a volume control.  On the Playback tab, the streams of audio that are currently playing will be displayed, right click on that and "move stream" to the appropriate device.

Hope this helps.

---

### Post by Bigadada_saba on 2008-05-16
Thanks it helps alot but how can the streaming video  and audio from my browser be herd trough the usb because that part still doesn't work

---


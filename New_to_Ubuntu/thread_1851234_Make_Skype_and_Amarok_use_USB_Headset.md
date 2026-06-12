---
title: "Make Skype and Amarok use USB Headset"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by mdavis1231 on 2011-09-27
In Ubuntu 11.04, could anyone show me step-by-step how to make Skype and Amarok use my Logitech USB Headset without my having to completely remove PulseAudio?  I have PulseAudio completely removed at the moment, but would really prefer not to have to do this.

[B]Mark in Cincinnati
*"It's great to be free from Windoze...YIPPEE!!!"*[/B] ):P

---

### Post by papibe on 2011-09-27
I have a USB Logitech webcam pro 9000. In order to make the mic work in Skype, I have to change the sound settings before creating a chat.

I go to Sound Preferences -> Input. There it is usually set to 'Internal Audio Analog Stereo, but I change it to '0809 Analog Mono'. Which is my web cam microphone.

The process to change both input and output to your handset should be similar.

Hope it helps,
Regards.

BTW, the '0809' coincides with the USB id if my camera:
```
$ lsusb | grep -i logitech
Bus 002 Device 003: ID 046d:**0809** Logitech, Inc. 

```

---

### Post by mdavis1231 on 2011-09-27
I had someone show me today remotely how to use pavucontrol to set individual applications to use different input/output permanently (until you manually change them).  So I reinstalled PulseAudio, installed pavucontrol, but couldn't figure out how to do it.  I'm wanting to not have to uninstall PulseAudio, but set my Skype and Amarok to permanently use only my Logitech USB headset.

---


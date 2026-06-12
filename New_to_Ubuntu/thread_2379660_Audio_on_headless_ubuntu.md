---
title: "Audio on headless ubuntu"
date: 2017-12-08
forum: New to Ubuntu
---

### Post by neek0la on 2017-12-08
Hi all,
I hope im posting this in the correct area.

Hi  all, Im running a mini pc (think chinese NUC) with u headless ubuntu.  Running great however i installed mopidy as a music server but cant get  any music to come from the speakers. Im not even too sure how to troubleshoot this as i have minimal  experience with the command line. Anyone have any idea how to determine the issue and resolve?
  I have inputted     sudo aplay -l 
  It outputs the following
  ```
**** List of PLAYBACK Hardware Devices ****
Home directory not accessible: Permission denied
card 0: HDMI [HDA Intel HDMI], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: HDMI [HDA Intel HDMI], device 7: HDMI 1 [HDMI 1]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
   card 0: HDMI [HDA Intel HDMI], device 8: HDMI 2 [HDMI 2]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 0: ALC892 Analog [ALC892 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC892 Digital [ALC892 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
  It seems to recognize the sound card hoever when i input;     aplay /usr/share/sounds/alsa/Front_Center.wav    i dont get any sound
  Any help would be greatly apreciated

---


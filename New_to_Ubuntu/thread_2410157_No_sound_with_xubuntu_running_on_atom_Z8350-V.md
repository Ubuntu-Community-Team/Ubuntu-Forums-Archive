---
title: "No sound with xubuntu running on atom Z8350-V"
date: 2019-01-11
forum: New to Ubuntu
---

### Post by sokoldy on 2019-01-11
As expected I'm having problems with the sound on the above, but it is something I have not come across before, so am wondering how to proceed.
The box is a mini PC with an atom Z8350-V quad core with 2 Gb memory running Xubuntu 18.04 with the latest kernel 4.20.0.
aplay -l shows that there are two cards- card 0 being Intel HDMI/DP LPE Audio +driver, card 1 bytcrrt5651 + driver.
Under Output Devices tab the Volume Control shows both channels and the volume output and during playback show these to be active as if the sound system is working properly.
Under Playback tab system sounds and playback are shown to be working, but no sound from speakers or headphones.
1. there is no output with speakers or headphones (both use the same jack)
2. When the computer is turned on the sound icon is greyed out. I can click on it and the box opens and I can start Pulseaudio(the icon then lights up). If I play an audio track or video, it plays but without sound.
The Configuration tab is greyed out and says' no cards available for configuration'
Any help with the above would be greatly appreciated.

---


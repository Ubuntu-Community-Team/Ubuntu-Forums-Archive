---
title: "pipewire doesn't work with the i5 11400, 730 HDMI Audio, Kbuntu"
date: 2023-01-17
forum: New to Ubuntu
---

### Post by vica2023 on 2023-01-17
[COLOR=#333333][FONT=sans-serif]why doesn't pipewire work with the i5 11400, 730 HDMI Audio? If you could set up a test procedure for my hardware that would be great?
Heres my info[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]aplay -l[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]card 1: PCH [HDA Intel PCH], device 0: ALC897 Analog [ALC897 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC897 Digital [ALC897 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [Sceptre N43]
  Subdevices: 0/1
  Subdevice #0: subdevice #0[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]works
speaker-test -Dhw:1,0 -c2
speaker-test -Dhw:1,1 -c2[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Playback device is hw:1,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
0 - Front Left
1 - Front Right
^CTime per period = 9.061709
[vic@500gbSSD ~]$ speaker-test -Dhw:1,0 -c2[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]speaker-test 1.2.8[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Playback device is hw:1,0
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 64 to 1048576
Period size range from 32 to 524288
Using max buffer size 1048576
Periods = 4
was set period_size = 262144
was set buffer_size = 1048576
0 - Front Left
^C 1 - Front Right
Time per period = 1.785710[/FONT][/COLOR]


[COLOR=#333333][FONT=sans-serif]Not working
speaker-test -Dhw:1,3 -c2[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif][vic@500gbSSD ~]$ speaker-test -Dhw:1,3 -c2[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]speaker-test 1.2.8[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Playback device is hw:1,3
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Playback open error: -16,Device or resource busy[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Why is device is hw:1,3 busy... I dont understand? Why no audio from this port... its listed as functional... I need an exact answer and test procedures... using Archlinux with kde.  * Asus 560, I5-11400 with graphics, 730, 32gb ddr4" Windows 11 works great at 4k 60hz, I really want to get this working out of the box no issues..." THIS SAME CONFIGUration works fine with the Dell Optiplex 3050, I5-6500 530, 16gb ddr4, 4k @30hz, installed on 500gb ssd usb, just went over and plugged in drive usb 3 and reboot uefi to boot off ssd)[/FONT][/COLOR]
[COLOR=#333333][FONT=sans-serif]Thanks Vic[/FONT][/COLOR]

---

### Post by #&amp;thj^% on 2023-01-17
Vic just a tip for you in UF, most folks won't bother with a wall of text.
Please wrap each command return in code tags IE:
```
aplay -l
card 1: PCH [HDA Intel PCH], device 0: ALC897 Analog [ALC897 Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 1: ALC897 Digital [ALC897 Digital]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 1: PCH [HDA Intel PCH], device 3: HDMI 0 [Sceptre N43]
Subdevices: 0/1
Subdevice #0: subdevice #0
```
Makes it  easily readable.
See my signature for code tags, Thanks, and Welcome to the Forums
EDIT OP also has a thread with no results here: [https://bbs.archlinux.org/viewtopic.php?id=274432](https://bbs.archlinux.org/viewtopic.php?id=274432)

---


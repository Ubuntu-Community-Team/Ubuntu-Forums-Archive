---
title: "[SOLVED] no sound in new ubuntu 8.04 install"
date: 2008-07-18
forum: New to Ubuntu
---

### Post by dimitris78 on 2008-07-18
Hello,

I just installed Ubuntu in my laptop (Medion MD 96282) and i get no sound at all. I looked in the forums a bit but couldn't fix the problem.
With an "aplay -l" in terminal I get:

**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: STAC92xx Analog [STAC92xx Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

I am using the i386 version of Ubuntu (my processor is Turion64 but I couldn't the ndiswrapper working at the amd64 version of ubuntu). I have no idea what my problem really is, so any suggestions are welcome!

thanks in advance, D.

---

### Post by cmnorton on 2008-07-18
This is a good place to start:

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

---

### Post by dimitris78 on 2008-07-19
I tried the steps in 'Basic troubleshooting' without any results. Any other suggestions? Should I report a sound bug?

---

### Post by cmnorton on 2008-07-19
It never hurts to report it as a bug on Ubuntu launchpad. You might be able to subscribe to an existing bug. You might want to attach your /var/log/dpkg.log with the bug report.

---

### Post by Ekolost on 2008-07-19
Help

---

### Post by dimitris78 on 2008-07-20
The master volume is unmuted, like everything else in volume control. There's no any surround option in my volume control, I try something else. Thanks anyway!

---

### Post by dimitris78 on 2008-07-29
Solved, with some help from the alsa-user mailing list.
I had to add: 
options snd-hda-intel model=gateway
to the /etc/modprobe.d/alsa-base file

---

### Post by cmnorton on 2008-08-05
I had to do this for my Thinkpad in 7.10, but the problem was solved in 8.04.

---


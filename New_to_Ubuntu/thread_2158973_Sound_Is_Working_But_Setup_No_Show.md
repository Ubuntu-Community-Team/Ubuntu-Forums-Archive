---
title: "Sound Is Working But Setup No Show"
date: 2013-07-01
forum: New to Ubuntu
---

### Post by BudTuba on 2013-07-01
Thanks to help from this board, I was able to repair my installation of Ubuntu 12.10.  The original problem was lack of sound.  Sound worked OK with Live CD, but not in installed OS.  After repairing using boot.repair and copying resolv.conf from CD to hard drive, it did start properly avoiding the low resolution screen at startup.  The sound did get corrected to the OS and I can hear it fine, but does not show the Soundblaster Audigy card on Settings.  Therefore, I cannot test sound or utilize the various schemes. 

The question now is how to get the hardware options to show in Sound settings.

Thanks for any help from people who understand this stuff.

---

### Post by dino99 on 2013-07-01
[https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

---

### Post by macguges on 2013-07-03
> **dino99 said:**
> [https://help.ubuntu.com/community/SoundTroubleshootingProcedure](https://help.ubuntu.com/community/SoundTroubleshootingProcedure)

Just to expand on dino99's recommendation for budtuba, who is new, if you take each step from this troubleshooting sequence in turn, following the instructions and reporting the results here, the community can methodically resolve your problem.  For instance you should begin with the first step,
> If you are using Ubuntu 12.04 LTS (Precise), first execute this command, wait 10 seconds **and reboot**: 

killall pulseaudio; rm -r ~/.pulse*

If that did not help, please proceed...

If you need clarification on any of these steps, post your question in a reply to this thread.

---

### Post by BudTuba on 2013-09-02
I Completed steps 1 and 2 and 3 Although rhythmplayer shows sound, no sound coming from speakers.  Also in Windows Xp when there is a signal, it automatically turns on sound amplifier, but apparently not in Ubuntu.  Testing sound with settings does not creat sound.

---

### Post by BudTuba on 2013-09-02
[http://www.alsa-project.org/db/?f=a5c969e6f15ea4b6c41ff493d64f2509caa2c432](http://www.alsa-project.org/db/?f=a5c969e6f15ea4b6c41ff493d64f2509caa2c432)
 is the alsa dump

---


---
title: "Sound intermittently works, intermittently doesn't as &quot;Dummy Output&quot;"
date: 2020-11-12
forum: New to Ubuntu
---

### Post by alchemistjosh on 2020-11-12
Hello all!

I am new to the world of Linux, and I'm having an issue with sound output. **Audio used to work without problems **on 20.04, but recently it has become a toss-up. **Sometimes when the computer boots, sound works without problems. Other times, the only sound output available is "Dummy Output." **Rebooting without making any changes sometimes bumps the sound from working to not working, or vice versa. **I can't recall any updates or other big system changes** that occurred around the same time as the problem started.

There are similar problems with "Dummy Output" posted in this forum and elsewhere, **but what appears to be different in this case is the intermittent nature of the problem**. I've tried to troubleshoot as much as possible on my own, but without success. If you have any guidance, I would certainly appreciate it!

 I dual-boot with Windows 10 and Ubuntu 20.04 (kernel 5.8.0), and sound has continued to work consistently under Windows. I'm sorry if I haven't provided enough information to help diagnose the issue! I have a lot to learn.

Here is what I have tried so far:
[LIST=1]
[*]Confirmed that the sound card is found (recommended [here]("https://ubuntuforums.org/showthread.php?t=2447446")):
```
sudo lspci | grep Audio
```
This returns the following:
```
03:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Raven/Raven2/Fenghuang HDMI/DP Audio Controller03:00.5 Multimedia controller: Advanced Micro Devices, Inc. [AMD] Raven/Raven2/FireFlight/Renoir Audio Processor
03:00.6 Audio device: Advanced Micro Devices, Inc. [AMD] Family 17h (Models 10h-1fh) HD Audio Controller
```
[*]Confirmed that sound card drivers are present (recommended [here]("https://ubuntuforums.org/showthread.php?t=2447446")):
```
aplay -l
```
This gives me:
```
**** List of PLAYBACK Hardware Devices ****card 0: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic_1 [HD-Audio Generic], device 0: ALC294 Analog [ALC294 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```
[*]Force-reloaded alsa (recommended [here]("https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip")) with the following & a subsequent reboot:
```
sudo alsa force-reload
```
With 6 successive reboots and no intentional system changes, I have 3 boots that lead to working sound and 3 that lead to no sound with "Dummy Output." The sequence of successes and failures appears random.
[*]Restarting pulseaudio (recommended [here]("https://ubuntuforums.org/showthread.php?t=2453139&page=2#12")) with:
```
pulseaudio -k
```
After waiting about 10 seconds, there is still no change; "Dummy Output" is still the only sound option listed.
[*]Forcing pulseaudio to rebuild config files (based on [this suggestion]("https://www.kubuntuforums.net/showthread.php/76776-Greeting-Groovy-Gorilla-Kubuntu-20-10?p=441199&viewfull=1#86")) using:
```
killall pulseaudio; mv ~/.config/pulse ~/.config/pulse_bkup; pulseaudio --start
```
No change; "Dummy Output" is still the only sound option listed.
[*]Reinstalled alsa and pulseaudio (recommended [here]("https://itsfoss.com/fix-sound-ubuntu-1304-quick-tip")) with the following & a subsequent reboot:
```
sudo apt-get install --reinstall alsa-base pulseaudio
```
With 3 successive reboots, I again get a mix of successful audio and no sound with "Dummy Output."
[*]Ran updates (as recommended in [this Google doc]("https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit#heading=h.817okbj1u7n1"), pinned on the sound troubleshooting forum):
```
sudo apt-get dist-upgrade
```
Again, with several successive rebootings, I still get a mixture of successful sound and no-sound "Dummy Output" boots.
[/LIST]

---

### Post by alchemistjosh on 2020-11-13
Tentatively, this problem appears to be resolved.Based on an old, [not-upvoted comment from Stack Exchange]("https://askubuntu.com/questions/1114041/ubuntu-18-04-sound-doesnt-work-dummy-output"), I tried booting with an older kernel version (5.4.0). That reproducibly resolved the problem, so I assume something became corrupted kernel-wise in the kernel I had been using (5.8.0)? I updated to 5.9.8, and I haven't noticed the "dummy" problem again even after a few reboots. Tentatively, it appears to be fixed.

---


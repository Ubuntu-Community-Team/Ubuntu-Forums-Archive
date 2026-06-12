---
title: "No HDMI sound in Kubuntu"
date: 2013-04-08
forum: New to Ubuntu
---

### Post by Absolute Terror on 2013-04-08
I'll try to be as specific as I can about this.

I have installed Pulse Audio, I run Pulse Audio but it seems like no matter what I change I don't get sound. I know for a fact sound works because at random points in time the system itself will make noise, but I still get no sound from VLC, Audacity or ANY web browser.

I am using nvidia-current-updates on Kubuntu 12.04.

---

### Post by SeijiSensei on 2013-04-08
Go to System Settings > Multimedia > Phonon and make sure the HDMI adapter is selected as the default audio device.

I'm a little puzzled by your statement that you "installed" PulseAudio.  Pulse has been the default sound system in Ubuntu for quite some time now and is the default in 12.04.

If that doesn't fix the problem, try installing **pavucontrol** from the repositories and run that.  Make sure the device is not muted by default.

---

### Post by Absolute Terror on 2013-04-08
Right. I meant to say that I installed "pavucontrol". Sound is set to output to HDMI/DisplayPort and even more curious, the little volume bar moves every time I play something with audio. I just can't hear anything. All of this is on the Output Devices tab. the Playback tab only shows "System Sounds - Mono" is this normal? Nothing is muted.

---

### Post by SeijiSensei on 2013-04-08
I don't use HDMI, but yes, pavucontrol looks the same on my system.  Did you check Phonon?

---

### Post by Absolute Terror on 2013-04-09
Played around with Pulse yesterday until I got it working but after a reboot there is no sound again.

---

### Post by Absolute Terror on 2013-04-12
Bump.

Someone suggested that I purge and or remove pulseaudio.

Tried it, nothing.

---

### Post by GregA on 2013-04-12
It's best not to install or uninstall anything on Ubuntu or Kubuntu until you've checked out a few things - read carefully the following

[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)

If you did get the audio working, and then it didn't after reboot, it's because a setting or status you achieved was not "saved" - - but read the above section (you may need to go to the terminal and bring up alsaconfig).

---

### Post by Absolute Terror on 2013-04-20
Bump.

---


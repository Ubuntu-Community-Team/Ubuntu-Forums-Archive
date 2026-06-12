---
title: "Lost some of my sound capabilities"
date: 2012-03-27
forum: New to Ubuntu
---

### Post by Curtis6767 on 2012-03-27
can hear sounds on Youtube or through VLC Media Player, but cannot hear the sound when ubuntu starts nor can I get my mic to work so can't use Google voice, etc

everything was fine until I went into System Settings and messed around in there and now can't put it back the way it was.

did a search but could not find a fix

I do not have a sound card just using the supplied Intel audio

ubuntu 11.10

---

### Post by gordintoronto on 2012-03-27
In System Settings/Sound, check that there is only one device in the Hardware tab. (What brand and model of computer?) In the Output tab, try a different "connector," such as "stereo duplex." Make sure the microphone is not muted in the Input tab.

Also, in the system sounds tab, make sure it's not muted.

---

### Post by Curtis6767 on 2012-03-27
In the Hardware section, there are two devices.

Manhattan HDMI Audio
 and
Internal Audio.

I think they've both been on the system for a while.

I have selected and de-selected these in every possible combination but no luck.

Nothing is muted.

---

### Post by d4m1r on 2012-03-27
Go to startup applications and check to see if "gnome login sound" is enabled.

---

### Post by Curtis6767 on 2012-03-27
GNOME login sound is enabled.

Just to add:

If I hit the "Test Speakers" tab, I get nothing regardless of which device I have selected.

I do get the sound effects.

---

### Post by gordintoronto on 2012-03-27
If you are using an HDMI cable to drive, for example, an HDTV, select that "device." Otherwise, stick with "Internal Audio."

What is the brand and model of your computer?

What "sound connector" is selected?

---

### Post by Curtis6767 on 2012-03-27
I have a ZT Systems Affinity PC with an Intel Core i7 processor with no sound card.

If I go into System Settings/ Sound/ Hardware, the Manhattan HDMI Audio is selected by default.

If I select Internal Audio and then close System Settings, when I reopen System Settings/ Sound/ Hardware the HDMI Audio is once again selected by default.

I am not using my PC for an HDMI Audio so I don't need this, at least that's what I think, but I don't know how to get rid of it, either.

---

### Post by Curtis6767 on 2012-03-28
I went over to the Multimedia forum and went through some of the steps in one of the troubleshooting guides. I went into alsamixer and saw that my mic had been muted, so I unmuted that and it works.

I got to the part in the guide where I typed in "aplay -l," which brought up a list of playback hardware devices and in the list that followed I'm showing three devices.

The next step in the guide is to do some editing and select/change the default device; however, since I'm a complete noob at linux/ubuntu I don't feel comfortable with this because if I screw something up, which is very likely, then I'm, well, screwed.

I have sound, which I always did.

I have my microphone, which I had lost.

I still don't get the GNOME login sound.

Two out of three ain't bad, but I'd really like to get this back the way it was up to about a week ago.

Just in case it helps, this is what I got when I typed in "aplay -l"

curtis@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Intel [HDA Intel], device 0: ALC889 Analog [ALC889 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: Intel [HDA Intel], device 1: ALC889 Digital [ALC889 Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Generic [HD-Audio Generic], device 3: HDMI 0 [HDMI 0]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by gordintoronto on 2012-03-28
If it were me, I would leave it alone.

---


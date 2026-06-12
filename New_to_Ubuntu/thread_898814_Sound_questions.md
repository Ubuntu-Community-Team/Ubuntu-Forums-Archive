---
title: "Sound questions"
date: 2008-08-23
forum: New to Ubuntu
---

### Post by fredfelter on 2008-08-23
I'm learning how to use Audacity (1.3.4) but finding that I can record only in 1 channel. I'm recording audio off the computer (Pandora), Audacity settings are for Stereo and my computer (TP T22) sound functions are perfect with streaming audio, including stereo reception.

I'm thinking it might be the ALSA settings. Problems:
   1) Sound & Video > Alsamixergui (0.9.7) > "alsamixer: function snd_cti_open failed for default. Connection refused" Do I even have alsamixer and if so how can I access it?
   2) Sound & Video > Gnome Alsa Mixer > I see no dual channel settings on any of the meters. Maybe it is set up as mono only but I can't figure out how to determine or change this? This mixer doesn't have the same appearance as the conventional Alsamixer I used to see before I messed around with PulseAudio (now removed) and changed everything for the worse. 

Thanks in advance. Ubuntu 8.0.4

---

### Post by nitro_n2o on 2008-08-23
you could access alsamixer for the terminal 
just type alsamixer and it'll give a nice cli "gui"

I remember having several problem with sound on my laptop long time ago.. I've installed alsa from source and compiled it specifically for my machine and that solved the problem(s)

give it a shot and enjoy compiling from source :)

---

### Post by fredfelter on 2008-08-23
Here is what I get from the terminal:

fred@fred-laptop:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused
alsamixer: function snd_ctl_open failed for default: Connection refused

Weird isn't it?

---

### Post by fredfelter on 2008-08-23
A couple more bits of data re: my setup:

1) Volume Control: Sound Fusion CS46xx (Alsa mixer). Is that referring to the Gnome Alsamixer?
2) Sound & Video > Sound Recorder > "Your audio capture settings are invalid. Correct in Multimedia Settings (whatever that is).
3) Preferences > Sound > Devices > the only tests that return a sound are Autodetect and OSS. The ALSA option does not.

Thanks for any help.

---

### Post by st33med on 2008-08-23
You removed PulseAudio... WHY????

PulseAudio is essential to play audio through the speakers, and, as such, you removed it and sound now plays in basic mono...

Of course, I believe you can set ALSA as your default sound manager. Go to System>>Preferences>>Sound and set every dropdown menu in the current tab to ALSA.

Then, try doing:
```
alsamixer
```

---

### Post by fredfelter on 2008-08-23
I removed PulseAudio because I couldn't make Audacity work and after a rather extensive search I decided that that would be a way to accomplish it, especially since at my novice level I couldn't decipher the extensive coding changes I'd have to do to make Audacity and PulseAudio coexist.

Here is the result of setting all to Alsa:
fred@fred-laptop:~$ alsamixer
*** PULSEAUDIO: Unable to connect: Connection refused
alsamixer: function snd_ctl_open failed for default: Connection refused

Now that I look at the reply I see PulseAudio. Does that mean I still have it? It's also a choice in the Pref > Sound > Devices options.

Thanks for the help.

---

### Post by Ranjan_Hegde on 2008-12-25
I am trying to use Audacity /sound recorder to record streaming audio. Audacity has a number of options available for playback and recording and I am not sure which one to use. None of them seem to work - Audacity can not see anything playing.  Under audio devices, I have the following.
Any help is greatly appreciated



Device ID: 0
Device name: OSS: /dev/dsp
Input channels: 16
Output channels: 16
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
8000
9600
11025
12000
15000
16000
22050
24000
32000
44100
48000
88200
96000
192000
==============================
Device ID: 1
Device name: ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 (hw:0,0)
Input channels: 2
Output channels: 2
Low Input Latency: 0.011610
Low Output Latency: 0.011610
High Input Latency: 0.046440
High Output Latency: 0.046440
Supported Rates:
8000
11025
16000
22050
32000
44100
48000
==============================
Device ID: 2
Device name: ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC ADC (hw:0,1)
Input channels: 2
Output channels: 0
Low Input Latency: 0.010667
Low Output Latency: -1.000000
High Input Latency: 0.042667
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 3
Device name: ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - MIC2 ADC (hw:0,2)
Input channels: 2
Output channels: 0
Low Input Latency: 0.010667
Low Output Latency: -1.000000
High Input Latency: 0.042667
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 4
Device name: ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - ADC2 (hw:0,3)
Input channels: 2
Output channels: 0
Low Input Latency: 0.010667
Low Output Latency: -1.000000
High Input Latency: 0.042667
High Output Latency: -1.000000
Supported Rates:
==============================
Device ID: 5
Device name: ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - IEC958 (hw:0,4)
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.010667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
48000
==============================
Device ID: 6
Device name: ALSA: front
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.011610
High Input Latency: -1.000000
High Output Latency: 0.046440
Supported Rates:
8000
11025
16000
22050
32000
44100
48000
==============================
Device ID: 7
Device name: ALSA: iec958
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.010667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
48000
==============================
Device ID: 8
Device name: ALSA: spdif
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.010667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
48000
==============================
Device ID: 9
Device name: ALSA: dmix
Input channels: 0
Output channels: 2
Low Input Latency: -1.000000
Low Output Latency: 0.042667
High Input Latency: -1.000000
High Output Latency: 0.042667
Supported Rates:
48000
==============================
Selected capture device: 1 - ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 (hw:0,0)
Selected playback device: 5 - ALSA: Intel 82801DB-ICH4: Intel 82801DB-ICH4 - IEC958 (hw:0,4)
Supported Rates: 48000

---

### Post by mr_niceguy on 2009-01-10
> **fredfelter said:**
> A couple more bits of data re: my setup:

1) Volume Control: Sound Fusion CS46xx (Alsa mixer). Is that referring to the Gnome Alsamixer?
2) Sound & Video > Sound Recorder > "Your audio capture settings are invalid. Correct in Multimedia Settings (whatever that is).
3) Preferences > Sound > Devices > the only tests that return a sound are Autodetect and OSS. The ALSA option does not.

Thanks for any help.

I had the same problem. I cannot say whether this is the best way to deal with it but I was able to get things working with the following:

Preferences > Sound > Devices

Under "Default Mixer Tracks" I selected the OSS option and then made sure Audacity was using OSS as well (under Edit > Preferences) and it started recording in stereo. I was also able to adjust the capture input level using alsamixer from the command line and tabbing to the [capture] level setting.

---


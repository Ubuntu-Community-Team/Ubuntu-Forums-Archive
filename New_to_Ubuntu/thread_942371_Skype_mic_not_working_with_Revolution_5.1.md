---
title: "Skype mic not working with Revolution 5.1"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by kuproverto on 2008-10-09
I have Skype v2.0.0.72-1 which was installed through Synaptic. My sound card is a Revolution 5.1. In Sound Preferences the three Sound playback drop downs are set to Autodetect, Sound Capture is set to Test Sound and the Default Mixer Tracks Device is the M Audio Revolution-5.1(Alsa mixer)

In | Skype | Options Sound Devices I can hear the test sound but when making a test call my voice isn't recorded. All the devices are listed as Default.

I've read various posts here in the forum and now I'm more confused. What is PulseAudio? Should I use it with this card? Does anyone have Skype working with this card?

---

### Post by arochester on 2008-10-09
I found that I had to change Sound In Sound Out and Ringing to the option with "HW" in it.

---

### Post by rick08 on 2008-10-09
You either need to change your mic volume and turn it all the way up or you have driver issues.

---

### Post by Bölvaður on 2008-10-09
System &#8594; Preferences &#8594; Sounds

Turn audio confrence (4rth and 5th option) to your device (probably alsa or even pulse audio).

I am not familiar to skype so when I go home tonight where I have headset and such, I'll check it out and try help. I wouldnt belief it is a driver problem just yet.

---

### Post by kuproverto on 2008-10-09
> I found that I had to change Sound In Sound Out and Ringing to the option with "HW" in it.

Thanks but that didn't work.

> You either need to change your mic volume and turn it all the way up or you have driver issues.

Again, thanks but that didn't work either.

> Turn audio confrence (4rth and 5th option) to your device (probably alsa or even pulse audio).

Thanks but neither ALSA or Pulse worked.

Any more ideas anyone?

---

### Post by markbuntu on 2008-10-09
A guide to getting Skype working with Pulseaudio is here:

[http://ubuntuforums.org/showthread.php?t=937323](http://ubuntuforums.org/showthread.php?t=937323)

For more extensive sound help, go here:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

### Post by kuproverto on 2008-10-09
Thanks but I'm still having problems. I've detailed them in my reply to your [other post]("http://ubuntuforums.org/showthread.php?p=5938613#post5938613")

---


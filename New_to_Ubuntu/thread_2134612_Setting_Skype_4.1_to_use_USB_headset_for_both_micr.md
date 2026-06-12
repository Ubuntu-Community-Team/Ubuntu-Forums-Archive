---
title: "Setting Skype 4.1 to use USB headset for both microphone &amp; speakers"
date: 2013-04-11
forum: New to Ubuntu
---

### Post by mdavis1231 on 2013-04-11
Recently I reinstalled my Ubuntu 12.04 LTS.  Before, I had fixed it to where PulseAudio did not "autospawn" at startup, and had created 2 launchers under "Sound" that would turn PulseAudio on when I wanted to watch a DVD in Totem (apparently for some reason Totem now requires PulseAudio to play DVD's in 12.04 LTS).  OK, then I started trying to figure out how to delay the spawning of PulseAudio at startup until AFTER Skype had loaded (which I had using ALSA and had everything set individually).  PulseAudio did go ahead and autospawn even after I appended "X-GNOME-Autostart-Delay=60" to the end of 'pulseaudio.desktop' (I never did figure out how to delay it), but Skype 4.1 seemed to automatically recognize my USB headset, and everything was miraculously working as it should!  Skype 4.1 was using my USB headset for microphone & speakers on calls, and all other sounds (login, logout, ringing) were playing through my computer speakers!  This was great!  I thought the problem was solved.  Now, for some reason, when I make a test call, Skype is only using my USB headset for microphone, but is NOT using my USB headset speakers to play the voice on the other end of the call.  How do I reset this to work as it was doing before without the whole "autospawn=no" thing, and having to turn PulseAudio on and off to play DVD's?  Or is there a way to delay PulseAudio from starting until AFTER Skype 4.1 has loaded?  HELP!!!

---

### Post by ajgreeny on 2013-04-11
I use xfce (xubuntu 12.04) but in that DE the command to start pulseaudio in the session autostart list is ```
start-pulseaudio-x11
``` It should therefore be possible to delay the start of pulseaudio with the use of **sleep** before the command.

You will probably need a compound command to do this, so try ```
bash -c "sleep 60; start-pulseaudio-x11"
``` the "60" being the number of seconds pause.

And good luck!

---

### Post by kostkon on 2013-04-11
> **mdavis1231 said:**
> Recently I reinstalled my Ubuntu 12.04 LTS.  Before, I had fixed it to where PulseAudio did not "autospawn" at startup, and had created 2 launchers under "Sound" that would turn PulseAudio on when I wanted to watch a DVD in Totem (apparently for some reason Totem now requires PulseAudio to play DVD's in 12.04 LTS).  OK, then I started trying to figure out how to delay the spawning of PulseAudio at startup until AFTER Skype had loaded (which I had using ALSA and had everything set individually).  PulseAudio did go ahead and autospawn even after I appended "X-GNOME-Autostart-Delay=60" to the end of 'pulseaudio.desktop' (I never did figure out how to delay it), but Skype 4.1 seemed to automatically recognize my USB headset, and everything was miraculously working as it should!  Skype 4.1 was using my USB headset for microphone & speakers on calls, and all other sounds (login, logout, ringing) were playing through my computer speakers!  This was great!  I thought the problem was solved.  Now, for some reason, when I make a test call, Skype is only using my USB headset for microphone, but is NOT using my USB headset speakers to play the voice on the other end of the call.  How do I reset this to work as it was doing before without the whole "autospawn=no" thing, and having to turn PulseAudio on and off to play DVD's?  Or is there a way to delay PulseAudio from starting until AFTER Skype 4.1 has loaded?  HELP!!!
All these were unnecessary, PulseAudio works just fine with Skype.

You only need to install the PulseAudio Volume Control (pavucontrol) utility, then start Skype and set a input and a output device specifically for Skype in pavucontrol (you might need to start a call beforehand). PulseAudio will remember your choice.

Thus, Skype audio will be send to your USB headset and all other sounds will play on your speakers and all will be fine and you happy.

Hope that helps.

---

### Post by gerowen on 2013-04-11
Set Skype to use Pulseaudio for both input and output.

Right click the volume icon in your system tray.

In the "Output" tab, select the headphones.

In the "Input" tab, select the headphones.

Do a test call, all should function normally.  This is all I have to do in 12.10, and if I remember correctly, it's exactly what I did in 12.04 as well.

---

### Post by mdavis1231 on 2013-04-28
The problem seems to have corrected itself.  I reinstalled Skype, and it actually detected my USB headset itself.  Now calls are going through my headset, and everything else is heard through the computer speakers.  Thanks everyone!

---

### Post by mdavis1231 on 2013-08-09
> **kostkon said:**
> All these were unnecessary, PulseAudio works just fine with Skype.

You only need to install the PulseAudio Volume Control (pavucontrol) utility, then start Skype and set a input and a output device specifically for Skype in pavucontrol (you might need to start a call beforehand). PulseAudio will remember your choice.

Thus, Skype audio will be send to your USB headset and all other sounds will play on your speakers and all will be fine and you happy.

Hope that helps.

Thanks!  After all these years using Ubuntu, I've finally learned how to use pavucontrol. =D>

---


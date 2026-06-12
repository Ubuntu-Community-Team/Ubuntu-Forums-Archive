---
title: "multimedia- skype can't record my voice"
date: 2015-12-18
forum: New to Ubuntu
---

### Post by houmingc on 2015-12-18
I just install skype into ubuntu.
In skype, under Options>Sound Devices>Open PulseAudio Volume Control>Input Devices>Port: Analogue input.
When i speak, i can see the GUI bar moving indicating audio input is working.

But when i call Echo/Sound Test Service in Skype, i am not able to record my voice.

Do i need to install some utilities into ubuntu.

---

### Post by ian-weisser on 2015-12-18
No, you don't need an additional utility.

Your Skype options don't match mine. I'm running Skype 4.3.0.37 under Ubuntu 15.10.
I don't have a 'Open PulseAudioVolume Control' within the Skype options.

I have Options --> Sound Devices  --> Microphone, and it's set to 'PulseAudio server (local)'
Pulse passes the real input to Skype. That's Pulse's job.

---

### Post by houmingc on 2015-12-19
I have Options --> Sound Devices  --> Microphone, and it's set to 'PulseAudio server (local)' too.
When i make a call oversea, the other party cannot hear my voice and i could hear the other party voice.

---

### Post by ian-weisser on 2015-12-19
One assumes you cannot hear you voice whenyou use the Skype test call?

If so, System Settings --> Audio --> Input Tab will display your audio inputs.
One of those should be the Microphone. Select it.
If Microphone is not an option, twll us what the options are.

---

### Post by houmingc on 2015-12-20
From System Setting>audio.
In input tab, there is two Sound  record Microphone(build-in Audio) and Analogue Input(build-in Audio).  When i voice up, i can see the input level moving. Thus indicating audio  input is working for both microphone and analogue input.
But when i use echo/sound test service, but there is no voice recorded.
Is there a ubuntu apps for recording, i could use to test?

Seems like system recording is working, but not skype recording.

---

### Post by ian-weisser on 2015-12-20
Lots of Ubuntu applications record audio.
arecord (shell only) is part of the default install of Ubuntu. See man arecord.
Many others (shell and GUI) are just one click aeay in Software Center.

---


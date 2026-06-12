---
title: "Firefox hogging soundcard"
date: 2008-05-25
forum: New to Ubuntu
---

### Post by dwally89 on 2008-05-25
Hi,

I'm running Hardy with Firefox, and whenever I have Firefox open, any other program can't play sound.

For example, if I have Firefox open and I try and play a song in Songbird, nothing happens, and its not a problem with Songbird as when I close Firefox, and restart Songbird, it works fine.

The same thing happens with Totem.

Does anyone know what the problem is here and how to solve it, as its extremely annoying having to close Firefox in order to listen to music.

Thanks

---

### Post by OoooMatron on 2008-05-25
i think its the puslse audio crap. uninstall it and use the alsa and it should be ok.

---

### Post by dwally89 on 2008-05-25
Is there no way to do solve the problem whilst still keep pulseaudio?

---

### Post by Bakon Jarser on 2008-05-25
There is a way.  Follow part A of this guide.  I'd only follow part A if I were you though.

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by dwally89 on 2008-05-25
Worked like a charm!

Thanks :-)

---

### Post by dwally89 on 2008-05-26
Just noticed, every application has sound now APART from Firefox.

How can I get the sound back into Firefox?

Thanks

---

### Post by Bakon Jarser on 2008-05-26
Is everything in firefox missing sound or just flash?  If it's a flash problem uninstalling it completely and installing the version on adobes website might fix it.  The solution in the guide I posted earlier is to install flash 10 beta.  Unfortunately flash 10 didn't allow me to view videos at BBC or go fullscreen at cbs.  youtube and several other sites I tried worked fine though.

---

### Post by dwally89 on 2008-05-26
I'm considering completely getting rid of Pulseaudio, as I can't see any advantages of it, and it only seems to be causing problems since I've had it.

How can I get rid of it?

Thanks

---

### Post by Bakon Jarser on 2008-05-26
> **dwally89 said:**
> I'm considering completely getting rid of Pulseaudio, as I can't see any advantages of it, and it only seems to be causing problems since I've had it.

How can I get rid of it?

Thanks

a kernel upgrade just got pushed out with some pulse audio fixes.  Did it help at all?

---

### Post by dwally89 on 2008-05-26
I got the upgrade, but haven't restarted yet.

I'll report back tomorrow.

---

### Post by dwally89 on 2008-05-27
OK after a reboot I still didn't have sound in Firefox, so I reversed the steps from [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578), which took me back to my initial state (only being able to have one program play sound at once), and I have now selected ALSA in System>Preferences>Control Centre>Sound Preferences, and everything works.

Could someone please explain to me the advantages of PulseAudio, because all it seems to cause is trouble...

Thanks

---

### Post by Bakon Jarser on 2008-05-27
From there web page:

> What Is PulseAudio?

PulseAudio is a sound server for POSIX and Win32 systems. A sound server is basically a proxy for your sound applications. It allows you to do advanced operations on your sound data as it passes between your application and your hardware. Things like transferring the audio to a different machine, changing the sample format or channel count and mixing several sounds into one are easily achieved using a sound server. 

Basically what it sounds like is that it performs a man in the middle attack on the audio streams for programs so that they can't take sole possesion of the sound card and also so that you can manipulate the audio stream if you want.  It actually sounds like cool stuff and I think will be a great addition once it's mature.  Right now it just seems to be causing a lot of headaches.

---


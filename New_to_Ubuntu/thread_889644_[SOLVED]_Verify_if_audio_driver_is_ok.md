---
title: "[SOLVED] Verify if audio driver is ok ?"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2008-08-14
Hi
I tried to record my voice (with mic) with SoundRecorder, but didn't work.  How can I verify the audio driver is installed correctly ?

Thanks

---

### Post by mikeyphi on 2008-08-14
> **Pierrot Lafouine said:**
> Hi
I tried to record my voice (with mic) with SoundRecorder, but didn't work.  How can I verify the audio driver is installed correctly ?

Thanks

Have you used the System/Preferences/Sound GUI to select the correct audio capture/playback, you can also use that GUI to test whether your choice is working.

Repost if that doesn't help!

---

### Post by Pierrot Lafouine on 2008-08-14
Hi
I tried to record with Applications/Sound&Video/Sound Recorder, but doesn`t work.
I tried all inputs :
+Front Mic Boost (what is this ?)
+Mic Boost (what is this ?)
+IEC958
+ Capture
+ Capture1
+ Capture2
+ Digital

I tried the GUI things:System/Preferences/Sound
All Test buttons worked fine, except Sound capture.  A DialogBox show this messages : 
***Failed to construct test pipeline for 'gconfaudiosrc! audioconvertert ! audioresample ! gconfaudiosink prfile = chat'***

What is the next step to debug this ?

---

### Post by Pierrot Lafouine on 2008-08-14
up

---

### Post by Pierrot Lafouine on 2008-08-14
up

---

### Post by Pierrot Lafouine on 2008-08-14
Anything I can try ?
Thanks

---

### Post by nicedude on 2008-08-15
You could check and make sure it isn't a pesky alsamixer setting ( don't know why but there are more than one set of volume controls )

command to open the console and see if you have mic turned on
sudo alsamixer


If that isn't it I don't know

---

### Post by Pierrot Lafouine on 2008-08-15
huumm, according to the text application (sudo alsamixer),
mic's volume are turned off.
How do I turn them on ?

Thanks

---

### Post by nothingspecial on 2008-08-15
You navigate through alsamixer using the arrow keys and mute/unmute channels using the m key.

---

### Post by Pierrot Lafouine on 2008-08-16
Thnaks, it solved my problems,
I'm now able to record my voice

---

### Post by Pierrot Lafouine on 2008-08-16
Thanks, it solved my problems,
I'm now able to record my voice

---

### Post by nothingspecial on 2008-08-16
Glad to here it.
Will your mark yhis thread solved please.

---


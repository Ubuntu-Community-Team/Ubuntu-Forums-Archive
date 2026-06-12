---
title: "Audacity only as root"
date: 2012-03-03
forum: New to Ubuntu
---

### Post by jimwill on 2012-03-03
I recently installed Trinity Kubuntu 10.10 amd64. When trying to use Audacity I found I could only use it as root! I have created a shortcut of "kdesudo audacity" but that exports everything as root ownership and I have to change owner and permissions to use the audio in other applications. I edit audio files daily and this gets to be rather time consuming! 
If I run audacity as a user it starts ok, but when trying to load an audio it shuts down!
"audacity
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
bt_audio_service_open: connect() failed: Connection refused (111)
Expression 'stream->capture.pcm' failed in 'src/hostapi/alsa/pa_linux_alsa.c', line: 3653
Segmentation fault
"
Is this a known bug in audacity 1.3.12-beta ? I have searched here and on the web and can't find anything. Does anyone here have a fix for this?

---

### Post by TheFu on 2012-03-03
Sorry, I don't know the answer, but perhaps this will help you figure it out.

I suspect the issue is a permissions problem on audio/dsp devices in /dev.  I think your account needs to be added to 1 or more groups based on the ownership of those devices in /dev/.

On my Ubuntu system, the group name is "audio" and it is used for /dev/audio, /dev/dsp, /dev/adsp,/dev/mixer, and /dev/sequencer*

On my system, I am not a member of the "audio" group, but "pulse" is.  Audio does work for me.
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems) and
[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) may help.

Sorry I didn't have an answer.

---

### Post by jimwill on 2012-03-03
Thanks [TheFu]("http://ubuntuforums.org/member.php?u=1037685"), but that didn't work. I added myself as members of audio and pulse groups but still get the same crash. Tried to change the 'interface' in audacity from ALSA but it is the only selection. However, after adding the groups I can now open audacity as a user, just can't export.

---

### Post by codemaniac on 2012-03-04
Have you tried checking the permissions on audacity binary .

```
ls -l /path to audacity binary/
```

If executable bits are off for a normal user , please turn them on.

Cheers

---

### Post by jimwill on 2012-03-04
> **codemaniac said:**
> Have you tried checking the permissions on audacity binary .

```
ls -l /path to audacity binary/
```If executable bits are off for a normal user , please turn them on.

Cheers

-rwxr-xr-x  1 root   root    7370432 2010-09-21 23:22 audacity

That doesn't seem to be the problem either. But thanks for having me check it!!!
(unless I'm reading the permissions incorrectly!)

---


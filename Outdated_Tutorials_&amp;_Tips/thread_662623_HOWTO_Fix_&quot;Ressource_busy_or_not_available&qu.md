---
title: "HOWTO: Fix &quot;Ressource busy or not available&quot;"
date: 2008-01-09
forum: Outdated Tutorials &amp; Tips
---

### Post by Munksgaard on 2008-01-09
**Symptoms:**
[LIST]
[*]Sound disappears
[*]Sound Preferences say something like: > audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Ressource busy or not available when you try to test the sound devices
[/LIST]

**Problem**
An unknown process is taking up the sound devices.

**Solution**
*It is assumed that the default sound device is ALSA. This can be set in the Sound Preferences.*

You have to find out what resource is using the sound device. As ALSA uses the /dev/snd/* device to play music, we can use a handy little tool to examine the cause of the problem.

Now, open a terminal, and type in:
```
lsof | grep snd
```
You should get something like this:
```
mixer_app  5572     philip   19u      CHR      116,6             14027 /dev/snd/controlC0
soffice.b  9727     philip  mem       REG        8,1   357520  6148653 /usr/lib/libsndfile.so.1.0.17
firefox-b 16410     philip  mem       CHR      116,4             13999 /dev/snd/pcmC0D0p
firefox-b 16410     philip   58r      CHR      116,2             13788 /dev/snd/timer
firefox-b 16410     philip   59u      CHR      116,4             13999 /dev/snd/pcmC0D0p
firefox-b 16410     philip   60u      CHR      116,6             14027 /dev/snd/controlC0
```

Now, we can see that firefox-b(in) is using /dev/snd/pcmC0D0p, which is the main sound output card. soffice.b and mixer_app are only using control files, and are thus not a problem. Supposing firefox-bin is locking up the sound device, all we have to do is to kill the program. This could be done either by typing:
```
killall firefox-bin
```
or, as we know the pid of the particular app, we can close that specific instance of firefox:
```
kill 16410 
```
Or we could be more persistent and kill it with -9:
```
kill -9 16410
```

Firefox won't always be the source of the problem, in my case I had problems with bittornado, but this will enable you to find the source of the problem and kill it.
That way you won't have to reboot every time you loose sound.

**Further reading on the subject and lsof::**
[http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25/]("http://linux.dsplabs.com.au/lsof-grep-snd-how-to-free-a-linux-sound-device-p25/")

---

### Post by Jacek.Mendinka on 2008-12-18
Hi,

somewhere in the ubuntu forums I found the following script which helps me identifying which process is blocking the audio device:

code:
```

jroks@ubuntu:~$ sudo fuser -v /dev/dsp /dev/sequencer /dev/sequencer2 /dev/snd/controlC0 /dev/snd/hwC0D0 /dev/snd/hwC0D1 /dev/snd/pcmC0D0c /dev/snd/pcmC0D0p /dev/snd/seq /dev/snd/timer
                     USER        PID ACCESS COMMAND
/dev/snd/controlC0:  joe        6942 F.... kmix
/dev/snd/pcmC0D0p:   joe        7053 F.... firefox-bin

```

HTH, greetings
Jacek

---


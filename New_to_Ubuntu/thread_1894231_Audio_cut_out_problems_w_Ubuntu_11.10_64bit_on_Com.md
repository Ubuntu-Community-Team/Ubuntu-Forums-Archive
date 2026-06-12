---
title: "Audio cut out problems w/ Ubuntu 11.10 64bit on Compaq Presario CQ62"
date: 2011-12-12
forum: New to Ubuntu
---

### Post by Ego Death on 2011-12-12
Hey guys, I did a fresh install of Ubuntu 11.10 64bit yesterday from Ubuntu 10.xx 64bit.

I've noticed that my audio cuts system wide after using either webcam or Firefox (youtube/flash).

I was wondering if there the was a way I could easily view the daemon process to reset it without a reboot.

---

### Post by Lisiano on 2011-12-12
To restart ALSA (Advanced Linux Sound
Architecture - what loads the audio drivers and controls your soundcard) it is enough to type this
```
sudo service alsa reload
``` or use this if it refuses to reload ```
sudo service alsa force-reload
```

Now if you just want to restart Pulseaudio (What manages the application sounds and tells ALSA on which soundcard to play the sound) it is usually enough to just kill pulseaudio. ```
killall -9 pulse
``` Note: I'm on my phone and the commands are on top of my head

---

### Post by davethewave83 on 2011-12-22
> **Lisiano said:**
> To restart ALSA (Advanced Linux Sound
Architecture - what loads the audio drivers and controls your soundcard) it is enough to type this
```
sudo service alsa reload
``` or use this if it refuses to reload ```
sudo service alsa force-reload
```

Now if you just want to restart Pulseaudio (What manages the application sounds and tells ALSA on which soundcard to play the sound) it is usually enough to just kill pulseaudio. ```
killall -9 pulse
``` Note: I'm on my phone and the commands are on top of my head

~$ killall -9 pulse
pulse: no process found
~$ sudo service alsa reload
alsa: unrecognized service
~$ sudo service alsa force-reload
alsa: unrecognized service
~$ killall -9 alsa
alsa: no process found

??

---

### Post by rybu on 2012-01-22
> **davethewave83 said:**
> ~$ killall -9 pulse
pulse: no process found
~$ sudo service alsa reload
alsa: unrecognized service
~$ sudo service alsa force-reload
alsa: unrecognized service
~$ killall -9 alsa
alsa: no process found

??

I have what appears to be the same problem.  It started with an Ubuntu update maybe 3 weeks ago.  Now the sound lasts for the first 5-10 minutes of uptime, but then it goes completely silent.  I get the same "unrecognized service" notices, above.

Here's my similar but unresolved thread: [http://ubuntuforums.org/showthread.php?t=1915782](http://ubuntuforums.org/showthread.php?t=1915782)

---


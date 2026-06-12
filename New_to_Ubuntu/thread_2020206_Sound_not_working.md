---
title: "Sound not working"
date: 2012-07-07
forum: New to Ubuntu
---

### Post by Jeroen300 on 2012-07-07
Hello everybody, I did the following:

Used ubuntu12.04mini-iso. After the baresystem was installed i did the following: sudo apt-get install xinit xorg xterm chromium-browser gksu synaptic. Pulseaudio and alsa-base are installed, I also installed xubuntu restricted extras. 

My problem is that I don't get sound.
Does anybody know if I should instaal something extra or do something to get the sound working?

On the same system xubuntu installation did have working sound.

Thanks for any relpy!

Greetings Jeroen

---

### Post by AlbertJB on 2012-07-08
And the hardware? ie. Do you use HDMI? .. I had problems with the cable for instance..

---

### Post by Jeroen300 on 2012-07-08
Hardware shouldn't be a problem I'm using virtualbox for this tryout for now. I've also checked mini-iso with md5, its fine. Im at a loss, Thanks for reacting!

---

### Post by Merrattic on 2012-07-08
Install alsa-utils then open up alsamixer and see what is muted?

Also check "lsmod" for sound drivers loaded, and report back on the output of "aplay -l"

---

### Post by mastablasta on 2012-07-08
have you seen the torubleshooting guides?: [http://ubuntuforums.org/showthread.php?t=1885240](http://ubuntuforums.org/showthread.php?t=1885240)

---

### Post by Jeroen300 on 2012-07-08
@ Merratic

Alsamixer is not muted but it seems there is no soundcard according to aplay -l see screenshot attachment. Some further help would be very much appreceated! Since I'm quite new at this I don't know what to look for.

---

### Post by Jeroen300 on 2012-07-08
@ Mastablasta

I've been looking for some sort of guide for quite some time, thanks! Going to see where it gets me.

---

### Post by Jeroen300 on 2012-09-22
To everybody who is reading this, The solution of the problem is very simple. Since I didn't install a complete system but builded it up myself, my user wasn't added to the audio-group. I managed it by sudo usermod -a -G audio username. Thanks everybody who reacted and to anybody reading this, I hope it helps!

Greetings

---


---
title: "no sound?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by Maximusmaximus on 2008-11-15
i have been having problems with sound software. i use the ALSA program that comes with ubuntu. i have tried many things to fix it by looking on the web and i cannot find anything. (link to an old thread would be cool)

im not entirely sure what all of this means, but i defiantly  get no sound through any program. (volume control still stays on menu bar)

max@kev-desktop:~$ alsa mixer
Usage: /sbin/alsa {unload|reload|force-unload|force-reload|suspend|resume}
max@kev-desktop:~$ /sbin/alsa force-reload
Terminating processes: 5936 7064.
mkdir: cannot create directory `/var/run/alsa': Permission denied
/sbin/alsa: Warning: Failed to create /var/run/alsa/. 
/sbin/alsa: Warning: Not keeping list of removed modules because /var/run/alsa is absent.
It will not be possible automatically to reload these modules. 
Unloading ALSA sound driver modules:/sbin/alsa: 219: cannot create /var/run/alsa/modules-removed: Directory nonexistent
 snd-rtctimer snd-emu10k1-synth snd-emux-synth snd-seq-virmidi snd-seq-midi-emul snd-emu10k1 snd-hda-intel snd-ac97-codec snd-pcm-oss snd-seq-dummy snd-mixer-oss snd-seq-oss snd-seq-midi snd-pcm snd-rawmidi snd-page-alloc snd-util-mem snd-seq-midi-event snd-hwdep snd-seq snd-timer snd-seq-device.
mkdir: cannot create directory `/var/run/alsa': Permission denied
Loading ALSA sound driver modules: (none to reload).
max@kev-desktop:~$ 



thanks in advance to all who can help

---

### Post by shredder12 on 2008-11-15
well you are doing things slightly wrong..
first of all it is "alsamixer" and not "alsa mixer" ..
so try to run like this...and tell what are you getting..

---

### Post by Joe Schmoe_10 on 2008-11-15
Did you uncheck external amplifier in settings? I had the same problem last week. Settings > Settings Manager > Sound ... just scroll down to the bottom and uncheck the box.

---

### Post by Maximusmaximus on 2008-11-15
> **Joe Schmoe_10 said:**
> Did you uncheck external amplifier in settings? I had the same problem last week. Settings > Settings Manager > Sound ... just scroll down to the bottom and uncheck the box.

you using gnome? i can't find it

---

### Post by Maximusmaximus on 2008-11-15
> **shredder12 said:**
> well you are doing things slightly wrong..
first of all it is "alsamixer" and not "alsa mixer" ..
so try to run like this...and tell what are you getting..

still nothing silly wiki page told me to do it that way and i turned all the volumes up full (accept for mic settings) and i stil lget nothign through all the programs i try

(sorry for double post)

---

### Post by shredder12 on 2008-11-15
well then may be you should try changing setting and testing for different options in your sound preferences.. system->preferences->sound
try some other settings instead of alsa and press the test button..if you are getting a beep sound..then its alright..otherwise we will figure out some other way..
well till then jst try these..

---

### Post by Maximusmaximus on 2008-11-15
well i went into the sound settings and i slicked test for sound events and under auto detect clicked test it chugged out and finally came around with no sound. i then went to the ALSA option and there was no chugging and still no sound same for the music and movies and audio conferencing sections and my default mixer tracks is "SB live 5.1 (Alsa Mixer)"

---

### Post by shredder12 on 2008-11-15
well i suppose you might not even be getting the system sounds at the time of logging on and logging off..
have you tried some other options other than..alsa and autodetect.. don't you have OSS or something like that..and try changing your mixer tracks too..many a times problem lies in these configurations..though it seems to be hectic..but it at least make sures that the problem is not with the configuration..
so try all of them if you haven't yet??

---

### Post by Maximusmaximus on 2008-11-15
i tried all of the individual settings and i got to a thing called  multi channel play back, it was the only one i got a beep from but it was very very feint and i still get no response from any other programs, also before posting this thread i did the comprehensive guide and gutted everything and it still does not work

---

### Post by shredder12 on 2008-11-15
well then i think it could be a problem with the sound drivers..can you post the output of following command: 
```
lspci
```
Well there is one more way to solve your problem if its really related to drivers..i think you should try installing the drivers provided by your computer manufacturer..in the form of a cd...there you might find a folder for linux drivers..if he has provided you with them then try installing them and see whether things work out or not...It's really hard to say this...but you may even need to try configuring the sound settings once again..
this is how we have to work out things sometimes..

---

### Post by kansasnoob on 2008-11-15
I always start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

But if this is Hardy or Intrepid you'll probably find this helpful:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by Eisenwinter on 2008-11-15
Post the output of the command:
```
asoundconf list
```

---

### Post by Maximusmaximus on 2008-11-17
> **kansasnoob said:**
> I always start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

But if this is Hardy or Intrepid you'll probably find this helpful:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

had a look there and it did not solve it

---

### Post by alwayshere on 2008-11-17
i sent this to a mate last night and i heard a few hours ago that it worked for him 

 This might sort ya sound

 sudo killall pulseaudio
 
then


 sudo alsa force-reload

 and then go to System>Preferences>Sound and change everything to ALSA

if ya get no sound try a restart and see how that goes

---


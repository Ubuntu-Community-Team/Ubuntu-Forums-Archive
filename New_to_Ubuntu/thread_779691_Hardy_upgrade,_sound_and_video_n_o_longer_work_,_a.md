---
title: "Hardy upgrade, sound and video n o longer work , audiopulse"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by fuwkej on 2008-05-02
Just upgraded to Hardy Heron and everything appeared to go well except that sound and video do not work (worked great with gutsy). 

No video playback, errors were as follows: 

Totem:  Failed to connect stream: invalid argument
Mplayer:   Mplayer interupted by signal 13 in module: play_audio

No audio playback

Audio tracks just remain at 0:00


I searched the forums and found that audiopulse caused problems with other users so I shut it off and then video worked but no audio. Tried rebooting computer but it went back to the original issues.

---

### Post by riven0 on 2008-05-02
Okay, try going to Sessions and deleting the PulseAudio server, then restart Alsa: **sudo /etc/init.d/alsa-utils restart**

That worked for me.

---

### Post by fuwkej on 2008-05-03
No joy. I tried those steps and neither video or audio worked, I did like I did before after that and shutoff pulseaudio through the system monitor and then I was able to play just video. I restarted the computer to see if your step would stop pulseaudio from starting up but it still starts up and neither audio or video works.

Here is the terminal screen for the steps you suggested:

[HTML]sudo /etc/init.d/alsa-utils restart
 * Shutting down ALSA...                                                         * warning: 'alsactl store' failed with error message 'alsactl: save_state:1251: No soundcards found...'...                                              [fail] 
 * Setting up ALSA...                                                            * warning: 'alsactl restore' failed with error message 'alsactl: load_state:1327: No soundcards found...'...                                            [ OK ] 
[/HTML]

Thanks for the help though, any other ideas?

---

### Post by fuwkej on 2008-05-03
Also when trying to use alsamixer i get the following error:

[HTML]alsamixer: function snd_ctl_open failed for default: No such device
[/HTML]

---

### Post by fuwkej on 2008-05-05
Anyone?

---

### Post by fuwkej on 2008-05-07
Okay after about 6 hours of research the sound now works again, and it was not complicated, got to wonder what kind of 'upgrade' this hardy heron is. Basically all I had to do was install the most recent alsa, and unmute the hidden option of 'surround' which is apparently my main speakers.

I went through about 8 walk throughs but the one that did it was:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

which was posted by user: groovete @ the following link:
[http://ubuntuforums.org/showthread.php?t=758962](http://ubuntuforums.org/showthread.php?t=758962)


Thanks for all who helped.

---


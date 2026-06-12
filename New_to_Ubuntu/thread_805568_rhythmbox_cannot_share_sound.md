---
title: "rhythmbox cannot share sound"
date: 2008-05-24
forum: New to Ubuntu
---

### Post by philphil on 2008-05-24
Having trouble in Hardy with playing music with Rhythmbox when something else e.g. Firefox is already using the sound card. 

In this case, to get Rhythmbox to play, I have to quit Firefox (stopping the thing playing the sound is not enough e.g. closing the tab I have youtube open in), quit Rhythmbox, reload Rhythmbox then it works....Not really good enough...I thought this would be fixed with the new fancy PulseAudio shennanigans those Ubuntu guys came up with in Hardy?  As it's not been fixed then I figure the problem is with Rhythmbox?

Any suggestions? I'm all up for using a new music player if anyone can suggest a good one that'll work?

Cheers!

---

### Post by joshsmith on 2008-05-24
[http://ubuntuforums.org/showthread.php?p=5035124#post5035124](http://ubuntuforums.org/showthread.php?p=5035124#post5035124)

---

### Post by Steve413z on 2008-05-24
there is some problems with PulseAudio, the easiest solution is to just go back to ALSA
System > Preferences > Sound > Devices > change all devices to ALSA instead of autodetect or pulseaudio

8.04 is the first ubuntu version to use pulseaudio, and it's buggy, i'm gonna wait till 8.10 to start using pulseaudio

---

### Post by philphil on 2008-05-25
> **joshsmith said:**
> [http://ubuntuforums.org/showthread.php?p=5035124#post5035124](http://ubuntuforums.org/showthread.php?p=5035124#post5035124)

thanks, but that wasn't it, I already have that installed

---

### Post by philphil on 2008-05-25
> **Steve413z said:**
> there is some problems with PulseAudio, the easiest solution is to just go back to ALSA
System > Preferences > Sound > Devices > change all devices to ALSA instead of autodetect or pulseaudio

8.04 is the first ubuntu version to use pulseaudio, and it's buggy, i'm gonna wait till 8.10 to start using pulseaudio

ah ok thanks for that, I'll try it when I get home

Edit:  awesome, that fixed it, thanks a lot!

---

### Post by Steve413z on 2008-07-26
OK...

now I found out the *CORRECT* way to solve this problem, besides just going back to ALSA


```

sudo apt-get install libflashsupport
```

---


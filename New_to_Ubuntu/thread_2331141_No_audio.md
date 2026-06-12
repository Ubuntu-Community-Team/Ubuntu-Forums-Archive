---
title: "No audio"
date: 2016-07-19
forum: New to Ubuntu
---

### Post by acomoon on 2016-07-19
Hello,

[COLOR=#000000]After an update and reboot, no audio comes out of my laptop anymore. I followed  instructions of sound troubleshooting in help assistance and it seems my laptop doesn't recognize the sound card inside and is driverless (even when it has sounds modules installed).  [/COLOR][COLOR=#000000] 

I have no idea what happened, before updating and rebooting, sound was fine and functional. I've tried some solutions found on internet, but no succeed. I use Ubuntu 14.04LTS[/COLOR]

[COLOR=#000000]Here are some hardware specifications:
[/COLOR][INDENT][COLOR=#000000]
[/COLOR][/INDENT]
00:1f.3 Audio device [0403]: Intel Corporation Device [8086:9d70] (rev 21)
	Subsystem: Dell Device [1028:06b2]

If you need more information, please let me know... I'm a new Linux user and totally clueless (but want to learn more).

Thanks for reading,
Alejandra.-

---

### Post by michal-klekowicki on 2016-07-19
Have you tried reinstallig **ALSA** and **PulseAudio**?

Open terminal.

```
 sudo apt-get remove --purge alsa-base pulseaudio
```

then:

```
sudo apt-get install alsa-base pulseaudio
```

and finaly:

```
sudo alsa force-reload
```

---

### Post by acomoon on 2016-07-19
It didn't work, now I'm concerned about what i did with instructions that was given... 

How can I change what I did? Configuration settings changed,:confused:

---

### Post by michal-klekowicki on 2016-07-19
> **acomoon said:**
> It didn't work, now I'm concerned about what i did with instructions that was given... 

How can I change what I did? Configuration settings changed,:confused:


Could you elaborate? Executing the above code reinstalled the modules and thus reseted the config - is that what are you refering to?

(Try to reboot the computer after install by the way :) )

---

### Post by acomoon on 2016-07-19
Sound settings were vanished from the general settings, (with others hardware's settings) no longer sound icon  in Ubuntu's desktop neither, after executing the coding above (and then I reboot)

I bought my laptop with Ubuntu pre-installed, now i'm trying to restore system to the factory shipped state ... :(

---

### Post by &amp;KyT$0P# on 2016-07-19
> **michal-klekowicki said:**
> Open terminal.

```
 sudo apt-get remove --purge alsa-base pulseaudio
```

then:

```
sudo apt-get install alsa-base pulseaudio
```
That is dangerous way to reinstall packages, as you will left with all the other packages depending on alsa-base and pulseaudio still deinstalled.  And given the nature of those packages, you will likely be left with broken system (or at the very least, really broken audio).

This is the better way to reinstall packages:
```
sudo apt-get --purge --reinstall install alsa-base pulseaudio
```

---

### Post by acomoon on 2016-07-21
If I have problems with packages, or its dependencies... Should I use 'dpkg' coding instead? Just a doubt 

Finally, I've restored system... Not only audio were in trouble also wireless conection (there is other thread related) and I was desperate.  In the other hand, I don't understand why, after an update, audio and wifi were damaged...

---

### Post by michal-klekowicki on 2016-07-28
It depends on what exactly was updated and what happened during update. If it was something crucial, like a kernel update, and you would mistakenly reset the computer, physical disturb the hdd, and so on, it could generate serious issues like that.

This is just speculation naturally. However things like that happened to me some time ago and I believe it was related to the ongoing degradation of my damaged Hard Drive. I also heard about updates failing while using faulty RAM kits in Linux and Windows alike (but it usually also leads to the overall instability of the system).

---


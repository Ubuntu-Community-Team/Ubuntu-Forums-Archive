---
title: "HowTo: Fix /dev/dsp1"
date: 2008-12-21
forum: Outdated Tutorials &amp; Tips
---

### Post by ibuclaw on 2008-12-21
Some games, and other proprietary software (To my knowledge, the ones that use OSS) have it hard-coded in them that the default soundcard, mixer and audio devices are located in the following locations:
```

/dev/audio
/dev/dsp
/dev/mixer

```
Although, for a minor few, this isn't the case of their setup.

If, your like me, and you use an external USB Soundcard, and your onboard soundcard is turned off in BIOS. Then your default soundcards may be pointing to these locations instead:
```

/dev/audio1
/dev/dsp1
/dev/mixer1

```
To which brings up warning messages in the terminal before the game starts, and ultimately results in no sound ingame.

**FIX:**
Open up the udev rules for alsa. If you are running Jaunty, you'll need to copy the file over:
```
sudo cp /lib/udev/rules.d/85-alsa-utils.rules /etc/udev/rules.d/85-alsa.rules
```

```
gksudo gedit /etc/udev/rules.d/85-alsa.rules
```
and add the following at the bottom:
```

KERNEL=="controlC[0-9]*", ACTION=="add", \
	RUN+="/sbin/start-stop-daemon --start --background --pidfile /var/run/alsa/bogus --startas /etc/init.d/alsa-utils -- start %n"
[B]KERNEL=="dsp1", SYMLINK+="dsp"
KERNEL=="mixer1", SYMLINK+="mixer"
KERNEL=="audio1", SYMLINK+="audio"[/B]

```
Save, quit, and reboot your system.

Now when you open up the terminal and type in **ls /dev** you'll now see the symlinks audio, dsp and mixer.

And you'll finally get sound from that game you got too...

Regards
Iain

---

### Post by Pipps on 2009-02-14
Dear Learned Guru

Thank you for this brilliant advice.

However, I am sorry to report that it has not improved my problem.

I am in exactly the same position as you apepar to be, concerning USB audio. However, after adding the aforementioned lines of code to the alsa-rules file, I still do not get sound from my USB speakers, and VLC media player still directs all sound to the laptop's onboard speakers via the onboard soundcard.

The output from "#ls /dev" includes the following:```

dsp                 ptye7  ptyuc  rtc         ttyb2  ttyr7  ttyx8
dsp1                ptye8  ptyud  rtc0        ttyb3  ttyr8  ttyx9
```

What is wrong with my system? And how can it be corrected?

Thank you for your time.

---

### Post by Pipps on 2009-02-14
I found a different [solution]("http://ubuntuforums.org/showthread.php?t=442083") that works. Ubuntu may be full of bugs, but at least VLC provides a workaround to this seemingly common problem.

---


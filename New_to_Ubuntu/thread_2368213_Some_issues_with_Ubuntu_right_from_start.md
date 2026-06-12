---
title: "Some issues with Ubuntu right from start"
date: 2017-08-08
forum: New to Ubuntu
---

### Post by mislav11 on 2017-08-08
Hello. I'm new here, I hope this is the right section.
Few weeks ago, I've tried out Ubuntu and it wasn't really good.
It installed fine but however generally Sound on Linux Distributions is really awful compared to Windows.

I've googled out the issue and all of people were recommending to download pulseaudio.
That didn't help at all and made the sound sound screetchy.
My general problem with sound in Linux is the fact that even at maximum volume it's below maximum one in Windows and that's noticeable and gets annoying.
Also tried googling that earlier, the solutions said to increase some sound stuff via terminal to 100 but they were already to 100.
What really grinds my gears is that there is absolutely no good bass on Linux anywhere, not even on Ubuntu, and i simply cannot live with that.
Other issue I had in Ubuntu, i literally tried downloading Opera, and it wouldn't open at all.

I'm not here to just complain about problems, reason why I'm making this topic is I want to ask you guys is it possible to get
sound to be equally loud as it gets on Windows, and is it possible to have equally good bass when using an equalizer.
I simply cannot listen to music without bass and being not loud at same time, it's horrible, a nightmare.

Thank you for reading.

---

### Post by ajgreeny on 2017-08-08
I am pretty sure that pulseaudio is installed by default in Ubuntu and most if not all the other *ubuntu versions, except perhaps Lubuntu, but even that now has it I believe.

I am therefore wondering why you needed to install pulseaudio if you are using a recent version of Ubuntu.  You may be missing the pavucontrol package in some *ubuntu versions but I am not sure about that.

The package pavucontrol (pulseaudio volume control) gives you very detailed control of volumes for the various output devices in your system so that is the first place to start looking for a solution to the lack of volume you are experiencing.

You may also find these posts useful if you are running 17.04 in order to install an equaliser for pulseaudio though I have never needed to install it; my sound quality is already great.
[https://askubuntu.com/questions/909879/pulse-audio-equaliser-that-has-presets/910010](https://askubuntu.com/questions/909879/pulse-audio-equaliser-that-has-presets/910010)
[https://ubuntuforums.org/showthread.php?t=2358624](https://ubuntuforums.org/showthread.php?t=2358624)

---

### Post by mastablasta on 2017-08-08
also for some reason you are assuming we all know what your hardware and software configuration is as well as what modules were loaded and such.

have a look here: [https://ubuntuforums.org/showthread.php?t=1422475](https://ubuntuforums.org/showthread.php?t=1422475)

---

### Post by mislav11 on 2017-08-09
I don't know if pulseaudio comes preinstalled on Ubuntu but nontheless sound wasn't as good as on Windows which is sad.
Which hardware configuration do i need to give? I didn't install anything i just had Ubuntu installed and that's all, didn't download any modules or anything like that

---

### Post by mastablasta on 2017-08-09
what is the sound chip you are using? have you checked dmesg log for any error messages? what about kernel log? (you can use a log viewer for these or open them at /var/log)

stuff you tried in terminal - was it alsamixer?

---


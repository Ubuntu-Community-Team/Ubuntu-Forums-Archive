---
title: "Audacity is sick. . ."
date: 2008-10-08
forum: New to Ubuntu
---

### Post by pi.boy.travis on 2008-10-08
Hi!  I have been using Audacity for a while with no problems.  Recently when I started it, it took about 30 seconds to start.  This is unusual, as I have a very modern machine.  After it starts, performing any action takes extremely long.  It often freezes, and if I try to kill the audacity process, it becomes a zombie process.  To top it all off, I can't play back or record anything.  I get an error message telling me that Audacity doesn't recognize any sound devices.  I can play back and record with any other program, and all my sound devices show up in the settings dialog.

I am using a Dell Inspiron 1520 running Ubuntu 8.04 (I haven't tried this yet on my 8.10 beta partition yet, and I will report back when I do)

Any ideas?  I have only installed updates since the last time I used it.  I am using whatever version is in the repositories, 1.3.4 beta I think. . . 

Thanks in advance!

---

### Post by mc4man on 2008-10-08
You may want to try going to home folder -> .audacity-data and deleting or renaming the audacity.cfg file and then starting audacity up and seeing if it works properly.

---

### Post by drs305 on 2008-10-08
According to the PulseAudio wiki, audacity doesn't support PulseAudio. Could that be what is causing your problems?

```
[http://www.pulseaudio.org/wiki/PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup")
```

---

### Post by pi.boy.travis on 2008-10-08
> **mc4man said:**
> You may want to try going to home folder -> .audacity-data and deleting or renaming the audacity.cfg file and then starting audacity up and seeing if it works properly.

> **drs305 said:**
> According to the PulseAudio wiki, it doesn't support PulseAudio. Could that be what is causing your problems?

```
[http://www.pulseaudio.org/wiki/PerfectSetup]("http://www.pulseaudio.org/wiki/PerfectSetup")
```

Thank you both for posting.

I have tried uninstalling and removing the configuration files with synaptic, but I will try your method as well.

I am using ALSA, but I;m not sure if that means I'm not using Pulseaudio.

---

### Post by pi.boy.travis on 2008-10-11
Deleting the configuration file got Audacity running normally, but I still can't record or playback. . . 

Any ideas?

---

### Post by pi.boy.travis on 2008-10-11
OK, I am now hearing interference through the speakers whenever audacity is running, but I still can't playback or record. . .

---

### Post by simtaalo on 2008-10-11
i used to use audacity when i had a windows machine but havent got on with it since i changed to linux. have you tried out sweep? very good alternative, it recognised my onboard sound card without any need to configure which is useful for work on the fly when i cant plug in my usb sound desk.

its in the repo's, or you can get the very latest version here [http://www.metadecks.org/software/sweep/](http://www.metadecks.org/software/sweep/)

---


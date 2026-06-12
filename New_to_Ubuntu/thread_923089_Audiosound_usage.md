---
title: "Audio/sound usage"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Pas_sa on 2008-09-18
Hi, I have some problems with audio in Ubuntu.

If I have Rhythmbox open, flash applets do not play audio. If I open Rhythmbox after a flash applet is loaded, I need to end task a process called 'pulseaudio' and then both will work at the same time.

Why can't two applications play audio at the same time without problems? Is there a workaround so I don't need to worry about this? (happens with games sometimes too..)

Thanks.

---

### Post by hellion0 on 2008-09-18
Looks like Flash isn't using PulseAudio on your setup. This link may help: [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

---

### Post by Pas_sa on 2008-09-18
That fixed the described problem but introduced new ones.. now certain applications have no audio (Sauerbraten) and they freeze upon exiting (Sauerbraten and ZSNES, both use SDL I believe.. ZSNES has never had working sound for me though).

As soon as I kill the pulseaudio process, they no longer freeze when exiting (however I still have no audio in Sauerbraten).

Some applications function differently; Guild Wars running under Wine without pulseaudio sounds perfect, as soon as pulseaudio is on, it becomes choppy and painful to listen to.

What's the go on all this..

---

### Post by Nepherte on 2008-09-18
If you are sure they use SDL, then installing this package should help:
```
sudo apt-get install libsdl1.2debian-pulseaudio
```

---

### Post by markbuntu on 2008-09-18
If you want your sound applications to play together, you can try my guide here:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

This will fix your rythmbox/flash problem. I do not use ZSNES or Sauerbraten so I cannot say if it will help with those but, if they can use pulseaudio somehow, I am sure it will fix that issue as well.

---


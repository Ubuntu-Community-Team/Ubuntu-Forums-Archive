---
title: "Sound problem on shut down"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by sim085 on 2013-02-28
Hello, I do not know if I need to worry, however when I shutdown my computer, just before the computer turns off, my speakers do a strange noise. I do not know how to explain the noise like fizzel sound. This also happens when I restart my computer. Is there anything I can do to solve the problem?

---

### Post by sim085 on 2013-03-01
Hello sorry to bring this up again. I have installed Windows on another partition and Windows7 does not do this fizzel sound when I restart or shutdown! So I think this is something related to Ubuntu. Is it possible to fix myself? Maybe by switching speakers off before shutdown. I do not want that I might be doing some damage!

---

### Post by audiomick on 2013-03-01
> **sim085 said:**
>  Maybe by switching speakers off before shutdown.

This is actually good practice even if you aren't getting any funny noises. One should always switch the speakers (amps) off first and on last in any audio system.

As far as Ubuntu goes, I noticed a couple of years back, and I think it was in conjunction with a change in the audio module in Ubuntu, that it suddenly started making a pop on startup and shutdown. I don't think there is much can be done about it. It seems the audio module is not starting the audio card "safely". I don't know if it is even theoretically possible, but it would be necessary to mute the output of the card until the system is up and running.

Anyway, yes, turn your speakers off before you shut down, and on only after the system is up and running.

---

### Post by sim085 on 2013-03-02
Hi Michael,

Thanks for your reply. I guess when you say "turn off" you mean **manually** turn off right? Can't I - by create/edit a script file turn the sound card off automatically just before shut down and turn it on on start up?

---

### Post by sim085 on 2013-03-02
btw - this is on my laptop and if I manually turn of the speakers it seems that just before shutdown these are turned on again!

---

### Post by audiomick on 2013-03-02
> **sim085 said:**
>  Can't I - by create/edit a script file turn the sound card off automatically just before shut down and turn it on on start up?

Possibly you could, but I don't know how. Sorry.

---

### Post by m4rcuz on 2013-04-14
I experienced a similar problem with my soundcard/speakers on shutdown/reboot,
and fixed by editing an alsa config file according info found online.

Run in a terminal window;

gksudo gedit /etc/modprobe.d/alsa-base.conf

and add the following line

options snd-hda-intel single_cmd=1

After i rebooted all was ok..

---


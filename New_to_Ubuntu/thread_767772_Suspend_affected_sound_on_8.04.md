---
title: "Suspend affected sound on 8.04"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by RustyTrowel on 2008-04-25
So far, I really have no complaints about Hardy Heron...I think it's great.  I do, however, have a small sound problem that may be my fault or hardware/driver specific.  I'm not computer savvy...so I hope I can do my best to explain the details.

Problem:  When I awaken the computer from Suspend the sound goes away.  If I restart the computer the sound comes back.  I'm not really sure what is happening.  

System:

ABIT NF-M2S with NVIDIA GeForce 6100 Motherboard
AMD Athlon 64x2 4600+
EVGA 256 MB GeForce 7600GT Graphics Card

Also: 

When I type aplay -l into the terminal I get a soundcard (HDA Nvidia ALC883) and I've got volume bars when I type in alsamixer.  I guess this is the part of the message where people cut and paste logs in...but I wasn't sure what the different logs represent.  Sorry.

Anyways.  Any ideas on the matter would be great to hear.

Thanks

---

### Post by hhpeter on 2008-04-25
I have the same problem...when I start the system the sound is there but if 
I put the laptop to sleep after I have no sound at all...
Asus s96s
Intel core 2 duo
nvidia geforce 8600gs
ubuntu 8.04 386
If somebody has  solved this issue please post back

---

### Post by certux on 2008-04-26
Hi,

I had the same symptom and solved the problem by unloading and then reloading the sound module (snd_hda_intel in my case):
```
modprobe -r snd_hda_intel
modprobe snd_hda_intel
```

This has been suggested quite a few times, but it first did not work for me since the first command gave an error message saying that the module was still in use. It turned out that kmix (I am using kde) blocked unloading the module, so I had to either kill kmix before unloading or issue ```
dcop kmix Mixer0 close
```
then un- and reload the module, followed by ```
dcop kmix Mixer0 open
```
which did the trick.
If you're using some other desktop environment you can find out which application is blocking the sound device with the command ```
lsof | grep /dev/snd
```

Hope that will work for you too.
Greetings
Sebastian

---

### Post by RustyTrowel on 2008-04-26
Sebastian,

Thanks for the response.


I tried to use "dcop" but wasn't able to close the interfering process (not sure why...I might not be typing things in correctly).  I ended up killing the process identified with the "lsof | grep /dev/snd" and then reloading the sound module.  While I did get sound, as soon as I Suspended again I lost it.

Thanks for the idea though.  

-David

---

### Post by hhpeter on 2008-04-27
this worked for me
after suspend-resume type in terminal

sudo su
/sbin/alsa force-reload

sound working, now, if somebody can help me make it happen automatically so I don't need to type it every time after resume

---

### Post by Ingenium on 2008-05-17
> **hhpeter said:**
> this worked for me
after suspend-resume type in terminal

sudo su
/sbin/alsa force-reload

sound working, now, if somebody can help me make it happen automatically so I don't need to type it every time after resume

Worked for me too. Great solution!

---


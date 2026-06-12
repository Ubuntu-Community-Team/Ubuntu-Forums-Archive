---
title: "Sound has dissappered after unplugging my computer????"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by K-D on 2008-09-08
I have been having a tidy up of my wiring today whilst plugging in a kvm switch and after plugging everything back in my sound is no longer working....This is really frustrating and would appreciate it if anyone would be able to help me work out whats going on!?!

I'm new to Ubuntu so go easy.....

---

### Post by Sealbhach on 2008-09-08
Sounds like the problem was caused by the wiring? If you've changed nothing else then maybe the wiring is not like it was?

Anyway, lets see if your sound card is found. Type

```
aplay -l 
```

in a terminal and post it here.

Also please give result of this:

```
cat /proc/asound/modules
```


.

---

### Post by K-D on 2008-09-09
This is the message that I get??

kris@kris:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: SI7012 [SiS SI7012], device 0: Intel ICH [SiS SI7012]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
kris@kris:~$ cat/proc/asound/modules
bash: cat/proc/asound/modules: No such file or directory
kris@kris:~$ 


I presume this means Ubuntu found my device??

---

### Post by bobnutfield on 2008-09-09
> cat/proc/asound/modules: No such file or directory

Note that you need a space after the cat command:

> cat /proc/asound/modules

---

### Post by K-D on 2008-09-11
This is what I get:

kris@kris:~$ cat /proc/asound/modules
 0 snd_intel8x0
kris@kris:~$

---


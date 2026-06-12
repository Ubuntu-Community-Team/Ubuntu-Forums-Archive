---
title: "Volume sounds like 5% at 50%"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by mike_pasara on 2008-10-22
Like the title says... When the master volume is at 50% it sounds likes it's at 5%, even 70% sounds too low... how can this be fixed. Switched from vista to ubuntu, wouldn't mind if my sound worked properly.

---

### Post by kpkeerthi on 2008-10-22
Open alsamixer (from terminal) and raise PCM channel.

---

### Post by kerry_s on 2008-10-22
make sure pcm is all the way up, in fact double click the volume icon and move them all up.

---

### Post by PocketDog on 2008-10-22
Do you have Alsa installed? If so, in terminal run```
alsamixer
``` and set master and PCM channels to 100%

If not, just search Synaptic for 'Alsa', install it and do the above

---

### Post by dileepdinesh on 2008-10-22
Hi, me too switched to ubuntu recently,,realy loves it..
I think i had the same problem. I believe this happens becoz the default volume settings  are low, may be u can solve this going to volume control (right click the volume icon on desktop), in that there will be playback and increase master volume and front volume,,( i increased all options there:)),this might solve ur problem

---

### Post by bobsmith2 on 2008-10-22
A follow-up question... I'm frequently needing to go in and raise the level of the PCM channel. It's a pain to have to do this all the time. I want PCM to be up ALL the way up, 100% of the time. Is there a way to lock PCM at 100% and get my software to change the Master volume instead of the PCM channel? Or can I just blow the PCM channel away (after locking it at 100%) since it's nothing but an annoyance? Thanks.

---

### Post by mike_pasara on 2008-10-22
it's at 100%

now my receiver can stay at a normal -40db and sound proper. But when the master volume for ubuntu is at 50% I can barely hear anything... it's like it sounds like it's set at 5%

---

### Post by kerry_s on 2008-10-22
> **bobsmith2 said:**
> A follow-up question... I'm frequently needing to go in and raise the level of the PCM channel. It's a pain to have to do this all the time. I want PCM to be up ALL the way up, 100% of the time. Is there a way to lock PCM at 100% and get my software to change the Master volume instead of the PCM channel? Or can I just blow the PCM channel away (after locking it at 100%) since it's nothing but an annoyance? Thanks.

it would be easier to leave the master at 100% and change the volume preference to control pcm.

---

### Post by bobsmith2 on 2008-10-22
> **kerry_s said:**
> it would be easier to leave the master at 100% and change the volume preference to control pcm.

Thanks kerry_s! I didn't know that was possible. It fixed my problem.

---

### Post by mike_pasara on 2008-10-23
Bump I guess... no one knows what the issue is?

---


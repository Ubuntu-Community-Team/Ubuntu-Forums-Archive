---
title: "Problem of no sound"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by raymano9 on 2008-12-01
Dear all,

I am new to ubuntu and i am facing problem of no sound. Initially when i installed ubuntu, i do not faced the issue of no sound. I can hear all the sound including the sound of ubuntu normal start-up sound. No problem with totem movie player too.

Out of a sudden i faced the problem of no sound. Not a single sound in all aspect. Is there anyone out there who can help me?


Regards,
Raymano9

---

### Post by halitech on 2008-12-01
try opening a terminal and post the results of this command```
aplay -l
```

also, check and make sure  your sound isnt muted.

---

### Post by raymano9 on 2008-12-01
thank you for your suggestion on the terminal part but it still does not work ....

how to make sure my sound is not mute? I use normal notebook keyboard to turn on the volume to the max .... still cant hear a single sound ...

---

### Post by halitech on 2008-12-01
what was the result of running the command I gave you? did it give you any information back or did it just drop a line?

---

### Post by raymano9 on 2008-12-01
below is the reply .... looks confusing to me ... cant understand a single thing ...


raymano@ubuntu:~$ aplay-l
bash: aplay-l: command not found
raymano@ubuntu:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 0: Intel ICH [Intel 82801DB-ICH4]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: I82801DBICH4 [Intel 82801DB-ICH4], device 4: Intel ICH - IEC958 [Intel 82801DB-ICH4 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

---

### Post by halitech on 2008-12-01
what it means is that Ubuntu is seeing your audio hardware and you are using an Intel chipset which I have not seen good things about. Usually, from what I've seen it involves removing ALSA and reinstalling it. Before we go that far, try the instructions on this page

[http://ubuntuforums.org/showthread.php?t=161193](http://ubuntuforums.org/showthread.php?t=161193)

---

### Post by raymano9 on 2008-12-01
I just read the link you gave me, following are they writes:

[B]I solved this problem and I get all sound out!!!

I found the solution occasionally.

It is that you must first select "external amplifier"(listed on the volume panel) and unselect it right away.

It make me feel very strange why have to do it but it does just work.[/B]



Where can i find the volume panel?

---

### Post by halitech on 2008-12-01
did you follow the instructions in post #2?

---

### Post by raymano9 on 2008-12-01
you mean

sodu alsamixer? i did ... but what i see is just the following attachment which i could not control any of it.

[IMG]http://img390.imageshack.us/my.php?image=screenshotig7.png][img=http://img390.imageshack.us/img390/4999/screenshotig7.th.png][/url][/IMG]

---

### Post by halitech on 2008-12-01
no attachment on this post

---

### Post by raymano9 on 2008-12-01
[IMG]http://img390.imageshack.us/my.php?image=screenshotig7.png][img=http://img390.imageshack.us/img390/4999/screenshotig7.th.png][/url][/IMG]

---

### Post by raymano9 on 2008-12-01
I have diffuculty attaching the picture .... i use via imageshack .... is that the way?

---

### Post by raymano9 on 2008-12-01
[IMG]http://img390.imageshack.us/my.php?image=screenshotig7.png[/IMG]

---

### Post by halitech on 2008-12-01
if you have it uploaded, just post the link to where it is

---

### Post by raymano9 on 2008-12-01
posted but somehow or rather nothing comes out .... let me try again ....


[IMG]http://img390.imageshack.us/my.php?image=screenshotig7.png[/IMG]

---

### Post by raymano9 on 2008-12-01
nothing comes out again ...

---

### Post by raymano9 on 2008-12-01
the link is

[http://img390.imageshack.us/my.php?image=screenshotig7.png](http://img390.imageshack.us/my.php?image=screenshotig7.png)

---

### Post by halitech on 2008-12-01
lets do it this way, does it look like the screen I just attached?

Edit: okay, so right idea but you only have master for controls? something is strange there

---

### Post by raymano9 on 2008-12-01
No ... your attachment looks like a mixer but mine is just graphic of just a picture of volume controler ...

i just find out ... you can click the following to see the picture ...

[http://img390.imageshack.us/my.php?image=screenshotig7.png](http://img390.imageshack.us/my.php?image=screenshotig7.png)

---

### Post by halitech on 2008-12-01
I see that, not sure why its not giving the other options. I'd suggest reading further down the page and see if anything else helps.

---

### Post by bobnutfield on 2008-12-01
This may or may not be your problem, but Pulse Audio seems to give people problems and interferes with otherwise working settings.  You might try to go to System>Preferences>Sound and make sure that you correct sound device is listed.  If it is, try using Alsa only settings by going to System>Preferences>Sessions and UNCHECK Pulse Audio.  It has worked for others, and allows the system to use Alsa as the only system sound configurator.

---


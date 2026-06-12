---
title: "[SOLVED] no audio on inspiron 1525 after 8.04 install&#8207;"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by cjdawson73 on 2008-06-04
please bear with me here, very green with ubuntu. just to a new inspiron with ubuntu and did the recommended upgrad to 8.04. now there is no sound. again, i'm new so detailed instructions would be helpful. The card '82801H (ICH8 Family) HD Audio Controller' is listed under device manager, the status says 'status'. Thanks!

---

### Post by ruffEdgz on 2008-06-04
I have the same Audio Drivers on my XPS and they worked well when I installed 8.04.

Go to System >> Preferences >> Sound and make sure they are all on 'Autodetect'. I have my device set to 'HDA Intel'.

Outside from that, I was good with getting my XPS 1530 to work and I would hope it would be the same for ya ;)

Hope it works for ya :D

---

### Post by wolfen69 on 2008-06-04
i have tried to get sound working with that soundcard with no luck. see [THIS]("https://help.ubuntu.com/community/HdaIntelSoundHowto") for some possible help.

---

### Post by xfceuser on 2008-06-04
hi, first type
```

asoundconf list

```

in the list find your sound card name then

```

sudo asoundconf set-default-card PARAMETER

```

instead of parameter type your sound card name.

then

```

gnome-alsamixer

```

if it said not installed, install it by the instruction it gives you.
then check and tune all the controls of the mixer.

---

### Post by cjdawson73 on 2008-06-04
thank, all mine are set to 'autodetect' as well. when I click on 'test' i get a the error:

'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument'

---

### Post by cjdawson73 on 2008-06-04
after 'asoundconf list'

i get:

'Names of available sound cards:'

nothing else. ??

---

### Post by ruffEdgz on 2008-06-04
That is odd... I check out this link: [https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525?highlight=(1525](https://wiki.ubuntu.com/LaptopTestingTeam/DellInspiron1525?highlight=(1525)) and found that it seems to work with Hardy but xfceuser's or wolfen69's solution looks like it could work out for ya (never bad to try :D).

Like I said before, my xps has the same audio drivers so you could try one of the solutions I found for the XPS: [https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#head-3db3b05e71bfc5d5815a28c25fe25b7055767ba7](https://wiki.ubuntu.com/InstallingUbuntuOnADellXPSM1530#head-3db3b05e71bfc5d5815a28c25fe25b7055767ba7)

Hope to hear that the audio is working :D

---

### Post by lsmobrian on 2008-06-04
> **cjdawson73 said:**
> thank, all mine are set to 'autodetect' as well. when I click on 'test' i get a the error:

'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument'

Do you have any applications open that might have some kind of lock on the sound settings.  I tried changing sound preferences and testing when rhythmbox was open and it made an error(not a ubuntu box right now, sry I cant test to see if its the same error)

---

### Post by cjdawson73 on 2008-06-04
all other apps are closed. thanks for the tips but still down

---

### Post by avtolle on 2008-06-04
The system is not detecting your soundcard (obvious conclusion, huh?). I believe I saw a solution for something similar here a few days ago, but didn't bookmark it. I suggest looking at the wiki piece linked above.

---

### Post by shadowfirebird on 2008-06-06
Same here.  This was fine in 8.04 yesterday -- It looks like it's been caused by a kernel upgrade, since that's the only thing I upgraded yesterday that wouldn't have kicked in right away.
...
Okay, that's confirmed.  I've just removed the kernel upgrade and sound came back.

Let me look around for advise from wiser souls, and I'll post here again.

---

### Post by shadowfirebird on 2008-06-06
There's a thread [here]("http://ubuntuforums.org/showthread.php?t=819680") that reports a similar problem, but no answers as I type this.

If you've upgraded your 8.04 Ubuntu within the last day or so and the sound has gone, this may help:

1) Open Synaptic Package Manager (in Administration tools).

2) click the search button.  Search for package names with "linux-image-".

3) You're looking for packages like this "linux-image-<bunch of numbers>-generic".  You're going to have at least one installed (green box).  If you don't, I'm confused, stop now.

4) right-click on 2.6.24-19 and select "mark for removal".

5) !!! Make sure that the previous kernel, 2.6.24-18, is installed, or your computer will stop working!!! (if not, right-click on it and select "mark for installation".)

6) Click "apply" and watch your computer reconfigure itself.

7) I found that deinstalling the current kernel confused my computer temporarily (!) -- I fixed it with a reboot.  (ctrl-alt-F1; login; "sudo shutdown -r now".)

Hope that helps.

---

### Post by cjdawson73 on 2008-06-10
this worked

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade](http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade)

---

### Post by jmacknmo on 2008-07-31
> **cjdawson73 said:**
> thank, all mine are set to 'autodetect' as well. when I click on 'test' i get a the error:

'audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Failed to connect stream: Invalid argument'

I am having a similar issue with my Shuttle KPC. I suspect it may be due to my running Squeezebox Slimserver on startup. How do I close it down so I can initialize the soundcard? 
Idiot's guide please...

Thanks

---


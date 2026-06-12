---
title: "No sound after suspend - resume"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by hhpeter on 2008-04-26
I just installed ubuntu 8.04 on my laptop its working like never before...
my webcam works, suspend works finally it resumes, but after that I have no sound at all...if I reboot the machine I have sound again 
Anybody had this problem? any workarounds?

---

### Post by hhpeter on 2008-04-26
Found a way to make the sound to work after suspend-resume
type:
sudo su
/sbin/alsa force-reload

after that sound is working but is kind of annoying that I need to type it everytime I resume from suspend.
Can somebody help me make this automatic

---

### Post by akudewan on 2008-04-27
Thanks for the workaround. This has been bugging me for quite some time now. I'll file a bug-report, if there isn't any yet...

Edit: I wonder if adding the command to /etc/acpi/resume.sh would automate the process. I'll try that later.

---

### Post by m4cph1sto on 2008-05-06
Any luck fixing this problem?  I also need to do $sudo /sbin/alsa force-reload to fix my sound every time I resume from suspend-to-ram.  Is there an appropriate script to add to /etc/acpi/resume.d to do this automatically?  I'm using the on-board sound on an Nvidia 680i motherboard.

edit: I tried modifying /etc/default/alsa to include:

force_unload_modules_before_suspend="all"

hoping this would reload everything after resume and solve the problem, but it had no effect.

I also tried editing /etc/acpi/resume.d/67-sound.sh to look like:

#!/bin/sh

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
/etc/init.d/alsa-utils restart
/etc/init.d/alsa-utils reset
fi

But this also had no effect.

---

### Post by akudewan on 2008-05-06
I have an NVidia 610i. The problem is still there, I tried adding the force-reload command to /etc/acpi/resume.sh, but then the system would not resume, and just hang...

---

### Post by atorch on 2008-05-06
Same problem here.

sudo su
/sbin/alsa force-reload

...the above works, but I would rather it be automatic.  I don't want to have to bring up a terminal each time I resume from suspend / hibernate.

---

### Post by reggie_mac on 2008-05-08
I'm also having the same problem, but being new to ubuntu i have no idea how to do much, but im thinking is it possible to add a script or mod a file that will shut down the device on suspend/hibernate then start it again on wake up?

EDIT:

now solved, followed this instructions on this thred

[http://ubuntuforums.org/showthread.php?t=616845](http://ubuntuforums.org/showthread.php?t=616845)

ie I added

```

options snd-hda-intel model=acer

```

to /etc/modprobe.d/alsa-base because i have an ALC268 on an Acer Laptop

then edited /etc/acpi/resume.d/67-sound.sh to 
```
 
#!/bin/sh

# Get sound back
if [ -x /etc/init.d/alsa-utils ]; then
/etc/init.d/alsa-utils restart
/etc/init.d/alsa-utils reset
fi

```

---

### Post by m4cph1sto on 2008-05-10
Has anyone had success resolving this issue on an Nvidia motherboard?  I'm on a 680i SLI with ALC882 HDA audio (Azalia) and I could not get the above solution to work for me.

---

### Post by zwastik on 2008-05-12
Same problem here, the above solution does not work for me!
sudo /sbin/alsa force-reload does work:
> Unloading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.
Loading ALSA sound driver modules: snd-hda-intel snd-pcm-oss snd-mixer-oss snd-pcm snd-page-alloc snd-hwdep snd-seq-dummy snd-seq-oss snd-seq-midi snd-rawmidi snd-seq-midi-event snd-seq snd-timer snd-seq-device.


I think the problem is about unloading some modules, but putting those modules in 
/etc/default/acpi-support 
# Add modules to this list to have them removed before suspend and reloaded
# on resume. An example would be MODULES="em8300 yenta_socket"
#
# Note that network cards and USB controllers will automatically be unloaded 
# unless they're listed in MODULES_WHITELIST
MODULES=""

does not work if someone wonders about it.

---

### Post by reggie_mac on 2008-05-13
When i was trying to get mine to work the force re-load was hit and miss, maybe try the /etc/init.d/alsa-utils reset after the reload (forced or otherwise) as im sure it was the command that sorted mine out for me.

---


---
title: "I can't set the resolution high enough"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by japc126 on 2008-04-27
While I used Ubuntu 7.10, my screen resolution was at 1280x1024 and I loved it. Now, with hardy heron, the highest it will go is 1024x768. Can I "force" it to be at 1280x1024?

I have an Nvidia gtx(or something, I'm not sure about the letters) 7300. Before I enabled restricted drivers the resolution could be set a little higher (but not 1280x1024), but with them the highest it will go is 1024x768

---

### Post by alienexplorers on 2008-04-27
Try running Envy and unload your graphic driver.  Switch Envy to manual mode and from the list of 3 drivers at the botttom select the middle driver.

---

### Post by dokdoom on 2008-04-27
Have you tried running

nvidia-settings

It is your friend. I had to install it though so don't be surprised if you can't run that command. Just install it you have to.

---

### Post by daimaru on 2008-04-27
just edit your /etc/X11/xorg.conf file and add your desired resolution to the Section "Screen" part.

```
Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation G80 [GeForce 8800 GTS]"
    Monitor        "Samsung SyncMaster 214T"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
        Virtual    1600    1200
        Modes        "1600x1200@65"    "1600x1200@60"    "1400x1050@60"    "1280x960@75"    "1280x1024@60"    "1280x960@60"    "1280x1024@75"    "1152x864@75"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
    EndSubSection
```

never mind the @65 or whatever Hertz stuff it suffices to just put in "1280x1024" for example. Just make sure that the resolution you want is the first one in the line.

---

### Post by japc126 on 2008-04-27
Thanks, nvidia-settings did the trick

---


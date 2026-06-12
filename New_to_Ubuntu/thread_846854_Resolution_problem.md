---
title: "Resolution problem"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by anotherconfused1 on 2008-07-01
I used to not have my video driver enabled. So I enabled it and now the max resolution I can go it 1024x768. I believe I was in around 1280x1024 before the driver was enabled. Any way to get it back? I can't select in System>Preferences>Screen Resolution.

---

### Post by anotherconfused1 on 2008-07-01
no advice at all?

---

### Post by tjwoosta on 2008-07-01
what is your video card and what driver did you use?

---

### Post by anotherconfused1 on 2008-07-02
It's an NVIDIA.  The driver is the one that it downloaded when I enabled it. I'm not sure how to check what the video card is exactly in Ubuntu.
edit: NVIDIA GeForce 7800 GT.

---

### Post by ibuclaw on 2008-07-02
```
sudo lshw -short | grep display
```
That should give you your graphics card name.

Try
```
sudo xrandr -s 1280x1024
```

If that gives you nothing, can you post the output of
```
sudo xrandr -q
```

Regards
Iain

---

### Post by tjwoosta on 2008-07-02
i cant remember what its called but i think i remember a program in synaptic that allows nvidia users to configure  resolution in xorg.conf or something

can anybody confirm this?

---

### Post by ibuclaw on 2008-07-02
> **tjwoosta said:**
> i cant remember what its called but i think i remember a program in synaptic that allows nvidia users to configure  resolution in xorg.conf or something

can anybody confirm this?
**Removed previous post**
[EDIT]
```
sudo apt-get install nvidia-settings
```

Then go into "**System>Administration>NVIDIA X Server Settings** and all the infomation available will be under the "**X Server Display Configuration**" tab.

Regards
Iain

---

### Post by anotherconfused1 on 2008-07-02
Ok thanks tinivole! It worked. I like higher resolution...

---


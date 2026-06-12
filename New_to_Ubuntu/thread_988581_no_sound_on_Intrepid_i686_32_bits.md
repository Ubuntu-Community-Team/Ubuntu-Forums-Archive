---
title: "no sound on Intrepid i686 32 bits"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by josil on 2008-11-20
Hello, I'm strugling to fix the sound problem. Ubuntu 8.10 installed on HP pavilion dv7 1045es. How do I find out if there is the correct ALSA driver in the kernel for the given sound card? How do I find out what sound card is installed?

Thanks in advance.

---

### Post by cariboo on 2008-11-20
If you run the following in a Application-->Accessories-->Terminal:

```
sudo lshw -c multimedia
```

and paste the output in your next post.

This will tell us if your sound card is detected properly.

Jim

---

### Post by josil on 2009-01-01
> **cariboo907 said:**
> If you run the following in a Application-->Accessories-->Terminal:

```
sudo lshw -c multimedia
```

and paste the output in your next post.

This will tell us if your sound card is detected properly.

Jim

This is the output. 

 *-multimedia            
       description: Audio device
       product: 82801I (ICH9 Family) HD Audio Controller
       vendor: Intel Corporation
       physical id: 1b
       bus info: pci@0000:00:1b.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=HDA Intel latency=0 module=snd_hda_intel

In the serie of replies to "[SOLVED] Sound problems-Intel 8201I (ICH9 Family) HD Audio", they suggested to try adding pci=noacpi as a boot option, if this apply in my case, what system file should I modify and how?

---

### Post by josil on 2009-01-01
Thanks cariboo907

problem reported and solved on "Sound trouble on certain HP laptop (in my case : dv7 1070)" at [https://bugs.launchpad.net/ubuntu/+bug/269586](https://bugs.launchpad.net/ubuntu/+bug/269586)

---


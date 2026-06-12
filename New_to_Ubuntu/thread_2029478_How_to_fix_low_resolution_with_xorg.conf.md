---
title: "How to fix low resolution with xorg.conf"
date: 2012-07-19
forum: New to Ubuntu
---

### Post by enewe101 on 2012-07-19
I just got my dual screen set up in ubuntu using an nvidia GeForce 8400  GS video card.  The nice thing is that it worked as an extended desktop  right away.  But the resolutions available are wrong.  They are not as  high as the monitor can go (1440x900), and they are not the right aspect  ratio either.

I didn't have any luck adding new modes with xrandr commands.  It would refuse them as if my hardware wouldn't support modelines for higher res.

Anyway, I'd rather achieve this by editing xorg.conf so the change will persist.   I've tried about a dozen permutations of xorg.conf files based on  examples around the net, but they almost all cause the screen to go black  on booting up.

Could someone have a look at this xorg.conf file and tell me what I might be doing wrong?  Note, if I take out the lines that start with "Modeline..." and "Modes..."  it doesn't cause the black screen, but of course doesn't help with the monitor resolution prob.

 ```

     Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
EndSection

Section "Monitor"
        Modeline        "1440x900@75" 136.75  1440 1536 1688 1936  900 903 909 942
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Modes "1440x900@75"
        EndSubSection
EndSection

```
Many thanks!

---

### Post by z3nhakr on 2012-07-19
it's been a long time since ive had an Nvidia card but i recall being able to change the resolution with the nvidia xserver settings app.

---


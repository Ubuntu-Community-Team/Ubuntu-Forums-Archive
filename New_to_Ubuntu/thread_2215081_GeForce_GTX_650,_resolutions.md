---
title: "GeForce GTX 650, resolutions"
date: 2014-04-03
forum: New to Ubuntu
---

### Post by sam_baker2 on 2014-04-03
hi,
I changed my display resolution to 800x600 to play an old game
and now I cannot change the resolution back to what it was 
originally ( 1280x720 )
When I run xfce4-display-settings, it shows 800x600 in the 
settings field, but when I try to rest it to 1280x720 it will not
change. 
Anybody have a clue as to how to get the display to set?
I have 12.04 LTS with a nvidia card.

thanks

---

### Post by Dreamer Fithp Apprentice on 2014-04-04
I had a similar problem recently under 13.10, using plain openbox, with an  Nvidia card.

For me the solution was```
sudo apt-get purge xorg*
sudo apt-get install xorg
```I was afraid purging xorg would uninstall all my gui applications, since they ARE dependent on xorg. But that didn't happen. Nothing was trashed. I didn't have to reinstall anything. Those 2 lines completely solved it. I'm still stunned. Nothing is EVER that easy.

More details here:
[http://ubuntuforums.org/showthread.php?t=2212531](http://ubuntuforums.org/showthread.php?t=2212531)

---

### Post by sam_baker2 on 2014-04-04
Thanks Dreamer, but that didn't seem to work for me.
I think I will try another post in the beginner section.

---

### Post by sam_baker2 on 2014-04-04
hi,
here is my system:
```

xubuntu 12.04 LTS 

uname -a
3.2.0-60-generic #91-Ubuntu SMP Wed Feb 19 03:54:44 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

lspci -nn | grep VGA:
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GK107 [GeForce GTX 650] [10de:0fc6] (rev a1)
 
```
I can't change my display resolution now after some previous updates.
Otherwords, I normally use 1280x720, but 
when I run xfce4-display-settings and try to change to (for example) 1680x1050, nothing happens.
It is odd, it will usually let me decrease the resolution, but is very difficult getting it
back to 1280x720. I set it to 480x480 and it was so large, I liked to never
got it back to a higher resolution.
It use to work, now it doesn't.
 
I have tried
 ```
sudo apt-get purge xorg*
sudo apt-get install xorg
```
I have also ran the "additional drivers" utilities
and have tried installing all of the different nvidia drivers that are
given :
Nvidia 304
Nvidia 304-updates
Nvidia 331 ( recommended )
Nvidia 331-updates

I also even tried :
```
sudo apt-get install nvidia-current-updates
```


any help appreciated.

---

### Post by grahammechanical on 2014-04-04
I am not using Xubuntu, so I may not be absolutely correct about every detail. With that in mind, this problem is not to do with Xserver. Another thing to remember is that if we install a proprietary video driver then we must use the settings utility for the proprietary video driver that was installed at the same time. The distribution comes with a Display utility but it is only useful if we are using the Nouveau open source video driver.

Please confirm that you are using a proprietary video driver and are trying to make adjustments using the proprietary video driver settings management utility.

Regards.

---

### Post by sam_baker2 on 2014-04-04
I'm pretty much a beginner when it comes to video cards.
How do I determine if I am using a proprietary video driver?

---

### Post by sam_baker2 on 2014-04-04
do any of these help?
```

_egrep -i "connected|card detect|primary dev" /var/log/Xorg.0.log:_
[    22.443] (--) NVIDIA(0):     Ancor Communications Inc ASUS VE278 (DFP-1) (boot, connected)


_find /dev -group video:_
( I get nothing with this command )


_glxinfo | grep -i vendor:_
server glx vendor string: NVIDIA Corporation
client glx vendor string: NVIDIA Corporation
OpenGL vendor string: NVIDIA Corporation

```

---

### Post by The Cog on 2014-04-04
The command ```
lspci -v
``` lists lots of hardware and the kernel driver in use for them. nvidia is the proprietary driver, and nouveau is the open source one. 

I have had no resolution problems with the nvidia driver. I always use the one from the repository (331.18 at the moment).

---

### Post by sam_baker2 on 2014-04-04
_lspci -v_
```

    01:00.0 VGA compatible controller: NVIDIA Corporation GK107 [GeForce GTX 650] (rev a1) (prog-if 00 [VGA controller])
    Subsystem: Gigabyte Technology Co., Ltd Device 3555
    Flags: bus master, fast devsel, latency 0, IRQ 88
    Memory at fd000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at d0000000 (64-bit, prefetchable) [size=32M]
    I/O ports at e000 [size=128]
    [virtual] Expansion ROM at fe000000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_304_updates, nvidia_331_updates, nouveau, nvidiaf
```

---

### Post by mörgæs on 2014-04-04
> **sam_baker2 said:**
> 
I think I will try another post in the beginner section.

Next time please ask a moderator to move your thread.
Merged.

---

### Post by pqwoerituytrueiwoq on 2014-04-04
i would suggest upgrading to 13.10 or 14.04 beta
12.04 was released before the GTX 600 series
i have had no issues with my 650 TI boost on 13.10 or 14.04
i have tried the VGA/DVI output, only HDMI

---

### Post by sam_baker2 on 2014-04-04
I think I will wait until 14.04 is not beta and then upgrade.
I wonder if we will have to back up all data from 12.04 and do a clean install
for 14.04, and then re-install everything, or if the 14.04 upgrade will
take care of everything automatically.

---

### Post by The Cog on 2014-04-04
I would suggest that if possible, backup /home and do a clean install. I've seen plenty of horror stories about upgrades. I always clean install.

---

### Post by pqwoerituytrueiwoq on 2014-04-04
> **sam_baker2 said:**
> I think I will wait until 14.04 is not beta and then upgrade.
I wonder if we will have to back up all data from 12.04 and do a clean install
for 14.04, and then re-install everything, or if the 14.04 upgrade will
take care of everything automatically.upgrade works, if you switch to 14.04 now be sure to use a tty, i had lightdm crash during the upgrade and i could not finish the upgrade, had to use a tty to recover, you dont want to reboot mid upgrade
after the upgrade if you have issue try the guest account if it i works it is something in your home folder that we can quickly fix from a tty
tty=ctrl+alt+f1

---

### Post by Dreamer Fithp Apprentice on 2014-04-18
FWIW, upgrade from the command line worked fine for me. I forget the command but I think it was on the same page with the download.

---


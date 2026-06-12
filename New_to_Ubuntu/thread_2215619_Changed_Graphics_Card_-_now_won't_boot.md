---
title: "Changed Graphics Card - now won't boot"
date: 2014-04-07
forum: New to Ubuntu
---

### Post by tank.tmt on 2014-04-07
Hello.

My radeon 6850 (I think) recently died so I replaced it with a gtx 750. Windows 7 will work fine with this but ubuntu won't normal boot. I do the safety boot thingie and uninstall jockey and restart and that doesn't help. So I use synaptic to remove everything found when I searched for 'ati', which were xorg files. Still no cigar. How can I get ubuntu to work with my new graphics card short of reinstalling the whole OS? (I no longer have access to the old 6850)

Cheers

---

### Post by meistersreign on 2014-04-07
Did you have proprietary drivers installed when you were using the ATI card, or just the default graphics drivers? I'm thinking Ubuntu might be still thinking you are using your old card, and doesn't recognize the new one. Are you able to get to a console using ctrl + alt + f2 ? If you can, I'd try to install the Nvidia drivers if you want proprietary by issuing "sudo apt-get install nvidia-current". I believe that nouveau is already installed by default. Or you could use the safety boot to get to a terminal as well.

Hope this helps!

---

### Post by tank.tmt on 2014-04-07
I didn't specifically install any drivers for it unless jockey does that. I tried installing the nvidia-current drivers and now it boots but slowly and into a 640x800 resolution which it insists is 19xx by 16xx. Also synaptic has one radeon thingie left in its menu but when i tell it to remove it, it says it has to remove a huge amount of other things that I thought were unrelated - so I get scared and leave it alone.

---

### Post by meistersreign on 2014-04-07
I could be wrong, but I don't think jockey is related to the graphics card drivers. You were more than likely using the open source drivers. Would you mind posting what exactly the radeon program left is, and what it's trying to remove with it? Usually when uninstalling a program it will only uninstall the dependencies that it relies on. If another program on your system happens to need one of those dependencies, it wouldn't be uninstalled. But before you did something like that I'd make a backup, but let's see exactly what it's trying to remove.

---

### Post by buzzingrobot on 2014-04-07
Check at nvidia.com to see which proprietary Nvidia driver supports that card.

---

### Post by grahammechanical on 2014-04-07
As I understand things, the open source video driver for AMD/Ati is called Radeon and the open source video drvier for Nvidia is called Nouveau and the development of both is somehow connected to the Xorg developers. Ubuntu does not use jockey unless this is an older version of Ubuntu. Newer version use ubuntu-drivers. Which version of Ubuntu are you using? You may need to re-install jockey. If using a newer version of Ubuntu:
 
Whether using a terminal or Recovery Mode>Root this command should install the newest but standard proprietary driver for whatever card we have

```
 ubuntu-drivers autoinstall
```

I have tested this in my machine with an Nvidia card. To see a list of available drivers

```
ubuntu-drivers list
```

To see what card we have and a list of drivers

```
ubuntu-drivers devices
```

Allow time for the commands to do their job. I have never had an AMD/ATI video card on this machine. Just Nvidia but my install of 14.04 has these two drivers installed xserver-xorg-video-radeon and xserver-xorg-video-ati. This is as well as Nouveau which I am at present using.

I hope I have muddied the waters a little. :)

Regards.

---

### Post by tank.tmt on 2014-04-12
Ok - so synaptic won't remove the radeon thing unless I fix packages - I try to do that and it still won't the list of things that it says will be affected is huge - is there a way to capture it as a text file because I couldn't select it to copy and paste?

---

### Post by tank.tmt on 2014-04-12
I've tried these:

[LIST=1]
[*]sudo apt-get update
[*]sudo apt-get autoclean
[*]sudo apt-get clean
[*]sudo apt-get autoremove
[/LIST]
But have stopped short of this

[LIST]
[*]sudo dpkg --remove -force --force-remove-reinstreq packagename
[/LIST]

---

### Post by meistersreign on 2014-04-12
Perhaps you don't need to remove the radeon package from the system. Are you still using  nvidia-current drivers and experiencing that 640x800 resolution? The idea came to me that maybe even though you have the nvidia drivers installed, since you were using the open source drivers in the past, they didn't really need a configured xorg - but nvidia proprietary drivers usually do. You should have an nvidia settings manager, usually in there you can change the resolution,  among other things. If not you may need to install it. There's also the "sudo nvidia-xconfig" command from the terminal that would normally give you a working xorg config file. I'd try the GUI first though as I'm not sure Ubuntu uses nvidia-xconfig.

---


---
title: "Ubuntu 12.04 - Black screen on boot. Android source compiling."
date: 2013-06-25
forum: New to Ubuntu
---

### Post by zkk007 on 2013-06-25
Black Screen on boot after running Android source building, specifically installing java required packages. **See post 4 for solution.**


Hi all,

I have used Ubuntu a little in the past and know my way around for daily use. I installed 12.04 on my Samsung Series 5 Ultrabook in a dual boot configuration. I use the stock bios to chose which system to boot (Windows 8 or Ubuntu). 

I did a fresh install, updated any updates, and did some work relating to Android source building. I restarted (Restart button said something like "Restart for updates to take effect". Upon boot, I get the Ubuntu boot screen with recovery option, a flash of the Ubuntu logo, and then the black screen. I have a feeling it has something to do with the system updates since I have rebooted Ubuntu on this computer in the past. 

My research has shown that it might be related to the graphic drivers. I can boot into Ubuntu recovery and have tried adding [SIZE=2]**nomodeset  **to the [/SIZE]linux/boot line in GNU GRUB, but now I get stuck on the Ubuntu load screen with all five dots colored orange. It has been on this screen for a good 15 minutes. 

The ultrabook has a Intel i5 processor with Intel HD4000 graphics. 

I can get into the system using the failsafeX mode if needed.

Any help would be appreciate!

---

### Post by ty74 on 2013-06-25
I am guessing you need to restore your original graphics drivers before the updates took effect. [http://askubuntu.com/questions/159663/how-to-reset-the-xorg-xserver](http://askubuntu.com/questions/159663/how-to-reset-the-xorg-xserver)

---

### Post by Bashing-om on 2013-06-25
zkk007; Hi ! Welcome to the forum .

Sounds possible that the update may have broken a driver .. but, intel ? Not to likely...Let us check and see:
To see your graphics card and info:
```

sudo lshw -C display
lspci -nnk | grep -iA3 v

```

[INDENT][INDENT]then we will see[/INDENT][/INDENT]

---

### Post by zkk007 on 2013-06-25
Hi, thanks for the response, but I figured out my problem.

When I was installing Android dependencies I noticed that I had a lot of ```
"Removing xserver-xorg-video-vesa-lts-quantal ..."
``` lines. In my research I had briefly read that this will mess with my drivers (not 100% sure why, but that's the gist I got from reading). I tried many things from removing "splash" from the kernel line, nomodeset, to trying to install the whole xserver-xorg-video dependencies from online in recovery mode and also trying to do it from a USB with the .deb files on it. None of this worked.

**To anyone who is compiling Android CM10.1 source code: **When you get to installing the java required packages, the code in terminal will automatically delete the xserver files as it is replaced (I think) by other files. This lead me, and possibly you, to a black screen when you rebooted. There is an easy fix!

Reboot into Ubuntu recovery with networking abilities and log in. Then

```
sudo apt-get update
sudo apt-get install linux-generic-lts-quantal xserver-xorg-lts-quantal
```

Wait for it to finish installing and reboot. Hopefully that fixed it for you too!

---

### Post by Bashing-om on 2013-06-25
zkk007; Outstanding !

That is troubleshooting procedure at it's best !

[INDENT][INDENT]enjoy
[/INDENT][/INDENT]

---


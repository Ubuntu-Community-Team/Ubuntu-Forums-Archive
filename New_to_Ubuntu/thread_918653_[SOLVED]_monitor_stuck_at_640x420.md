---
title: "[SOLVED] monitor stuck at 640x420"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by bumanie on 2008-09-13
My monitor previously ran with 1024x768 resolution. Since kernel upgrade (which I have now removed and am booting with previous working Kernel) is stuck at 640x420. Graphics card nvidia 8600gt - have uninstalled and reinstalled hardware driver. Nvidia settings-manager has no higher resolutions available. How to fix this???

---

### Post by Unterseeboot_234 on 2008-09-13
Same thing, only I'm stuck on 320x210 for this partition.

---

### Post by bumanie on 2008-09-13
It's fixed. Booted into recovery mode and did a "attempt to fix xserver" - It worked. Now I feel stupid for not thinking of trying > sudo xfix in ternminal that probably would've worked too.

---

### Post by Unterseeboot_234 on 2008-09-13
This IS ridiculous. I haven't checked my sound yet. Last update obliberated my audio. This what I did to get back to a Hi-Res desktop.

I followed advice from this link **[monitor resolutions]("https://help.ubuntu.com/community/FixVideoResolutionHowto")**

under the Heading: **Adjust Only Resolution Settings on Dell Laptop**
and, I don't have a Dell, I have the nVidia tho'. I did change to the Vesa graphics card option.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and the above command in Terminal brings up a terminal program. you are supposed to be able to select multiple resolutions with your keyboard. I don't know what magic key does select the options available. I use arrow keys to select 1024 x 150 and hit RETURN

I get a warning that xOrg file got overwritten. CTL-alt-Backspace, I come back up to 1440x900, Menu --> Applications --< System Tools --> nVidia Settings GUI tells me I will need to reconfigure xOrg.

Moral of the story, xOrg.conf with nVidia option, with the auto-update glx made my xOrg file junk. Envy script along with nvidia cannot auto-detect your monitor and that's when xOrg.conf file begin to corrupt over time.

From now on, I will make a copy of xOrg.conf BEFORE I make any future updates.

hope this helps

---

### Post by bumanie on 2008-09-13
> sudo dpkg-reconfigure -phigh xserver-xorg 
that is the outmoded method of fixing xserver the new is > sudo xfixTry that. Just noticed my sound is gone too. I'll have a look at that soon.

---


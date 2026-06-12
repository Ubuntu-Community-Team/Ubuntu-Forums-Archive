---
title: "ATI/AMD Driver Issues"
date: 2012-01-12
forum: New to Ubuntu
---

### Post by Empyreon on 2012-01-12
Hello 
I have an HP dv6 - 3064ca and my laptop has two graphics cards:
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series]

I have gone through 'update drivers' and i get two drivers for the graphics cards. [IMG]http://i531.photobucket.com/albums/dd360/nimazza/Screenshotat2012-01-12130254.png[/IMG](in Attached picture) The first one comes up with the error when i try and download it, the second driver (third in the list) works when i download it, but then is deactivated when i try the first one. :confused::confused::confused::confused:
Please help me out guys D:

---

### Post by ubiquitin.jf on 2012-01-12
I had this problem. I was able to resolve it by removing the fglrx package before trying to install the fglrx-update version using Synaptic rather than Jockey.

---

### Post by Empyreon on 2012-01-12
I tried that, but didn't work. Maybe i did it incorrectly, could u explain it in a more detailed manner? maybe with images? Thx in advance!

---

### Post by Mark Phelps on 2012-01-13
Don't try to install the Post-Release drivers.  We have been getting LOTS of posts about how they don't work.

---

### Post by tastro on 2012-01-13
i have the same issue with the "post-release".

---

### Post by Empyreon on 2012-01-13
> **Mark Phelps said:**
> Don't try to install the Post-Release drivers.  We have been getting LOTS of posts about how they don't work.

ok, then what should i do? even with the bottom driver activated my graphics cards aren't fully functional. I can see time delays in every media i play, which never happened in windows 7.

---

### Post by Mark Phelps on 2012-01-13
Additional Drivers offers a choice of TWO ATI driver sets.  The Post-release is known NOT to work.  The other choice should work.

Could also be that your laptop is using the lower-end graphics chipset by default.  Linux doesn't support switchable graphics -- that is a Windows feature.  To get the higher-end graphics working, you will have to find a way to disable the lower-end graphics chipset -- probably a BIOS setting.

But, when you do that, it will ALSO be disabled for Win7.

As said, Linux doesn't really support switchable graphics.

---

### Post by Empyreon on 2012-01-14
> **Mark Phelps said:**
> Additional Drivers offers a choice of TWO ATI driver sets.  The Post-release is known NOT to work.  The other choice should work.

Could also be that your laptop is using the lower-end graphics chipset by default.  Linux doesn't support switchable graphics -- that is a Windows feature.  To get the higher-end graphics working, you will have to find a way to disable the lower-end graphics chipset -- probably a BIOS setting.

But, when you do that, it will ALSO be disabled for Win7.

As said, Linux doesn't really support switchable graphics.

I dont really mind that, so could i know how to switch it to high graphics only? Also will it be irreversible to change the graphics back to low?

---

### Post by Mark Phelps on 2012-01-15
First, you need to confirm that your PC has switchable graphics.  You will need to check the documentation that came with it, or go to the sellers website to find out that info.

---

### Post by Empyreon on 2012-01-15
> **Mark Phelps said:**
> First, you need to confirm that your PC has switchable graphics.  You will need to check the documentation that came with it, or go to the sellers website to find out that info.

What do you mean? I know it is switchable. I switch then all the time on windows 7.

---

### Post by Mark Phelps on 2012-01-15
OK, then read through the following:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

---

### Post by Empyreon on 2012-01-15
> **Mark Phelps said:**
> OK, then read through the following:

[https://help.ubuntu.com/community/HybridGraphics]("https://help.ubuntu.com/community/HybridGraphics")

Ok thank you, I will try it out. I have some other questions, hope u don't mind if I PM u.

---

### Post by Empyreon on 2012-01-15
Unfortunately, it isnt working i keep getting 'no such file' for the switcheroo.
```
root@nima-HP-Pavilion-dv6-Notebook-PC:~# sudo su
root@nima-HP-Pavilion-dv6-Notebook-PC:~# grep -i switcheroo /boot/config-2.6.*
grep: /boot/config-2.6.*: No such file or directory
root@nima-HP-Pavilion-dv6-Notebook-PC:~# ls -l /sys/kernel/debug/vgaswitcheroo/switch
ls: cannot access /sys/kernel/debug/vgaswitcheroo/switch: No such file or directory
root@nima-HP-Pavilion-dv6-Notebook-PC:~# lspci | grep VGA
01:05.0 VGA compatible controller: ATI Technologies Inc M880G [Mobility Radeon HD 4200]
02:00.0 VGA compatible controller: ATI Technologies Inc Madison [AMD Radeon HD 5000M Series]
root@nima-HP-Pavilion-dv6-Notebook-PC:~# ls /sys/kernel/debug/vgaswitcheroo
ls: cannot access /sys/kernel/debug/vgaswitcheroo: No such file or directory
root@nima-HP-Pavilion-dv6-Notebook-PC:~# 
```

---

### Post by Mark Phelps on 2012-01-16
> **Empyreon said:**
> Ok thank you, I will try it out. I have some other questions, hope u don't mind if I PM u.

Actually -- YES, I DO mind.  Read my sig ... I wrote it for a reason.

---

### Post by Empyreon on 2012-01-16
> **Mark Phelps said:**
> Actually -- YES, I DO mind.  Read my sig ... I wrote it for a reason.

Oh true,  my bad. Can u help me with switcheroo? (The current forum)

---

### Post by Mark Phelps on 2012-01-16
> **Empyreon said:**
> Oh true,  my bad. Can u help me with switcheroo? (The current forum)

Sorry, don't have the money to afford one of the newer PCs with switchable graphics, so don't really have first-hand experience with it.

You can try looking through the posts on the Phoronix forum.  They do a lot of leading-edge work with new video technologies, especially those using AMD and Nvidia video.  They may have some advice that will help.

---


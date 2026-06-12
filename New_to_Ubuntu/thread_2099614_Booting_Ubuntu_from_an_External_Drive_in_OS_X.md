---
title: "Booting Ubuntu from an External Drive in OS X"
date: 2012-12-29
forum: New to Ubuntu
---

### Post by HydrogenSulfite on 2012-12-29
Hello, there, Ubuntu forum posters. Last night, I created a Linux-ready partition on one of my external hard drives. I then booted up my Ubuntu installation DVD, loaded the installer, and started to install the system. The installer automatically noticed that my external drive had a partition fit for Ubuntu, and successfully installed there. Now, I am clueless as to how the newly-installed OS can be booted from this drive. Logically, I tried booting my computer whilst holding the alt/option key, but that only gives me two options: my main drive, and a drive entitled "Windows." Thinking that the second drive might actually be my Ubuntu drive, I chose that one. Upon selecting this drive, a grub error screen appears. 

Is there something here that isn't being done correctly? Is there a special command I can input to resolve the grub error? This Linux nub here has nary an idea as to how his problems can be fixed.

---

### Post by Andy45 on 2012-12-30
Is this a USB drive? If so, it should appear as a usb device in your BIOS boot menu.

---

### Post by Powned2death on 2012-12-30
I was trying the same thing basically for two days now. I have an extra internal drive that I enclosed. It has Ubuntu on it and my internal hdd has win 7 ultimate on it. My bios allows me to change order to whatever settings. But when it goes to boot it says 
unknown filesystem
grub rescue>

Other times it will just sit with a cursor and blank screen. I tried using Easybcd in win 7 to set-up boot records and save settings. Only after re-installing ubuntu 3x did I figure this one out. 

I did however get it to work one time with easybcd. 
My set-up was win 7 on internal drive and ubuntu on the ext/hdd (mass storage). It booted up and loaded but when i went to use the programs it lagged and not responded. So i had to re-boot cause it was locked-up. Then when I went to reboot I got the same message thats been haunting me for two days Unknown filesystem & grub rescue>. This was btw right before the last time I re-installed ubuntu. So far might best luck has been with Easybcd. There are a couple of tuts on youtube. for using it. You might have better luck.
Several other forums and even this one say win 7 on ext/hdd will not work so dont waste your time. I think I've given up pretty much because once you do get it running it lags and freezes anyway!!  Guess I just have to manually remove and insert hdd when I want to swithc OS's. A pain in the A and also wears on my contact pins.

---


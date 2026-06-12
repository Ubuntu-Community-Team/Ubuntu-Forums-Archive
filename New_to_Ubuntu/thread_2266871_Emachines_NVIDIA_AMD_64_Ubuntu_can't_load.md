---
title: "Emachines NVIDIA AMD 64 Ubuntu can't load"
date: 2015-02-25
forum: New to Ubuntu
---

### Post by Anh_Tran on 2015-02-25
Hi all,

I have a desktop, Emachines, NVIDIA graphics card and AMD proc 64 bits (great, all weirdo). It already has a Windows 7 on that; perfectly fine. No Internet connection for now. The problem is I can't load into the normal mode, the screen is all black and no mouse, no keyboard response. The only thing that I can do is go to Advanced Options on GRUB, go to Network, say Yes and it will kick me in a safe-mode or something. I've been playing around with Xorg.conf and some similar files. None works. Any ideas would be greatly appreciated.

// it seems like the Unity is broken, but I'm not exactly sure. I've tried different of Ubuntu, 14.04, 14.10, all 64 bits and AMD

;)

---

### Post by Anh_Tran on 2015-02-28
Later on I found out that my graphics card is GeForce 6150SE nForce 430. I try installing NVIDIA driver as ubuntu package and binary drivers. I got error for both and the screen is frozen after log in, or it may work but with the lowest screen resolution 740 x 680 (?). Any help would be appreciated.

---

### Post by kc1di on 2015-02-28
Hello  Anh_Tran  I have the same Graphics card as you.  in order to get it to work you have to boot the first time with nomodeset parameter.

you can do that with the Live dvd/usb by hitting the tab key and selecting F6 select nomodeset and hit the esc key. 
When it boots you can then install ubuntu.  After the install you'll have to boot the first time with nomodeset again.  Go to a terminal and install the nividia-304 driver.

```
sudo apt-get update
sudo apt-get install nvidia-304
```

when it is finished reboot and you should be good to go. 
good luck :)

---

### Post by Anh_Tran on 2015-02-28
Thanks for your help kc1di. Actually my screen freezes right after login, so I ctrl + alt + f1 to go to terminal mode, 304 is the right number. I've tried nvidia-304-updates as well but no luck; so the only option left is to reinstall this Ubuntu. Can you describe the process of live dvd boot in nomodeset again? I know I'm supposed to do something like this

[http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu](http://askubuntu.com/questions/38780/how-do-i-set-nomodeset-after-ive-already-installed-ubuntu) 

but I'm not sure about doing that before installing Ubuntu.

p/s: I got it. F6 with purple screen does the trick

---

### Post by Anh_Tran on 2015-03-01
kc2di, I did what you told me. It at first seem to be alright but the unity freezes right after the login. Is there anyway to fix this? Thanks!

---

### Post by kc1di on 2015-03-01
Give us a little more info on the machine. CPU speed, Ram, ETC -- it may be that unity will not work with your machine and you'll need to use a less demanding desktop.
I  suggest Mate - or XFCE

---

### Post by Anh_Tran on 2015-03-01
```

lscpu

```

> 
Architecture: x86_64
CPU op-mode(s): 32-bit, 64-bit
Byte Order: Little Endian
CPU(s): 2
On-line CPU(s) list: 0,1
Thead(s) per core: 1
Core(s) per socket: 2
Socket(s): 1
NUMA node(s): 1
VendorID: AuthenticAMD
CPU Family: 16
Model: 6
CPU Mhz: 800.000
BogoMIPS: 5424.17
Virtualization: AMD-V
L1d cache: 64K
L2i cache: 64K
L2 cache: 1024K
NUMA node0 CPU(s): 0,1


RAM ~4GB. I would be surprise if this machine can't run Ubuntu... My impression is there is something wrong with the graphics card. I also have Windows 7 running parallel (dual boot) and it doesn't have any problem at all.

update 1: I followed [http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/](http://itsfoss.com/fix-unity-freezes-after-login-ubuntu-14-04/) to remove all nvidia packages, then it boots just fine. The screen resolution is extremely low, but it's functional. :p any suggest?

---

### Post by kc1di on 2015-03-01
I have a very similar set up here - and my Nvidia card is the same as yours and since the latest updates i've been unable to run unity either.  I think your right about the graphics card.
for some reason it will not run unity any longer.  I switch to Mate. and it runs fine , you still have to use the 304 driver though. I'm not sure what changed but filed a bug report about it.
till they fix whatever it is guess will have to use a different desktop , KDE, Mate, Lubuntu and XFCE all work fine. but unity crashes everytime now. 

Sorry maybe someone else has it running with that card.

---

### Post by Anh_Tran on 2015-03-01
Thank you very much kc1di. I have it run at low resolution with no nvidia driver now. It's functional, but the screen resolution is 740x680 (4:3); it might be that the graphics card is actually not GeForce 6150SE nForce 430 because the computer is refurbished. I witnessed this happen with my personal laptop: I couldn't find the correct driver for my graphics card in Windows. Only when I called the manufacturer (Dell) then they run a detection on my computer, then it detects the correct driver. I'm not sure if Ubuntu has the same capability, but if you know please let me know. Thanks again kc1di!

---

### Post by kc1di on 2015-03-02
in Ubuntu to can simply go to a terminal and type```
lspci | grep VGA
```

you'll get an output like this that will tell you what video card your running. ```
00:0d.0 VGA compatible controller: NVIDIA Corporation C61 [GeForce 6150SE nForce 430] (rev a2)
```

You can just copy and past the above command in your terminal.

---


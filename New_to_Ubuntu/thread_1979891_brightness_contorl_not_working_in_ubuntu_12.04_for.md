---
title: "brightness contorl not working in ubuntu 12.04 for sony"
date: 2012-05-14
forum: New to Ubuntu
---

### Post by robotu on 2012-05-14
hi
i own a sony vaio vpceh25en laptop... i recently installed the ubuntu 12.04 platform after reading a lot of good reviws about it and am liking it also but i am facing just one little problem that the BRIGHTNESS doesnt change by using the fn + f5 or f6 key it just shows in the bar that the brightness has decreased but no effect...
also i have reasearched a lot to rectify this problem within this forum and outside too but nothing helped me much....

PLEASE HELP.....

---

### Post by Gaba_p on 2012-05-14
Have you checked available answers like these?

[http://ubuntuforums.org/showthread.php?t=1468734](http://ubuntuforums.org/showthread.php?t=1468734)
[http://ubuntuforums.org/showthread.php?t=1875126&highlight=brightness+laptop](http://ubuntuforums.org/showthread.php?t=1875126&highlight=brightness+laptop)
[http://askubuntu.com/questions/128285/brightness-controls-not-working-on-a-sony-vaio-vpcy2](http://askubuntu.com/questions/128285/brightness-controls-not-working-on-a-sony-vaio-vpcy2)
[http://ubuntuforums.org/showthread.php?p=11910629#post11910629](http://ubuntuforums.org/showthread.php?p=11910629#post11910629)

Cheers.

---

### Post by coffeecat on 2012-05-14
I have a Vaio VPCEJ1Z1E which has the Nvidia GeForce 410M GPU which a google search suggests that yours does too. Make sure you have the nvidia proprietary driver installed from Additional Drivers and then apply the xorg.conf fix as described in this post - which works for me - and reboot.

[http://ubuntuforums.org/showpost.php?p=11613896&postcount=7](http://ubuntuforums.org/showpost.php?p=11613896&postcount=7)

The third link that Gaba_p posted has the same fix and tells you how to edit your /etc/X11/xorg.conf file.

---

### Post by ratnadeep gaikwad on 2012-12-09
I have a sony Vaio VPCEG3AEN and the following worked for me:

I opened the file /etc/X11/xorg.conf and changed the below section

sudo gedit /etc/X11/xorg.conf

Initially the setion was:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection


Changed it to:

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option  "NoLogo"        "True"
    Option "RegistryDwords" "EnableBrightnessControl=1"
EndSection


Note: Some forums suggest a change in the /etc/default/grub file
You need to revert back those changes for this to work

---

### Post by srinivas karthik on 2013-07-01
hi,

 I have  a Sony Vaio SVE15115enb (E-series) with ubuntu 12.04. I had this brightness settings problem and tried lot of commands and edited some files yet not solved which suggested in different posts in other websites. I  finally got the solution.

I have a 1GB grahic card AMD RADEON which ubuntu  doesn't recognises. 

1) So, go to SYSTEM SETTING --> then ADDITIONAL DRIVERS.you can find the drivers which are all inactive. 
2) Make the graphic card driver "active".It takes some time to get install.
3)Then RESTART. and it works with Fn + F5 or F6.

hope it works for you.

It also solved another problem too.Whenever I start my ubuntu, the screen gets shake.So every time i start my laptop  I close laptop lid and after few seconds I re-open the lid.But now its working normally.No more screen shaking or scramble.

---

### Post by coffeecat on 2013-07-01
> **srinivas karthik said:**
> I have a 1GB grahic card AMD RADEON which ubuntu  doesn't recognises. 

1) So, go to SYSTEM SETTING --> then ADDITIONAL DRIVERS.you can find the drivers which are all inactive. 
2) Make the graphic card driver "active".It takes some time to get install.
3)Then RESTART. and it works with Fn + F5 or F6.

@srinivas karthik, Ubuntu does recognise your card, but it seems from what you say that the default open source driver does not allow screen brightness control with your particular AMD card. You have installed the proprietary driver and this has fixed it for you.

However, the OP is using a Sony laptop with a nvidia card and the posted solutions are for nvidia as well. Since the OP has not logged in since they posted over a year ago, I'm closing this thread. If anyone needs help with brightness control with a Sony laptop, please start a new thread. Different cards often need different solutions.

---


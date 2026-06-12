---
title: "Installation problems - Dell Inspiron 15 5577 with NVIDIA GPU. Please advise!"
date: 2018-01-11
forum: New to Ubuntu
---

### Post by lightrey on 2018-01-11
Hey!

I'm in the beginning phases of my Linux journey. I did some searching on the forum and found people with similar issues, but they were either not resolved or the solution didn't quite fit my problem so I'm posting here. This is  my situation - 

- Just got a new Dell Inspiron 15 5577 with NVIDIA GTX 1050 GPU ([https://www.amazon.com/gp/product/B06XFGF7SN/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1](https://www.amazon.com/gp/product/B06XFGF7SN/ref=oh_aui_detailpage_o01_s00?ie=UTF8&psc=1))
- Created a bootable USB with Rufus and verified the integrity on another laptop. No errors found when I checked the disc and the live version worked great
-  I disabled secure boot on my new laptop
- When I boot my new laptop with the USB and check the disc for defects, it returns 0 errors but freezes when trying to reboot... I had to do a hard reset.
- When I try to boot a live Ubuntu on my new laptop, it freezes on the Ubuntu loading screen and requires a hard reset

I've done some research and read a lot of people are having a hard time with NVIDIA GPUs and Linux, but have gotten around that by somehow doing a chmod command or something. I also checked the ubuntu certified hardware list and my laptop is unfortunately NOT listed. I hate myself for not checking before purchasing, but I didn't even know it existed! I assumed any Dell laptop would be able to run Linux  #-o 

My questions are as follows:
1) Is it possible to install linux on a machine that isn't listed on the official certified list?
2) Are my problems stemming from the NVIDIA GPU drivers or something else?
3) Should I keep fighting the good fight and figure out how to get Linux installed, or just return the laptop and get another one?


Thanks!
Rey

---

### Post by Autodave on 2018-01-11
It is possible to install on a mcahine that isn't on the list.  As far as the Nvidia GPUs are concerned, I much prefer them over the others.

Are you trying to dual boot w/Windows? Did you turn off *fast boot?*

---

### Post by lightrey on 2018-01-11
I'm dual booting with Windows now, but once I get Linux up and running I plan on wiping Windows. 

I turned off fast boot and it still won't work. When I try loading the live version, it just freezes on the Ubuntu load screen. So frustrating! Any other ideas? 

Thanks,
Rey

---

### Post by Bashing-om on 2018-01-11
lightrey; Hello -


Try booting with the nomodeset boot parameter. Once booted into the install one can then install the proprietary driver for nvidia.
> 
A common kernel (boot)parameter is nomodeset, which is needed for some graphic cards that otherwise boot into a 
               black screen or show corrupted splash screen. See [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) on how to use 
               this parameter


[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by a2buntu on 2018-03-08
lightrey, I am about to follow in your footsteps with my dell inspiron 15 5577.
how did you proceed?

---

### Post by wildmanne39 on 2018-03-08
Hello and welcome to the forum a2buntu, please start your own thread, you will be more likely to receive the help you need that way.

Thanks

---

### Post by tnthomas on 2018-03-08
My laptop is a Dell inspiron 15 7567 with the gtx 1050, running Ubuntu 16.04....installed on a Samsung 960 EVO M.2 ssd.

You disabled secure boot- that is good.  Are you booting in legacy or uefi?

> **lightrey said:**
> read a lot of people are having a hard time with NVIDIA GPUs and Linux,

I can't imagine that, Linux and nvidia have always been quite compatible.......maybe it was AMD/ATI GPUs?

---

### Post by wildmanne39 on 2018-03-08
Please do not post duplicates, if you need to add more information just edit your previous post.

Thanks

---

### Post by monkeybrain20122 on 2018-03-08
> **tnthomas said:**
> 


I can't imagine that, Linux and nvidia have always been quite compatible......



Unless you have a laptop with Optimus, then it can be a bit tricky to set up from what I heard (luckily I have never had an optimus machine)

---


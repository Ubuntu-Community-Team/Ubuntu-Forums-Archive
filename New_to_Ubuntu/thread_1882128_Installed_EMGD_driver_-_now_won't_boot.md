---
title: "Installed EMGD driver - now won't boot"
date: 2011-11-16
forum: New to Ubuntu
---

### Post by TCAllen07 on 2011-11-16
Hi all, 

I installed Ubuntu 11.04 (Natty) on my Dell Mini 10v (aka Inspiron 1011), and found that using a second monitor via VGA output slowed everything down drastically. A friend said it probably didn't have the right graphics driver, so it was using the CPU to run the second monitor instead of using hardware acceleration? :-s 

A blog indicated that my netbook has a GMA 500 graphics chip. So I found [this wiki]("https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo") suggesting the EMGD might be my best choice. I followed their instructions, which seemed innocuous enough (just adding a repository and installing the driver...), specifically: 
```
sudo add-apt-repository ppa:gma500/emgd-1.8
sudo apt-get update
sudo apt-get install xorg-emgd emgd-dkms
sudo emgd-xorg-conf
```

And restarted for the changes to take effect. And now it won't boot!!

It says to use this to remove: 
```
sudo apt-get purge emgd-support*
```

But can I try this from the recovery mode option in Grub? I figured I'd ask before doing anything to potentially screw it up worse...



If it's pertinent, another blog suggested this to find out about your display, and maybe I don't have that driver after all?
```
trevor@xubie:~$ lspci |grep Display
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
```


EDIT: 
Here's a picture of the screen where it freezes when I try to boot, in case it helps. it's a bit tough to read, so I'll try to copy it word-for-word when I get a chance this evening or tomorrow.  (See attached jpg)

---

### Post by mikewhatever on 2011-12-15
The Dell Mini 10v doesn't have GMA500, despite what the blog says. If it had, you would have seen something like this in the output of lspci:
```
00:02.0 VGA compatible controller: Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

```

Dell has many netbook models, all confusingly called Mini 10. The one with GMA500 is known as 1010.

---

### Post by TCAllen07 on 2011-12-16
Thanks. That makes sense, as the Dell "Mini 10" is the 1010 and I have the "Mini 10v" which is the 1011. 

In any case, I decided to fresh install with 11.10 to start over, so the issue became moot. I'll mark this as closed. Thanks again!

---


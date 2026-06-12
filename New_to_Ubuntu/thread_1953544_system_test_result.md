---
title: "system test result"
date: 2012-04-06
forum: New to Ubuntu
---

### Post by quarkhirad on 2012-04-06
I ran the application system testing. It detected a lot of stuff its quite brilliant. However, there are just two things 

1) It detected my laptop as having 2.9Gb of ram. But i have 8GB. 

2) When i connected my TV hdmi cable to my laptop. I could not change my display to the tv. I even tried going to system setting display and then detect displays. 

Note : in windows i connect the cable to the tv. Then using tv remote i select hdmi input. On my laptop i then press Fn + F2. it then changes the display. 

I have a dell L502X laptop with ubuntu 11.10 installed.

Can someone please explain no 1 and please solve 2 as i need this to connect the overhead projector in college for my presentations. Please help

---

### Post by PhantomTurtle on 2012-04-06
1. Do you have 32-bit or 64, although you should have gotten a pae kernel even with 32-bit. Check to see if you have pae or not. You don't have to if you use 64-bit.
2. You might need proprietary drivers for this. Can you post what video card you have.

---

### Post by quarkhirad on 2012-04-06
> Do you have 32-bit or 64, although you should have gotten a pae kernel even with 32-bit. Check to see if you have pae or not. You don't have to if you use 64-bit.

My system is a 64 bit. However, ubuntu is 11.10 32 bit. Please explain what is PAE

> 
2. You might need proprietary drivers for this. Can you post what video card you have.

I have an N-vida graphics card. For further deltails you can also read my post about install drivers for my laptop. 
```

http://ubuntuforums.org/showthread.php?t=1932392
```

---

### Post by PhantomTurtle on 2012-04-06
PAE is a Physical Address Extension Kernel. It will let you use more than 3GB RAM(I think up to 64GB) on a 32-bit kernel. Here are instructions on how to check if you can get it and how to install it: [https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE"). Alternatively you can just get the 64-bit version, which requires you to reinstall.
I'm sorry I cannot help with your Graphics card problem. Maybe someone else can help with that. If I get more info however I will post here.

EDIT: Also I think you can use the utility that comes with the Nvidia drivers to try and do teh multi monitor thing.

---

### Post by quarkhirad on 2012-04-06
> **PhantomTurtle said:**
> PAE is a Physical Address Extension Kernel. It will let you use more than 3GB RAM(I think up to 64GB) on a 32-bit kernel. Here are instructions on how to check if you can get it and how to install it: [https://help.ubuntu.com/community/EnablingPAE]("https://help.ubuntu.com/community/EnablingPAE"). Alternatively you can just get the 64-bit version, which requires you to reinstall.
I'm sorry I cannot help with your Graphics card problem. Maybe someone else can help with that. If I get more info however I will post here.

EDIT: Also I think you can use the utility that comes with the Nvidia drivers to try and do teh multi monitor thing.

Thanks. But the how to only talks about 10.04 and previous verssion. Please give me guide for 11.10.

---

### Post by PhantomTurtle on 2012-04-06
> **quarkhirad said:**
> Thanks. But the how to only talks about 10.04 and previous verssion. Please give me guide for 11.10.

Don't worry it's the same on anything higher than 10.04.

---


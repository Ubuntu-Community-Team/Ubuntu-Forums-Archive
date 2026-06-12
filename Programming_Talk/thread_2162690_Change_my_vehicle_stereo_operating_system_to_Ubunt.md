---
title: "Change my vehicle stereo operating system to Ubuntu? Win Embedded 6.0 (hyundai)"
date: 2013-07-15
forum: Programming Talk
---

### Post by Altazink on 2013-07-15
Dont know if this is the right area to post this in but i figure it will be moved if not.

I currently have a ugraded stereo package on my 2013 hyundai veloster (sat nav, backup camera, bluetooth and large touch screen etc.) and have been using ubuntu on my computers on and off for a few years.

My issue is my stereo is limited on its options on what i can do with it.... however I have been able to access its base operating system of windows embedded CE 6.0. and i have full access to make changes. This leads me to believe I may be able to find a way to dual boot the system so I have the option of going into the stereo or a version of ubuntu. I am just curious on if anyone has any thoughts on which version of ubuntu would best work to load etc.

I know many other people who own this car or the advanced stereo on other hyundai models would be interested in this information as well as it presents a mod option as well as the possibility to expand ubuntu.

Basically what i need to start is the version of ubuntu that would work on it.. and the way to get it loaded within windows embedded ce 6.0. If you provide the way to make it dual boot too you would be my hero lol.

I was thinking a phone operating system version of ubuntu as it is probably set to work of the same processor type as my stereo would have would be needed.

thank you

Altazink

---

### Post by lukeiamyourfather on 2013-07-15
If you install Ubuntu on the machine it will likely lose all meaningful functionality (backup camera, navigation, Bluetooth, etc.) because those require specialized drivers and software. There might be open source alternatives but I haven't seen any before personally. Also, just because you can doesn't mean you should. I love Linux as much as the next guy but the last thing I want to do is **** around with a terminal or updates to get my GPS to work.

---

### Post by tgalati4 on 2013-07-15
You would need to do some research to find out what CPU your car computer is running.  A quick google search brings up:  [http://stackoverflow.com/questions/914778/windows-mobile-6-cpu-architectures](http://stackoverflow.com/questions/914778/windows-mobile-6-cpu-architectures)

So, unless you compile a very stripped-down version of linux, I'm not aware of any distros that run on ARMv4 chipset.  Then, if you get it to run, you would need to find or write your own device drivers.  You would have better luck with velcro and a 7" Android tablet.

---

### Post by sanderj on 2013-07-15
> **tgalati4 said:**
> you would have better luck with velcro and a 7" android tablet.

lol. +1

---

### Post by lukeiamyourfather on 2013-07-15
There are builds of Windows Embedded CE 6.0 for x86, ARM, SH4 and MIPS. The ARM builds support multiple version of ARM but with some limitations depending on the version (v4, v5, v6, v7). Like I said before though, there's not really a point to installing Ubuntu on it even if you could.

---


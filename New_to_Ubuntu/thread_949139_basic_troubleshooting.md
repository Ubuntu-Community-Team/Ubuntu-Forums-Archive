---
title: "basic troubleshooting?"
date: 2008-10-15
forum: New to Ubuntu
---

### Post by mbinz on 2008-10-15
Hi
I am new to linux
I successfully(?) installed ubuntu 8.04 on a dell xps 1330. got compiz fusion running and everything else i need. this is the first time that i want to keep this (a linux) system as my primary one.

since 5 hours the laptop keeps "freezing" no key inputs - nothing. in about 5 hours this happend 4 times.

i really dont know where to start debugging... it could just be everything! please give me some advise what i should do, to track the error down.

hardware: dell xps 1330, intel T9300,4 gig ram, 128MB NVIDIA GeForce 8400M GS
software: ubuntu 8.04, gnome 2.22.3

Thanks a lot!

---

### Post by 73ckn797 on 2008-10-15
Search the forums using various keywords. It may require some time but will be worth it when you find the answer. Not the quick solution but a certain one.

---

### Post by mbinz on 2008-10-16
i know how to use a search. i just dont know where to start.

---

### Post by handydan918 on 2008-10-16
Next time it happens, try [raising skinny elephants.]("http://en.wikipedia.org/wiki/Magic_SysRq_key")

You maight also start looking through logs for messages. 

/var/log contains a lot of logs, and info can also be had in a terminal with ```
dmesg
```

This may be an issue of drivers, especially proprietary ones. I would start with using ```
lsmod
``` to find out what drivers are loaded for the hardware shown by ```
lspci
```
Paying particular attention to nvidia/ati video cards, and wireless devices that use ndiswrapper.

---

### Post by kpkeerthi on 2008-10-16
> **mbinz said:**
> Hi
I am new to linux
I successfully(?) installed ubuntu 8.04 on a dell xps 1330. got compiz fusion running and everything else i need. this is the first time that i want to keep this (a linux) system as my primary one.

since 5 hours the laptop keeps "freezing" no key inputs - nothing. in about 5 hours this happend 4 times.

i really dont know where to start debugging... it could just be everything! please give me some advise what i should do, to track the error down.

hardware: dell xps 1330, intel T9300,4 gig ram, 128MB NVIDIA GeForce 8400M GS
software: ubuntu 8.04, gnome 2.22.3

Thanks a lot!

Turn off compiz from System -> Preferences -> Appearance -> Visual Effects -> None. See if your stability improves.

If no luck, turn off nvidia driver from System -> Admin -> Hardware Drivers.

---

### Post by mbinz on 2008-10-16
Thanks for the replies.
i am going to turn off the nvidia driver.

one more thing: i noticed that the wifi led started to blink, when "active" (i guess when data is sent/received) - that started at the same time the freezing started. any ideas?

Thanks

---

### Post by handydan918 on 2008-10-16
> **mbinz said:**
> Thanks for the replies.
i am going to turn off the nvidia driver.

one more thing: i noticed that the wifi led started to blink, when "active" (i guess when data is sent/received) - that started at the same time the freezing started. any ideas?

Thanks

yep.

---

### Post by mbinz on 2008-10-18
after turning off the wireless devices (wlan, bluetooth) the laptop ran for 20 hours without a freeze - thats a record and i think that is the problem.
now i need to fix this problem. any help will be appreciated

---

### Post by mbinz on 2008-10-18
i think this is the right thread for my problem:
[http://ubuntuforums.org/showthread.php?p=5990291#post5990291]("http://ubuntuforums.org/showthread.php?p=5990291#post5990291")

---


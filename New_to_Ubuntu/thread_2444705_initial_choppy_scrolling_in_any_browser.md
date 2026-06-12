---
title: "initial choppy scrolling in any browser"
date: 2020-06-03
forum: New to Ubuntu
---

### Post by gerrard000 on 2020-06-03
Hi. Any fix for this? Only solution that I found is to keep nvidia x server opened and check preferred mode - maximum performance. But then gpu temp is higher +5-7°C. No way to keep core/mem clock to max 2100/12000mhz just for that. btw, I'm using 144hz monitor. Under Windows 10 is flawless and even moving windows is smoother. On any linux distro is not so good. On 60hz monitor is not noticeable, but on 144hz it is. 

edit: If not scrolling 2-3 seconds and start scroll, first scroll is choppy. After that is smooth...until stop scrolling for 2-3 seconds again. 
i7 4771, gtx 1660ti, ubuntu 20.04, nvidia driver 440.64

---

### Post by dino99 on 2020-06-03
Even get such issue with a xeon igpu here: scrolling is 'jumping back and forth'. Looks to be a kernel module problem, but have not tested with an older kernel yet.

---

### Post by gerrard000 on 2020-06-03
I tried eos and mint too. Same result. With kde plasma desktops (kubuntu and kde neon) when scroll text get little blurred. It's very strange, can't explain. Looks like...disabled AMA option on monitor (Advanced Motion Accelerator). Looks like slow pixel reaction.
For now will use ubuntu. I like it. It's user friendly for newbie like me and if have problem will get more google results, becuase is most popular distro :D. But these few little bugs are annoying. Like this and lacks of option to control middle scroll speed. Anyway thanks for fast response. :)

---

### Post by sdsurfer on 2020-06-03
I would check graphics drivers, see which one is in use, see if there is an Nvidia driver available and that is selected. In a terminal,
```
lspci | grep VGA
```

Will tell you what is available.

I have had issues and found in Software and Updates -> Additional Drivers the Nvidia driver loaded but it was using the default driver. Selecting the Nvidia driver solved the issues, you can give that a try.

---

### Post by CelticWarrior on 2020-06-03
@sdsurfer

The OP already said: > i7 4771, gtx 1660ti, ubuntu 20.04, nvidia driver 440.64
an that they used Nvidia X Server settings to enable maximum performance mode. That means the Nvidia drivers are installed and working.

---

### Post by gerrard000 on 2020-06-03
Thanks for trying to help. Driver is 440.64 [https://imgur.com/c0ThSDw](https://imgur.com/c0ThSDw)
[IMG]https://imgur.com/c0ThSDw[/IMG][IMG]https://imgur.com/c0ThSDw[/IMG][IMG]https://imgur.com/a/s07l0Y1[/IMG]Is it safe if enable [wayland]("https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop")? Just for test.

---

### Post by CelticWarrior on 2020-06-03
> **gerrard000 said:**
> Is it safe if enable [wayland]("https://linuxconfig.org/how-to-enable-disable-wayland-on-ubuntu-20-04-desktop")? Just for test.

It's safe but last time I checked it wasn't working with Nvidia proprietary drivers.

---

### Post by daniewicz on 2020-06-04
I am not familiar with [COLOR=#000000]144hz monitor technology. Do you need to tweak mouse settings to accommodate the monitor?[/COLOR]

---

### Post by gerrard000 on 2020-06-05
No. 125, 500 or 1000 hz polling rate not affect smoothness. I think that initial scroll lag after few seconds idle is related with nvidia drivers. And I have no idea why need higher core/memory clock just for scrolling.

lag [https://imgur.com/ySRutrn](https://imgur.com/ySRutrn)

no lag [https://imgur.com/Q26GJYl](https://imgur.com/Q26GJYl)

---


---
title: "Ubuntu on Dell Mini 10"
date: 2011-11-27
forum: New to Ubuntu
---

### Post by Boozebeard on 2011-11-27
Hello

I have never tried a running any kind of Linux OS before but I have just aquired an old Dell Inspiron Mini 10 from my dad. At the moment it has xp home on but I was thinking about trying Ubuntu on it.

I've had a play with the netbook remix running on a memory stick but the performance is really bad and I can't change the resoloution. I've done some googling and it seems that there are quite a lot of problems with the graphics drivers on these netbooks with ubuntu. Most of the stuff I found was quite old so I was wondering if any developments have been made since then?

Really I'm just wondering if it's worth my time trying to get ubuntu running well on this machine and if so what exactly do I need to do?

Thanks

---

### Post by snowpine on 2011-11-27
I recommend you open a Terminal (by pressing Alt+F2 and typing gnome-terminal) and enter the following to identify your video card:

```
lspci | grep VGA
```

If it says "GMA500 Poulsbo" then read the following:

[https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsPoulsbo)

If it's something else, then post back with the info, and I'll try to help.

---

### Post by Boozebeard on 2011-11-27
it says:

Intel Corporation System Controller Hub (SCH Poulsbo) Graphics Controller (rev 07)

---

### Post by snowpine on 2011-11-27
Bummer. :(

Read here for more info: [http://ubuntuforums.org/showthread.php?t=1229345](http://ubuntuforums.org/showthread.php?t=1229345) (make sure you read through to the end to get the latest updates)

---

### Post by Boozebeard on 2011-11-27
Looks complicated :C

---

### Post by snowpine on 2011-11-27
> **Boozebeard said:**
> Looks complicated :C

The guys in that thread know a lot more than I do! :) Say hi over there, tell them you're new and ask for a quick summary.

---

### Post by Sealbhach on 2011-11-27
> **Boozebeard said:**
> Looks complicated :C

It's not that bad, you can just copy and past most of it. It would take me less than three minutes to do all of that. :)

You can also copy and paste the commands into your terminal, so you don't have to worry about typing the wrong thing.

.

---

### Post by Boozebeard on 2011-11-27
Well I did what it said in that thread. It seemed to all work correctly but the performance doesn't seem any different. I also tried installing the EMGD drivers but the links given on that site don't see to work anymore.

---

### Post by kappclark on 2011-11-27
I am replying to this on a dewll mini running 10.04

The wireless was my only problem

---

### Post by Boozebeard on 2011-11-27
You mean it just worked out of the box or that you managed to get it working with tweaks? You can change the resolution and scrolling and dragging windows isn't all choppy? It would be nice to get working because it's much much more responsive than XP.

Did you get the wi-fi working in the end? I haven't even started trying to fix that.

Does your have the same Poulsbo graphics accelerator?

Edit: I'm gonna do a fresh install and try again when I'm at home and can use my desktop at the same time.

---

### Post by mikewhatever on 2011-12-07
> **kappclark said:**
> I am replying to this on a dewll mini running 10.04

The wireless was my only problem

Really? :rolleyes:

AFAIK, Dell mini 10 has BCM4312 with the driver available from an Ubuntu repository. Install, and the wireless works. Was that the problem?

How about the performance, the out of the box resolution, the touchpad and the screen brightness keys??? All worked?

---


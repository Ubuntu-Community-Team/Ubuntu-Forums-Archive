---
title: "I think I own a top secret nvidia card"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by Rifts on 2008-05-02
lol ok so i have a geforce go 7600 and i installed linux and now im stuck in low-resolution mode anyway i was trying to get a driver to fix it but if i go onto the nvidia website to get the driver its an option there is only the 7800s and 7900s   so what do i do

---

### Post by dasunst3r on 2008-05-02
Have you tried installing Envy to see what it can do for you?  It is in the repositories.

More info: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Rifts on 2008-05-02
yah i have tried envy like 5 times

---

### Post by fatality_uk on 2008-05-02
> **dasunst3r said:**
> Have you tried installing Envy to see what it can do for you?  It is in the repositories.

More info: [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

+1, but don't expect to be playing Quake 4 on that thing!!!

---

### Post by smoker on 2008-05-02
> **Rifts said:**
> yah i have tried envy like 5 times

are you using 'heron?', if so, 'envyng' is what you need, i believe,

---

### Post by steveneddy on 2008-05-02
You know, the nvidia drivers are in the repos.

And you have to change xorg.conf

don't forget to restart.

Why don't you [look here]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Hardware"). Envy downloads a version of the nvidia driver that will make your X not work after the next kernel update. Run the nvidia driver from the repos first, then as you learn more about Linux, try the Envy way.

---

### Post by Rifts on 2008-05-02
> **smoker said:**
> are you using 'heron?', if so, 'envyng' is what you need, i believe,
 yah im on heron and envy hasnt worked


[QUOTE=smoker]Why don't you look here. Envy downloads a version of the nvidia driver that will make your X not work after the next kernel update. Run the nvidia driver from the repos first, then as you learn more about Linux, try the Envy way. [/QUOTE]

that guide is for 7.10 should i still try it?

---

### Post by Grishka on 2008-05-02
envy is not needed on hardy. activate the extra repos in system/administration/software sources, and use system/administration/hardware drivers.

---


---
title: "instalation  problem"
date: 2015-12-28
forum: New to Ubuntu
---

### Post by slage63 on 2015-12-28
Hi Lad's. I using HP-Pavilion laptop 4 RAM 64-bit Ubuntu 15.10.My fan is on all times.  Any idea how  to check what unnecessary processes running on it and how to fix it. Thank you in advance

---

### Post by leunam12 on 2015-12-28
You may have to clean the fan, which is very difficult on some laptops. Youtube is your friend here. What I usually do is remove the keyboard to expose the fan (or part of it) and then blow air into the fan from the exhaust vents and all the dust will come out from the exposed part of the fan.

---

### Post by slage63 on 2015-12-28
i think i will go to professionals.what video scares me. Thank you anyway

---

### Post by Herdo on 2015-12-28
> **slage63 said:**
> i think i will go to professionals.what video scares me. Thank you anyway


I was about to say it's not a big deal.  On ThinkPad's it's usually just two screws on the back, then the keyboard slides right out.  Takes two minutes tops.


Then I saw this video:  [https://www.youtube.com/watch?v=ZT0ovCntxbs](https://www.youtube.com/watch?v=ZT0ovCntxbs)

Who designed these things!?

---

### Post by grahammechanical on 2015-12-28
There is a command to run to see what processes are running & how much CPU & memory they are using

```
top
```

System Monitor will show something similar using a graphical user interface. But I have installed 2 utilities to monitor what my computer is doing. They both put an app indicator in the top panel with drop down menus.

PSensor = fan speeds & temperature reading for CPU, GPU & hard disks as well as motherboard.

System Load Indicator (indicator-multiload) = visual representation of CPU, memory & swap usage as well as network activity.

Regards.

---

### Post by leunam12 on 2015-12-30
Having taken a lot of laptops apart, I have found very few whose exhaust vents are not clogged with dust and fibers of all kinds, lint, dog and cat hair, etc. The cooling system on most laptops is not very effective and everything is so small that the little fins on the heatsink get obstructed very easily. People use their laptops on dusty places, put them on their lap, couch, bed, table cloth, etc. The laptop pulls fibers from the fabric and dust very fast; the fan will run constantly to prevent overheating. If the laptop has an nVidia chip it will die very easily due to overheating (black screen of death) and has to be reflowed, which doesn't always work. It is better to learn how to take the keyboard off the laptop and do regular maintenance blowing the dust off.

Slage63, what model laptop do you have?

---

### Post by otto11235 on 2016-01-27
> **grahammechanical said:**
> 

System Load Indicator (indicator-multiload) = visual representation of CPU, memory & swap usage as well as network activity.

Regards.

After upgrading to Mint 17.3 this app crashed my Cinnamon (I had it as a startup application).

---

### Post by scottbomb on 2016-01-27
Actually not top but powertop. Top is good for monitoring process memory and CPU usage but it doesn't report on the battery. You'll have to download powertop: ```
sudo apt-get install powertop
```

---


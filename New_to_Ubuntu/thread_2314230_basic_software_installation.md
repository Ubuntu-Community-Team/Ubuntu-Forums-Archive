---
title: "basic software installation"
date: 2016-02-19
forum: New to Ubuntu
---

### Post by sandeep24 on 2016-02-19
Hi everyone,
I am new to Ubuntu environment, my laptop is showing a signs of heating up,(after  installing updates), Just need to know basic software thats are required for better running of the system( without heating up) ..so that I can run a web development environment on my laptop.
thank you,
sandeep

---

### Post by grahammechanical on 2016-02-19
I would start looking for physical reasons why a laptop is overheating.

If we want to keep an eye on what the OS is doing, there are some applications we can install to monitor various sensors. I have installed Psensor & System Load Indicator (indicator-multiload). They both put an app indicator in the top panel which gives us easy access to the information being collected by those applications.

Psensor records temperatures & fan speeds. And it does that for the CPU, Motherboard, hard drives & video adapter. Psensor allows us to set temperature alarm trigger points.

System Load Indicator monitors CPU, Memory, disk read & write activity & swap usage. 

Both of these applications can be installed from the software centre and will load at startup,

Regards.

---

### Post by trag on 2016-02-20
Sudo apt get install "thermald" or try "tlp" but not both as they will conflict

---

### Post by oldos2er on 2016-02-21
> **trag said:**
> Sudo apt get install "thermald" or try "tlp" but not both as they will conflict

While we appreciate those offering help, it's nice if you can double check commands before posting them, especially in *New to Ubuntu*. I would've posted ```
sudo apt-get update && sudo apt-get install thermald
```

Just FYI.

---


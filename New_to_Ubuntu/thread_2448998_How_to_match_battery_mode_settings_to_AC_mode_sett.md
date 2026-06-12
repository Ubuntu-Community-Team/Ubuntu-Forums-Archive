---
title: "How to match battery mode settings to AC mode settings in Ubuntu 20.04"
date: 2020-08-17
forum: New to Ubuntu
---

### Post by yehudahecht on 2020-08-17
[COLOR=#242729][FONT=Arial]I'm new to Ubuntu, so please forgive me if this is a stupid question.
I have an [ASUS A15]("https://www.asus.com/Laptops/ASUS-TUF-Gaming-A15/") with Ubuntu 20.04 installed. I've been having an unusual problem with my laptop where the screen freezes after a few seconds when the computer is unplugged.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]As per [this answer on the SuperUser StackExchange]("https://superuser.com/a/609731/749508"), I am assuming it is related to battery mode options. The answer suggests matching all battery options to AC options. On Ubuntu that seems to be a bit more complex. I don't have [TLP]("https://linrunner.de/tlp/") installed (yet). What are the things I need to look for in order to match battery mode settings to AC mode settings? The Power Settings menu in 20.04 is somewhat sparse.
The laptop as an NVIDIA[/FONT][/COLOR] GeForce GTX 1660TI GPU, and I have installed the NVIDIA 440 driver.

---

### Post by TheFu on 2020-08-19
How did you install the nvidia driver?  Using the ubuntu tools, hopefully, not by visiting any website and downloading a file.  People really new to Linux shouldn't download any files to be installed directly. Always use the package manager and let it get the correct package for the system, maintain the dependencies, etc.

Many common questions are answered in the Ubuntu Desktop Guide: [https://help.ubuntu.com/stable/ubuntu-help/index.html.en](https://help.ubuntu.com/stable/ubuntu-help/index.html.en)

---

### Post by yehudahecht on 2020-08-19
I don't recall if it was ubuntu-drivers or apt, but I installed it on the command line.

---

### Post by TheFu on 2020-08-20
> **yehudahecht said:**
> I don't recall if it was ubuntu-drivers or apt, but I installed it on the command line.

BTW, are you new to Linux AND Ubuntu or have you been running Linux/Unix systems 25 yrs and just new to Ubuntu?  It matters.

Would be helpful to see an overview of the system hardware.
```
inxi -Fxxpzc0
```

Could be configuration, bug, bugs, or hw issues. Just don't have enough info to guess.

---


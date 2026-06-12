---
title: "Acer D270 fan continuously running"
date: 2012-06-11
forum: New to Ubuntu
---

### Post by ranrag on 2012-06-11
I recently purchased a Acer D270 netbook and observed that its fan is continuously running even on temperature as low as 40C.

Currently I have windows installed on it and today I am planning to install ubuntu 12.04 on it. So, I was wondering does linux provide any package to give some more control on my fan speed like if ```
temp < 50C
``` I don't want my fan to be running.

And also is this behavior normal with these Acer netbooks.

---

### Post by idrinktea on 2012-06-11
I have the same model(2 weeks old), and the fan is also continuously running. I didn't like it at first, because I can hear it if the environment is quiet. But I think this is actually normal, and I can get 7 hours of batter life, so it doesn't seem to affect the battery much.

The air pushed out does feel warm, so it must be running to keep something cool. But it is definitely not the OS that is causing it to run like this, because it starts even before the OS is loaded(even when I am in the BIOS settings). Probably the integrated GPU or something is causing the machine to get hot, maybe inefficient airflow, so the fan has to run. 

I've long since wiped Windows and installed Mint 13(based on Ubuntu 12.04) Mate 64 bit. At first Mint caused the screen to be at maximum brightness, but easily fixed by typing in the terminal: sudo setpci -s "00:02.0" F4.B=35 (lower value to decrease brightness and vice versa) . I ended up adding this line to /etc/rc.local to make it automatic, so I don't have to manually adjust brightness in the terminal for every session. I am including all this info just in case you get the same problem when installing Ubuntu 12.04.

I am not worried about the constant fan(although it does concern me that the fan being on constantly will wear the bearings and the fan will die an early death). But I think it wouldn't be too difficult to replace it. Am really loving this machine.

EDIT: The hdd does seem to click every 2 seconds for a while, when the machine is idle. But this is intermittent. I am hoping it's not a sign of impending hdd death. :)

---


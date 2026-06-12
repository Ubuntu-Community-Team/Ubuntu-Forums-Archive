---
title: "How do you kill X?"
date: 2011-09-30
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by cmfrtblynmb on 2011-09-30
What is the command for killing X server on 11.10? Old commands do not work. Also for some reason recovery mode does not boot. 

I have to kill X to install Nvidia driver from source.

Thanks

---

### Post by linuxman94 on 2011-09-30
You shouldn't need to kill X in order to install the drivers...

---

### Post by effenberg0x0 on 2011-09-30
From source? Didn't you get the message about the need to kill X when installing the NVidia proprietary drivers from NVidia website? Those drivers do need and ask you to exit all X sessions otherwise the install procedure won't continue.

If so:

$sudo service lightdm stop
$sudo killall -s KILL X
$cd to where you downloaded the drivers to.
$sudo chmod +x NVIDIA-Linux-x86-280.13.run (or whatever the downloaded driver file name is)
$sudo ./NVIDIA-Linux-x86-280.13.run (or whatever the downloaded driver file name is)
$sudo service lightdm restart (or reboot with $sudo reboot now, which is better)

Regards
Effenberg

---

### Post by cmfrtblynmb on 2011-10-01
Thank you Effenberg. That worked. (Although second command did not work, I guess X was already killed, so it did not need to work at all. First command did the trick)

This should appear on first page when people look for "kill x command ubuntu...etc"

---


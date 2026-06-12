---
title: "Yet Another NVidia Driver Problem Thread"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by Smortypi on 2012-12-11
Since I re-installed Ubuntu, I have attempted to install a working nvidia driver. Despite having a functioning  NVidia Graphics Card (see below for specifics), I was never offered the chance to install the proprietary driver. As a result, I attempted to install the one from the repos (nvidia_experimental_304). After finishing this, I attempted to run nvidia-settings, only to get a prompt to run nvidia-xconfig with the message "You do not appear to be running the Nvidia Driver. Run nvidia-xconfig and restart x) After doing so and restarting the X Server, my resolution was reset to 800x600. Despite this, I ran nvidia-settings once more. Oddly enough, I recieved the same prompt.  I have found no solution to this, and the only workaround I have is to  rm /etc/X11/xorg.conf . I have infact tried to install the driver provided by NVidia on their website, much to the same result.

Modprobe outputs this:
~$ modprobe nvidia
>>FATAL: Error inserting nvidia_experimental_304 (/lib/modules/3.5.0-19-generic/updates/dkms/nvidia_experimental_304.ko): No such device

Lscpci outputs:
~$lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [Quadro NVS 5400M] (rev a1)

I also can not seem to get nouveau to work again, despite using many of the methods provided on the forums. I am thus left without any  3d acceleration, and limited everything pretty much. Any help is appreciated.

I am currently using a tty and Links2 is admittedly hard to navigate, however I shall try to reply in a timely manner.

---

### Post by NM5TF on 2012-12-11
what distro are you running???

do you happen to have AMD processor???

there is a problem with the newer kernels associated
with AMD processors & Nvidia graphic cards....

I had to go back to the 3.2.0-33 kernel to make it work
with my Nvidia card & AMD Athalon X 2 4000+ processors

I also had to dump the nvidia-current drivers & go back
the older driver....

Tommy

---

### Post by pqwoerituytrueiwoq on 2012-12-11
> **NM5TF said:**
> what distro are you running???

do you happen to have AMD processor???

there is a problem with the newer kernels associated
with AMD processors & Nvidia graphic cards....

I had to go back to the 3.2.0-33 kernel to make it work
with my Nvidia card & AMD Athalon X 2 4000+ processors

I also had to dump the nvidia-current drivers & go back
the older driver....

Tommy
i call BS
i am running a AMD Phenom II 965 (unlocked quad core) and a nVidia GTX 550 TI (driver: 310.19) on the 3.7.0-4-generic kernel

Quadro is a combo of Intel and Nvidia graphics, which is knows to be problematic under linux, there is a workaround (that i can't recall)

---

### Post by Smortypi on 2012-12-12
> **pqwoerituytrueiwoq said:**
> i call BS
i am running a AMD Phenom II 965 (unlocked quad core) and a nVidia GTX 550 TI (driver: 310.19) on the 3.7.0-4-generic kernel

Quadro is a combo of Intel and Nvidia graphics, which is knows to be problematic under linux, there is a workaround (that i can't recall)

You pretty much nailed it. It's an intel i5-3210M, and I am running Quantal right now.

I also forgot to mention that the older drivers didn't work for me either.

---

### Post by NM5TF on 2012-12-12
> **pqwoerituytrueiwoq said:**
> i call BS
i am running a AMD Phenom II 965 (unlocked quad core) and a nVidia GTX 550 TI (driver: 310.19) on the 3.7.0-4-generic kernel

Quadro is a combo of Intel and Nvidia graphics, which is knows to be problematic under linux, there is a workaround (that i can't recall)

really???

how do you explain this thread then???

[http://ubuntuforums.org/showthread.php?t=2085789](http://ubuntuforums.org/showthread.php?t=2085789)

maybe you should share your vast knowledge & wisdom with
the upstream devs....I'm sure they would appreciate the help..

---

### Post by pqwoerituytrueiwoq on 2012-12-12
if there is a amd/nvidia issue it must be with a specific series of cpus or nvnida gpus, possibly the really old ones, but definably not all of them, even with the open source nvida driver it runs good on this hardware in 12.10/13.04

i did not do anything special to get anything working it just works
64bit xubuntu+compiz+nvidia

anyway there may be a working driver for the op in the xorg edgers ppa

---


---
title: "Nvidia Driver Ubuntu 22.04"
date: 2022-06-19
forum: New to Ubuntu
---

### Post by outlaw67 on 2022-06-19
Running Ubuntu 22.04 server.What is the best way to install the latest Nvidia driver ?

---

### Post by Bashing-om on 2022-06-19
outlaw67; Hello - Welcome to the Forum :D

> 
server.What is the best way to install the latest Nvidia driver ?


Run terminal commands:
```

sudo apt update
sudo apt upgrade
sudo ubuntu-drivers autoinstall

```

Where the kernel will choose the latest appropriate driver for the installed card.
reboot the system to see the effect.

[INDENT][INDENT]my bit to try to help
[/INDENT][/INDENT]

---

### Post by outlaw67 on 2022-06-19
Okay with this allow to use command nvidia-smi or do i have to install ?

---

### Post by Bashing-om on 2022-06-19
outlaw67; Well

As nvidia-smi is a virtual package; I expect it to install along with the driver install.

Been a while since I installed a Nvidia proprietary driver - but for sure I do not recall having to install any other apps to use nvidia-smi.

-KISS-

---

### Post by outlaw67 on 2022-06-19
Thanks.Was able to install 515 driver through ppa repository but can't figure out to get nvidia-smi. With nvidia driver 510 can get nvidia-smi by installing nvidia utilities but doesn't work with 515.

---

### Post by Bashing-om on 2022-06-19
outlaw67; Humm ,,,,

515 is bleeding edge - sure that your card is compatible ?
post back:
```

lspci -k | grep -iEA5 'vga|3d'

```

And we can check with Nvidia what version driver they recommend.

[INDENT]we can do that
[/INDENT]

---

### Post by outlaw67 on 2022-06-19
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290625&stc=1[/IMG]

---

### Post by Bashing-om on 2022-06-19
outlaw67; Sorry ---

My eyes are not good enough to de-cypher what I am looking at.
Please post here the text output - between code tags:
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
```

lspci -k | grep -iEA5 'vga|3d'

```

[INDENT]the old grey mare :)
[/INDENT]

---

### Post by outlaw67 on 2022-06-19
Thanks for help.I can't figure out what you sent me

---

### Post by Bashing-om on 2022-06-19
outlaw67; Hey -

Not to know is not a sin ---

we were all new at one time ---
Lemme try again.
In a terminal execute the terminal command lspci -k | grep -iEA5 'vga|3d'

copy that output (left click with mouse - hold and drag)
and paste into this thread (middle click with mouse)
per the instructions in the tutorial: code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Now that I can read :)

[INDENT]where there's a will there's a way
[/INDENT]

---

### Post by outlaw67 on 2022-06-19
Tried but can not copy from terminal command

---

### Post by outlaw67 on 2022-06-19
01:00.0 VGA compatible controller: NVIDIA Corporation GA102 [GeForce RTX 308GB] (rev a1)
        Subsystem: eVga.com. Corp. Device 4877
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GA102 High Definition Audio Control(rev a1)
        Subsystem: eVga.com. Corp. GA102 High Definition Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD roller SM981/PM981/PM983
        Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB
        Kernel driver in use: nvme

---

### Post by outlaw67 on 2022-06-19
01:00.0 VGA compatible controller: NVIDIA Corporation GA102 [GeForce RTX 3080 12GB] (rev a1)
        Subsystem: eVga.com. Corp. Device 4877
        Kernel driver in use: nvidia
        Kernel modules: nvidiafb, nouveau, nvidia_drm, nvidia
01:00.1 Audio device: NVIDIA Corporation GA102 High Definition Audio Controller (rev a1)
        Subsystem: eVga.com. Corp. GA102 High Definition Audio Controller
        Kernel driver in use: snd_hda_intel
        Kernel modules: snd_hda_intel
04:00.0 Non-Volatile memory controller: Samsung Electronics Co Ltd NVMe SSD Controller SM981/PM981/PM983
        Subsystem: Samsung Electronics Co Ltd SSD 970 EVO Plus 1TB
        Kernel driver in use: nvme

---

### Post by Bashing-om on 2022-06-19
outlaw67; Well well !

[https://www.nvidia.com/Download/driverResults.aspx/189809/en-us/](https://www.nvidia.com/Download/driverResults.aspx/189809/en-us/)
Confirms that you do indeed require the 515 version driver.

And the output of the lspci command confirms that the Nvidia driver is loaded.
So, as to nvidia-smi; I can accept that this app requires the GUI . As this is a server install I too can accept that there is no GUI, as this interface is not needed, nor installed by default, for a server use case. Those here who do run Nvidia graphics on a server can for sure advise better.

What info do you want to gather that nvidia-smi provides ? I bet there is a text alternative in the event that a GUI is not installed ( and should not be on a server - attack vectors !). 

[INDENT]looking for that other way
[/INDENT]

---

### Post by outlaw67 on 2022-06-19
gpu temp and load

---

### Post by outlaw67 on 2022-06-19
I could get nvidia-smi to work on 510 driver with installing nvida utilities.

---

### Post by Bashing-om on 2022-06-19
outlaw67; Whaelll

temps:
```

sensors

```

load:
```

top

```

among many other ways.

[INDENT]many paths to an end - ubuntu
[/INDENT]

---


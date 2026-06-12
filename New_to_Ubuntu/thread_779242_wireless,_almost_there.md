---
title: "wireless, almost there?"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by moecoors on 2008-05-02
Got my drivers downloaded. THe installer (GTK?) asked for and installed the inf. file. Message then was "hardware detected" however there is no wireless option in Networks.
 Installer did not ask for sys. files which I understand are needed.
What is the next step?
thanks

---

### Post by moecoors on 2008-05-03
Tried putting sys and inf files in one folder but installer only accepted the inf.  Next step?
thanks

---

### Post by SunnyRabbiera on 2008-05-03
you might not even need the sys files, I was able to get wireless working on my other computer without it.
are you using ndiswrapper?

---

### Post by lswest on 2008-05-03
do this:
```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo gedit /etc/modules
``` then add "ndiswrapper" to the modules file.  If that doesn't work, post back saying what your card is and what version of Ubuntu you're running.

---

### Post by moecoors on 2008-05-03
I loaded ndiswrapper and ndis gtk from the live CD. They both show on the Synaptics list as present,also the "Windows wireless drivers' window comes up and wants a inf file so I'm thinking that it's active. 
Ubuntu version 8.04
Wireless card Linksys WPC300N
 Driver is 4.150.22.0
I didn't run the command lines yet. I was wondering if it was necessary.

---

### Post by moecoors on 2008-05-04
Tried the terminal, when I entered sudo ndiswrapper -m, I got," module configuration already contains alias directive" soooo I'm stuck again. Sounds like everything is there, now to wake it up.

---

### Post by lswest on 2008-05-04
can you post the output of ```
lshw -C network
``` please?

---

### Post by moecoors on 2008-05-04
Sorry don't know how to get the info from Hardy to Vista. I guess I could write it all out into Vista, but how about saving a terminal screen to a file to vista ? Sorry  beginnner for sure.

---

### Post by freebeer on 2008-05-04
Can your Vista read your linux partitions?  If so, then redirect the output of the command to a text file, then copy the contents of the file.

```

lshw -C network > filename.txt

```

the ">" will redirect the output that normally goes to the screen to the file called "filename.txt" (you can use any name you like).

---

### Post by moecoors on 2008-05-05
No, Vista can't access Hardy files. I'll write it out and post.

---

### Post by moecoors on 2008-05-05
Here goes.
*.network
     description: Ethernet interface
     product: 828801 CAM(ICH3) PRO/100 VE(LOM)Ethernet Controller
     vendor: Intel Corporation
     physical id: 8
     bus info: pci@0000:02:08.0
     logical name:eth0
     version: 42
     serial: 00:0e:7b:cl:30:07
     width: 32 bits
     clock: 33MHz
     capabilities: bus_master cap-list ethernet physical configuration: broadcast=yes driver=e100 driver version=3.5.23-k4-NAPI firmware=N/A latency=64 max latency=56 mingnt=8 module=e100 multicast= yes
  networks: UNCLAIMED
      description: Network controller
      product: BCM43XG
      vendor: Broadcom Corporation
      physical id: 0
      bus info: pci@0000:03:00.0
      version: 01
      width: 32 bits
      clock: 33MHz
      configuration: latency=0
      bus info: pci@0000:03:00.0

---

### Post by moecoors on 2008-05-05
Free Beer? Is it Coors?

---

### Post by lswest on 2008-05-06
well, check to make sure your card is actually on when you boot Ubuntu, and then run: ```
sudo modprobe -r ssb
sudo modprobe -r b43
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
``` and if that gives you internet (it should, for this session only though) have a look at my post on this thread: [http://ubuntuforums.org/showthread.php?t=780212](http://ubuntuforums.org/showthread.php?t=780212) (the second to last one) and follow the steps for making the boot script.

---

### Post by moecoors on 2008-05-06
When I enter "sudo modprobe -r b 43" the message is module not found.
How do I turn the card on? The led lights are not on so I guess its dead. It comes active by itself in vista.
 I hope I haven't tested you guys to much, I'll get it eventually ( with your help)

---

### Post by lswest on 2008-05-22
sorry i haven't replied for 2 weeks, this thread kind of got lost in my busy life.  If it says the b43 driver is not found, then that means you're not using the b43 driver, and you'll have to check to see which driver you do have in use, or which is conflicting with it. ```
lshw -C network
``` might help, or check the hardware drivers app.

Sorry, forgot you had already posted that output, check the hardware drivers (under system-->administration-->hardware drivers) and see if any are in use, otherwise just try it without the b43 step.

---


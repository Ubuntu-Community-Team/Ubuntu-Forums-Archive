---
title: "Laptop VGA output - configure"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by newbuntuxx on 2008-07-25
hey....

I have a toshiba laptop. I recently installed ubuntu 8.04 32 bit on it, it works just fine. 

I dont know how to work the VGA output so i can a view on my TV. I looked around and was unable to find any graphic dislay manager.

Any help or tips are appreciated!

---

### Post by talsemgeest on 2008-07-26
What graphics card are you using?

---

### Post by northern lights on 2008-07-26
Can you please post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by newbuntuxx on 2008-07-26
```
hs@hs-laptop:~$ sudo lshw -C display
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: RS300M AGP [Radeon Mobility 9100IGP]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: agp agp-3.0 pm vga_controller bus_master cap_list
       configuration: latency=66 mingnt=8
```

Sorry about the late reply..

---

### Post by talsemgeest on 2008-07-27
Ok, you should install envy, it is in the repositories. Once you have done that, you can install the latest driver for your graphics through that program, and it will configure everything for you. After that you can go programs > accessories > catalyst control center and configure everything you need from there.

Hope this helps :)

---

### Post by newbuntuxx on 2008-07-27
```
python pulse.py ati 
root@hs-laptop:/usr/share/envy# python pulse.py ati 
EnvyNG - Version 1.1.1
Ubuntu Hardy 32bit
Your graphic card has been detected as a ATI Mobility Radeon 9000/9100 IGP Series
Your graphic card is supported by the legacy Driver
EnvyNG ERROR: ATI's legacy driver does not support your operating system
root@hs-laptop:/usr/share/envy#
```


thats what i get when envy tried to install the ati drivers. This is what i am using:

Ubuntu 8.04.1, kernel 2.6.24-16-386

thanks

---

### Post by talsemgeest on 2008-07-27
I'm sorry, but that has got me stumped...

---

### Post by argail1980 on 2008-07-27
I don't think you need to install new drivers to have TV-out

have a look at:[http://ubuntuforums.org/showthread.php?t=830212]("http://ubuntuforums.org/showthread.php?t=830212")

---


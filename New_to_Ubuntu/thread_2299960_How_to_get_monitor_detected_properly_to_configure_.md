---
title: "How to get monitor detected properly to configure on optimus enabled laptop"
date: 2015-10-22
forum: New to Ubuntu
---

### Post by Sorawit_Kongnurat on 2015-10-22
So I have finally got the nerve to erase windows and move on to Linux fully. However, I have got this one problem that I just can't seem to solve. I have installed the latest nvidia driver 355 but in nvidia x settings I couldn't configure my refresh rate. I think this is due to the fact that display are being run out of the Intel graphic card. What should I be doing ? In windows I would have to install Intel graphic driver and configure my refresh rate there but do Linux have a Intel graphic? If yes where can I find such file? 

*I usually connect my laptop to an external monitor which support 144hz and I would like to take advantage of that refresh rate

Thank you

---

### Post by grahammechanical on 2015-10-22
As far as I know we do not need to install an Intel video driver as they are built into the kernel. I do not have Optimus technology but it is my understanding that the driver provided by Nvidia does not do automatic switching between the Intel video adapter and the Nvidia video adapter. We make the switch in the Nvidia settings utility. Once the machine is running on the Nvidia adapter it might then recognise the external monitor and you might be able to create a profile for that display.

Regards.

---

### Post by Sorawit_Kongnurat on 2015-10-22
I am stuck with only these option to play with which I think isn't normal. Then this happen when I connect my external monitor (The two screen work but I want to configure my refresh rate which I can't seem to do).

Can someone who got a clue help me with this :cry: 
This is my only problem and I would be very very happy if I were to fixed it.

I don't know if my problem is solved but I configure some settings in monitor.xml and got this going. Is this consider 144hz working ? I dunno how I can check it :(

---

### Post by col48 on 2015-10-23
Does this help?  It's not an area I am familiar with...

[HTML]https://askubuntu.com/questions/59621/how-to-change-the-monitors-refresh-rate[/HTML]

---

### Post by Sorawit_Kongnurat on 2015-10-25
So I have wondered around and check through a lot of question that was related to my problem. I believe there is a bug in my xorg.conf which is preventing this. I have tried updating my nvidia but the problem remain so I reverted back to 346.49. 

```
Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection


Section "Device"
    Identifier "intel"
    Driver "intel"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "SNA"
EndSection


Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection


Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection


Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection
```

I believe if I can get nvidia to detect my monitor this should solve my problem.

---

### Post by Sorawit_Kongnurat on 2015-10-26
I still cannot fix this problem... I think I have got 144hz working by configuring the monitor.xml but I got no way to check. In addition I have gone ahead and install bumblebee correctly but steam is now not working :( I installed bumblebee in the hope that I would be able to access my monitor from the nvidia setting. Yet, that didn't work too :( Can anybody be kind enough to give me a hand...

---

### Post by Sorawit_Kongnurat on 2015-10-29
I think I want to delete this thread for now. My questions are getting all out of place and I think this might be in the wrong forum. Thanks to everyone who helped me with this problem so far.

---


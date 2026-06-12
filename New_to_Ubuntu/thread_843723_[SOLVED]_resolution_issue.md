---
title: "[SOLVED] resolution issue"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by tadcan on 2008-06-28
I have updated (8.04) and my resolution is now 640x480. I have an Nvidia 8800 GTX graphics card.

I had a restricted driver in 7.10.Doesn't seem to be available any more.

---

### Post by cprofitt on 2008-06-28
> **tadcan said:**
> I have updated (8.04) and my resolution is now 640x480. I have an Nvidia 8800 GTX graphics card.

I had a restricted driver in 7.10.Doesn't seem to be available any more.

The problem is likely with the system detecting your monitors refresh rate. I had this issue and had to resolve it by forcing it in the xorg.conf file.

This is what I had to do:

```

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "1"
    Option         "TwinViewXineramaInfoOrder" "DFP-1"
    Option         "metamodes" "CRT: **1280x1024_60** +1280+0, DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection

```

I have two monitors hence the metamodes including settings for two monitors.
EndSection

---

### Post by tadcan on 2008-06-29
Ah the xorg.conf file you say, very interesting Mr.Bond, do tell more.

Seriously how do I find this file?

---

### Post by frodon on 2008-06-30
You have resolution issue ?

Reboot in safe mode, run xfix then once rebooted again ensure with the restricted manager that your nvidia drivers are in use. This solves the issue for most users without editing any config file.

---

### Post by azangru on 2008-06-30
> **tadcan said:**
> Ah the xorg.conf file you say, very interesting Mr.Bond, do tell more.

It's right in /etc/X11 :)

> **tadcan said:**
> Seriously how do I find this file?

The right question would be how do I ***edit*** this file, because you'll have to do that under super-user priviledges. You'll have to start up the terminal and enter

sudo gedit /etc/X11/xorg.conf

(please notice that Unix is case-sensitive, so "X" in X11 has to be upper-case)

---

### Post by Tomatz on 2008-06-30
Open a terminal and type:
```

gksu nvidia-settings
```

Setup your correct resolution ;)

---

### Post by tadcan on 2008-06-30
Thanks frodon that solved the problem.

Thanks for everyones imput.

I have restricted and multiverse ticked but when I go to the restricted driver manager I dont see the option to install the Nvidia driver. Is there something else to do.

---

### Post by shearn89 on 2008-07-02
try nvidia-settings. Set up my cards perfectly on 3 different computers. Code mentioned above. ^^

---

### Post by tadcan on 2008-07-04
All that happens is I get a fresh line in the terminal.

```
tadcan@Quad:~$ gksu nvidia-settings
tadcan@Quad:~$ gksu nvidia-settings
tadcan@Quad:~$ 
```

---


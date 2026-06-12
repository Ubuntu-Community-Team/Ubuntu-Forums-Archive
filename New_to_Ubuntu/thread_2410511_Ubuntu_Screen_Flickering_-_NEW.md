---
title: "Ubuntu Screen Flickering - NEW"
date: 2019-01-16
forum: New to Ubuntu
---

### Post by Milos_Milutinovic on 2019-01-16
Hello everyone.
I'm new at Ubuntu OS.

My laptop:
HP 255 G6 with Full HD resolution, AMD processor and integrated graphic card. 

My Issue:
Screen of my laptop is flickering from time to time, no matter what I do, specially during web page scrolling with my mouse wheel.
Here is a short video recorded about my issue:

[https://drive.google.com/open?id=1jTrSd_Xk-fzPCdVIM5g5-FZW0payNcu7](https://drive.google.com/open?id=1jTrSd_Xk-fzPCdVIM5g5-FZW0payNcu7)

I saw one topic with similar issues and they asked for this informations, so... here they are, might be helpful.

```

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"

```

```

Linux milutinko-HP-255-G6-Notebook-PC 4.15.0-43-generic #46-Ubuntu SMP Thu Dec 6 14:45:28 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

```

00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Device [1002:98e4] (rev d4)
    Subsystem: Hewlett-Packard Company Device [103c:8330]
    Kernel driver in use: amdgpu

```

```

DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated

```

---

### Post by oldrocker99 on 2019-01-16
Your problem may be easy to solve: Try another HDMI cable. It's worked for me more than once.

---

### Post by Milos_Milutinovic on 2019-01-16
Don't understand...
In what reletaion is HDMI cable and screen of my laptop?

---

### Post by Milos_Milutinovic on 2019-01-24
Any solution for my issue?

---

### Post by MartyBuntu on 2019-01-24
Did you install the proprietary AMD graphics driver?

---

### Post by Milos_Milutinovic on 2019-01-27
No... Ubuntu did it automatically during instillation process... Don't know how to do that, help?

---

### Post by oldrocker99 on 2019-01-28
> **Milos_Milutinovic said:**
> Don't understand...
In what reletaion is HDMI cable and screen of my laptop?
Oops. I was referring to a desktop. The proprietary AMD drivers aren't liked too well by a lot of people. The radeon open-source driver, developed with a lot of help from AMD/ATI, is considered to be superior.

---

### Post by m4ppo on 2019-03-26
Hi all,
I have the same problem with a Lenovo X1 carbon (2015)
here are some specs that may be useful

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=18.04
DISTRIB_CODENAME=bionic
DISTRIB_DESCRIPTION="Ubuntu 18.04.1 LTS"



```

```
Linux username 4.15.0-45-generic #48-Ubuntu SMP Tue Jan 29 16:28:13 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux


```

```
00:02.0 VGA compatible controller [0300]: Intel Corporation HD Graphics 5500 [8086:1616] (rev 09)    
Subsystem: Lenovo HD Graphics 5500 [17aa:2227]
Kernel driver in use: i915



```

```
DESKTOP_AUTOSTART_ID=1048bb07303935eda615535791255626800000016590007
DESKTOP_SESSION=ubuntu
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
GNOME_DESKTOP_SESSION_ID=this-is-deprecated



```




can anyone help?

thank you very much!

---


---
title: "Nvidia driver issue"
date: 2013-07-15
forum: New to Ubuntu
---

### Post by Utram on 2013-07-15
I have a nvidia geforce GT 640M video card on a Toshiba Satellite P850-31X.

I installed the most recent and appropriate "NVIDIA-Linux-x86_64-319.32.run" driver. But it doesn't activate, I'm now stuck with a 640x480 resolution.

NVIDIA X Server settings just throws me this error msg:
> 
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

"nvidia-xconfig" doesn't even exist(yes, I used sudo). What do I do? And how do I reactive whatever driver which came preinstalled? The installation didn't copy my xorg file, I vaguely remember that it stated that it would.

---

### Post by Bashing-om on 2013-07-15
Utram; Hi !

Your 640M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. See these links here for installing the drivers: Switchable laptop graphics issues on Ubuntu 12.04?
640M+optimus=BumbleBee

[http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310](http://askubuntu.com/questions/160242/switchable-laptop-graphics-issues-on-ubuntu-12-04/160310)
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee](https://wiki.ubuntu.com/Bumblebee?action=show&redirect=bumblebee)
[http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html](http://www.webupd8.org/2013/04/bumblebee-321-released-with-ubuntu-1304.html)

[INDENT][INDENT]there is an option
[/INDENT][/INDENT]

---

### Post by Utram on 2013-07-15
> **Bashing-om said:**
> Utram; Hi !

Your 640M is an Intel/Nvidia hybrid card, and it is not officially supported by Nvidia. 

Interesting, if Nvidia doesn't provide linux support for this particular card then why did it list the driver under the model name?

---

### Post by VinDSL on 2013-07-15
Just did a quick search of supported products, on the nVidia site.

Looks like you need the same legacy driver that I'm running 304.88 (currently).

SOURCE:  [http://www.nvidia.com/object/linux-display-ia32-304.88-driver.html](http://www.nvidia.com/object/linux-display-ia32-304.88-driver.html)

Might want to try it...

Oops!  You're 64-bit

SOURCE: [http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.32-driver.html)

Hrm...

Have you tried the nVidia drivers in the Ubu PPAs?

---

### Post by Utram on 2013-07-15
> **VinDSL said:**
> 
Have you tried the nVidia drivers in the Ubu PPAs?

What are those? Sorry, but I'm not too familar with Linux/ubuntu abbrevations.

---

### Post by Utram on 2013-07-16
> **Bashing-om said:**
> 
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)


Thanks, this one worked. Mid-level eye candy came by default and games now work.

---

### Post by Bashing-om on 2013-07-16
Utram; Great !

Glad it worked out for you.
Not admittedly the greatest solution that might be desired. But, the important thing, it is a solution.

[INDENT][INDENT]ain't ubuntu wonderful
[/INDENT][/INDENT]

---


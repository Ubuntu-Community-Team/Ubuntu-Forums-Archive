---
title: "need help with internet connection"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by mylesvarns on 2008-05-23
Hello,
I am completely new to Ubuntu and just downloaded 8.04 today. I cannot connect to my houses wireless internet. it won't even show up on the network manager thing. I don't know what to do. anyone have any ideas how to fix it?

---

### Post by bsharp on 2008-05-23
post the output of 
```
iwconfig
```

---

### Post by mylesvarns on 2008-05-23
post it in what?

---

### Post by superprash2003 on 2008-05-23
go to the terminal(Application->Accessories->Terminal) and type iwconfig and an output would show on the terminal window.Highlight the output , right click and click on copy .. and paste it here in the forums

---

### Post by mylesvarns on 2008-05-23
lo             no wireless extensions

eth0           no wireless extensions

---

### Post by fochsenhirt on 2008-05-23
> **mylesvarns said:**
> lo             no wireless extensions

eth0           no wireless extensions

I'm guessing you have a broadcom chipset, which in my experience means you need to use ndiswrapper. See [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526) and [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003). Or see the description of how I did it on my Compaq Presario A900 at [http://ochsenhirt.org/2008/05/02/install-ubuntu-804-on-compaq-presario-a900-laptop-howto/](http://ochsenhirt.org/2008/05/02/install-ubuntu-804-on-compaq-presario-a900-laptop-howto/).

---


---
title: "How to compile the kernel for a newbee"
date: 2007-02-12
forum: Programming Talk
---

### Post by williammanda on 2007-02-12
I need to add a driver for a tv tuner card. My understanding is that when this happens I would need to re-compile the kernel. Are there any simple instructions (with examples) that I could get to step me through this procedure?
I would like to say that I am very well pleased so far using Ubuntu coming from windows.
Thanks

---

### Post by Jussi Kukkonen on 2007-02-12
> I need to add a driver for a tv tuner card. My understanding is that when this happens I would need to re-compile the kernel. Are there any simple instructions (with examples) that I could get to step me through this procedure?
In 99% of the cases you do not need to compile the kernel, as drivers can be loaded when they are neeeded . Just get the drivers, compile and install. If the driver is from linuxtv.org (as usual), it's quite easy.

Reply with more details if you need more help.

---

### Post by williammanda on 2007-02-12
Thanks for your reply.
I do need more detail, since I am very new to linux. I would appreciate something that would give step by step instructions. his way I could learn and understand what the process is about.
Thanks

---

### Post by pay on 2007-02-12
[Here's](http://www.howtoforge.com/kernel_compilation_ubuntu) howto compile the kernel. The drivers form linuxtv.org say that they are already in the 2.6.X kernel so you won't need to install the drivers separetly.

---

### Post by williammanda on 2007-02-13
Thanks for your reply. The pcHDTV-5500 works only with the linux driver but not the DVB. I thought there was something wrong and I replaced the pcHDTV-5500 with my fusion HDTV5 rt gold card and it worked fine under DVB. I have used both cards with kernel 2.6.18 but there seems to be an issue under 2.6.17 kernel. I have also loaded Feisty on another computer, which has the 2.6.20 kernel and I have the same situation. I not sure if there is something missing due to the alpha rating.
Thanks

---

### Post by pay on 2007-02-13
> **williammanda said:**
> Thanks for your reply. The pcHDTV-5500 works only with the linux driver but not the DVB. I thought there was something wrong and I replaced the pcHDTV-5500 with my fusion HDTV5 rt gold card and it worked fine under DVB. I have used both cards with kernel 2.6.18 but there seems to be an issue under 2.6.17 kernel. I have also loaded Feisty on another computer, which has the 2.6.20 kernel and I have the same situation. I not sure if there is something missing due to the alpha rating.
ThanksWell feisty might be alpha, but the kernel is the stable release.

---

### Post by Jussi Kukkonen on 2007-02-13
> **williammanda said:**
> The pcHDTV-5500 works only with the linux driver but not the DVB.
Can you say that in other words -- I'm not sure what works and what doesn't (I'm not familiar with that piece of hardware either)?

> 
I do need more detail, since I am very new to linux.

Ok, the general situation regarding DVB television (I'm assuming this is what you are interested in) is this:
The DVB driver subsystem is developed on linuxtv.org and it is included in the linux kernel, so in the best case you don't have to do anything to get the drivers -- they're included in your distributions kernel. However, DVB cards are still quite new and the manufacturers constantly create new models or, annoyingly, change the hardware on existing models. This means that sometimes your kernel does not yet include a driver that is already available at linuxtv.org.

To find out if your card works and what you should do to test, take a look at the wiki:
[http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page)
especially [http://linuxtv.org/wiki/index.php/How_to_install_DVB](http://linuxtv.org/wiki/index.php/How_to_install_DVB)
and  also [http://linuxtv.org/wiki/index.php/First_steps_with_a_DVB_card](http://linuxtv.org/wiki/index.php/First_steps_with_a_DVB_card)

---


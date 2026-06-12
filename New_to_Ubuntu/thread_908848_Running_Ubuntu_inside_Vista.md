---
title: "Running Ubuntu inside Vista"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by rusty377 on 2008-09-02
Hello all,

I downloaded desktop version and installed using the run from Windows option. It created a ubuntu 15 GB folder on the c drive and also if I reboot it has option to start ubuntu. My question is - how do you run ubuntu from inside windows?- is there an Icon or program I can't find for some reason?  I also tried running it from the startup choice of ubuntu and it gets up to about 82% installed and just sits there (maybe too impatient?). I really want to just run from Vista for now though. Could someone please help?

Thanks

---

### Post by Presto123 on 2008-09-03
Have you tried running it as a virtual machine? It seems that VMware is a very popular choice around here.

I have yet to use a virtual machine as I just went all out and created a dual partition.

---

### Post by Tatty on 2008-09-03
It sounds like you have installed it using WUBI, is this correct?

If so, then no you cant run it from inside windows afaik, as it is an operating system so it needs to boot from startup.

If you want to run it from within windows then you will need to install it in a virtual machine as rusty377 said.  Though please realise that this will run much slower than it would otherwise do, and you may not be able to get many drivers (such as proprietry graphics card drivers) installed in it, as they will not have the direct access they require to the hardware.

It sounds as though something has gone wrong with your WUBI install, as it seems to be failing to boot, If you want to try to fix this could you please give us some more information on where exactly it goes wrong?

---

### Post by jemate18 on 2008-09-03
Another virtualization is xVM from sun 

download it at
> [http://www.sun.com/download/index.jsp](http://www.sun.com/download/index.jsp)

---


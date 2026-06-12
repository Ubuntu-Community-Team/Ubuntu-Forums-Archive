---
title: "Windows in a VM"
date: 2013-06-25
forum: New to Ubuntu
---

### Post by conure on 2013-06-25
Hey everyone, 

I am about to do a full install of Ubuntu on my main system.

I need Windows for school, for example, I have an Adruino board specifically from my university which has drivers which only work in Windows. Also, some of the robotics software I have doesn't work well in wine.

The thing is, I want an extremely responsive native installation of Ubuntu because it's much nicer to work with. If I install Windows via VirtualMachine within Ubuntu, does that Windows OS have 100% functionality in terms of drivers and software. For example, if I install the Arduino board within Windows in the VM, will it operate exactly as it would as a native installation?

I hope this makes sense - please not I'm not asking about performance, as I know that a Windows VM will not perform as quickly as a native install.

hope you can advise!

---

### Post by Kopkins on 2013-06-25
It will not be exactly like a native install. By running it in a VM you have to share your system resources. So to use Windows, Ubuntu will have to be running. That mean that memory and CPU cycles are taken up by both systems. Unless your computer has a higher memory capacity and a great processor, you will lose a lot of performance. 

However, you can always dual boot, Meaning that you have both a native install of both Windows and Ubuntu. This way you will get the most performance out of both of them. My Macbook is triple booting two Linux distrubutions and OSX. 

Is Windows installed on your computer now?

Kopkins

---


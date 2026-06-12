---
title: "Ubuntu Kylin is slow"
date: 2014-12-24
forum: New to Ubuntu
---

### Post by jon80 on 2014-12-24
I just installed Ubuntu with Kylin as the IDE, and, surprisingly with 1Gb of ram allocated to the virtual machine (Virtual Box), the UI navigation is too slow, and, I even have problem browsing and copying files.  I was hoping to use this machine for writing games, so definitely this indicator will put me off.

I am pleased to note that it comes bundled with the Maltese language, I hope that open source programmers are acknowledged for this culturally sensitive effort as I am a Maltese native :)

Do you have any hints please?

---

### Post by nerdtron on 2014-12-25
Did you installed guest additions? is hardware acceleration enabled? how many processor did you allocate to the VM?

---

### Post by DuckHook on 2014-12-26
VirtualBox (or any VM) is very hard on any older system. It needs a lot of power to run effectively, especially in CPU and GPU. 1GB RAM is not that much either, as I usually recommend 2GB to run Ubuntu even on bare metal. You probably don't need any more than 2GB in a VM, but your CPU and GPU are likely the bottlenecks in your system. You will have to post your HW specs and also what OS is hosting the VM.

It may be better for you to run one of the lighter 'buntu flavours instead of Ubuntu. Try Xubuntu or Lubuntu. Neither use 3D, so you take the load off of the GPU right away. They also use less CPU cycles and less RAM, so 1 GB is sufficient in both cases. Lubuntu is lighter than Xubuntu, but does not look as nice.

Lastly, why are you using Kylin? As far as I know, this is the Chinese varient of Ubuntu and does not add anything to Ubuntu's utility in Maltese.

---


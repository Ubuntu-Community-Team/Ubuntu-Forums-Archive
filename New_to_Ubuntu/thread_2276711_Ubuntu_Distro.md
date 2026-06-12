---
title: "Ubuntu Distro"
date: 2015-05-04
forum: New to Ubuntu
---

### Post by Ahmet_Kurt on 2015-05-04
Hi All,

We will starting a new project. We decided to use ubuntu based OS. Below is our constraints and use cases. Could you please suggest best Ubuntu Version(Ubuntu/Kubuntu/Lubuntu ...)

* OS must be in 64-bit architecture
* We want to use most recent Linux Kernel
* We will use USB, Serial, Ethernet interfaces

* We do **NOT** need Graphical Interface(SSH is OK)

* Our application will start while booting as a service and do **NOT **need User Interaction
* I must be as stable as it can
* We want our application use most of the system resources

Thanks for your help,

* We do not need Office, Web Browser, Mail Client vs user applications

---

### Post by Vladlenin5000 on 2015-05-04
If you don't need GUI then why you list normal desktop releases (with GUI)? Ubuntu server should be enough...

---

### Post by Lars Noodén on 2015-05-04
Yes, you probably want the [server edition](http://www.ubuntu.com/download/server) rather than a desktop flavor.  

Specifically you should look at 14.04 LTS and not any of the other versions.  The non-LTS versions must be upgraded every 6 months, with a 3-month grace period.  In contrast, 14.04 LTS is good through [April 2019](https://wiki.ubuntu.com/Releases) and as a bonus has less experimental [systemd](http://forums.debian.net/viewtopic.php?f=20&t=120652&start=0) material than the subsequent versions.

---

### Post by grahammechanical on 2015-05-04
@Ahmet_Kurt

We are assuming that this application will be running on desktop/laptop hardware because that is what most of us on this forum use. But if the intention is for that app to run on an embedded device then you might want to consider Snappy Ubuntu Core.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

Ubuntu Snappy Core is very new. It is under active development

> 
**Internet of Things: Snappy on Devices**

 [&#8216;Snappy&#8217; Ubuntu Core]("http://www.ubuntu.com/cloud/tools/snappy")  is the smallest and most secure edition of Ubuntu. It is a super-lean,  transactionally updated version of Ubuntu, perfect for inventors,  technologists and the active and growing Ubuntu developer community, for  cloud container hosts and smart, connected devices. It powers drones,  robots, network switches, mobile base stations, industrial gateways, and  IoT home hubs.



[https://insights.ubuntu.com/2015/04/21/ubuntu-15-04-desktop-phone-and-iot-towards-a-converged-future/](https://insights.ubuntu.com/2015/04/21/ubuntu-15-04-desktop-phone-and-iot-towards-a-converged-future/)

I am sure that there are developers that use an operating system with a Graphical User Interface to develop apps even when those apps are going to run on an OS without a GUI. So, I am more than little confused about your question.

What your app is capable of doing is surely less to do with the computer operating system that is running on the device and more to do with the code written by the developer.

The Ubuntu family is made up of Ubuntu; Xubuntu; Kubuntu; Lubuntu; Ubuntu Gnome and Ubuntu Mate. Each memeber of the family comes as a 64 bit OS. The latest versions have the latest Linux kernel and hardware stacks. And each of them comes with Linux driver modules for serial; ethernet and USB interfaces because these modules are standard in the Linux kernel.

Regards.

---

### Post by Ahmet_Kurt on 2015-05-05
> **grahammechanical said:**
> @Ahmet_Kurt

We are assuming that this application will be running on desktop/laptop hardware because that is what most of us on this forum use. But if the intention is for that app to run on an embedded device then you might want to consider Snappy Ubuntu Core.

[https://developer.ubuntu.com/en/snappy/](https://developer.ubuntu.com/en/snappy/)

Ubuntu Snappy Core is very new. It is under active development



[https://insights.ubuntu.com/2015/04/21/ubuntu-15-04-desktop-phone-and-iot-towards-a-converged-future/](https://insights.ubuntu.com/2015/04/21/ubuntu-15-04-desktop-phone-and-iot-towards-a-converged-future/)

I am sure that there are developers that use an operating system with a Graphical User Interface to develop apps even when those apps are going to run on an OS without a GUI. So, I am more than little confused about your question.

What your app is capable of doing is surely less to do with the computer operating system that is running on the device and more to do with the code written by the developer.

The Ubuntu family is made up of Ubuntu; Xubuntu; Kubuntu; Lubuntu; Ubuntu Gnome and Ubuntu Mate. Each memeber of the family comes as a 64 bit OS. The latest versions have the latest Linux kernel and hardware stacks. And each of them comes with Linux driver modules for serial; ethernet and USB interfaces because these modules are standard in the Linux kernel.

Regards.


Thanks for your attention.

We are planning to develop application on Ubuntu Desktop Edition. I'm asking for Target Platform. Actually our target platform is embedded but components are similar to Desktop Level. Only difference is our target platform is ruggetized.

Below is the specs of candidate target Board
- Intel i7
- 4 GB RAM
- 8 GB Flash
- 16 GB External Storage
- Gigabit Ethernet
- USB 2.0

---

### Post by mastablasta on 2015-05-05
Ubuntu minimal install? then add what you need. it's gone be fast.

---

### Post by Ahmet_Kurt on 2015-05-06
> **mastablasta said:**
> Ubuntu minimal install? then add what you need. it's gone be fast.

Actually i'm searching something like this. I will check LTS version of the Ubuntu Minimal and Ubuntu Server Edition.

Thanks for your help.

---


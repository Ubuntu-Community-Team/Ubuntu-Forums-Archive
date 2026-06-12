---
title: "Installing Ubuntu on an i686 laptop"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by zaqaz1 on 2012-05-22
Hi, I'm installing Ubuntu on a friend's laptop after his OS was corrupted.  It's a Fujitsu Siemens Amilo Pro V1000 with a pentium 4 processor.  When I boot Ubuntu from a CD I get a message saying "This kernel requires an x86-64 CPU, but only detected an i686 CPU.  Unable to boot - please use a kernel appropriatefor your CPU".  Is there a way around this or is there somewhere I can download an i686 version?

---

### Post by cariboo on 2012-05-22
Just download and install the 32-bit version, as a P-4 is a 32-bit CPU.

---

### Post by grahammechanical on 2012-05-22
According to this

[http://www.immortalsgate.com/dkauk/Laptops/Siemens_Amilo_Pro_V1000.htm]("http://www.immortalsgate.com/dkauk/Laptops/Siemens_Amilo_Pro_V1000.htm")

the CPU is an Intel mobile Celeron 2.5GHz.

According to this

[http://www.cpu-world.com/CPUs/Celeron/Intel-Mobile%20Celeron%202.5%20GHz%20-%20RH80532NC060256.html]("http://www.cpu-world.com/CPUs/Celeron/Intel-Mobile%20Celeron%202.5%20GHz%20-%20RH80532NC060256.html")

it is a 32bit CPU. You must be trying to install the 64bit Ubuntu.

Go to here

[http://www.ubuntu.com/download/desktop]("http://www.ubuntu.com/download/desktop")

and download the recommended 32bit Ubuntu. Also called i386 in comparison to the 64bit Ubuntu called amd64.

i686 means that your CPU is the 6th version of the Intel x86 micro-architecture. Whereas amd64 is called that because AMD first came out with a 64bit CPU running x86 code.

So, do not get confused. Both i386 and amd64 Ubuntu OS will run on Intel and AMD CPUs. An 32bit or i386 Ubuntu will run on either a 32bit or a 64bit CPU but a 64bit or amd64 Ubuntu will only run on a 64bit CPU.

Regards.
Regards.

---


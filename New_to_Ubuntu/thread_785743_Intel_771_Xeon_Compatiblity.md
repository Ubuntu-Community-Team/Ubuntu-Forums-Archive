---
title: "Intel 771 Xeon Compatiblity"
date: 2008-05-07
forum: New to Ubuntu
---

### Post by LRT on 2008-05-07
My motherboard manual says my CPU is a:

Dual Intel® 64-bit Xeon LGA 771 quad core/ dual core processors at a front side bus speed of 1333 MHz/1067 MHz/667MHz

The motherboard is a Supermicro X7DVL-E

check it out here: [http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-E.cfm]("http://www.supermicro.com/products/motherboard/Xeon1333/5000V/X7DVL-E.cfm")

i have a few questions about this:

1 - is anyone running ubuntu 8.04 on this hardware? 

2 - do i have to run the 64-bit version of ubuntu on this hardware? what do you recommend??

3 - the graphics card is an ATI ES1000 controller with 16 MB of video memory. does ubuntu 8.04 support that??

4 - where can i find an official comprehensive HCL for ubuntu 8.04?

background:
this machine used to run a windows 2003 sbs server. i finally took it down and i am planning on installing ubuntu 8.04 on it. this is going to be a server install that will support a production environment. i need to make sure the hardware will work. thanks in advance for your help!

---

### Post by Delever on 2008-05-07
"XEONs are capable of EM64T, which is AMD's x86_64 technology licensed and rebranded".

You should go with 64-bit version. Booting from ubuntu cd will answer further questions without touching your hard drive, if you don't select "install".

---

### Post by LRT on 2008-05-08
thanks. i wasn't sure about the ubuntu 64bit. i'll boot the live cd and see what happens.

---

### Post by sy88 on 2008-05-08
Don't forget to check if all the software you want is 64 bit compatible!  If it becomes a big hassle, just install 32 bit since there isn't much of a difference from the user's point of view.

---

### Post by LRT on 2008-05-08
thanks for the warning. the software i will be using is standard server software. mainly dhcp, samba, and iptables. i will also be running BackupPC. 

will i have issues with any of these on 64bit???

---

### Post by Cadmus on 2008-05-08
Major programs like Samba and DHCP server you'll have no problems with. As far as I know the only programs that cause problems are those that are a bit esoteric and have a small user/coder base.

---

### Post by LRT on 2008-05-08
great thanks!

---


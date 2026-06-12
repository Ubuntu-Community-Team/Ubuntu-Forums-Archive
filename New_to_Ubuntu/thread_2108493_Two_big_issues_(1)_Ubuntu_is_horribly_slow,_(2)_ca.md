---
title: "Two big issues: (1) Ubuntu is horribly slow, (2) can't setup ati mobility driver"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by Broax on 2013-01-24
Hi everyone! 

I'm a absolute beginner in Ubuntu. I decided to give it a try 'cause I already use mostly open source software, the recent direction windows is taking seems a bit scary and the recent hype valve created around Linux really tickled my interest. 

I'm an absolute zero in regards to anything that isn't Microsoft so you'll have to help me, help you, help me! 

Anyway... I just installed Ubuntu from the Windows installer on the site and gave it 30Gb. After the installation everything looked good but then I started to noticed everything was a bit slow. Most of the time windows freeze for minutes or just end up crashing. I was trying to search for info around the web but this slowness was killing me. Things got particularly bad if I tried to do simple tasks simultaneously like unzip a file while chatting on facebook (mozilla). Actually while doing this the computer crashed and I rebooted to windows so that I could do this post.

The second issue is: After successfully installing steam (I was actually able to install a 32bit compatibility package) I noticed I was using some generic graphic driver. But apparently installing graphic drivers for a laptop is a big issue as I can't even find them to start with!! 

Anyway... Just ask for any information you need and please tell me how I can give it to you as I am so far a complete illiterate who doesn't even know how to check the installed OS version.

As for hardware I can help:
Toshiba Satellite L500 laptop
CPU: Intel Pentium Processor T4200 2.00 GHz (Dual Core 64bit)
RAM: 4Gb
Graphics: ATI Mobility Radeon HD 4570 (dxdiag tells me it has 2gb but I'm pretty sure only 1Gb is dedicated).

If you require any other relevant information feel free to ask and I'll do my best to reply. I shouldn't have a problem coming up with information with windows. Inside Linux it's a different tale. 

On a side-note: I seem to have pretty much the same free space available which leads me to think this particular Linux installation isn't making partitions and instead is emulation the file system linux uses.. Could this be related to the slowness I'm experiencing?

---

### Post by lukeiamyourfather on 2013-01-24
Ubuntu has a handy utility to install proprietary drivers like graphics drivers. A driver for AMD/ATI cards should show up on the list which you can enable from there. I think the program is just called "Hardware Drivers" if I remember correctly.

---

### Post by gifford on 2013-01-24
The install of the proprietary drivers will depend on which version of Ubuntu you are using, 12.10 or 12.04 LTS.

---

### Post by Broax on 2013-01-24
> **lukeiamyourfather said:**
> Ubuntu has a handy utility to install proprietary drivers like graphics drivers. A driver for AMD/ATI cards should show up on the list which you can enable from there. I think the program is just called "Hardware Drivers" if I remember correctly.

I'm using windows ATM but I'll switch to linux in a couple of minutes and give it a try... =) 

> **gifford said:**
> The install of the proprietary drivers will depend on which version of Ubuntu you are using, 12.10 or 12.04 LTS.

I think I installed 12.10 and NOT 12.04 LTS. The installer is wubi.exe. How would I check that to give you that information?

---

### Post by audiomick on 2013-01-24
Boot into it and look for the system monitor. The first tab on that shows you the version.

---

### Post by gifford on 2013-01-24
In 12.04 you can install by going to system settings and under hardware, additional drivers.
In 12.10, you need go to software sources and the tab for additional drivers.

---

### Post by Broax on 2013-01-24
Ok, so here's the info I got:
Distribuição 12.10 (quantal) 64-bit
Kernel Linux 3.5.0-22-generic
GNOME 3.6.0

Should I reinstall this with version 12.04? Would it make things easier on me?

EDIT: I went to to software sources/additional drivers and there's no button I can click to change anything.. I'll add a screen grab, it's in Portuguese but I think you can understand everything from context... 

[IMG]http://i.imgur.com/2S7rXOEl.png[/IMG]

Original size: [http://i.imgur.com/2S7rXOE.png](http://i.imgur.com/2S7rXOE.png)


Also, since rebooting the system feels much more responsive and doesn't freeze at all... Any clues on what could be causing this? Could there be any fan that's not working on linux causing the system to overheat (a friend warned me about this) or could it be related to the fact that it's not using native partitions unlike traditional installations (my own deduction)?

---

### Post by MadmanRB on 2013-01-24
Yeah, WUBI can ber much slower then a normal install, as its like running off a virtual install of the system.
Dont get me wrong WUBI is a great way to try ubuntu out but dont let it give you the wrong impressions.
A more proper full install of Ubuntu would run better, I also suggest running 12.04 for stability sake.

---

### Post by Broax on 2013-01-24
> **MadmanRB said:**
> Yeah, WUBI can ber much slower then a normal install, as its like running off a virtual install of the system.
Dont get me wrong WUBI is a great way to try ubuntu out but dont let it give you the wrong impressions.
A more proper full install of Ubuntu would run better, I also suggest running 12.04 for stability sake.

Hmmm... taking all that into account, if I wish not to format my Windows installation can I use the ubuntu install disk to resize the partitions or should I use old tricks like Partition Magic? Is there any good free program that could help me resizing partitions without deleting the content?

Also would ver 12.04 make it easier to install my graphics card? I would probably like to try to make the graphics card work before I'd start hacking and slashing my partition table...

---

### Post by alphacrucis2 on 2013-01-24
> **Broax said:**
> Hmmm... taking all that into account, if I wish not to format my Windows installation can I use the ubuntu install disk to resize the partitions or should I use old tricks like Partition Magic? Is there any good free program that could help me resizing partitions without deleting the content?

Also would ver 12.04 make it easier to install my graphics card? I would probably like to try to make the graphics card work before I'd start hacking and slashing my partition table...

It may be that the AMD Catalyst driver for 12.10 doesn't support your card. AMD have a habit of dropping support for older cards in their latest drivers. You may have more luck with 12.04 as that will use an older AMD proprietary driver.

PS. Windows 7 can shrink its own partition via the control panel -- Administration -- Computer Management --- Storage -- Disk Management. That is the best and safest way to make space for Ubuntu ext4 & swap partitions. The Ubuntu install CD does include a utility called gparted which also allows you to resize, create and delete partitions but it is probably safer to let Windows do the resize itself.

PPS. Whenever messing around with partitions it is always recommended to make sure you have a backup of any data. Always better to be safe than sorry.

---

### Post by Broax on 2013-01-24
> **alphacrucis2 said:**
> It may be that the AMD Catalyst driver for 12.10 doesn't support your card. AMD have a habit of dropping support for older cards in their latest drivers. You may have more luck with 12.04 as that will use an older AMD proprietary driver.

Well, from what I can gather from these forums 12.04 is the way to go... So I'll just uninstall this and reinstall ver 12.04. I'll update on the result once it's done... =)

---

### Post by MadmanRB on 2013-01-24
Do keep in mind there is also the util.ity on the live installer too to dual boot, as usually ubuntu likesd splitting the drive in half.
Make sure to defrag windows though if this has been a system thats been on there for a while.

---


---
title: "New Ubuntu user"
date: 2013-10-28
forum: New to Ubuntu
---

### Post by aadikirni on 2013-10-28
Can i use Ubuntu without any knowledge of Linux operating systems?. If so then what will be the scope of my Experience?. Do i need to some prior knowledge of a Linux Operating system before venturing into Ubuntu?.

I have heard from [http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/) that the Hardware and the Pheriperals wont need any new driver software if you are using Linux. Can anybody please shed some light on that.

I am captivated by the whole Open-source software thing, and i want to use Ubuntu for more than just "use". Anybody got some ideas for a budding and an interested Linux learner. I just want to know where to start.



P.S: I know you all would have found many threads like this and will probably think that i am a lazy ass. I just wanted to ask all my questions collectively instead of searching for them one-by-one. So, i would be pleased if someone would find time to answer some old and "asked" questions.:o

                                                                                                     Thank you in advance

---

### Post by fantab on 2013-10-28
Well, you can learn to swim only by jumping into the waters. There is a learning curve to linux, but this cannot be reached without using linux. So take the plunge.

In Gnu/Linux most of the drivers are built in (into the linux-kernel), most of the times you don't have to install any other driver. However there are some hardware manufacturers who will only release 'proprietory' drivers for linux, for example Graphic cards like nvidea or radeon, which you will have to install separately. Anything that is NOT opensource will not be default.

You should begin with: [LINUX is NOT Windows]("http://linux.oneandoneis2.org/LNW.htm").

For a beginner it will be good idea to start with Dual-Boot of ubuntu and Windows. Until you are comfortable with linux you will have the other OS to fall back upon. Also there will be certain games and applications in Windows which will not run in Linux and that there may not be a decent alternative in Linux.

Certain Windows programs can be run on Linux using [WINE]("http://www.winehq.org/about/"), check [Wine Database]("http://appdb.winehq.org/") to see if it helps.

---

### Post by sudodus on 2013-10-28
Welcome to the Ubuntu Forums :-)

> **aadikirni said:**
> Can i use Ubuntu without any knowledge of Linux operating systems?.

Yes> 
If so then what will be the scope of my Experience?. Do i need to some prior knowledge of a Linux Operating system before venturing into Ubuntu?. You can use the standard applications with some fantasy and prior experience of other operating systems (Windows or MacOS). Things are not exactly the same, but you can use trial and error to find out how it works. > 

I have heard from [http://www.whylinuxisbetter.net/](http://www.whylinuxisbetter.net/) that the Hardware and the Pheriperals wont need any new driver software if you are using Linux. Can anybody please shed some light on that.This is correct for many computers and peripheral devices, but not all. Some of them need 'proprietary drivers to be installed' and some hardware cannot run at all because nobody made a linux driver for it.> 

I am captivated by the whole Open-source software thing, and i want to use Ubuntu for more than just "use". Anybody got some ideas for a budding and an interested Linux learner. I just want to know where to start.If you want to use the full potential of linux, you need to learn about it. Some things are easy, some are a bit harder to learn. There are many threads here at the Ubuntu Forums including tutorials, and there are lots of wiki pages about Linux in general and Ubuntu in particular. Browse the internet to find texts that suits your way of thinking :-) [COLOR=#696969]You will probably get several tips in new posts in this thread.[/COLOR]> 

P.S: I know you all would have found many threads like this and will probably think that i am a lazy ass. I just wanted to ask all my questions collectively instead of searching for them one-by-one. So, i would be pleased if someone would find time to answer some old and "asked" questions.:o

                                                                                                     Thank you in advance

---

### Post by aadikirni on 2013-10-28
You are right about the whole "plunging" thing. I am very[SIZE=3] [/SIZE][FONT=arial, sans-serif][SIZE=3][SIZE=2]excited about it too. The whole open-source,free world concept is a definite catch. Although a whole new UI completely different from windows is still difficult to grasp. Hope i will like it [/SIZE][/SIZE][/FONT]:)[FONT=arial, sans-serif][SIZE=3][SIZE=2] [/SIZE][/SIZE][/FONT]

---

### Post by aadikirni on 2013-10-28
Also which one of these options you think is a good idea, Dual-boot or a Ubuntu installed on a VMware ..?

---

### Post by sudodus on 2013-10-28
It depends very much on your hardware and installation of Windows. Please specify the computer hardware

- Brand name and model
- CPU, RAM (size), graphics card/chip, wifi card/chip

- version of Windows XP, Vista, 7, 8? 32-bit or 64-bit? Home or Professional?
- installed with BIOS or UEFI?

---

### Post by sudodus on 2013-10-28
> **aadikirni said:**
> You are right about the whole "plunging" thing. I am very[FONT=arial][SIZE=3][SIZE=2]excited about it too. The whole open-source,free world concept is a definite catch. Although a whole new UI completely different from windows is still difficult to grasp. Hope i will like it [/SIZE][/SIZE][/FONT]:)

There are several flavours of Ubuntu with different desktop environments. If you have a fast internet connection you can download and try several of them 'try them live' without installing, and install the one that suits your computer and yourself.

Lubuntu
Xubuntu
standard Ubuntu
Kubuntu

---

### Post by fantab on 2013-10-28
> **aadikirni said:**
> Also which one of these options you think is a good idea, Dual-boot or a Ubuntu installed on a VMware ..?

Definitely Dual-Boot. If your hardware supports VMware then VMware. But I won't recommend it. Run the real thing.

---

### Post by aadikirni on 2013-10-28
Yes!. I will check my laptop configuration and post it tomorrow

---

### Post by aadikirni on 2013-10-28
Time of this report: 10/28/2013, 21:50:26
       Machine name: SONY-VAIO
   Operating System: Windows 7 Home Basic 64-bit (6.1, Build 7601) Service Pack 1 (7601.win7sp1_gdr.110408-1631)
   Processor: Intel(R) Core(TM) i3-2330M CPU @ 2.20GHz (4 CPUs), ~2.2GHz
   Memory: 4096MB RAM
   Card name: NVIDIA GeForce 410M
   Display Memory: 2265 MB
   yes i have a Wifi but card/chip idk .... chip i guess.. 
   and it was definitely a BIOS install ....... can my lap survive a dual-boot?

---

### Post by sudodus on 2013-10-28
Your computer can run dual boot as well as Ubuntu with reasonable speed in a virtual machine (VMware, VirtualBox or KVM-qemu).

The very first test is to try 'live' booted from CD/DVD/USB without installing anything. The next step is to choose between dual boot and a virtual machine. You may want to try Ubuntu or some of the Ubuntu flavours in a virtual machine, and after a while create a dual boot system for a gradual transfer from Windows to linux. But it is also possible to start with dual booting right now. Dual boot is risky because you need to edit partitions, so you should start by backing up the whole Windows system or at least all your personal files.

After a year or two, maybe you will boot/log into Windows less than once a month.

---

### Post by Baldrick_NZ on 2013-10-29
From my experience, the varience of the learning curve really depends on two things..

1/ How much experience the user has had with Windows
2/ How keen the user is to try Linux, and stick with it.

If you have had extensive experience with Windows, Your Linux learning-curve will be steeper. Conversely, if you have had limited experience with Windows, the linux learning curve will be much less severe.

I personally think the reason for this is that Linux (generally speaking) makes logical human assumptions as to what you want to achieve when you do 'X', whereas when you do 'X' in Windows you often don't get the same result. So, it's much easier for the logical thinker who has limited (or no) knowledge of Windows to pick-up Linux, than one who has been immersed in the not-so-logical world of Windows. 
This then leads to point two. 

Others may have a different point of view, but this is what I've observed through friends and family who have tried Linux and stayed with it, or the learning curve was too step so stuck with Windows.

Me? I came from a Windows background, but applied point two, and as a result have been personally Windows free for four years now - and still loving it!

Hope that helps.

---


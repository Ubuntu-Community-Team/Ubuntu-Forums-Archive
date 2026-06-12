---
title: "Intalled ATI Radeon Driver but still feel the heat"
date: 2013-10-31
forum: New to Ubuntu
---

### Post by bluefireprofits on 2013-10-31
Hello Everyone,

Yesterday I did a clean install on my PC, after installing xubuntu 13.10, I proceeded to install additional driver toolkit.

When I re-checked I got these two different messages. More over I am still feel the laptop still being heated  up on the left hand side of the touchpad, which was not the case when I had windows 7 installed on it.

[[img]http://s24.postimg.org/8fdmu20v5/b_RIi_Bt_F.jpg[/img]](http://postimg.org/image/8fdmu20v5/)
[[img]http://s24.postimg.org/pdcnfwa8x/dx1_Wa_Uv.jpg[/img]](http://postimg.org/image/pdcnfwa8x/)
[[img]http://s24.postimg.org/z5oid0zxd/h_FUkdqe.jpg[/img]](http://postimg.org/image/z5oid0zxd/)

Please help me on this heating issue with the laptop.

Regards
Alex

---

### Post by UltimateCat on 2013-10-31
Does your Radeon card have a fan of it's own?

If not is this computer a Desktop or a Laptop and what kind?
I'll look up the spec's tomorrow-

Some Toshibia laptops are notorious for overheating-
I had to take a friend of mine's apart because of overheating--

Depending on how old your computer is it could be dust build up on the fan and the heat sink could just need cleaned.

You can run Memtest to see if the RAM is bad-
[http://www.memtest.org/](http://www.memtest.org/)

You can use the temperature command to see how hot it is getting-
```
sensors -f | grep -i temp

```


Here's the newest driver for your card-(if you like)
I prefer installing the .run scripts with bash but everyone has different preferences-

[http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx)

---

### Post by bluefireprofits on 2013-10-31
> **UltimateCat said:**
> Does your Radeon card have a fan of it's own?

If not is this computer a Desktop or a Laptop and what kind?
I'll look up the spec's tomorrow-

Some Toshibia laptops are notorious for overheating-
I had to take a friend of mine's apart because of overheating--

Depending on how old your computer is it could be dust build up on the fan and the heat sink could just need cleaned.

You can run Memtest to see if the RAM is bad-
[http://www.memtest.org/](http://www.memtest.org/)

You can use the temperature command to see how hot it is getting-
```
sensors -f | grep -i temp

```


Here's the newest driver for your card-(if you like)
I prefer installing the .run scripts with bash but everyone has different preferences-

[http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx](http://support.amd.com/en-us/kb-articles/Pages/Latest-LINUX-Beta-Driver.aspx)



May be this is the first time I am using linux and bit paranoid about the temperature and working of this new operating system.

Just install sensor application and the temperature readings seem to be just fine.

[[img]http://s24.postimg.org/slh4sxwip/2s_Kwl_Rv.jpg[/img]](http://postimg.org/image/slh4sxwip/)

But I am going to install the latest ATI driver [Beta Version]. Lets see.

Thanks a lot
Alex

---

### Post by bluefireprofits on 2013-10-31
[[img]http://s24.postimg.org/ahipm1o81/KQN2k6b.jpg[/img]](http://postimg.org/image/ahipm1o81/)

The area shown in purple gets heated up but the fans are running fine and temperature sensor are showing perfect temperature. 
I want to learn linux but not at the expense of loosing my machine. Please guide.

My System Specs
Computer
********


Summary
-------

-Computer-
Processor        : 4x AMD A6-3400M APU with Radeon(tm) HD Graphics
Memory        : 3509MB (709MB used)
Operating System        : Ubuntu 13.10
User Name        : Alex (Alex)
Date/Time        : Thursday 31 October 2013 03:32:22 PM IST
-Display-
Resolution        : 1366x768 pixels
OpenGL Renderer        : Unknown
X11 Vendor        : The X.Org Foundation
-Multimedia-
Audio Adapter        : HDA-Intel - HD-Audio Generic
Audio Adapter        : HDA-Intel - HD-Audio Generic
-Input Devices-
 Power Button
 Lid Switch
 Power Button
 AT Translated Set 2 keyboard
 Video Bus
 Video Bus
 HD-Audio Generic HDMI/DP,pcm        : 3=
 HD-Audio Generic Front Headphone
 HD-Audio Generic Mic
 HP WMI hotkeys
 SynPS/2 Synaptics TouchPad
 HP Webcam-101
  USB OPTICAL MOUSE
-Printers-
No printers found
-SCSI Disks-
ATA ST9500325AS
hp DVDRAM GT50N



Regards
Alex

---

### Post by UltimateCat on 2013-10-31
Your Welcome Alex-

If it comforts you that is exactly the area is which my Sony Vaio laptop get's warm.
63 degree's is ok, don't worry-


> I want to learn linux but not at the expense of loosing my machine. Please guide.

These links can help you with learning Linux-

[http://www.lm-sensors.org/](http://www.lm-sensors.org/)    (for monitoring hardware)
[http://www.lm-sensors.org/browser/lm-sensors/tags/V3-3-3/CHANGES](http://www.lm-sensors.org/browser/lm-sensors/tags/V3-3-3/CHANGES)
[http://en.wikipedia.org/wiki/Fan_control#Need_for_fan_control](http://en.wikipedia.org/wiki/Fan_control#Need_for_fan_control)
[http://www.techradar.com/us/news/software/operating-systems/beginner-s-guide-to-linux-where-to-start-1066778](http://www.techradar.com/us/news/software/operating-systems/beginner-s-guide-to-linux-where-to-start-1066778)

About Bash The Bourne Again Shell--

[https://docs.google.com/viewer?a=v&pid=gmail&attid=0.1&thid=13f09139acea41b4&mt=application/pdf&url=https://mail.google.com/mail/?ui%3D2%26ik%3D7659d668c7%26view%3Datt%26th%3D13f09139acea41b4%26attid%3D0.1%26disp%3Dsafe%26realattid%3Df_hhhffe100%26zw&sig=AHIEtbQSfi2lq2-oVUPXmZY1LFdk1Ooczw](https://docs.google.com/viewer?a=v&pid=gmail&attid=0.1&thid=13f09139acea41b4&mt=application/pdf&url=https://mail.google.com/mail/?ui%3D2%26ik%3D7659d668c7%26view%3Datt%26th%3D13f09139acea41b4%26attid%3D0.1%26disp%3Dsafe%26realattid%3Df_hhhffe100%26zw&sig=AHIEtbQSfi2lq2-oVUPXmZY1LFdk1Ooczw)

[http://linuxcommand.org/learning_the_shell.php](http://linuxcommand.org/learning_the_shell.php)
[http://ss64.com/bash/](http://ss64.com/bash/)

Aside from that you can read the Ubuntu Documentation and that will help you to understand a lot-
Understanding package management is helpful too but take your time.
It took me 4 years to get good at running Linux so pace yourself-

Investing in a good Linux Book will give you knowledge and wisdom that will help you to not only understand your OS but also help you to run it and keep it running efficiently-
I read the "Ubuntu Linux Bible" for about 2 years and it was very helpful.

This is a good book as well--When I ran Debian this book was a great tool to have on hand-
[http://debian-handbook.info/](http://debian-handbook.info/)

You can also learn a lot from the Debian and linuxtopia websites-
[http://www.debian.org/](http://www.debian.org/)
[http://www.linuxtopia.org/](http://www.linuxtopia.org/)

[http://www.linuxtopia.org/LinuxSecurity/](http://www.linuxtopia.org/LinuxSecurity/)
[http://www.linuxsecurity.com/](http://www.linuxsecurity.com/)

And last; you can learn a lot from looking around in the Xubuntu Forum
[http://xubuntu.org/help/](http://xubuntu.org/help/)


Cheers-:D

---

### Post by UltimateCat on 2013-10-31
The command for finding out your motherboard, graphics card, sound card, and what processor you have is:
```
lspci

```

It will look something like mine-
```
 ~]$ lspci
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Thames [Radeon HD 7550M/7570M/7650M]
01:00.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Turks/Whistler HDMI Audio [Radeon HD 6000 Series]
07:00.0 Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)
08:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 07)


```

You have an AMD processor. I have in this Vaio an Intel 3rd generation dual core processor-
Atheros is my network interface card and Radeon is my graphics card.
Reading through output can be overwhelming but as time goes by you'll understand how linux see's things-

Good luck to you and I hope this has helped you-

Cheers ;)

---

### Post by bluefireprofits on 2013-11-01
Hello UltimateCat,

Thanks a lot for all the details and info you have given on linux. For now I am not feeling at ease with linux and moved back to windows 7. 
I am not afraid of the learning curve, rather I need some time to understand how things work inside linux and how I can benefit from it. 

If you don't mind answering it... I have a question for you. Whenever and whrever I go and ask one simple noobish question "why is linux better than windows"====> Thr comes one straight answer from the core "because it more stable and secure" without even exploring what other OS can or has to offer. If people talk about stability and security I can easily provide that in windows too, provided they use some common sense which is true in the case of linux too. 

In last two days of my usage my applications crashed n number of times it can be because I am using a an unstable derivative of unstable derived product i.e. ubuntu. 

Please show me a way or a place where I can get more information of all the major linux distributions and how they work [debian, arch, slackware, red-hat] why so many and why don't they follow the same extension. So many questions,,,, help me. 

Thank and Regards
Alex

---

### Post by Mark Phelps on 2013-11-01
Instability in MS Windows comes about primarily due to two factors: infections and bad drivers.  The first happens because folks do foolish things, like open suspicious emails, go to websites they shouldn't, install apps they shouldn't.  Infections CAN happen in Linux, too -- but they are very rare.

The second happens because folks succumb to promotions for apps that claim to automatically keep their drivers up to date -- and all too often, install older drivers or, in some cases, the wrong drivers.  If you avoid these and only update drivers from authorized sources, you won't have the driver problem.

Application crashing can happen in Linux, too, and can be due to driver problems -- especially on newer machine that use newer hardware for which the Linux drivers either have not matured yet, or folks have forced the installation of drivers they should not have.  Also, unlike in Windows, in Linux, folks can easily build apps from source code -- and that can lead to app problems, as well.

One common area of driver problems is hybrid graphics -- in which two different video chipsets are at work on the same PC.  Different combinations require different drivers and, in most cases, there are not stable Linux drivers to handle these situations.  Looks like yours may be one of these.

Overheating, is unfortunately, a common problem with recent Linux kernels because they don't handle CPU power management as well as does MS Windows.  There are some limited things you can do to address the overheating, but not all of them work.

---

### Post by bluefireprofits on 2013-11-01
Hello Mark,

You are perfectly right about the hybrid graphics. I have 1.5 GB of graphic card. 1 Gb is solo and another 512 is integrated with the chipset. ***May be I am facing this problem with ubuntu linux***, coz this was not the case when I tried manjaro linux and using it was a breeze too. I only dropped it coz its very new in the arena and I don't want to hop from one distro to another.

May be I need to read more about different linux flavors and what they have to offer. Only then I'll be ready to test another one.

Thanks again

---

### Post by mastablasta on 2013-11-02
so you have APU + another GPU?

tlp might be worth to look at. i do not have any overheating issue with AMD APU. i think A6 is well supported.

Manjaro is repackaged Arch Linux which is not that young. Arch linux comes with newer kernel than Ubuntu and drivers in linux are part of kernel so newer kernel+ newer drivers. so if it's stabel it's not oa bad option. you can also install newer kernel in ubuntu... 

anyway use what work best for you.

regarding security: Ubuntu offer a number out of box security features: [https://wiki.ubuntu.com/Security/Features](https://wiki.ubuntu.com/Security/Features)
there is no 100% security but Ubuntu has a lot more hurdles to go through than windows. for example windows gives out fixes once a month Ubuntu will give them as soon as they are available. so when vulnerability is discovered in windows it gives hackers at least a month, ubuntu may patch it wihtin the same day etc. many such things,

regarding stability i don-t have any crashes. especiall LTS has many bugs fixed. but anyway stability means crashes are predictable (if there are any), bugs are known (possible workarrounds exist if they are not crushed yet). i don't think 12.04 has any showstopper bugs. at least i didn't get any. using Xubuntu and Kubuntu 12.04.

---


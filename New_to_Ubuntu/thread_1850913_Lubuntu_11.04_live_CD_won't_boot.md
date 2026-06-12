---
title: "Lubuntu 11.04 live CD won't boot"
date: 2011-09-27
forum: New to Ubuntu
---

### Post by Big Lizard on 2011-09-27
The live CD gets to the blue Lubuntu load screen, the goes to a black screen, loads a few lines, then gets to

 ubunut@ubuntu:~$

From there...nothing. What is the command to run Lubuntu live?

---

### Post by Rex Bouwense on 2011-09-27
Welcome to the forums Big Lizard.  Which version of Lubuntu 11.04 did you download?  In other words, was it the 32 bit desktop version?

---

### Post by Big Lizard on 2011-09-27
Hi Rex. I have the 32 bit desktop version. I've also burnt to CD/RW and CD to see what happens.

The main OS on this computer is Mint 10, so here are the details of this machine:

```
bob@bob-AM2N1K-M-Plus ~ $ inxi -F
System:    Host bob-AM2N1K-M-Plus Kernel 2.6.35-22-generic i686 (32 bit) Distro Linux Mint 10 Julia
CPU:       Dual core AMD Athlon 64 X2 5000+ (-MCP-) cache 1024 KB flags (lm nx sse sse2 sse3 svm) bmips 4018.38 
           Clock Speeds: (1) 1000.00 MHz (2) 1000.00 MHz
Graphics:  Card nVidia C61 [GeForce 6150SE nForce 430] X.Org 1.9.0 Res: 1360x768@50.0hz 
           GLX Renderer GeForce 6150SE nForce 430/PCI/SSE2/3DNOW! GLX Version 2.1.2 NVIDIA 260.19.06 Direct Rendering Yes
Audio:     Card nVidia MCP61 High Definition Audio driver HDA Intel BusID: 00:05.0
           Sound: Advanced Linux Sound Architecture Version 1.0.23
Network:   Card-1 Realtek RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller driver rtl8180 at port bc00 BusID: 01:05.0
           Card-2 nVidia MCP61 Ethernet driver forcedeth at port ec00 BusID: 00:07.0
Disks:     HDD Total Size: 250.1GB (3.2% used) 1: /dev/sda ST3250410AS 250.1GB 
Partition: ID:/ size: 116G used: 7.6G (7%) fs: ext4 ID:swap-1 size: 6.29GB used: 0.00GB (0%) fs: swap 
Sensors:   System Temperatures: cpu: 16.0C mobo: N/A gpu: 0.0: 
           Fan Speeds (in rpm): cpu: N/A 
Info:      Processes 165 Uptime 4 min Memory 283.3/1885.0MB Runlevel 2 Client Shell inxi 1.4.12 
bob@bob-AM2N1K-M-Plus ~ $ 

```

---

### Post by amjjawad on 2011-09-27
> **Big Lizard said:**
> The live CD gets to the blue Lubuntu load screen, the goes to a black screen, loads a few lines, then gets to

 ubunut@ubuntu:~$

From there...nothing. What is the command to run Lubuntu live?

Hello and Welcome :)

I assume you already checked MD5SUM for your downloaded iso before burning it?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes#A11.04](https://help.ubuntu.com/community/UbuntuHashes#A11.04)

When you boot your machine and see the menu, please don't choose Try Lubuntu without installation because apparently, there is a bug and I already informed the developers. Instead, choose "Install Lubuntu" and once you see the Language Selection Step, press Quit then Quit. Right after that, you'll see Lubuntu LiveCD.

Enjoy and thanks for choosing Lubuntu ;)

---

### Post by Big Lizard on 2011-09-27
> choose "Install Lubuntu" and once you see the Language Selection Step, press Quit 
Thanks! That worked, and it's a pretty good trick to save to my Linux Tips and Tricks folder.

I read the known issues before posting, but nothing about this was mentioned.

Thanks to both of you for your help.:D

---

### Post by amjjawad on 2011-09-27
> **Big Lizard said:**
> Thanks! That worked, and it's a pretty good trick to save to my Linux Tips and Tricks folder.

Glad it worked and you most welcome :)


> I read the known issues before posting, but nothing about this was mentioned.

I had a discussion with the developers today (mailing list) and I hope they will work to fix it soon. If not with Lubuntu 11.10 then with 12.04.


If you need anything, please let me know.

Lubuntu is great and you made the right choice so enjoy and have fun.

---


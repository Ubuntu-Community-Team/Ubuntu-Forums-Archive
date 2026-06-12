---
title: "New to Ubuntu"
date: 2012-05-19
forum: New to Ubuntu
---

### Post by MoonPhyr on 2012-05-19
Hello,
I believe I've seen a similar posting on here concerning Ubuntu being slow and unresponsive. 
I've installed the latest version 12.04 within my windows 7 ultimate. I'm not ready to ditch win7 64 ever.
However, I've developed an interest in Ubuntu these last few months and finally installed it. I really like the OS, it is unique, different and quite beautiful. However, I'm very new at it and finding the experience has a learning curve to it. I've learned that Ctrl/Alt/Del doesn't give me the same results as in Windows. I can deal with the learning curve though. My problem is that Ubuntu feels hesitant. Unresponsive, and lags. The most simple task like trying to open firefox seems daunting. I don't feel my laptop is slow, it runs an intel pen dual-core processor, 2.0 GHz, 2 gbs ram.
yet, i constantly have to log-off re-login just to make it function. Last night I was online with it, and it performed better than most times but still, I'd like any suggestions that could help me enjoy this wonderful OS as an Alternative to windows. perhaps I'm doing a number of wrong things? Settings?   
thank you  =-):guitar:

---

### Post by bodhi.zazen on 2012-05-19
Can you identify your hardware. Most slow down are caused by poor drivers, most common are either graphics or wireless.

---

### Post by HermanAB on 2012-05-20
Simple really.

Run top.  See what is chewing CPU time. Google it and if useless, kill it.

If you are running Unity or Gnome, install XFCE or LXDE, log out, select the the new DE and log in again.

---

### Post by carl4926 on 2012-05-20
Open a terminal
type in it:** top** and hit enter

Is anything hogging your RAM or CPU?

Also, in a terminal type: **lspci -nnk**

Use your mouse to copy and paste the result here and put it in code tags.
From that we'll be able to see much of your hardware and drivers

---

### Post by MoonPhyr on 2012-05-20
Thanks everyone for your help. This seems to be a great forum, especially for noobs like myself. I will attempt to do the suggested actions, then hopefully have some results. Thank you all, you Ubuntu users are very kind to Noobs like me and I really appreciate it!
=-)

---

### Post by MoonPhyr on 2012-05-20
yes,  here are the hardware specs:

Acer Aspire 5735-4774

Windows 7 64x Ultimate
Intel Pentium dual-core processor T3200

up to 732 MB Mobile Intel Graphics 
Media Accelerator 4500M
2 gb DDR 2


probably not a monster of a laptop, but does the job great. I'm pondering the idea of bumping up the RAM to either 8 or 16 gigs..
Additional hardware I couldn't find out about..

---

### Post by MoonPhyr on 2012-05-20
xxx@ubuntu:~$ top

top - 23:01:55 up 13 min,  1 user,  load average: 0.76, 0.63, 0.45
Tasks: 153 total,   1 running, 152 sleeping,   0 stopped,   0 zombie
Cpu(s):  5.1%us,  1.3%sy,  0.0%ni, 93.6%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1979156k total,  1884336k used,    94820k free,   544448k buffers
Swap:   262140k total,       24k used,   262116k free,   909816k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3037 qi        20   0  659m  84m  33m S    5  4.4   0:20.64 firefox            
 2777 qi        20   0 1080m  69m  27m S    4  3.6   0:05.34 compiz             
 2537 root      20   0  176m  22m 7688 S    3  1.2   0:05.41 Xorg               
 2843 qi        20   0  512m  18m  10m S    2  1.0   0:01.00 unity-panel-ser    
 2749 qi        20   0 27016 2856  616 S    0  0.1   0:00.75 dbus-daemon        
 2759 qi        20   0  735m  17m  12m S    0  0.9   0:00.56 gnome-settings-    
 2796 qi        20   0 20168  940  768 S    0  0.0   0:00.03 syndaemon          
    1 root      20   0 24452 2400 1348 S    0  0.1   0:00.81 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/0        
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
   10 root      20   0     0    0    0 S    0  0.0   0:00.06 ksoftirqd/1        
   11 root      20   0     0    0    0 S    0  0.0   0:00.56 kworker/0:1        
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset

---

### Post by MoonPhyr on 2012-05-20
qi@ubuntu:~$ lspci -nnk
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: agpgart-intel
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: i915
    Kernel modules: i915
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
00:1a.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1a.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1a.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1a.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: ehci_hcd
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.3 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 [8086:2946] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
    Kernel driver in use: pcieport
    Kernel modules: shpchp
00:1d.0 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1d.1 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1d.2 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: uhci_hcd
00:1d.7 USB controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: ehci_hcd
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel modules: iTCO_wdt
00:1f.2 SATA controller [0106]: Intel Corporation 82801IBM/IEM (ICH9M/ICH9M-E) 4 port SATA Controller [AHCI mode] [8086:2929] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
    Subsystem: Acer Incorporated [ALI] Device [1025:0176]
    Kernel modules: i2c-i801
02:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8071 PCI-E Gigabit Ethernet Controller [11ab:436b] (rev 16)
    Subsystem: Acer Incorporated [ALI] Device [1025:013f]
    Kernel driver in use: sky2
    Kernel modules: sky2
03:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
    Subsystem: Quanta Microsystems, Inc EM303 802.11bgn Wireless Mini PCIe Card [AR9281] [1a32:0303]
    Kernel driver in use: ath9k
    Kernel modules: ath9k
qi@ubuntu:~$

---

### Post by carl4926 on 2012-05-20
> **MoonPhyr said:**
> yes,  here are the hardware specs:

Acer Aspire 5735-4774

Windows 7 64x Ultimate
Intel Pentium dual-core processor T3200

up to 732 MB Mobile Intel Graphics 
Media Accelerator 4500M
2 gb DDR 2


probably not a monster of a laptop, but does the job great. I'm pondering the idea of bumping up the RAM to either 8 or 16 gigs..
Additional hardware I couldn't find out about..

Similar to my G550 Lenovo
Which is working great with 12.04

More RAM is good, but 2GB should be fine

Your top output seems OK too

---

### Post by MoonPhyr on 2012-05-20
yeah, seems to be running better the last 15 minutes. I downloaded XFCE, extracted it but don't know it it actually installed or not. I'm very new to Ubuntu so it'll take time for me to learn my way around.
So we have similar pc specs,eh? cool. Thanks for your input.  I did some research the last few minutes, seems you're right, I should be ok with the 2 gigs  =-)
This is a work in progress, but so far I'm liking the whole Ubuntu experience as a nice alternative.

---

### Post by carl4926 on 2012-05-20
XFCE is a desktop environment
You sound like you downloaded the .iso
But to install XFCE you add it from the Software Centre - But if I were you I wouldn't. Not yet anyway.

If you are new at this, you'll probably do multiple new installs before you really have the hang of it.

---

### Post by carl4926 on 2012-05-20
> **carl4926 said:**
> XFCE is a desktop environment
You sound like you downloaded the .iso
But to install XFCE you add it from the Software Centre - But if I were you I wouldn't. Not yet anyway.

If you are new at this, you'll probably do multiple new installs before you really have the hang of it.


Just to clarify. You are running Unity Desktop. You could have downloaded Xubuntu and installed that. The you would be running XFCE.

You can install other desktop environments regardless of which Desktop version you initially installed.  You switch to the different desktop at the login screen by choosing the session type you want to use.

---

### Post by coldjeanz on 2012-05-20
When you say "within Windows 7" do you mean you  used wubi? If so then that's probably why it's slow

---

### Post by xedi on 2012-05-20
From what I heard, Wubi is not that much slower in everyday usage and affects disk speeds but in this case here, Ubuntu seems to lag universally. It still could be something to look into, though.

Edit: I googled a bit and someone with similar specs claims that a wubi install was very slow but a native was fine, so maybe it's really something worth trying out. BTW you don't have to ditch win 7, you can install Ubuntu also natively alongside it.

Generally Windows 7 shouldn't be faster than Ubuntu, so if Windows 7 is fine but Ubuntu is not, then there is something wrong. I once had a bad upgrade after which everything was incredibly slow, even the internet speed and a fresh install fixed that. I don't know if maybe a similar error could appear in a fresh installation and I doubt reinstalling would fix it.

---

### Post by lisati on 2012-05-20
> **xedi said:**
> From what I heard, Wubi is not that much slower in everyday usage and affects disk speeds but in this case here, Ubuntu seems to lag universally. It still could be something to look into, though.

I'm wondering if defragging within Windows might help a little.

---

### Post by MoonPhyr on 2012-05-21
Yeah, from what i can see, I did download the iso. Ubuntu is so different than from what I'm used to. I'm learning that you can't install anything like u can in Windows.  Just need to learn my way around is all. But i do like Linux so far.

---

### Post by MoonPhyr on 2012-05-21
> **coldjeanz said:**
> When you say "within Windows 7" do you mean you  used wubi? If so then that's probably why it's slow


Yes, I'm running Ubuntu 12.04 via Wubi within Win7 Ult 64.  These last couple of times I've logged in, it's been running pretty good. Not so many lags like before. At this point I'm not thinking of running it natively in its own partition. Maybe later on when I'm less lazy I'll create a separate partition for it but as of now, this seems to work well for me.:guitar:

---

### Post by MoonPhyr on 2012-05-21
> **carl4926 said:**
> XFCE is a desktop environment
You sound like you downloaded the .iso
But to install XFCE you add it from the Software Centre - But if I were you I wouldn't. Not yet anyway.

If you are new at this, you'll probably do multiple new installs before you really have the hang of it.

Yeah, from what i can see, I did download the iso. Ubuntu is so  different than from what I'm used to. I'm learning that you can't  install anything like u can in Windows.  Just need to learn my way  around is all. But i do like Linux so far.:guitar:

---

### Post by MoonPhyr on 2012-05-21
> **xedi said:**
> From what I heard, Wubi is not that much slower in everyday usage and affects disk speeds but in this case here, Ubuntu seems to lag universally. It still could be something to look into, though.

Edit: I googled a bit and someone with similar specs claims that a wubi install was very slow but a native was fine, so maybe it's really something worth trying out. BTW you don't have to ditch win 7, you can install Ubuntu also natively alongside it.

Generally Windows 7 shouldn't be faster than Ubuntu, so if Windows 7 is fine but Ubuntu is not, then there is something wrong. I once had a bad upgrade after which everything was incredibly slow, even the internet speed and a fresh install fixed that. I don't know if maybe a similar error could appear in a fresh installation and I doubt reinstalling would fix it.

Yeah, I'm using Wubi within Win7 64 but now as i type this, Ubuntu is tunning fine. Isn't lagging like before, don't know if there is any influence from the rest of the programs on my disk but i did run System mechanic 10 and Diskeeper earlier on my Windows. But somehow i don't feel like that would make a difference on this os. None the less, Ubuntu is running fine right now and see no reason to create its own partition to run natively but it is something I'm keeping in mind for future usage. As of now, I'm enjoying this OS with the Wubi. I'm just trying to get used to how it operates so differently than windows. Unlike windows, you just can't install anything that easily; or i have to get used to the lingo.

---

### Post by mastablasta on 2012-05-21
> **MoonPhyr said:**
>  I'm learning that you can't install anything like u can in Windows. 
 
Wrong statement. You can install but you can't install windows programmes in another OS without something like WINE or an emulator. you can install majority of Linux programmes since this is a linux system. for some it is a bit more problematic but most are in the Ubuntu's rich repositories. for everything else there are PPA's, .deb files and vairous install scripts.  as a last ditch effort there is source compile. 
 
 
Ubuntu, Debian and Red Hat really do have good software support.

---

### Post by xedi on 2012-05-21
> **MoonPhyr said:**
>  Ubuntu is running fine right now and see no reason to create its own partition to run natively but it is something I'm keeping in mind for future usage. As of now, I'm enjoying this OS with the Wubi. I'm just trying to get used to how it operates so differently than windows. Unlike windows, you just can't install anything that easily; or i have to get used to the lingo.

Good to hear that it runs fine now, even though it's weird that it didn't before.

As far as installing goes, I find most programs to be easier to install than in Windows and getting them updated, because the update manager handles them centrally in one place.

The first place to look if you want to install a program is the software-center. That is the most straight-forward and safest option. There you just click on install, type in your password and it is installed.

The second easiest are .deb packages. If you have one, double click on them and it will open the software-center and you can install them as above.

---

### Post by bodhi.zazen on 2012-05-21
> **MoonPhyr said:**
> Yeah, from what i can see, I did download the iso. Ubuntu is so different than from what I'm used to. I'm learning that you can't install anything like u can in Windows.  Just need to learn my way around is all. But i do like Linux so far.

It is a bit of a change

See:

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

and 

[https://help.ubuntu.com/12.04/ubuntu-help/index.html](https://help.ubuntu.com/12.04/ubuntu-help/index.html)

---

### Post by TBABill on 2012-05-21
OP, I didn't see anyone correct how to install the desktop for you, but if you'd like to use Xfce or LXDE desktop environments you can install them quite easily via terminal or software center. To do so via terminal, just ```
sudo apt-get install xubuntu-desktop
``` Change the word Xubuntu to Kubuntu (KDE) or Lubuntu (LXDE) to get those desktop environments as well. Just log out, click the sprocket and choose the new DE, then enter password and login.

---

### Post by MoonPhyr on 2012-05-28
> **xedi said:**
> Good to hear that it runs fine now, even though it's weird that it didn't before.

As far as installing goes, I find most programs to be easier to install than in Windows and getting them updated, because the update manager handles them centrally in one place.

The first place to look if you want to install a program is the software-center. That is the most straight-forward and safest option. There you just click on install, type in your password and it is installed.

The second easiest are .deb packages. If you have one, double click on them and it will open the software-center and you can install them as above.

Yes, I'm happy it's running better.  It takes getting used to, but it's such a simple interface and yet alien to me. I still need to tweak it a bit, and explore the software available to me. I like that there is lots of music apps for musicians/artists free of charge.

---


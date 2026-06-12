---
title: "Unsupported hardware (not AMD)"
date: 2015-05-24
forum: New to Ubuntu
---

### Post by Elie_Daou on 2015-05-24
I recently bought a new lenovo from a dealer and asked him to install Ubuntu on it. He did and it runs great, but there is one thing which is annoying. I constantly get this notification on the top right of my screen saying "Unsupported Hardware". [img]http://i.imgur.com/kjHMIYK.png[/img]
I have been relentlessly searching for it's cause but to no avail. 
NB: When I first received the laptop there were some HP programs pre-installed and I suspect that the dealer got the software from an Ubuntu HP laptop but I'm not exactly sure if it is any relevant to the problem at hand.

---

### Post by dino99 on 2015-05-24
/var/log/dmesg and/or xorg.0.log might help you identify the culprit

---

### Post by jeremy31 on 2015-05-24
Can you post terminal results of ```
lspci -nn; lsusb
```

---

### Post by Elie_Daou on 2015-05-24
results from runnign lspci -nn lsusb:
```
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
00:03.0 Audio device [0403]: Intel Corporation Device [8086:0a0c] (rev 0b)
00:14.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB xHCI HC [8086:9c31] (rev 04)
00:16.0 Communication controller [0780]: Intel Corporation Lynx Point-LP HECI #0 [8086:9c3a] (rev 04)
00:1b.0 Audio device [0403]: Intel Corporation Lynx Point-LP HD Audio Controller [8086:9c20] (rev 04)
00:1c.0 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 3 [8086:9c14] (rev e4)
00:1c.3 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 4 [8086:9c16] (rev e4)
00:1c.4 PCI bridge [0604]: Intel Corporation Lynx Point-LP PCI Express Root Port 5 [8086:9c18] (rev e4)
00:1d.0 USB controller [0c03]: Intel Corporation Lynx Point-LP USB EHCI #1 [8086:9c26] (rev 04)
00:1f.0 ISA bridge [0601]: Intel Corporation Lynx Point-LP LPC Controller [8086:9c43] (rev 04)
00:1f.2 SATA controller [0106]: Intel Corporation Lynx Point-LP SATA Controller 1 [AHCI mode] [8086:9c03] (rev 04)
00:1f.3 SMBus [0c05]: Intel Corporation Lynx Point-LP SMBus Controller [8086:9c22] (rev 04)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 10)
02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)
03:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1341] (rev ff)
Bus 001 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 003: ID 0bda:0129 Realtek Semiconductor Corp. 
Bus 002 Device 004: ID 5986:055e Acer, Inc 
Bus 002 Device 005: ID 0cf3:3004 Atheros Communications, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

```
Thanks for the help

---

### Post by jeremy31 on 2015-05-24
What does ```
dmesg | grep -i 380d
``` show

---

### Post by Elie_Daou on 2015-05-24
Absolutely nothing, it simply takes me a new command line 
```
elie@Z50-70:~$ dmesg | grep -i 380delie@Z50-70:~$ 

```
Is this supposed to happen ? The notification is still showing.

---

### Post by deadflowr on 2015-05-24
I think this is because the 3d controller is an nvidia optimus card.
You might need to install the nvidia drivers for it.
See
[https://wiki.ubuntu.com/X/Config/HybridGraphics](https://wiki.ubuntu.com/X/Config/HybridGraphics)

You might also post the output for
```
lspci -nnk | grep 3D -A2
```
which should show if you are running the open-source or closed-source driver for the card.
If the kernel in use says nouveau then follow the wiki.
If it says nvidia, then perhaps something else is afoot...

---

### Post by jeremy31 on 2015-05-24
I was hoping the unsupported hardware would show up but it might be xorg that is the issue, we can check that log
```
cat /var/log/Xorg.0.log | grep -i 380d
```

---

### Post by Elie_Daou on 2015-05-24
@deadflowr
```
03:00.0 3D controller [0302]: NVIDIA Corporation Device [10de:1341] (rev ff)
``` 
is what I get after using ```
lspci -nnk | grep 3D -A2
```
So i guess something else is afoot ?

@jeremy31
```
[     6.154] (--) PCI:*(0:0:2:0) 8086:0a16:17aa:380d rev 11, Mem @ 0xc3000000/4194304, 0xd0000000/268435456, I/O @ 0x00005000/64
```
is the result of ```
 [COLOR=#000000][FONT=Ubuntu Mono]cat /var/log/Xorg.0.log | grep -i 380d 
```[/FONT][/COLOR]

---

### Post by grahammechanical on 2015-05-24
I have a cold and it is a wonder that I can think at all but I am coming at this from a different direction. I see this:

> 02:00.0 Network controller [0280]: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter [168c:0036] (rev 01)

Do Atheros wireless adapters still need to have its driver installed through Additional Drivers? Not knowing the answer, I ask: How are you connecting to the internet? Is it by ethernet cable or by WiFi?

If it is by WiFi then I am wrong. But if the connection is through ethernet cable then try disabling WiFi. And if that gets rid of the notification, then we know that it is the WiFI adapter that needs a driver.

Regards.

---

### Post by Elie_Daou on 2015-05-24
I am connected through an ethernet cable, regardless I disabled WiFi and the notification persisted. Thanks for trying though ^^

---

### Post by jeremy31 on 2015-05-24
I think deadflowr is likely on the right track with the video card being the issue as the Xorg log message points to the Intel part of the hybrid video you have

The wifi is not the issue as that wifi card is supported by the kernel with module ath9k

---

### Post by Elie_Daou on 2015-05-24
> **jeremy31 said:**
> I think deadflowr is likely on the right track with the video card being the issue as the Xorg log message points to the Intel part of the hybrid video you have

The wifi is not the issue as that wifi card is supported by the kernel with module ath9k
Well then what should I do ? install the drivers ? and sorry for my obliviousness but how did you deduce that from that heap of numbers that I got ? :o

---

### Post by jeremy31 on 2015-05-24
The heap of numbers from Xorg ```
PCI:*(0:0:2:0) 8086:0a16:17aa:380d rev 11, Mem @ 0xc3000000/4194304, 0xd0000000/268435456, I/O @ 0x00005000/64
```
And your lspci info ```
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
```
Show similar info, the 8086:0a16 from Xorg matches the ID from the graphics controller and I would bet ```
lspci -nnk | grep -iA2 haswell
``` would show a susbsytem ID with 17aa:380d

---

### Post by Elie_Daou on 2015-05-24
```
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)	Subsystem: Lenovo Device [17aa:3978]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
	Subsystem: Lenovo Device [17aa:380d]
	Kernel driver in use: i915

```
you sir are on point. So it indeed is he graphics card ? Noob question again but how do you suggest I find/download the needed drivers ?
Really appreciate your help :)

---

### Post by jeremy31 on 2015-05-24
> **Elie_Daou said:**
> ```
00:00.0 Host bridge [0600]: Intel Corporation Haswell-ULT DRAM Controller [8086:0a04] (rev 0b)    Subsystem: Lenovo Device [17aa:3978]
00:02.0 VGA compatible controller [0300]: Intel Corporation Haswell-ULT Integrated Graphics Controller [8086:0a16] (rev 0b)
    Subsystem: Lenovo Device [17aa:380d]
    Kernel driver in use: i915

```
you sir are on point. So it indeed is he graphics card ? Noob question again but how do you suggest I find/download the needed drivers ?
Really appreciate your help :)

I am not familiar with hybrid graphics but the key to the issue seems to be in the Xorg log, so I would recommend ```
gedit /var/log/Xorg.0.log
``` then CTRL + a, CTRL + c to select the entire file and copy it, then paste it at paste.ubuntu.com and post the URL

---

### Post by Elie_Daou on 2015-05-24
[http://paste.ubuntu.com/11337143/](http://paste.ubuntu.com/11337143/)
There it is, might there be some online sources that might help ?

---

### Post by jeremy31 on 2015-05-24
Does it boot without ```
[COLOR=#000000]pcie_aspm=force radeon.modeset=0
``` in /etc/default/grub?[/COLOR]

---

### Post by Elie_Daou on 2015-05-24
How exactly can I find out if it does/doesn't ? Sorry for the repeated silly questions have only been using Ubuntu for 3 days >.<

---

### Post by deadflowr on 2015-05-24
You're pastebin output shows you need to do some upgrading.
the 3.11 kernel series is out of date and unsupported.
Same goes for the Xserver in use.

From the output I can tell it was installed from Ubuntu 12.04.4.
Ubuntu long-term-support releases such as 12.04 have release points that include upgraded hardware support stacks.
**It's extremely confusing**, but to try to make sense it works like this:
Ubuntu releases a new release every 6 months, on the dot.
Every 2 years, or every 4th release, Ubuntu releases an LTS (long-term-support) version.
Because so many users want to be able to run the long term-support releases, Ubuntu releases an upgraded version every 6/9 months.
The upgraded LTS version, called a point release, contains the newer hardware stack that is used in the latest Ubuntu 6 months release.
(Told you it was confusing)

And now, to make it even more complicated, the point releases for the releases in between one lts to another are only supported until a point release comes for the new lts.

I already know none of this makes any sense.
So read this to hopefully get a better sense of what I mean
[https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

And this on 12.04 hardware stack end of life
[https://wiki.ubuntu.com/1204_HWE_EOL](https://wiki.ubuntu.com/1204_HWE_EOL)

Hope art least that the wiki pages help make sense to you...

---

### Post by Elie_Daou on 2015-05-25
I sort of kind of understand it, or at least I think I do. From what I got I need to upgrade my system from 12.04.4 to .5 or 14.04 LTS but sadly the wiki does not really help with the procedure and the online tutorials do not seem to work for me( The terminal is saying there is no new release regardless if I use -d or not). Any ideas ?

---

### Post by mörgæs on 2015-05-25
Before changing anything it would be interesting to know how it works in a 15.04 live boot.

---

### Post by Elie_Daou on 2015-05-25
Actually I am very curious about how all of this works, I mean I've been a windows user for over a decade and this is my first dip into the UNIX universe. However the online sources are not much help as most are either outdated or it is my system that is. Therefore I just want to get this thing running so I can further explore this truly interesting OS. 


UPDATE: I got the update running, turns out my [COLOR=#111111][FONT=Consolas]/etc/update-manager/release-upgrades  was set to "Prompt=never" and I just changed it to "Prompt=lts" and it worked. So if I have not screwed up big time it should update to 14.04 LTS. The update is still downloading though and is not done, will post when it finally is.
[/FONT][/COLOR]

---

### Post by deadflowr on 2015-05-25
> **Elie_Daou said:**
> I sort of kind of understand it, or at least I think I do. From what I got I need to upgrade my system from 12.04.4 to .5 or 14.04 LTS but sadly the wiki does not really help with the procedure and the online tutorials do not seem to work for me( The terminal is saying there is no new release regardless if I use -d or not). Any ideas ?

Do Not worry about whether you understand it.
There are users who have been using Ubuntu for a long time who don't understand it.
(The hardware stack enablement concept is rather new, and still very rough around the edges)

You've figured out how to change the upgrade status.
But there is an optional, and optimal, way to do so, for future reference:
to do so with 12.04 all you need to do is open the update manager and go down and click on the button marked Settings.
In the settings, go to the updates tab and you'll see a line for notify of new ubuntu releases(or something to that affect)
Basically you will have 3 options: lts, any, or never.
Once you've made the select of which upgrade you want close the window and in the main update manager window click on check.
This will refresh the package database.
Newer versions of Ubuntu such as 14.04, have a separate program called Software and Updates, but it is the same thing, just a different name.

Hope that helps.

---

### Post by Elie_Daou on 2015-05-25
Alright, so I just updated to 14.04 LTS and things appear to be working smoothly. However the notification is still present and the Touchpad has stopped working. These are both driver problems but I cannot figure out what drivers to install to fix them or where to download them from. Any help would be really appreciated.

---

### Post by deadflowr on 2015-05-25
Well, perhaps see if you can install additional drivers.

If you go to the program I mentioned earlier, Software and Updates, there is a tab marked additional drivers.
Click that and it will begin a scan of your system to see if any, what we would call, restricted drivers can be installed.
Restricted drivers are those which are not open source.
In some cases they can be better supported than the open source drivers which are used by default.

See if that gives you any options or helps...

---

### Post by mörgæs on 2015-05-26
Normally Additional Drivers only adds drivers for graphics and wirefree cards. It would surprise me if it changed anything for the touchpad.

Open source drivers are part of the kernel, hence the suggestion in post #22.

---

### Post by Elie_Daou on 2015-05-26
I tried Software and Updates it told me "No additional drivers available". It also says that "No proprietary drivers are in use" not sure if it helps but just saying if it might mean anything. Is there no way to manually install additional drivers ? 
@morgaes but shouldn't the 14.04 kernel also contain the drivers ? (not sure if I'm sounding completely stupid or what I just said makes actual sense :|) Anyways if I did live boot it into 15.04 what should be the expected result ? and what is the optimal way to do so.

[COLOR=#000000][/COLOR]Thanks for all the help I've been getting, you guys are awesome ^^

---

### Post by Elie_Daou on 2015-05-31
Not exactly sure how this works here, but Bump ?

small update: I upgraded to Ubuntu 15.04 and the initial problems are still there: Unsupported Hardware notification still shows and my touchpad is still not functional at all (even though my mouse does work) 
Any help would be greatly appreciated.

---


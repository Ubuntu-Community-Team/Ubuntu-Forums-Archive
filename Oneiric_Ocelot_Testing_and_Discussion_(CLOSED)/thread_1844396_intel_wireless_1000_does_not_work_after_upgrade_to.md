---
title: "intel wireless 1000 does not work after upgrade to 11.10"
date: 2011-09-15
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by erikschmitz on 2011-09-15
After installing Ubuntu 11.10 (AMD64), my intel wireless 1000 bgn will not connect to my WAP. It can see the networks in the vicinity, but it continually asks me for the password.  

It worked fine in 11.04. 

This is on an HP Pavillion DV6t-6000 laptop.

Is this a known issue, or should I file a bug? Seems like it would be a linux kernel problem... and the problem is present on both 3.0.0-09 and 3.0.0-11

---

### Post by garvinrick4 on 2011-09-15
You are using the "iwlagn" driver and intel 1000 card.
Check in```

gksudo gedit /etc/modprobe.d/iwlagn.conf
```should have nothing in there. If has a line of code like.
                                 ```
options iwlagn 11n_disable50=1 11n_disable=1
```[COLOR=#000000][FONT=Times New Roman][SIZE=3]delete the line and save and reboot. 
[/SIZE][/FONT][/COLOR]


[COLOR=#000000][FONT=Times New Roman][SIZE=3]Let me know. Driver should work in 11.10 out of box with 3.0 kernel and up.[/SIZE][/FONT][/COLOR]

##that is one of my cards and drivers we will get it fixed I am using now on 11.10 with same kernel.
If that fix does not work show me output of. Let me know.
```
uname -a
``````
lspci -k
```[COLOR=#000000][FONT=Times New Roman][SIZE=3]
[/SIZE][/FONT][/COLOR]

---

### Post by garvinrick4 on 2011-09-15
@erickshmitz
 It has been an hour since last post so I am going to consider you are running. It is 2:22 AM here
and I am going to call it an evening. Enjoy your Ubuntu.  Will check thread tomorrow in case
of any problems and still not running properly.

---

### Post by erikschmitz on 2011-09-16
Hi Garvinrick4, 

I'm sorry I was not able to reply last night. I have tried your suggestions, however I do not have a file at /etc/modprobe.d/iwlagn.conf

I created a blank file and rebooted, however that did not help.

You are correct that I am using the iwlagn driver, lspci confirms it. Below is my uname -a and lspci -k output. Thank you for taking the time to assist me, I really appreciate it.

```

Linux hpdv6 3.0.0-11-generic #18-Ubuntu SMP Tue Sep 13 23:38:01 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux


```

```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: agpgart-intel
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: i915
	Kernel modules: i915
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: mei
	Kernel modules: mei
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: ehci_hcd
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: HDA Intel
	Kernel modules: snd-hda-intel
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b4)
	Kernel driver in use: pcieport
	Kernel modules: shpchp
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: ehci_hcd
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel modules: iTCO_wdt
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: ahci
	Kernel modules: ahci
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel modules: i2c-i801
01:00.0 VGA compatible controller: ATI Technologies Inc Whistler XT [AMD Radeon HD 6700M Series] (rev ff)
	Kernel driver in use: radeon
	Kernel modules: radeon
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: r8169
	Kernel modules: r8169
0d:00.0 Network controller: Intel Corporation Centrino Wireless-N 1000
	Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN
	Kernel driver in use: iwlagn
	Kernel modules: iwlagn
13:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: rts_pstor
	Kernel modules: rts_pstor
19:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
	Subsystem: Hewlett-Packard Company Device 1657
	Kernel driver in use: xhci_hcd
	Kernel modules: xhci-hcd
```

---

### Post by garvinrick4 on 2011-09-16
Hi erikshmitz,
 First lets make sure you are set right in the network applet in upper right,
right click to network settings
ON
security is WPA2 (or what your router is set to)
Network Name (your ssid)
If not :
configure:
add a new one with your ssid and  wpa2 and password  and check  connect at startup.
If all is set correctly and jives with router,  driver and card should work with kernel driver:
Reboot and use wifi and see if connects.

If not run this for me.
```
lsmod | grep iwl
```
```
dmesg | grep iwl
```
```
locate iwlagn
```

---

### Post by erikschmitz on 2011-09-16
Ok, so I double checked all of the settings, deleted the existing config from network manager, and manually created a new one using my SSID and WPA2 password. Still no-go. Here are the outputs you requested.

lsmod
```

iwlagn                314213  0 
mac80211              310872  1 iwlagn
cfg80211              199587  2 iwlagn,mac80211

```

dmesg
```

[    7.465162] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, in-tree:
[    7.465165] iwlagn: Copyright(c) 2003-2011 Intel Corporation
[    7.465221] iwlagn 0000:0d:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    7.465230] iwlagn 0000:0d:00.0: setting latency timer to 64
[    7.465264] iwlagn 0000:0d:00.0: Detected Intel(R) Centrino(R) Wireless-N 1000 BGN, REV=0x6C
[    7.485457] iwlagn 0000:0d:00.0: device EEPROM VER=0x15d, CALIB=0x6
[    7.485460] iwlagn 0000:0d:00.0: Device SKU: 0X9
[    7.485462] iwlagn 0000:0d:00.0: Valid Tx ant: 0X1, Valid Rx ant: 0X3
[    7.485975] iwlagn 0000:0d:00.0: Tunable channels: 13 802.11bg, 0 802.11a channels
[    7.486070] iwlagn 0000:0d:00.0: irq 53 for MSI/MSI-X
[    7.520110] iwlagn 0000:0d:00.0: loaded firmware version 39.31.5.1 build 35138
[    7.524807] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[   13.061690] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   21.538988] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   29.996336] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   38.423653] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   52.459188] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   60.896497] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   69.463790] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   77.841090] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   91.716672] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  112.160185] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  120.547514] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  128.984807] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  137.392145] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  145.869438] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  154.306773] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  162.724064] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  171.141409] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[  185.206951] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

```

locate
```

/lib/modules/3.0.0-9-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-3.0.0-9-generic/include/config/iwlagn.h

```

---

### Post by garvinrick4 on 2011-09-16
```
rfkill list
```Does it say softblocked? Post results please.

---

### Post by erikschmitz on 2011-09-16
looks like wifi is all enabled

```

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no

```

---

### Post by garvinrick4 on 2011-09-16
```
sudo rfkill unblock all
```## This seems to be a problem that quite a few users have come up with on upgrade to 11.10 
 dmesg:
iwlagn fail to flush all tx fifo queues

---

### Post by garvinrick4 on 2011-09-16
I am going to ask chili555 for his support in this problem seems to be new and
in upgrade from 11.04 to 11.10.

I have two installs of 11.10 and a HP with Intel 1000 card and iwlagn driver and
they work but with fresh installs and no bluetooth.

Until chili555 is available going to google around a bit with the error message and see if
any have found solution yet.

chili555 is pretty darn good with anything Network, I spent a three or four months 
following his posts when trying to gain knowledge in Network cards and their drivers.
He also wrote me a short synopsis on his thinking on figuring problems all network, nice guy.

Will return: Have left chili555 a message.

Keep this thread updated if you anything is found on the problem on your end.
Seems to be something that is needed by many on upgrade to 11.10 with iwlagn.
September 4th 2011 (same exact errors and same kernel on upgrade)
[http://askubuntu.com/questions/59976/iwlagn-wireless-failed-after-upgrade-to-ubuntu-11-10-beta](http://askubuntu.com/questions/59976/iwlagn-wireless-failed-after-upgrade-to-ubuntu-11-10-beta)

---

### Post by erikschmitz on 2011-09-16
Thank you again for your help garvinrick. I'll keep you posted as I tinker with it. I'll do a fresh install from beta1 cd tomorrow and let you know how it goes.

---

### Post by garvinrick4 on 2011-09-16
> **erikschmitz said:**
> Thank you again for your help garvinrick. I'll keep you posted as I tinker with it. I'll do a fresh install from beta1 cd tomorrow and let you know how it goes.
Why don't we try a different kernel and see if iwlagn works with:
You have 64 bit so take the'
all.deb
64 bit headers
64 bit image
Download those 3 and install in that order, they are in .deb so if you click on will install
thru UBuntu software center. Install in order given, all.deb, headers, image.
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.0.4-oneiric/]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.0.4-oneiric/")
If any trouble can install at command line;
Drop all three on Desktop:
cd Desktop
ls
sudo dpkg -i (copy and paste all.deb)
sudo dpkg -i (copy and paste headers)
sudo dpkg -i (copy and paste image)
Now reboot with wired cable unplugged and lets see if it was a kernel driver thing going on. Cannot hurt anything have all your new 11.10 kernel still installed. Might just do it. Seems to be an upgrade thing so fresh install will most likely do it. Lets see if is the kernel only takes 10 minutes or so.

---

### Post by garvinrick4 on 2011-09-16
rick@rick:~$ uname -a
Linux rick 3.0.4-030004-generic #201108301138 SMP Tue Aug 30 11:42:30 UTC 2011 x86_64 x86_64 x86_64 GNU/Linux
rick@rick:~$ 

Have installed on a 11.10 install I have and using now with iwlagn:
rick@rick:~$ locate iwlagn
/lib/modules/3.0.0-11-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.0.0-9-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/lib/modules/3.0.4-030004-generic/kernel/drivers/net/wireless/iwlwifi/iwlagn.ko
/usr/src/linux-headers-3.0.0-11-generic/include/config/iwlagn.h
/usr/src/linux-headers-3.0.0-9-generic/include/config/iwlagn.h
/usr/src/linux-headers-3.0.4-030004-generic/include/config/iwlagn.h
rick@rick:~$

---

### Post by erikschmitz on 2011-09-16
I got kernel 3.0.4 installed and it went just fine. I verified that the 3.0.4 iwlagn.ko modules were present, and still it is not working.

I tried renaming /lib/firmware/iwlwifi-1000-5.ucode to force the driver to load iwlwifi-1000-3.ucode and rebooted, but that didnt fix anything. I reverted that change back out.

When I boot into the 11.10 beta in "live" cd mode, the wifi does not work there either, so I don't have a lot of hope for a fresh install working.

---

### Post by RikoW on 2011-09-16
Are you guys sure, you dealing with a kernel problem? I also can't connect using NM, but NM doesn't even let me edit or add any networks nore lists the old ones. 

I suspect a NM problem ...
[http://ubuntuforums.org/showthread.php?t=1845219]("http://ubuntuforums.org/showthread.php?t=1845219")

Cheers,

                Riko

---

### Post by erikschmitz on 2011-09-16
I'm not positive... the dmesg logs with the flush error make me think its a driver or kernel problem. My network manager scans all of the local ssids and I can see almost 20, I just can't connect. 

It pops up and asks me for my password, I enter the password, and then about 30 seconds later it pops up and asks me for my password again.

---

### Post by RikoW on 2011-09-16
I had the same symptoms. Wifi card is Intel5100

I'll post the downgrade instruction on the other thread.

- Riko

---

### Post by garvinrick4 on 2011-09-16
It is a intel "iwlagn" driver thing in 11.10, we know it works in 11.04. Google searched for
quite a long time and came up with indentical problems with others with intel cards using
iwlagn driver. The baffling thing is I have the same intel centrino 1000 with iwlagn in 11.10 and I cannot duplicate the problem. Got to be an answer but I guess it is for a user that
has better set of Networking skills than I. Am going to keep looking. 
@erikschmitz
 Keep the 11.10 Live CD handy so we can check on it later if you revert to 11.04 packages. Good luck to you and enjoy your Ubuntu, sorry I could not make this a Solved thread.

##dmesg error is for anyone reading with knowledge of this error in 11.10 with intel's iwlagn driver
 185.206951] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

---

### Post by garvinrick4 on 2011-09-16
> I had the same symptoms. Wifi card is Intel5100

I'll post the downgrade instruction on the other thread.@RikoW
I see you downgraded your network manager to the version installed in Natty
and it cleard up your Networking problem with Intel and iwlagn driver, Thank you
for giving us that advice it clears up a lot. Did you find a bug report by chance.

---

### Post by garvinrick4 on 2011-09-16
Below is latest network-manager build from launchpad. Upgrade beta1 or
imagine it is also in dailys if anyone wants to test with iwlagn problem to see
if network manager solves issue. I cannot duplicate so need one with errors.
Use .deb package from your 32 or 64 bit download and click on will install in Ubuntu Software manager.

_[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)_
[https://launchpad.net/ubuntu/+source/network-manager/0.9.0-0ubuntu3](https://launchpad.net/ubuntu/+source/network-manager/0.9.0-0ubuntu3)

Natty builds network manager:
[https://launchpad.net/ubuntu/natty/+source/network-manager/+builds](https://launchpad.net/ubuntu/natty/+source/network-manager/+builds)

---

### Post by chili555 on 2011-09-17
Gents and ladies--

I am just now en route back home from a cruise and a trip to Cape Cod. I have been away from my computer for about three weeks by order of my mental health provider, Mrs. Chili!!

I have not yet successfully tried 11.10, so I am feeling around in the dark a bit so far. Has the backports compat-wireless package made it to Oneric yet? In Synaptic, can you see and install *linux-backports-modules-cw-3.xx-generic*? Would one of you try it while I fly back home this morning? After doing so, reboot and check dmesg for this awful stuff:> [   13.061690] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   21.538988] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   29.996336] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   38.423653] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

---

### Post by garvinrick4 on 2011-09-17
>  Has the backports compat-wireless package made it to Oneric yet? No they haven't,  only thing I have found is compat-wireless 3.1 rc1 with July patches for iwlagn.
Was a patch for the "iwlagn 0000:0d:00.0: fail to flush all tx fifo queues" I saw in dmesg at Intel site
for 2.6.39 to 3.1 rc1.1 I think it was, I few months  back anyway.
I do have that driver in two installs 11.10 cannot reproduce, in this thread posted revert to
last Natty version network-manager 0.8.4 have success in Oneiric kernels. 0.9.0-0ubuntu3
is latest network-manager oneiric. The latest bugs at Intel I have found with patches in July 27th
compat-wireless with no backports or compat-wireless patches up to date I have used up
all resources. I am going to call this thread a day unless a new user with problem chimes in and wants
to try compat-wireless in 3.1 kernel. 
Network manager problem or Intel iwlagn problem? Thanks chili555 hope you enjoyed your vacation 
will most likely be nice to get to the comforts of home after 3 weeks.

---

### Post by erikschmitz on 2011-09-17
I tried downgrading to the natty network-manager, and i still get the flush errors on my intel 1000 bgn.

Currently, I'm at 
  11.10 beta 1
  3.0.4 kernel
  Natty network-manager

I'll give anything you guys suggest a shot. I see a few posts back garvinrick4 suggested trying the newest network-manager from launchpad, I'll give that a shot, and poke around for the compat libs that chili suggested.

thanks guys.

---

### Post by RikoW on 2011-09-18
Maybe it is actually a driver problem then for you which showed up with similar symptoms as my NM problem. At least you know now, that it's not NM :)

I did not see see those flush messages you have reported.

Good luck,

          Riko

---

### Post by garvinrick4 on 2011-09-18
Yes, I do believe after seeing messages at Intel by the one that maintains the iwlagn
driver for Intel that it is a driver thing going on, but only for some, have not found 
common denominator  though, driving me nuts. Not only for this thread but it is my driver
and cannot duplicate. Last time this happened was a fix by dropping N speeds in iwlagn and
Intel has never fixed. Was cured for me when 3.0 came out. So all my installs of 10.10 and 11.04 are 3.0 and up, 11.10 came out with 3.0 installed. 
Now a diifferent dmesg error of course and not for all with iwlagn just for some. When enough upgrade to 11.10 a common
denominator will pop up or hopefully Intel will repair kernel driver before then. On 
10-13-11 will be a flood in Forums of "wifi cannot connect" in Forums and no one will be able to help, not good.
dmesg error:
[   13.061690] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   21.538988] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   29.996336] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   38.423653] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues

# Downloading dailys and testing and for me the dailys are rather nice and with no errors with iwlagn driver or network manager.

---

### Post by chili555 on 2011-09-18
> only thing I have found is compat-wireless 3.1 rc1 with July patches for iwlagn.Did you compile it? What was the result?

---

### Post by garvinrick4 on 2011-09-19
@chili555
> Did you compile it? What was the result?
I have the iwlagn driver in this laptop I am on. HP-G71 340-US
and cannot reproduce this error. If you do find a fix for this "iwlagn" error
dmesg error:
[   13.061690] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   21.538988] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   29.996336] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
[   38.423653] iwlagn 0000:0d:00.0: fail to flush all tx fifo queues
Please post to this thread if you would. Sooner or later when users start installing
11.10 in the 10th month of this year we will surely have a lot of posts looking 
for assistance with Intel cards and this driver. Thanks chili555, Rick.

---


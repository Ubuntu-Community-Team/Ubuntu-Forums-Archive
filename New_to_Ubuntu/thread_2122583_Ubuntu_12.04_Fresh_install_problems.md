---
title: "Ubuntu 12.04 Fresh install problems"
date: 2013-03-05
forum: New to Ubuntu
---

### Post by Iampanda on 2013-03-05
I really am a complete noob when it comes to Linux operating systems, and I've looked everywhere but cannot fix this.
I have a laptop (Dell Latitude D620) which used to have Windows 7 on it, but it went to crap and a friend told me to try Ubuntu. She had a cd with 12.04 on it and it installed perfectly and the first time it booted to the desktop with no problems. I then did all the updates and the screen went black. I rebooted the laptop and it went right to the update window and asked if I wanted to complete the updates, so I clicked yes. It then completed everything and rebooted itself. From there is where the problems began.
It would show the splash screen with the Ubuntu logo, but after that the screen would go black. No login screen or anything. I could not even get to the terminal. I could reboot into 'Safe Mode' and get to a terminal that way and I searched many forums with similar-sounding problems and nothing helped. After what seemed like forever trying different solutions - I guess Ubuntu has problems with Nvidia graphics - I gave up and just re-installed it from the disk. I figured that I would just not update it and try to find solutions in teh mean time. The install worked and went to the desktop again.
Well I just tried to turn the laptop on again and it goes to the login screen, but after I log on, it just goes to the default backgroung with the mouse pointer, no menu or icons. I can get to the terminal and I tried many more 'fixes', but I cannot update anything. Running sudo apt-get update does not work, it just says Failed to Fetch. Another solution was to run sudo apt-get install aptitude gnome-panel gnome-shell (I guess that fixed it for many people), but it would fail the install. I have the internet cable plugged right into the laptop and it works on the other computer, just not this one.
Sorry for the huge post, but the more details the better. Any help would be great.

---

### Post by ajgreeny on 2013-03-05
It could be a graphic driver problem and need booting with the **nomodeset** option, so follow the instructions below to see if this works.


[LIST=1]
[*]When you next power-on, hold shift and you should see the grub menu. 
[*]With the first line highlighted in the menu hit "E" for edit. 
[*]Use cursor keys to go to the line that looks something like ```
linux /boot/vmlinuz-3.2.0-37-generic root=UUID=9555e579-7173-40ff-b0ef-5c254e1e1bb4 ro **quiet splash** $vt_handoff
``` and add **nomodeset** to the line after **quiet splash**. 
[*]Use Ctrl+X to boot and with luck you may get to a normal desktop. 
[*]If this works use ```
gksudo gedit /etc/default/grub
``` to open that file with root permissions and again add nomodeset to the line GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" so it reads GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset" 
[*]Run command ```
sudo update-grub
``` and reboot, hopefully this time to a normal desktop. 
[/LIST]

---

### Post by Iampanda on 2013-03-07
It did not work. I found the first line with quiet splash and made it quiet splash nomodesest and when I booted it, it said I was in low-graphics mode, which made sense, but there was no mouse pointer. It took me quite a while  to click the OK buttons haha. The second popup asked me why I was in this mode (one-time only, troubleshoot, reboot, etc.) and I left it on the pre-selected one-time and managed to find the OK button. The third popup said please wait while the display resets, had a unavailable cancel button, a full green progress bar, and an OK button. After 10 minutes, I clicked the Ok button (I didn't know if it was doing something). It then went straight to a black screen with vertical blue lines and in the top left corner looked like the _ for typing into a terminal, but it wouldn't type. I could not even get to the terminal from this screen. I don't know if somehow I did something wrong in that first step or if this laptop cannot run Ubuntu...

Thank you very much for your help and also for your fast reply. :)

---

### Post by Iampanda on 2013-03-10
Anyone have any input here?

---

### Post by ManamiVixen on 2013-03-10
What video card does the laptop have? If you don't know. type "     lspci -v -s `lspci | awk '/VGA/{print $1}'`" into a terminal and type the output here. If you need a terminal if the desktop wont show, on the keyboard, press ctrl+alt+F1 and type it there.

---

### Post by Iampanda on 2013-03-11
First of all, my mistake. It is Ubuntu 12.10, not 12.04. The disc said 12.04 but I just realized it says 12.10 on the login screen. Not sure if this changes anything.
It said lspci -s: invalid slot number. It's integrated graphics. I typed instead: lspci | grep "VGA" and came up with this:
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
VGA was in red text

---

### Post by Bashing-om on 2013-03-12
Iampanda; Hi !
Continue to look at this as a graphics driver problem. Terminal codes:
```
sudo lshw -C display
lspci -nnk | grep -iA3 vga
``` to see what driver (if any) is loaded, and what drivers the kernel is aware of.[INDENT=4]just try'n to help

[/INDENT]

---

### Post by steeldriver on 2013-03-12
I'm not sure that the Intel chips recognize the 'nomodeset' boot option - I have one in an old Thinkpad and iirc the Intel equivalent is 'i915.modeset=0'

I seem to remember that the newer i915 driver does not actually support a non-KMS mode, so the actual effect of the switch is to dump you to the default VESA driver, nevertheless it may be worth a try

Having said that, the last time I installed anything on that Thinkpad I think it worked out of the box so I'd kind of assumed the newer kernel / driver combos were OK

---

### Post by Simica on 2013-03-12
Did you try simply soulution - to run proprietery drivers?

---

### Post by Iampanda on 2013-03-12
Bashing-om:
            sudo lshw -c display
*-display:0
  description: VGA compatible controller
  product: Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller
  vendor: Intel Corporation
  physical id: 2
  bus info: pci@0000:00:02.0
  version: 03
  width: 32 bits
  clock: 33MHz
  capabilities: msi pm vga_controller bus_master cap_list rom
  configuration: driver=i915 latency=0
  resources: irq:16 memory:eff00000-eff7ffff ioport:eff8(size=8) memory:d0000000-dfffffff memory:efec0000-efefffff
*-display:1 UNCLAIMED
  description: Display controller
  product: Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller
  vendor: Intel Corporation
  physical id: 2.1
  bus info: pci@0000:00:02.1
  version: 03
  width: 32 bits
  clock: 33MHz
  capabilities: pm bus_master cap_list
  configuration: latency=0
  resources: memory:eff80000-efffffff

                  lspci -nnk | grep -iA3 vga
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)
  subsystem: Dell Device [1028:01c2]
  Kernel driver in use: i915
  Kernel modules: intelfb, i915

---

### Post by Iampanda on 2013-03-12
steeldriver:
  How would I go about dumping to the default VESA driver?
Simica:
  I may sound really stupid for this, but it won't update anything at the terminal so how would I get the Intel drivers?

---

### Post by Iampanda on 2013-03-12
I thank you all for your input and assistance in hopefully resolving this problem.

---

### Post by steeldriver on 2013-03-12
OK sorry I just read your original post again and it doesn't sound like your issue is anything to do with graphics mode setting / drivers - just that you can't update or repair the desktop because of lack of network connectivity?

Is there an option to go into safe mode with networking?

---

### Post by Bashing-om on 2013-03-12
Iampanda; 
Chipset and driver are identified and the only driver with full support  is loaded.
I agree with steeldriver, need to get ya up on the 'net and get ya updated.
Then see bout getting the desktop back.
This is a fresh (re)install and not updated, correct ?[INDENT=2]back'n up and regroup'n
[/INDENT]

---

### Post by Iampanda on 2013-03-13
Correct. However, when I try to update (sudo apt-get update) it fails to fetch the updates. It finds a bunch and says that it will need this much space, do I want to continue, I say yes and it goes through and fails to fetch them all. Could that be a network problem? It didn't have a problem connecting last time I had it installed when I updated it the first time and everything went wrong.

---

### Post by steeldriver on 2013-03-13
Well other than a network problem it could be that your selected repositories are unavailable

Have you done basic network tests e.g. 

1. is the interface up and does it have sensible looking IPv4 parameters e.g.

```
ifconfig -a
```

2. can you ping your gateway IP address?

```
ping -c4 192.168.1.1
```

[adjust the 192.168.1.1 numbers based on the subnet parameters reported in (1)]

3. can you ping an external host by IP? e.g. a google server such as

```
 ping -c4 74.125.226.41
```

4. can you ping an external host by name (i.e. is DNS name resolution working)?

```
ping -c4 google.com
```

5. is there a sensible default route / metric?

```
ip route list
```

---

### Post by Iampanda on 2013-03-14
Ok. When I plug in the internet cable now, it will pop up Wired Connection 1 Disconnected. Don't know why it's not working now. 
ifcongif -a came up with
eth0    Link encap:Ethernet  HWaddr 00:15:c5:50:de:27
inet6 addr: fe80::215:c5ff:fe50:de27/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:233 errors:0 dropped:0 overruns:0 frame:0
TX packets:62 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:16312 (16.3 KB)  TX bytes:15803 (15.8 KB)

lo       Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:32 errors:0 dropped:0 overruns:0 frame:0
TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:2480 (2.4 KB)  TX bytes:2480 (2.4 KB)

ping -c4 127.0.0.1 came up with:
PING 127.0.0.1 (127.0.0.1) 56(84) bytes of data
64 bytes from 127.0.0.1: icmp_req=1 ttl=64 time=0.041 ms
64 bytes from 127.0.0.1: icmp_req=2 ttl=64 time=0.040 ms
64 bytes from 127.0.0.1: icmp_req=3 ttl=64 time=0.044 ms
64 bytes from 127.0.0.1: icmp_req=4 ttl=64 time=0.048 ms
--- 127.0.0.1 ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 2997ms
rtt min/avg/max/mdev = 0.040/0.043/0.048/0.005 ms

ping -c4 74.125.226.41:
connect: Network is unreachable

ping -c4 google.com
ping: unknown host google.com

ip route list came up with nothing

---

### Post by Iampanda on 2013-03-14
I am not quite sure how to fix the connectivity problem now. At the login screen, it has the little network icon and when I click on it, three options are white: Wired Connection 1, disconnect, and VPN Connections. Everything else is grayed out (Wired Network, Enable Networking although it has a white check mark next to it, and Connection Information).

---

### Post by steeldriver on 2013-03-14
Doh! I just typed out a big reply assuming you were still stuck in the recovery console

If 'Wired connection 1' thinks it's connected, but 'ifconfig eth0' shows no valid IPv4 address, then it sounds like there is a problem with your network card / driver or possibly with your DHCP service - can you open a terminal and do

```
sudo lshw -C network
```

and

```
dmesg | grep eth0
```

and report back

---

### Post by Iampanda on 2013-03-14
sudo lshw -C network:
*- network
description: Network Controller
product: BCM4311 802.11a/b/g
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:0c:00.0
version: 01
width: 32 bits
clock: 33MHz
capabilities: pm msi pciexpress bus_master cap_list
configuration: driver=b43-pci-bridge latency=0
resources: irq17 memory:efdfc000-efdfffff
*-network
description: Ethernet Interface
product: NetXtreme BCM5752 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:09:00.0
logical name: eth0
version: 02
serial: 00:15:c5:50:de:27
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.123 duplex=full firmware=5752-v3.19 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:44 memory:efcf0000-efcfffff

dmesg | grep eth0:
[1.228652] tg3 0000:09:00.0: >eth0: Tigon8 [partno(BCM5752KFBG) rev 6002] (PCI Express) MAC address 00:15:c5:50:de:27
[1.228661] tg3 0000:09:00.0: >eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[1.228665] tg3 0000:09:00.0: >eth0:RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[1.228669] tg3 0000:09:00.0: >eth0: dma_rwctrl[76180000] dma_mask [64-bit]
[20.442177] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[22.433643] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[22.434359] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[24.081571] tg3 0000:09:00.0: >eth0: link is up at 100 Mbps, full duplex
[24.081578] tg3 0000:09:00.0: >eth0: Flow control is on for TX and on for RX
[24.081896] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[103.295405] tg3 0000:09:00.0: >eth0: Link is down
[108.203541] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[312.776326] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[314.369004] tg3 0000:09:00.0: >eth0: Link is up at 100 Mbps, full duplex
[314.369015] tg3 0000:09:00.0: >eth0: Flow control is on for TX and on for RX
[314.369376] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[399.347918] tg3 0000:09:00.0: >eth0: Link is down
[404.207044] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[450.717624] tg3 0000:09:00.0: >eth0: Link is up at 100 Mbps, full duplex
[450.717635] tg3 0000:09:00.0: >eth0: Flow control is on for TX and on for RX
[450.718001] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[484.593495] tg3 0000:09:00.0: >eth0: Link is down
[489.204985] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[697.887706] tg3 0000:09:00.0: >eth0: Link is up at 100 Mbps, full duplex
[697.887717] tg3 0000:09:00.0: >eth0: Flow control is on for TX and on for RX
[697.888135] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

Every eth0 is red text.

---

### Post by Iampanda on 2013-03-14
For future use (As I'm almost positive I will need to do much more terminal codes and relay them to you), is there a shortcut to print the screen and auto-save I tot a flash drive so I can easily just attach them here? Or do you prefer to have it typed out?

---

### Post by cruizer04 on 2013-03-14
Lampanda... I too am new to all this and this is where i went and read about installation: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) Maye helps you too.

---

### Post by Iampanda on 2013-03-14
Ubuntu is the only OS on the hard drive, and after typing in [ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD", it said Legacy boot on HDD, which means I am the EFI boot. It is an older laptop and I'm not sure if the hardware didn't support the UEFI (but I could've sworn my Windows was 64-bit) or if the disc I installed it from was 32-bit. However, the page says that if Ubuntu is the only OS the HDD, it shouldn't matter which one it boots in.

---

### Post by Iampanda on 2013-03-14
Maybe this helps a bit, but just to clarify I formatted the disk, installed Ubuntu, everything was perfect, ran updates, everything stopped working, reinstalled Ubuntu (not a repair, fresh install), internet was working but did not do updates, brought laptop home, would not go to desktop but would go to login screen, internet not being detected now, however, it notices that the cable is plugged in (at least I am gathering this from the fact that Wired Connection 1 is selected but says it is disconnected, compared to when I remove the cable it just says Disconnected). The cable itself is good and everything else as I am using the same internet connection on this computer...

---

### Post by cruizer04 on 2013-03-14
I gave you the link for if you have windows 8 and all that uefi boot stuff...here's the download page, maybe download the ISO for 12.10 that is compatable for your system and set it up to run off the image, I have Win 8 as my host so i went with the amd64 iso. because of the UEFI boot, [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) Good luck BTW if yours is 32 bit you need the i386 iso, if it's 64 bit you need the amd64, there is a bittorrent link to download the one you need.

---

### Post by steeldriver on 2013-03-14
I'm kind of leery of trying to advise further - I know the Broadcom *wireless* drivers can be tricky but I would have expected the *wired* device to be OK out of the box - I don't want to waste your time just throwing ideas at you but things you could try

- check that your /etc/network/interfaces file has nothing apart from the lo (loopback) definition that might be interfering with network-manager

- delete the 'Wired connection 1' using the GUI applet (under 'Edit connections...') and reboot - it should create a new completely vanilla wired connection (just in case there's something funny in the old one)

---

### Post by Iampanda on 2013-03-14
Cruizer04- I will probably just try to do a fresh install with 12.10 since this is not working out properly. Thanks.
Steeldriver- Thank you so much for all of your help. I cannot access any GUI or desktop at all. If I remember correctly in the terminal, I would type in cd /etc then manually go down to interfaces (by way of cd /network, then cd /interfaces) and look that way, unless Ubuntu managed that differently from Windows which I wouldn't doubt. I do not know how I would delete the Wired Connection 1. It is grayed out and won't let me click it.

Again, Thank you everyone for your input. I'll be sure to let you know if I manage to fail again. :)

---

### Post by mörgæs on 2013-03-14
If you do a clean install on 12.10, you could use the opportunity to try Xubuntu in stead of Ubuntu. For semi-old hardware it's a better choice.

---

### Post by Iampanda on 2013-03-14
Thanks morgaes. I will try Xubuntu instead of Ubuntu and see how it goes.

---

### Post by Bashing-om on 2013-03-14
guys, I am surprised to see ipv6 and no ipv4 routing in the output. Is ipv4 routing enabled ?
check:
From communications icon in top task bar; right click -> edit connections ->click on the wired connection ->edit;
1st screen insure MTU = Automatic, ipv4 settings; method box = Automatic (DHCP), lower left corner ->available to all users check box is checked;
ipv6 settings; again the method is set to Automatic and avail to all users box is checked.

Transfer of data. Oh man let us by all means do so easier ! Called copy and paste !-
Here should be a simple enough method:
1. open file manager -> new file
2. mouse at start of data to be copied -> hold left mouse button and drag across all data lines to be copied; right click - choose "copy"
3. in the new file window right click - choose paste [paste in the content of the "clipboard"].
4. Rename the "new file" to something more descriptive.
5. copy the file to the usb device.

easy peasy

---

### Post by Iampanda on 2013-03-14
I cannot click on the Edit Connections at all. The computer that needs help is a laptop. I am on a desktop now. Cannot copy and paste to a computer that it was not copied on. And seeing as how the desktop on the laptop is not accessible, I would not be able to copy/paste to a word program or what have you to transfer it to this computer to upload for you. Also, in the terminal, how am I to copy/paste? No mouse pointer and when using the arrow keys if just inputs the previous thing I typed in. I know how to copy thank you but seeing as I cannot simply select whatever from there, it is no use.

---

### Post by Bashing-om on 2013-03-14
Iampanda; Apologize if I sounded condescending - did not understand the situation.
Perhaps the better solution at this time with all these problems is to start fresh with another (re)install.
Whatever you choose to do, we are here to assist.[INDENT=2]
stepp'n on toes ?

[/INDENT]

---

### Post by steeldriver on 2013-03-14
so I'm very confused now - I kind of assumed earlier that you were only able to get to a console (terminal) and prepared a long reply about getting networking running from that - but then in post #23 you talk about the 'Wired Connection 1' - which is obviously a feature of the GUI ?!@*

---

### Post by Iampanda on 2013-03-14
At the login screen it has the network icon on the top taskbar but I cannot get to any programs or anything and the only thing I can click on with the network icon is to disable connection from the drop down menu. I tried right-clicking Wired Connection 1 and Connection Properties (or whatever it was at the very bottom) but it just closes the drop-menu out and does nothing. I can log in but it just goes to a blank desktop with no icons. I can easily get to the terminal. The login screen looks perfect I just can't change anything from the drop-menu with the networking. Sorry for the confusion, I'm sick and my brain hurts. :/

---

### Post by Bashing-om on 2013-03-15
Iampanda;

It is a puzzle'n thing...
As your system was working prior to the updates. Let's try an older kernel and see if you boot up and all is good with that kernel.

At the grub menu select on that menu "other versions" and boot up an older kernel - I have not seen 12.10 so my directions may be a bit hazy- This way we can at least eliminate hardware problems if it boots up.[INDENT=3]
try'n to help

[/INDENT]

---

### Post by steeldriver on 2013-03-15
... I wonder if the OP just needs to reset unity... ?

[http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html](http://www.webupd8.org/2011/04/how-to-reset-unity-launcher-icons-or.html)

---

### Post by Bashing-om on 2013-03-15
@ steeldriver ... had the same thought also, sure worth a shot !

---


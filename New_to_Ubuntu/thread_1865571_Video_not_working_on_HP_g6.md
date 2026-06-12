---
title: "Video not working on HP g6"
date: 2011-10-20
forum: New to Ubuntu
---

### Post by crjackson on 2011-10-20
I purchased a new HP g6 (g6-1c57cx) laptop a 3 days ago for my wife, and she wants Ubuntu installed right away but I'm have problems with that and fear I may be stuck with a windows paper weight.

When I install the LiveCD it starts to load and the screen goes black. I found that tapping the F6 during LiveCD boot, gets me an options screen and I'm able to select 'nomodeset' which then allows it to boot into the Live session.

Everything in the Live session works, but the screen resolution is way off and there is no 3D or compositing support, so I'm afraid to install it like this since it would be of no use this way.

Can someone tell me how I can get graphics support on this machine so I can move forward with the install?  Below is some terminal output that my be of help.

```
ubuntu@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.2 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 3 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM65 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
01:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8188CE 802.11b/g/n WiFi Adapter (rev 01)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5116 PCI Express Card Reader (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
ubuntu@ubuntu:~$ 

```

---

### Post by vandamme on 2011-10-20
Do you have 4 partitions used on your machine? I have a G62 and I thought I'd pass this on FWIW. I multi-boot so when I found all 4 physical partitions used, I had to remove one to make logical partitions. So I made Windoze backup DVD's and trashed the recovery partition.The others are used for bios flashing and something else that sounded important (HP tools). 

I just updated to 11.10 and the Gnome 3 video is crap, can't read most of the menu items and the windows are off-sync. Gnome 2 and Unity are fine. I also boot Bodhi and Mint Debian fine.

---

### Post by crjackson on 2011-10-20
I was aware of the partition issue and have also imaged the drive and made a set of back-up DVD's. My only concern is how to fix the graphics support.

---

### Post by mörgæs on 2011-10-20
This thread is good to consult for graphics problems:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by crjackson on 2011-10-20
> **mörgæs said:**
> This thread is good to consult for graphics problems:
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

I looked it over and didn't see anything that looked like a particular fix for me. Are you saying that I should repost my question in that thread?

---

### Post by crjackson on 2011-10-20
While it's not the solution I was hoping for, it looks like 11.04 works just fine. Video is correctly detected and working well on the LiveCD as does wireless. I guess 11.10 is more buggy and no one knows how to work with it yet.

---

### Post by crjackson on 2011-10-20
The install for 11.04 went well.  Marking this as solved, but it's too bad I couldn't run the newest version.

---


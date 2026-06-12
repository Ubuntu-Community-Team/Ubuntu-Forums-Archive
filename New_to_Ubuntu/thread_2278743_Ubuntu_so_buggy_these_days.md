---
title: "Ubuntu so buggy these days?"
date: 2015-05-18
forum: New to Ubuntu
---

### Post by thinh4 on 2015-05-18
Hi,

I installed ubuntu 14.04 2 weeks ago, and it constantly gave me the screen flicking about 2-3 times a day. The only way is then to press the power button off and on again. This loses my unsaved work... Then I upgraded to ubuntu 15.04 last week. Not much better outcome ... if I leave the machine overnight, next morning it doesn't respond.. even though I close all my applications just for sure. 

This morning when I came in, the screen was flickering, I did a power off/on again. Then it gave me a "Filesystem root has only 0 bytes disk space remaining",... i then tried du unsuccessfully as it can't even do that. I had to shut it down and turned it on again.. then it's ok now...

Are they any fixes available for these please?

Regards
Thinh

---

### Post by Vladlenin5000 on 2015-05-18
Hi and welcome.

First of all, please post details about your hardware. Nobody can even start thinking about troubleshooting without a frame of reference.
IMO, and without further details, the symptoms strongly suggest failing hardware.

---

### Post by thinh4 on 2015-05-18
Hi,

Thank you for your reply. I am not really sure how to get the hardware in ubuntu. So did a google and type in lspci -nnk and here is what I've got
```

 lspci -nnk 
00:00.0 Host bridge [0600]: Intel Corporation 4th Gen Core Processor DRAM Controller [8086:0c00] (rev 06)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: hsw_uncore
00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: i915
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: snd_hda_intel
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: xhci_hcd
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: mei_me
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: ehci-pci
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: snd_hda_intel
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
	Kernel driver in use: pcieport
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
	Kernel driver in use: pcieport
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: ehci-pci
00:1f.0 ISA bridge [0601]: Intel Corporation B85 Express LPC Controller [8086:8c50] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: lpc_ich
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c02] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: ahci
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 04)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: r8169
02:00.1 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816a] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
02:00.2 Serial controller [0700]: Realtek Semiconductor Co., Ltd. Device [10ec:816b] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
02:00.3 IPMI SMIC interface [0c07]: Realtek Semiconductor Co., Ltd. Device [10ec:816c] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:090c]
	Kernel driver in use: ipmi_si

```

---

### Post by SeijiSensei on 2015-05-18
> 00:02.0 VGA compatible controller [0300]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor Integrated Graphics Controller [8086:0412] (rev 06)
I have this same controller on the machine I'm using right now.  I have it connected with HDMI to an HDTV and have never seen any flickering. Is yours connected via HDMI, DVI, or VGA?

---

### Post by wildmanne39 on 2015-05-18
Right now this looks like his main issue:
> Filesystem root has only 0 bytes disk space remaining
Hopefully this will help.
[http://askubuntu.com/questions/622369/root-partition-disk-is-full-how-to-clear-it](http://askubuntu.com/questions/622369/root-partition-disk-is-full-how-to-clear-it)
As SeijiSensei posted earlier this seems to be happening a lot.

---

### Post by Vladlenin5000 on 2015-05-18
A pretty common hardware configuration, not even the graphics stands out. And not much issues with ACER desktops that I'm aware of.
I would start by testing the RAM, just in case.

---

### Post by tgalati4 on 2015-05-18
Post the output of:

```
df -h
```

If /boot is full of old kernels, then you don't have room to apply updates.  Yes, there are bugs, but things are generally fixable.

---

### Post by Vladlenin5000 on 2015-05-18
> **Wild Man said:**
> Right now this looks like his main issue:

Hopefully this will help.
[http://askubuntu.com/questions/622369/root-partition-disk-is-full-how-to-clear-it](http://askubuntu.com/questions/622369/root-partition-disk-is-full-how-to-clear-it)
As SeijiSensei posted earlier this seems to be happening a lot.


It's an issue that deserves to be address on its own but I'm not sure about it being the main issue here.
It happened to me once a few months ago - sudden loss of hundreds of GB (single root + swap)* - but no graphical glitches, flickering or freezing, just the usual problems every system with less than 500MB free has (yes, I let it go that far).
I know what caused it - some shady software for flashing Rockchip devices (tablets, etc.) - but I still don't know why.

---

### Post by thinh4 on 2015-05-18
Thank you all for your replies.

I have 12G of RAM. And I am using DP instead of HDMI or VGA.. I had dual monitors..but I took one off recently because of the flickering issues..  I have 1T disk space.. and only installed less than 50G worth of stuff... this morning when I tried df -h . it showed that 100% usage for "/". As I said, I restarted the box.. and it went away... so main issue now is the flickering screen. Touch wood, it has not happened today yet.

Thanks & regards
Thinh

---

### Post by thinh4 on 2015-05-19
The screen just flickered again and had to power off. This morning when I came in and the machine didn't respond at all..was waiting for the password screen to come up and type a letter at a time... any more advices please?

Thanks
Thinh

---

### Post by SeijiSensei on 2015-05-19
Reboot and run memtest86 from the grub menu.  Let it run overnight at a minimum.

---

### Post by thinh4 on 2015-05-26
Hi, 
Sorry I've been a bit slow in responding.. first of all, I don't know how to get to grub menu in order to run memtest86+ as the Shift key didn't work on ubuntu 15.04... then I found out I had to do this [http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu](http://askubuntu.com/questions/126160/how-can-i-add-the-memtest86-options-back-to-the-grub-menu)

Finally I saw the menu comes up when booting and there are 2 options relating to memtest in the menu. Pressing on either one of them does nothing. It just gave me a purple/pink colour screen with nothing else.

So please show me how to run memtest86.  The flickering screen just happened again 2 hours ago... so really need to solve it somehow...

Thanks & regards
Thinh

---

### Post by jacobpratt909 on 2015-05-27
I honestly don't know what to say about that, possibly a virus on your computer (if you dual boot) or something wrong with your RAM/Hard drive. If you can try running the Ubuntu live cd and look around your local file system. You may need to format and reinstall if it pertains to be a problem.

---

### Post by thinh4 on 2015-05-27
No, I don't have any dual boot. Screen flickering just happened again... and I am thinking of installing mint over ubuntu...

---

### Post by dino99 on 2015-05-27
let us see how it has been installed >  sudo blkid

---

### Post by thinh4 on 2015-05-29
sudo blkid

/dev/sda1: UUID="D829-E688" TYPE="vfat" PARTUUID="d44bf364-32e4-4c0d-9de0-d5bd95dff6c2"
/dev/sda2: UUID="50d536c2-5e07-4a7a-a29e-e979c7dee386" TYPE="ext4" PARTUUID="e1b89146-ba1c-4a61-be42-62ea425172a3"
/dev/sda3: UUID="9784af20-476a-4389-a206-0f575b450aba" TYPE="swap" PARTUUID="9d9c6b0c-1843-4475-9e5f-45abbd60d874"

Thanks

---

### Post by Richard_Romick on 2015-05-30
> **thinh4 said:**
> Thank you all for your replies.

I have 12G of RAM. And I am using DP instead of HDMI or VGA.. I had dual monitors..but I took one off recently because of the flickering issues..  I have 1T disk space.. and only installed less than 50G worth of stuff... this morning when I tried df -h . it showed that 100% usage for "/". As I said, I restarted the box.. and it went away... so main issue now is the flickering screen. Touch wood, it has not happened today yet.

Thanks & regards
Thinh

It's good you have so much ram, but have you run a memory test on it?  When you restart your computer, you should be able to bring up the grub boot menu by holding down shift.  Then you can run the built in memtest.

Edit: apparently I didn't see the entire second page of posts.

I believe you can boot from the CD you used to install Ubuntu and then run memtest off of that.  Also, if it won't run memtest from the drive booting Ubuntu, there may be a problem with your installation.  I believe you said this was your second version of Ubuntu you installed?  Perhaps you have a hard drive problem.  Its not free, but Spinrite is great for detecting and correcting hard drive problems.  Maybe some of the other people on this forum can suggest some free tools you can use to check your HDD.

---

### Post by thinh4 on 2015-05-31
I went and bought a cheap graphics card... tried it for the last couple of days... haven't seen any issues yet.. so hopefully it did fix the problem for good.. thank you all for your help.

---


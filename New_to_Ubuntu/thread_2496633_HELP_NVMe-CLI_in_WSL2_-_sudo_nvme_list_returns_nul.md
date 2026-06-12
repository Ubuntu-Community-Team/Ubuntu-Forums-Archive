---
title: "HELP: NVMe-CLI in WSL2 - sudo nvme list returns nul"
date: 2024-04-06
forum: New to Ubuntu
---

### Post by ddoubleuc on 2024-04-06
Hi Gang

UPDATE: thanx for your support ... issue resolved

ORIGINAL POST

I'm running nvme-cli-2.8 in WSL2 and hoping to learn how to manage my internal NVMe PCIe SSD e.g. return P/E cycles. In order to ID that SSD, I run "sudo nvme list" and all columns (Node SN Model Namespace etc) return blank. The SSD contains Windows 11 so I thought maybe the OS managing the SSD as virtual disks (sda sdb sdc) might confuse nvme-cli so I ran the same command on WSL2 to try IDing a USB SSD and same result.

Any idea why nvme-cli is not seemingly recognizing SSDs on my PC?

thanks for considering

---

### Post by TheFu on 2024-04-06
I have no idea about WSL or WSL2, but don't those provide a virtual machine to run a layer of Linux under MS-Windows?  If so, direct hardware access deosn't happen. The Linux there only sees virtual hardware, not the real hardware in the system.  That's called running under a "VM" - virtual machine.

This is pretty common.  For example, inside a VM, the actual NIC isn't important. The guest VM doesn't know the real GPU or real NIC or real HDD/SSD. It only sees the fake versions emulated in the virtual environment.

But I could be wrong.  I know little about MS-Windows or WSL.

---

### Post by yancek on 2024-04-06
WSL is pretty limited and you would probably be better off using virtualbox or similar in windows to boot and run a Linux OS.  That or putting some 'live' Linux on a usb to test/try it.  WSL will not give you the actual experience of using Linux due to its limitations.

---

### Post by ddoubleuc on 2024-04-06
Hi Fu &#8230; thanx for touching base &#8230; I&#8217;m not sure re VM however yancek&#8217;s response supports yours and I think I&#8217;ll try Linux live on USB for full experience

---

### Post by ddoubleuc on 2024-04-06
Thanks yancek&#8230;I&#8217;ll give Linux live a go

---

### Post by MAFoElffen on 2024-04-07
Since I do dual-boot with Windows, and do DEV Testing for Win Insider & Win Server Insider... (I've also done Windows since version 1.0.) I can answer you without tap-dancing around this:
WSL(x) is Linux compatibility layer. It is not Native Linux. It is not a virtual machine or emulation. So no. Quit trying to use WSL as if it was. (That will just frustrate you wondering why things don't work like they just do in Linux.)

There are reasons why they added WSL. Relating with the host's system directly is not part of that. It is really handcuffed. Playing with 'WSL' will give you a wrong, biased, misguided perspective of Linux, and what it is.

With WSL, it follows Microsoft's long history, since after Windows version 3.0, of shielding common Users from the hardware and settings that affect the OS...

Lots of native Linux utilities that interactive with the hardware directly do not work under the WSL, because of what it really is, and how it is implemented. Lots of the basic base Linux utils are not even there because of that.

You want two examples? 
#1) You have to mount a volume specifically with PowerShell, to mount and remap it, to even access data on the host from within WSL. That still does not deal low-level access to the device under that. 

#2) Run my 'system-info' script under WSL... That script uses Linux base util's to show hardware info and system settings. It has a check of those basic utilities that most all Linux Distro's have already as a default. Under WSL it spits out a long list of what is not there.

That is just the reality of that. WSL is NOT Linux.

If you want a native Linux Experience, either install it as a VM within Hyper-V, or commit to install it as dual-boot, alongside of Windows.

As a VM, you are still be shielded from your host's hardware. You can learn Linux, and see how it relates to the virtual devices...

As a dual-boot, you can really see the full-deal. Where it interacts natively with your hardware. If you are trying to use utilities such as nvme-cli, where you want to learn how to interact natively with hardware at a low-level, then this is the choice for you to explore.

Linux is "very" powerful, if you learn it, and get comfortable with it.

I'm both a Linux and Windows Systems Admin. My niche is getting them to "play nice" together. Working in the past as a certified Dell, HP, & Lenovo Onsite Warranty Tech, I carried an Ubuntu LiveUSB in my kit. Not just because all three vendors have Ubuntu pre-installed offerings, but to work on Windows machines. You don't know just how many Windows Desktops and Windows Servers I diagnosed, and rescued with that 'tool'. 

Linux is well worth it to learn. You wonder why Linux Admins get paid more? Good skill to add to your resume. I challenge you to explore and learn Linux on your own. Members here will gladly answer your questions on Native Linux, where they have vast experience on.

---

### Post by ddoubleuc on 2024-04-07
Thanx for your detailed advice MAFoE … I’m in the process of resolving my attempted ‘Try Ubuntu’ from USB drive (separate help request) and looking forward to learning more of Linux

---


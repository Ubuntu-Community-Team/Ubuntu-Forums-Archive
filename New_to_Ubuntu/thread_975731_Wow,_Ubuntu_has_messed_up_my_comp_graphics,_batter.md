---
title: "Wow, Ubuntu has messed up my comp: graphics, battery, wireless, etc."
date: 2008-11-08
forum: New to Ubuntu
---

### Post by Adamantus on 2008-11-08
I recently got a new computer (HP dv5 notebook PC, Atheros AR242x ethernet card, AMD Turion X2 64 bit  2.1 GHz processor, 4 GB of memory). I started out with Vista 64 which was working fine.

Anyway, I finally installed Intrepid 8.10 using Unetbootin, but now I have quite a few problems that I can't seem to fix.

1) Battery problems. It says my computer's battery capacity is at 69% (poor). And whenever I go onto battery power, the batter icon doesn't seem to update (stuck at 100%). Plus, I keep hearing this high-pitched buzzing which I'm pretty sure is coming from the battery, and it is especially bad when I am running on battery power. Also, I'm pretty sure the battery life is significantly shorter than when I was running Vista.

2) The wireless card is incompatible and I can't seem to get it working. I've enable the wireless card, but their are no wireless networks available. In addition, the touchpoint wireless button on my laptop is stuck on orange (off), and I can't seem to change it to blue (on). I've tried using Mad Wifi, but I can never seem to get through all the steps without something failing. If someone could tell me how to use (with very simple language), it would be very helpful.

3) Every time I shut down and sometimes when I open programs, the screen will very quickly flash colorful lines across the screen as the window opens. I have my graphics card enabled.

Anyway, that's it. My computer was running fine with Vista, but I wanted to use Linux to increase the speed (which also doesn't seem to be significant at all). Hopefully you guys can help me with these problems.

---

### Post by porchrat on 2008-11-08
When you say your wireless card is incompatible what exactly do you mean?  The drivers that come standard with Ubuntu rarely work.  Generally you need to install drivers specific to your wireless module.

To determine what wireless module you are running use this command:

```
lshw -C network
```

---

### Post by Adamantus on 2008-11-08
Here's the output:

WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:09:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:68:aa:f6:00
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI ip=66.254.239.224 latency=0 module=r8169 multicast=yes
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: a6:a2:54:af:bf:c2
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by randy78 on 2008-11-08
As per your wireless issue, a quick Google search for "Atheros AR242x ethernet card " gave me this: [http://ubuntuforums.org/showthread.php?t=850185]("http://ubuntuforums.org/showthread.php?t=850185")

Because many hardware manufacturers are unwilling to release open source drivers, you can't realistically expect Ubuntu to just make everything work...

Granted, I've never had an issue with this before because I've always researched my hardware before installing Ubuntu because I wanted to make sure it will be compatible.

In order for Ubuntu to utilize all 4 gigs of RAM, you'll need to run the 64bit edition (Vista as well... no 32bit OS supports 4 gigs of RAM).

Also, you used UNetBootin to install... it's not an officially supported package and you should have used WUBI if you're inexperienced with installing.

I don't want to discourage you or start a flame war, but your lack of planning is what messed up your computer, not Ubuntu.

---

### Post by Adamantus on 2008-11-08
The first time I installed Ubuntu on my last laptop, I just bought a magazine with a disk and installed from there. Should I just re-install using that disk?

Also, I installed the 64 bit version  and unetbootin was the only thing that worked.

---

### Post by randy78 on 2008-11-08
What version is on that disk? I think your best bet would be to download Ubuntu 64bit, defrag Windows and run the WUBI installer from within Windows (it's in the ISO, you'll need something like UltraISO in windows to open it)

Just be sure to regularly defrag Windows, as WUBI will put the new installation of Ubuntu within the free space of your Windows install.

Hope this helps ;)

---

### Post by medic2000 on 2008-11-08
Please write "lspci" in terminal and post the output.

---

### Post by porchrat on 2008-11-10
Use the madwifi drivers for your atheros card, they worked for me.  I know 8.04 had issues where when you updated the kernel headers you had to do a "make clean" and "make install" again, but I believe ubuntu 8.10 solved that.  My advice is to get ubuntu 8.10 from [www.ubuntu.com](www.ubuntu.com) and then install the madwifi drivers.

---

### Post by bumanie on 2008-11-10
There are multiple threads about that wifi card since 8.10's release. I got mine going with ndiswrapper and apparently if you open the backports, drivers are available there - I haven't tried that, as ndiswrapper is working fine. I could not get the madwifi drivers to work.

---

### Post by ichi@YUKI on 2008-11-10
When I first had Ubuntu installed, I encountered similar problems--the one regarding my Wireless card and my battery. Don't worry, everyone new to Ubuntu encounters those problems, and almost all the questions have already been answered in the forums.

For the battery however, I thought that my battery life was shorter in Ubuntu rather than in Windows but in the end, it's my fault for not getting the modules designed to get my battery working. Although it's easier to recondition batteries in Windows (since ThinkPad has a utility..), it seems the battery's capacity gauge in Ubuntu (the one that pops up the first time you boot Ubuntu) is quite accurate. 

So just like the answer to the wireless card problem, I suggest entering keywords concerning your battery in the search bar. ^_^

---


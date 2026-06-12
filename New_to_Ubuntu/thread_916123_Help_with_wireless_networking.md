---
title: "Help with wireless networking"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by cdnaerogeek on 2008-09-10
Hi all,

I just installed Hardy Heron (64 bit) on my new Gateway T1625 laptop and all is well except for my inability to get the wireless network working. (I have used Linux for some basic stuff before, so I'm not a total n00b, but the networking bit is new to me.)

I've gone through some of the documentation and determined:
a) Ubuntu does recognize my network card (RTL8101E), and
b) the r8169 driver is installed

However, when I go to System > Administration > Network, the wireless network doesn't show up as an option.

Here's the output to the lshw and iwconfig commands:
> andrew@andrew-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 01
       serial: 00:03:25:50:0e:ea
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.2LK ip=192.168.1.114 latency=0 module=r8169 multicast=yes
andrew@andrew-laptop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


I know wireless networking has been covered in a lot of other threads, but the info is fragmented, and I haven't found the solution to my particular problem yet.

---

### Post by SunnyRabbiera on 2008-09-10
By the looks of it that prefix looks to be a realtek card, can you give us more information?

---

### Post by Titan8990 on 2008-09-10
Just a heads up, wireless + 64bit won't always work correctly. I had a 64bit Hardy install in which I installed the 64bit Windows drivers for my wireless card using ndiswrapper. This toasted the machine (mainly because I didn't test before adding the ndiswrapper module to /etc/modules).

Anyways, I grabbed a 32bit *buntu copy and loaded the 32bit Windows driver with ndiswrapper and everything worked perfectly.

---

### Post by SunnyRabbiera on 2008-09-10
> **Titan8990 said:**
> Just a heads up, wireless + 64bit won't always work correctly. I had a 64bit Hardy install in which I installed the 64bit Windows drivers for my wireless card using ndiswrapper. This toasted the machine (mainly because I didn't test before adding the ndiswrapper module to /etc/modules).

Anyways, I grabbed a 32bit *buntu copy and loaded the 32bit Windows driver with ndiswrapper and everything worked perfectly.

Indeed, try that too.
You will have to re format again but it will probably work.

---

### Post by cdnaerogeek on 2008-09-10
It is indeed a Realtek card. I don't have the specs with me right now, so I'll try and upload them later.

I should also mention that I was skimming around Realtek's website earlier and they claim to have a driver with 64-bit support:

[http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=7&Level=5&Conn=4&DownTypeID=3&GetDown=false)

(Scroll down to the Unix/Linux section and find the following description)
LINUX driver for kernel 2.6.X and 2.4.X (Support x86 and x64)

I don't know if anyone has experience working with this driver, but the instructions in the readme file don't seem compatible with *buntu 8.04 (though it does mention RedHat,Fedora, and SUSE by name)

If that doesn't work, it looks like I'll have to try the 32-bit version.

---


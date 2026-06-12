---
title: "No network connection reported..."
date: 2008-06-20
forum: New to Ubuntu
---

### Post by sajackson on 2008-06-20
I am using Ubuntu 32bit on an AMD Duron based machine. My network icon at the top of the screen has an exclamation mark on it (!) and says "No network connection". The thing is I am using it now and connected to the internet fine (DHCP via router and cable modem). Also I can connect to the shared folders on my Windows machines and download files, etc.

"ifconfig" returns the following:-

eth0 Link encap:Ethernet HWaddr 00:e0:20:7e:18:69
inet addr:192.168.0.106 Bcast:192.168.0.255 Mask:255.255.255.0
inet6 addr: fe80::2e0:20ff:fe7e:1869/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:1221 errors:0 dropped:0 overruns:0 frame:0
TX packets:881 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:1682127 (1.6 MB) TX bytes:95405 (93.1 KB)
Interrupt:10 Memory:e3000000-e30000ff

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:850 errors:0 dropped:0 overruns:0 frame:0
TX packets:850 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:42500 (41.5 KB) TX bytes:42500 (41.5 KB)

The IP address of my router is set to 192.168.0.1

Any ideas how to make Ubuntu realize it is actually working OK?

---

### Post by sajackson on 2008-06-21
I did a "lspci" and got the following message about the ethernet card:-

00:0c.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. Unknown device 2031 (rev 01)

Maybe this explains why Ubuntu thinks there is no network connection even though there is.

Any ideas how to fix this?

---

### Post by hyper_ch on 2008-06-21
if it works, then don't worry about it

---

### Post by sajackson on 2008-06-21
Hi hyper_ch, normally I would agree but it causes Firefox to always startup in offline mode, which I know is easy to go to the file menu and click but still a pain I would like to avoid. The other reason I would like to get to the bottom of it is because I am using this machine to learn about Linux and usually the best way to do that is by encountering problems and solving them.

---

### Post by sajackson on 2008-06-21
As far as I have been able to suss the problem is due to the NIC card I am using being a 'fake' Realtek card using a Hangzhou Silan chip. See the following post:-

[http://vishalmanohar.wordpress.com/2007/07/07/configuring-hangzhou-silan-on-ubuntu-linux/](http://vishalmanohar.wordpress.com/2007/07/07/configuring-hangzhou-silan-on-ubuntu-linux/)

I also had a look at the CD that came with the card and it has a folder with Linux drivers. One is for kernel 2.6 and the instructions in the readme file go like this:-

==========================================================================

Building and Installation
=========================

To build a binary RPM* package of this driver run 'rpmbuild -tb
<filename.tar.gz>'. Replace <filename.tar.gz> with the specific file name
of he driver.

NOTES: For the build to work properly it is important that the currently
       running kernel MATCH the version and configuration of the installed
       kernel source. If you have just recompiled your kernel, reboot the
       system and choose the correct kernel to boot.

       RPM functionality has only been tested in Red Hat distributions.

1. Move the base driver tar file to the directory of your choice. For
   example, use: /home/username/sc92031 or /usr/local/src/sc92031.

2. Untar/unzip the archive by entering the following, where <x.x.x> is the
   version number for the driver tar:

     tar xfz sc92031-<x.x.x>.tar.gz

3. Change to the driver src directory by entering the following, where
   <x.x.x> is the version number for the driver tar:

     cd sc92031-<x.x.x>/src/

4. Compile the driver module:

     make install

   The binary will be installed as below:

       /lib/modules/<kernel_version>/kernel/drivers/net/sc92031/sc92031.[k]o

   The install location listed above is the default locations. It may
   not be correct for certain Linux distributions. For more information,
   see the ldistrib.txt file included in the driver tar.

5.  Reboot now:


     shutdown -r now 

6. Install the module:

     modprobe sc92031

7. Assign an IP address to the interface by entering the following, where
   <x> is the interface number:

     ifconfig eth<x> <IP_address>

8. Verify that the interface works. Enter the following, where <IP_address>
   is the IP address for another machine on the same subnet as the interface
   that is being tested:

     ping <IP_address>

=========================================================================

Before I try this I was wanting to check if it will still allow me to use DHCP rather than a fixed IP address and does it sound OK to you experts out there.

I may still take hyper_ch's advice and just live with it since it does actually work as it is.

---

### Post by Nikitas350 on 2008-06-23
See this: [http://ubuntuforums.org/showthread.php?t=800179](http://ubuntuforums.org/showthread.php?t=800179)

---

### Post by sajackson on 2008-06-23
Hi Nikitas350, Thanks for the reply. I tried what you said in the other post and it has stopped Firefox always starting in offline mode OK. The Network icon on the task bar still has the ! on it and still reports no Network though.

At least I don't have to put Firefox online each time I run it up which is a definite improvement. I may still try installing the driver anyway since I am trying to learn as much as I can about Linux anyway.

Do you think it would be easy to uninstall if it stops my network running completely?

---


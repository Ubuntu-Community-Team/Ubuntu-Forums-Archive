---
title: "[SOLVED] WiFi drivers with Ubuntu boot CD"
date: 2008-05-20
forum: New to Ubuntu
---

### Post by nabab on 2008-05-20
Hi there,

Sorry I'm reposting this thread as my original title (First steps with Ubuntu) was not saying much...

So I have launched Ubuntu on my Sony laptop from the boot Cd and got this message about my wireless card:
> 
Proprietary drivers are being used to make this computer work properly.

Device driver:
- Atheros Hardware Access Layer (HAL) (in use)
- Support for Atheros 802.11 wireless LAN cards (in use)


Then I have typed a few commands recomended by hyper_ch and here is the result:
> 
ubuntu@ubuntu:~$ lspci | grep Ath
06:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
ubuntu@ubuntu:~$ lsusb | grep Ath
ubuntu@ubuntu:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1a:80:1f:bd:98  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:9510 errors:0 dropped:0 overruns:0 frame:0
          TX packets:9510 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:475500 (464.3 KB)  TX bytes:475500 (464.3 KB)

ubuntu@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


My questions are:
- Do you reckon it will be a concern having this WiFi card working, knowing the Linux drivers exist?
- Is it possible to install drivers when you're only using the boot CD to test? (I'd say you can't but hopefully you'll say the opposite...)

Thanks!

Thomas

---

### Post by MaindotC on 2008-05-20
You can install the drivers but typically the boot cd doesn't not directly use the hard drive for its file system and only what it can store in memory.  That being said I doubt you have enough memory to install the restricted drivers.  If you're concerned about erasing a hard drive, just create a small partition for the installation + package updates you'll have to download.  If it fully works and you want Ubuntu to consume the rest of the hard drive you can always use a partition manager to expand Ubuntu.

---

### Post by nabab on 2008-05-20
Thanks for the reply, yes I know I can always do that, but I would have liked to test without changing anything to my actual system.
When you're talking about memory, you mean the RAM? This laptop has 2 Gig of RAM so if it's possible to load the driver in the RAM it should be doable.
Does anyone have a tip or a link for doing that?

Cheers,

T

---

### Post by avtolle on 2008-05-20
> **nabab said:**
> Thanks for the reply, yes I know I can always do that, but I would have liked to test without changing anything to my actual system.
When you're talking about memory, you mean the RAM? This laptop has 2 Gig of RAM so if it's possible to load the driver in the RAM it should be doable.
Does anyone have a tip or a link for doing that?

Cheers,

T
It *should* be doable, but I don't think it can be for this reason. To get the Atheros wireless running under 8.04, there are several steps to be performed, including without limitation, disabling the restricted drivers shown being in use. Then, one needs to consult any one of several "how tos" on the Forum, including this one: [http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html), assuming this is the appropriate wireless card. As you likely know, the drivers would be installed in RAM as you would be doing this from the Live CD; but, as you will see, a reboot of the system is needed to make the needed changes "permanent", which, of course, means that the same will be lost from RAM on reboot. No joy here, I fear. Perhaps someone else can show the errors, if any, in my thought process here, in which case you may have some success.

---

### Post by MaindotC on 2008-05-20
Yes, I mean RAM.  If it works for you wonderful but consider that it's already loading the entire operating system into memory.

One way to install the restricted drivers is to select System -> Administration -> Restricted Drivers Manager.  You should be prompted for the administrative password.  The window that appears will allow you to select the driver for your wireless card, and it will also have an option to enable or disable it.  Once you enable it, the driver will be automatically downloaded.  Good luck!

---

### Post by nabab on 2008-05-20
Thanks, I have installed it properly and everything was detected fine.

---

### Post by MaindotC on 2008-05-20
Star me plz :-p

---


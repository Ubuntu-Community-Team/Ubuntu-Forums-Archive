---
title: "Getting an Asus P5KPL-CM onboard LAN to work"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by Rhythmdvl on 2008-08-05
In first putting together the system (all new components), the link light on the motherboard isn’t lit, and the desktop says “no network devices have been found.” 

Turning to the Asus CD, there are Linux device drivers to install and a couple text files. 

From one, there is the following paragraph:

>  Configuring a network driver to load properly when the system is started is distribution dependent. Typically, the configuration process involves adding an alias line to /etc/modules.conf as well as editing other system startup  scripts and/or configuration files. **Many popular Linux distributions ship with tools to make these changes for you. **To learn the proper way to  configure a network device for your system, refer to your distribution  documentation. If during this process you are asked for the driver or module  name, the name for the Linux Base Driver for the Atheros AR8121/AR8113 is arl1e

Does Ubuntu have a tool to make the installation of the device drivers easier? The other readmes have detailed information on some settings, but many of them are vaguely worded, especially in that they leave installation choices up to the installer.

ETA: another bit of data about the hardware:
> This file describes the Linux* Base Driver for the Atheros(R) AR8121/AR8113 PCI-E Ethernet Adapter, version 1.0.0.0 This driver supports the 2.4.x and 2.6.x kernels.

This driver is only supported as a loadable module at this time. Atheros is not supplying patches against the kernel source to allow for static linking of the driver. For questions related to hardware requirements, refer to the documentation supplied with your Atheros(R) adapter. All hardware requirements listed apply to use with Linux.


Thanks, 

Rhythm

---

### Post by ConMan318 on 2008-08-05
I just built one a couple weeks ago with an Asus mobo, and Ubuntu wouldn't recognize the ethernet port.  Are you using 64-bit Ubuntu?  If so, the drivers for networking with onboard network ports are kind of behind, from what I hear.

I honestly recommend buying a PCI or PCIe network card, whatever empty ports you have.  That's what I had to do; I made a thread and didn't get any responses about getting Ubuntu to configure the drivers, so I don't think you will be able to get much help as to the topic of your thread.

You can find them at Newegg for pretty cheap (I got an Intel one for 20-something bucks), and I also picked up an even cheaper (less than 20 bucks) backup one from Best Buy.

Both of mine instantly connected as soon as I attached them to the motherboard and plugged in an ethernet cord.

Sorry I can't really help solve the problem you made your thread for, but if you find that no one is able to help you, keep this option open as an extremely easy fix.

---

### Post by AClark on 2008-08-05
No need to spend more money. I just built a new machine with a P5Q Asus board.  Using the instructions in the readme on the CD I got the onboard Gigabit Lan working perfectly.

If you are willing to do a little command line work it doesn't take long.

I created a folder named Drivers in my home folder and copied l1e-l2e-linux-v1.0.0.4.tar.bz2 to it from the Asus CD.

cd to that folder and
CODE
tar zxf l1e-l2e-linux-v1.0.0.4.tar.bz2

Now there will be two new folders - in my case the path was home/awc/Drivers/atl1e/src

change directory to the /src folder and 
CODE
make install

This gave me an error message - something about "CFlags" and fixing it to use "EXTRA_CFLAGS" 

A quick search turned up a suggestion to try 
CODE
sudo KBUILD_NOPEDANTIC=1 make install

That did the trick for me and now the driver module has been created and is in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e

2.6.24-16-generic is the kernel that my Hardy install is using - you may have to sustitute if yours is different.

so now
CODE
cd /lib/modules/<YourLinuxKernalVersionHere>/kernel/drivers/net/atl1e
sudo insmod ./atl1e.ko

Now the module is loaded into the kernel and the lan works.

Their readme file goes on to give instructions for configuring the interface but my lan was instantly connected - I suppose by Network Manager.  I prefer WiCD so later when I installed that I set my preferred config in WiCd.

I hope this makes sense - good luck !

I have to get up early tomorrow so don't think me rude if I don't answer any questions - -I'm sleeping.

PS Since we manually added this module I'm guessing we may have to do this again the next time there is a kernel update so save the instructions (If they work for you)

---

### Post by Rhythmdvl on 2008-08-06
Ohhhh... so close! 

Thanks a lot for the direction -- a main reason for picking this board was the Gigabit LAN. Buying a card won't be too expensive (fortunately), but the thought of it is a bit vexing. 

I'm getting an odd error -- I tried the KBUILD_NOPEDANTIC=1, but the output looked like it wasn't right. Also, when I switched directories, I didn't have atl1**e** -- I just had atl1. 

Here (if I can do this right) is the output from the make install attempt:

```
suazionuser@HappyLinux:~/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src$ sudo KBUILD_NOPEDANTIC=1 make install
make -C /lib/modules/2.6.24-16-generic/build SUBDIRS=/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.24-16-generic'
  CC [M]  /home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.o
In file included from /home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:1:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at.h:10:5: warning: "AUTO" is not defined
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at.h:82:5: warning: "DBG" is not defined
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:109: warning: initialization from incompatible pointer type
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_init_module’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:135: error: implicit declaration of function ‘pci_module_init’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_probe’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:215: error: implicit declaration of function ‘SET_MODULE_OWNER’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:352:53: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:351: error: ‘INIT_WORK’ undeclared (first use in this function)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:351: error: (Each undeclared identifier is reported only once
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:351: error: for each function it appears in.)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:355:51: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:358:53: error: macro "INIT_WORK" passed 3 arguments, but takes just 2
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_up’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:952: error: ‘SA_SHIRQ’ undeclared (first use in this function)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:952: error: ‘SA_SAMPLE_RANDOM’ undeclared (first use in this function)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:953: warning: passing argument 2 of ‘request_irq’ from incompatible pointer type
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_vlan_rx_kill_vid’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:1249: error: ‘struct vlan_group’ has no member named ‘vlan_devices’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_restore_vlan’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:1267: error: ‘struct vlan_group’ has no member named ‘vlan_devices’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_rx_checksum’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2270: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_tso’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2487: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2488: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2489: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2489: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2490: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2494: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2498: error: ‘struct sk_buff’ has no member named ‘nh’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2499: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_tx_csum’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2517: error: ‘CHECKSUM_HW’ undeclared (first use in this function)
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2519: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2520: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_tx_map’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2570: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2570: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c: In function ‘at_xmit_frame’:
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2743: error: ‘struct sk_buff’ has no member named ‘h’
/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.c:2743: error: ‘struct sk_buff’ has no member named ‘h’
make[2]: *** [/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src/at_main.o] Error 1
make[1]: *** [_module_/home/suazionuser/Drivers/LinuxAttan_Lan/AtL1Linux_v1.1.40.1/src] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.24-16-generic'
make: *** [default] Error 2

```


I'm fairly certain a more advanced user could get it to work without all the struggle -- before buying the board I'd checked Linux compatibility and LAN was OK. But if I can't get it I can't get it, and a thirty dollar card isn't necessarily worth ten hours of trying (of course, as I get more familiar with Linux, I'll be able to return to it again).

---

### Post by Rhythmdvl on 2008-08-06
Well I'll be. I got it to work, and I figured if anyone follows this thread, it would be a good idea to point them to how things worked out. 

In my searches, I came across a post on an obscure message board called "Ubuntuformums.org" Now, who would have ever looked there? Anyway, the thread is [02:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)](http://ubuntuforums.org/showthread.php?t=770173). 

Post #7 was:
[quote=pdelahun] Solved !!!
Hi Guys

Thank you, thank you so much !!!

I have got it working !!!

Ok first the network card is Atheros(R) AR8121/AR8113 PCI-E

Ok these are the steps i followed to get it working!

1) I installed ubuntu hardy 64bit, i has build-essential package installed
2) Then i downloaded the linux driver from: [http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM](http://support.asus.com/download/download.aspx?product=1&SLanguage=us-en&type=map&model=P5KPL-CM)
(as per my original post)
3) I then transfered the driver via usb stick to my laptop and unpacked the zip. (Actually i unpacked it on windows first as it has a .rar file that i could not unpack on linux Then i packed it up again on windows).
4) cd into <HOME_DIR>/LinuxDrivers/L1e_Lan/l1e-l2e-linux-v1.0.0.4/src
5) then i ran: sudo KBUILD_NOPEDANTIC=1 make
6) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
7) that worked and put a driver in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e/at1le.ko
8 ) i cd into that director and i run: sudo insmod ./atl1e.ko

That is it !!! it worked as soon as i plugged in network card.

Thank you all so much !!!! I hope this helps everyone else[/quote]


I'm not sure how this differed from **AClark's** suggestion. I'd tried that with the CD and the downloaded drivers. I'm not sure how the location differed, but the other link lead me to a RAR file, which I didn't have before. Chugging along just as the quoted instructions were laid out got me to a working onboard LAN. 

THANKS!!!!!

---

### Post by AClark on 2008-08-06
Glad to hear you got it working! Nothing like the feeling of solving a problem.

I would really like to know why that file worked & the one on the CD didn't. Maybe a newer version?  The output from your unsuccessful try indicated a pretty fundamental problem - practically every statement in the make file generated an error!

Just a note for others having problems - In my original search for a solution to my problem I found a post (don't remember where) that indicated that the Atheros drivers would probably be included in the kernel in the not too distant future.

So someday a kernel update may eliminate all this fuss.

---

### Post by jcliburn on 2008-08-06
The driver for the L2e NIC (PCI ID 1969:1026) was recently accepted into the mainline kernel.  It should be released with 2.6.27.

---

### Post by smokey_58au on 2008-08-08
Thanks AClark.  I followed your method and it worked exactly as described on my new P5KPL-CM board.  As soon as I pressed "Enter" on the last command the LAN automatically connected and I was away.  Well done.

---

### Post by edthefox on 2008-08-15
Thanks for sharing this info **AClark**, It's much appreciated. I was having the exact same problem setting up my ***ASUS P5KPL-CM*** and a quick search of the forums brought me here! Great Post!

---

### Post by linux_newbie101 on 2008-09-08
My Asus P5KPL-CM onboard LAN now works thanks Rhythmdvl and AClark's postings! :)

I just built a new PC desktop using an ASUS P5KPL-CM motherboard and had no problems installing Ubuntu 8.04 LTS. I was also able to install my wireless LAN with a Netgear WG311 Wireless-G PCI Adapter, NDISWrapper and XP driver (thanks to the detailed instruction from a very good book "Beginning Ubuntu Linux" - by Keir Thomas and Jaime Sicam, copyright 2008 )

However, I had trouble having the onboard LAN to work until I read your postings.

I copied the Linux LAN driver in the P5KPL-CM CD to my Desktop directory and did the following.

1) cd into <HOME_DIR>/linux-v.1.0.0.7/src
2) then i ran: sudo KBUILD_NOPEDANTIC=1 make
3) then i ran: sudo KBUILD_NOPEDANTIC=1 make install
4) that worked and put a driver in /lib/modules/2.6.24-19-generic/kernel/drivers/net/atl1e/at1le.ko
5 ) then i cd into that directory and i run: sudo insmod ./atl1e.ko

Now both wireless and wired LAN are now working, Time to move on to my other peripherals like network printer!

Thanks guys!

---

### Post by sulekha on 2008-10-23
> **AClark said:**
> No need to spend more money. I just built a new machine with a P5Q Asus board.  Using the instructions in the readme on the CD I got the onboard Gigabit Lan working perfectly.

If you are willing to do a little command line work it doesn't take long.

I created a folder named Drivers in my home folder and copied l1e-l2e-linux-v1.0.0.4.tar.bz2 to it from the Asus CD.

cd to that folder and
CODE
tar zxf l1e-l2e-linux-v1.0.0.4.tar.bz2

Now there will be two new folders - in my case the path was home/awc/Drivers/atl1e/src

change directory to the /src folder and 
CODE
make install

This gave me an error message - something about "CFlags" and fixing it to use "EXTRA_CFLAGS" 

A quick search turned up a suggestion to try 
CODE
sudo KBUILD_NOPEDANTIC=1 make install

That did the trick for me and now the driver module has been created and is in /lib/modules/2.6.24-16-generic/kernel/drivers/net/atl1e

2.6.24-16-generic is the kernel that my Hardy install is using - you may have to sustitute if yours is different.

so now
CODE
cd /lib/modules/<YourLinuxKernalVersionHere>/kernel/drivers/net/atl1e
sudo insmod ./atl1e.ko

Now the module is loaded into the kernel and the lan works.

Their readme file goes on to give instructions for configuring the interface but my lan was instantly connected - I suppose by Network Manager.  I prefer WiCD so later when I installed that I set my preferred config in WiCd.

I hope this makes sense - good luck !

I have to get up early tomorrow so don't think me rude if I don't answer any questions - -I'm sleeping.

PS Since we manually added this module I'm guessing we may have to do this again the next time there is a kernel update so save the instructions (If they work for you)

Hey dude your howto worked for me , thanks a lot
BTW can any one write a how to on how to update the bios 
in Asus P5KPL-CM ,in ubuntu, i mean is there any specigic tools for doing that, as it is in winXP...????

---

### Post by JesseLaw on 2009-04-18
I had the same problem - but this fix didn't work for me. 
I am installing the ASUS P5KPL-CM with a image of UBUNTU 8.04 that has been prepared with EMC ([www.linuxcnc.com](www.linuxcnc.com))


This is what I did:

I got an error with the make process:

src/at_main.c:708: error: 'retval' undeclared

I looked at src/at_main.c line 708 and found a variable definition inside an if statement a few lines above #708:  

#ifdef CONFIG_PM
    int retval = 0;
#endif

I just copied the declaration outside the if block so that it would always get defined like this: 


#ifdef CONFIG_PM
    int retval = 0;
#endif
    int retval = 0;

ran the commands as mentioned previously in the thread: 

sudo KBUILD_NOPEDANTIC=1 make install
sudo insmod ./atl1e.ko

and ethernet started working.

It probably isn't a good idea to modify driver code - but it hasn't given me problems yet.


Anyway, thought I'd add my experience. Thanks to those that started this thread.

---

### Post by towerofpower256 on 2009-05-08
Just one thing I'd like to add which completely threw me off. My driver was installed and kicking but I still couldn't see the network or interface. I had to manually assign it an entry in /etc/network/interfaces as Ubuntu doesn't seem to do this automatically.

```
auto eth0
iface eth0 inet dhcp
```

or

```
iface eth0 inet static
address 192.168.1.X
netmask 255.255.255.0
gateway 192.168.1.X
```

That would've saved me HOURS of frustration, so I thought I'd pass it on.

---


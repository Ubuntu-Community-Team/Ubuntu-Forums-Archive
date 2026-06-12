---
title: "PCMCIA - RT8139 or DSE XH8267 installation problems."
date: 2008-04-29
forum: New to Ubuntu
---

### Post by MilosI on 2008-04-29
EDIT : I have posted this in the incorrect board, please visit [http://ubuntuforums.org/showthread.php?p=4831230](http://ubuntuforums.org/showthread.php?p=4831230) for the latest post in Networking and Wireless and then see if you can help us!

EDIT 1: Sorry it should say RTL8139 in the title!

**Hello everyone,**

Thanks for opening this thread.

We are running **Ubuntu 8.04 LTS Server Edition**.

I have been having great trouble trying to setup this card to work on my friend's laptop which is by the way really old (originally run Windows 98, which is of course from 1998 ).
The drivers that came on the CD were for Windows and Linux, it was difficult to understand the readme for the file and even after asking for help in a channel on FreeNode there wasn't any more luck.

The message that it displays in */var/log/messages* is "CardBus not supported" when the card is inserted.

*ifconfig eth0* says device not found.
After trying to *make* ndiswrapper to possible emulate the windows driver or whatever ndiswrapper does, it said Error 2. Great, what the heck does that mean.

This is what the readme for the file said:

> 
RTL8139 driver(written by Donald Becker) is distributed with Linux
after kernel version 2.0.34. It is better to build it into kernel.

The procedure to activate rtl8139 on linux if not build in kernel:

  step 1: compile:
           The instruction for compiling the driver is include at the
           end of the driver file. (run this instruction at
           /usr/src/linux)

  step 2: insert the driver as module:
           insmod rtl8139.o
      parameter can be added by adding options=..... behind the istrruction
              0x16(bit 4):full duplex
              bit 0-3    :default port
      (run 'lsmod' to see if the module is inserted)

  step 3: bind your card to an IP address

   /sbin/ifconfig eth0 ${IPADDR} broadcast ${BROADCAST} netmask ${NETMASK}
     (run 'netstat -i' to see if there is a interface 'ne0')

  step 4: add your card to IP routing table, then add gateway also
     your card:
	   /sbin/route add -net ${NETWORK} netmask ${NETMASK} eth0
           (should be able to ping local network now)
     gateway:
           /sbin/route add default gw ${GATEWAY} netmask 0.0.0.0 metric 1

  step 5: start inet deamon.
           /usr/sbin/inetd
           (you are on the network now)

*make sure that your kernel is built with network,CardBus, fast_ethernet 
 and module support. Otherwise, you have to rebuild your kernel.
 	(1:go to /usr/src/linux directory
         2:run 'make menuconfig' or 'make config'
         3:mark the options list above.
         4:exit and rebuild your kernel.
            make dep;make clean;make zImage
            the file 'zImage' will be at 
              /usr/src/linux/arch/i386/boot/zImage
         5:modify /etc/lilo.conf.(this file specify where kernel image is)
         6:run 'lilo'  )

You cna run 'netconfig' which will do step 3,4,5 for you. This will create
'/etc/rc.d/inet1' and 'inet2' files. These two files will run at boot time.
Then just add a line at the beginning of 'inet1'.
        'insmod /your driver'path/rtl8139.o'

then your driver will work every time you boot.


The PCMCIA card was bought in a shop called Dick Smith Electronics, and here is the website with information about the card.

[http://www.dse.co.nz/cgi-bin/dse.storefront/4816cf3905e0420c273fc0a87f3b0686/Product/View/XH8267](http://www.dse.co.nz/cgi-bin/dse.storefront/4816cf3905e0420c273fc0a87f3b0686/Product/View/XH8267)

--------------------------------------------------------------

Any help would be appreciated, and remember we don't have ethernet on this machine, (that's what we're trying to get) and so if there's anything required to download we have to get the package and then burn it to a disc, mount and then be able to install whatever is needed.

Thanks once again.

---


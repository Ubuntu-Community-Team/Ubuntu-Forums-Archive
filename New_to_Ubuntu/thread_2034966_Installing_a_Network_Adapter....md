---
title: "Installing a Network Adapter..."
date: 2012-07-29
forum: New to Ubuntu
---

### Post by suvindu on 2012-07-29
Okay, so I'm going to install Ubuntu 12.04 on this Computer, by formatting my Partition with Windows 7. Before that, I downloaded the Linux installaton for my network adapter. But, I don't know how to install it. My Adapter is a TP Link TF-3200.  Below are the files in the linux installation directory.
[http://i.imgur.com/88Ri5.png](http://i.imgur.com/88Ri5.png)

and This is the content of the "Readme" File...
```
	      
	                   Linux Driver 

Contents:
-----------
1. File Description
2. Driver Installation for Linux
3. Driver Parameter
4. None EEPROM
5. EEPROM MP (OEM Only)

1. File Description
-------------------

Filename                Description
====================    =======================================================
sundance_main.c         Linux Driver Source Code.
                        This file is the main part of Linux Driver.

compat.h                Network interface message level settings.

crc32.h                 Crc function for early Linux 2.4.19pre kernel inclusion

ethtool.h:              Defines for Linux ethtool.

mii.h                   definitions for MII-compatible transceivers.

mii.c                   MII interface library.

makefile                Make File For IP100 Linux Driver.
                        Using "make all" for your kernel.

readme.txt              A summary of the contents for Linux Driver.
                        This file, which you are reading me now.



2. Driver Installation for Linux
-----------------------------------------
a. for kernel 2.4.x
   a1. Redhat 7.3 (linux kernel 2.4.18)
   a2. Mandrake 8.1 (kernel 2.4.8)
b. for kernel 2.6.x
c. automatically load and configure at next boot time

   a.for kernel 2.4.x
   -------------------
     a1. Redhat 7.3 (linux kernel 2.4.18)
     a1.1. install way 1:
         #make all =>generate sundance.o
         #cp sundance.o /lib/modules/2.4.18-3/kernel/drivers/net/
         #insmod ./sundance.o
         #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1...
            xxx  is your ip address, ex: 192.168.102.211
            yyy  is your netmask address, ex:255.255.255.0

     a1.2.  install way 2:
        #make all =>generate sundance.o
        #cp sundance.o /lib/modules/2.4.18-3/kernel/drivers/net/
        #insmod./sundance.o
        #setup
        [network configuration] =>to setup your ip address
        #ifup eth0
           eth0 is your network adapter, ex: eth0, eth1...	


     a2. Mandrake 8.1 (kernel 2.4.8)
       #make all  => generate sundance.o
       #cp sundance.o /lib/modules/2.4.8-26mdk/kernel/drivers/net
       #insmod ./sundance.o
       #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy
           eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1...
           xxx  is your ip address, ex: 192.168.102.211
           yyy  is your netmask address, ex:255.255.255.0


   b. for kernel 2.6.x
   -------------------
      #make all  => generate sundance.ko
      #insmod ./sundance.ko (or sundance.o)
      #ifconfig eth0 xxx.xxx.xxx.xxx netmask yyy.yyy.yyy.yyy
            eth0 is your network adapter,use "dmesg" to check it, ex: eth0, eth1...
            xxx  is your ip address, ex: 192.168.102.211
            yyy  is your netmask address, ex:255.255.255.0      
   
   c. automatically load and configure at next boot time
   -----------------------------------------------------
     c1. cp sundance.o /lib/modules/`uname -r`/kernel/drivers/net
     *note: The `uname -r` is a command. Don't replace `uname -r` with
            2.4.18, 2.4.20smp, or some others. Must type `uname -r` directly.

     c2. Add the following lines at /etc/modules.conf:
	           
	      alias eth0 sundance
	      options sundance <optional parameters>
	           	           
     c3. Run "netconfig" or "netconf" to create configuration script 

              ifcfg-eth0 located at /etc/sysconfig/network-scripts or 
              create it manually.
              [see - Configuration Script Sample]

     c4. Driver will automatically load and configure at 
              next boot time.
              
     c5. Configuration Script Sample
     ===========================
         Here is a sample of a simple configuration script:

         DEVICE=eth0
         USERCTL=no
         ONBOOT=yes
         POOTPROTO=none
         BROADCAST=207.200.5.255
         NETWORK=207.200.5.0
         NETMASK=255.255.255.0
         IPADDR=207.200.5.2
              

3. Driver Parameter
-------------------
  If you want to change the link speed, you could use parameter after 
  insmod command.
  
  insmod sundance.o <optional parameter>    ; add parameter

  ========================================================================
   example: insmod sundance.o media=100mbps_hd
   or	    insmod sundance.o media=3
   or	    insmod sundance.o media=1,2,3,4	; for 4 cards or IP100
  ========================================================================              
  
  Parameter Description
  =====================
  You can install this driver without any addtional parameter. However, if 
  you are going to have extensive functions then it is necessary to set 
  extra parameter. Below is a list of the command line parameters supported 
  by the Linux device driver.

media=xxxxxxxxx			- Specifies the media type the NIC operates at.
				  autosense	Autosensing active media.
				  10mbps_hd	10Mbps half duplex.
				  10mbps_fd	10Mbps full duplex.
				  100mbps_hd	100Mbps half duplex.
				  100mbps_fd	100Mbps full duplex.
				  0		Autosensing active media.
				  1		10Mbps half duplex.
				  2		10Mbps full duplex.
				  3		100Mbps half duplex.
				  4		100Mbps full duplex.
				  By default, the copper devices operate at 
				  autosense, the fiber devices operate at
				  100Mbps full duplex.
				  Note that, the fiber adapter only support 
				  100Mbps half/full duplex types.	

  If wanting to change speed, this driver needed to be unloaded and reloaded with 
  new media parameter. Use rmmod to unload and insmod to reload driver.
  ========================================================================
   example: rmmod sundance.o 
   	    insmod sundance.o media=3
  ========================================================================    

flowctrl=[0|1]			- Specifies the flow control function.
				  0	Disable flow control.	
				  1	Enable flow control.	

4. None EEPROM
--------------
  If you want to use none eeprom solution. Please put EEPROM EEDO pin to GND.
  And, please add following -DNO_EEPROM define in Makefile, and re-compile again.

MAPPING_MODE= -DUSE_IO_OPS -DNO_EEPROM

5. EEPROM MP (OEM Only)
-----------------------
  This is a special tool for OEM embedded system to burn eeprom value with 
  MAC address. It is not for normal user. If you need this tool, please contact
  us directly. Thanks.
  
  5.1. unzip mp.zip and put 'mp directory' in the same directory with
  sundance_main.c

  5.2. Change Makefile:
  Form: "MAPPING_MODE= -DUSE_IO_OPS"
  To: "MAPPING_MODE= -DUSE_IO_OPS -DMP_EEPROM"

  Rebuild and load driver

  5.3. Read MAC address form EEPROM
  #cat /proc/ICPlus_eth0/IPF_EEPROM

  5.4. Write MAC address to EEPROM
  #echo "001122334455">/proc/ICPlus_eth0/IPF_EEPROM

  5.5. Convert EEPROM.TXT to eeprom_data.h
  run eep_cvrt.exe will convert EEPROM.txt to eeprom_data.h for linux driver
  use.
```

The Readme file may contain instructions on how to install the driver; but I don't understand it :( Can someone simplify it for me? If I can't get this done, I'll be stuck with Windows7 :(


Thanks.

---

### Post by suvindu on 2012-07-30
At least give me the steps? :s  I've never used Linux before o_o

---

### Post by BkkBonanza on 2012-07-30
Almost all PCI network adapters should work out of the box without any user installed drivers. It would be very unusual if you had to do anything at all.

What you have above is source code files for compiling a driver it seems. 99.9% likely you don't need that at all.

You should just boot the linux disk and select install. It should detect and load any driver needed.

---

### Post by Ubun2to on 2012-07-30
> **suvindu said:**
> ```
2. Driver Installation for Linux
-----------------------------------------
a. for kernel 2.4.x
   a1. Redhat 7.3 (linux kernel 2.4.18)
   a2. Mandrake 8.1 (kernel 2.4.8)
```


Well, this alone raised a red flag. Red Hat (which is based on the Linux kernel) and Mandrake (which is based on Mandriva, which is based on Red Hat) use .RPM (RPM Package Manager) files.
Ubuntu uses .DEB (Debian) files (as it is based on Debian, which is based on the Linux kernel).
So, you either downloaded the wrong drivers, or they didn't have any .DEB files.

---

### Post by BkkBonanza on 2012-07-30
Actually that whole driver info indicates he's using a sundance driver. AFAIK the **sundance** driver has been supplied since long ago. It should be already built in the 

/lib/modules/`uname -r`/kernel/drivers/net directory 

as sundance.ko

---

### Post by suvindu on 2012-07-30
I did need the drivers, I installed 12.04 yesterday and It kept saying "Device not Ready" and "Unplugged" so I had to switch to Windows 7.

EDIT: I had to install the drivers for the card in Windows 7, too.

---

### Post by BkkBonanza on 2012-07-30
You can check if the driver is loaded with the **sudo lsmod** command (it should show up) and if need be you can load it with **sudo modprobe sundance**.

There could be some config issue that is preventing the kernel from knowing the right driver to load.

Also, post output of **ifconfig -a**. You may have the driver loaded but the interface isn't configured to be brought up yet.

---

### Post by suvindu on 2012-07-30
```
eth0      Link encap:Ethernet  HWaddr 94:0c:6d:85:c8:b8
          inet addr: fe80::960c::6dff:fe85::c8b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
          RX Packets:775 errors:0 dropped:0 overruns:0 frame:0
          TX Packets:40 errors: 0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:99977 (99.9KB)  TX Bytes:7125 (7.1KB)
          Interrupt:18 Base address:0xbc00

lo        Link encap:Local Loopback
          inet addr:127.0.0.1 Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING MTU:16436 Metric:1
          RX Packets:2840 errors:0 dropped:0 overruns:0 frame:0
          TX Packets:2840 errors: 0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueulen:0
          RX bytes:231848 (231.8KB)  TX Bytes:231848 (231.8KB)
```

---

### Post by BkkBonanza on 2012-07-30
That shows you do have a working ethernet adapter present but it has not been configured with an IP. So next step is to post your /etc/network/interfaces file to see how that eth0 is configured. If it's correct then it can be brought up with,

sudo ifup eth0

but if it doesn't have the right setup, then we'd have to edit that first. Typically Netowork Manager should be doing this for you but obviously there is some reason it hasn't.

---

### Post by suvindu on 2012-07-30
The interfaces file says:
 
```

auto lo
iface lo inet loopback
```

---

### Post by BkkBonanza on 2012-07-30
Ok. That partly explains why it isn't up and going. But usually Network Manager would be taking care of that for you automatically. So there must be a reason it hasn't, like you removed it or it wasn't installed for some reason.

Assuming you're using a desktop install, have you looked at Network Manager (on the system menu or the Network icon) and made sure it has good settings for your LAN? It looks like the eth0 interface is available which means the driver is loaded. So the next step is settings.

If Network Manager isn't there for some reason you can install it or configure eth0 manually by adding some lines to that file above. A typical config in the interfaces file would be adding,

auto eth0
iface eth0 inet dhcp

then restart networking, or just,

sudo ifup eth0

---

### Post by suvindu on 2012-07-30
```
sudo ifup eth0
``` Seems to have done nothing. How do I 'Restart Networking'?

---

### Post by BkkBonanza on 2012-07-30
What error message if any did ifup give you?

Full restart is,

sudo /etc/init.d/networking restart

(and notice if any error messages are spit out). But either only makes sense if you have edited the interfaces file.

And then post output of ifconfig command. 

Do you know for sure that your network (router) is set for DHCP?

---

### Post by suvindu on 2012-07-30
I did change interfaces. The output of ifconfig:
```

eth0      Link encap:Ethernet  HWaddr 94:0c:6d:85:c8:b8  
          inet addr:192.168.2.2  Bcast:192.168.2.255 Mask:255.255.255.0
          inet6 addr: fe80::960c:6dff:fe85:c8b8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2710 errors:0 dropped:0 overruns:0 frame:0
          TX packets:713 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:583765 (583.7 KB)  TX bytes:74931 (74.9 KB)
          Interrupt:18 Base address:0xbc00 
 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2008 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2008 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:159632 (159.6 KB)  TX bytes:159632 (159.6 KB)

```
 
And.. I don't really know anything about DHCP, I had my network working on windows though. I'm trying to configure a Wired Connection.
 
EDIT: 'Network' from Settings says: Wired Connection. Unplugged. It is plugged in, though.

---

### Post by BkkBonanza on 2012-07-30
Your output above indicates you now have an IP address assigned, which is great. You should be able to use it now. If you can't then post output of **route -n** command here as you may have routing issues still.

You must have DHCP enabled on the LAN (wired or wifi either can use it) since DHCP is what gave you your IP address 192.168.2.2

---

### Post by suvindu on 2012-07-30
IT WORKS!! THANKS ALOT! 
 
I am sooo sticking with Linux :D :D :D

---

### Post by milesykins on 2012-09-12
Many thanks for the really helpful replies.  I had exactly the same issue, was using TP Link TF-3200 but had errors saying it was unplugged. With the information given here I got it working in no time.  I'd just like to recap on what the necessary steps for the fix actually were in case I need to reinstall Ubuntu again.

add the following lines to /etc/network/interfaces

auto eth0
iface eth0 inet dhcp

then restarting the network with, 

sudo /etc/init.d/networking restart
(or just restarting the pc but that's gonna take more time)

Does this sound like all that was needed?  I'd also used the **modprobe sundance **command but **lsmod **DID include sundance.

Had a horrible feeling that sorting this out  was going to be some complicated make file then add stuff to files all over the place kinda fix at first. Not what I'd have needed on my first ever home linux install.

Thanks again, couldn't have done it without reading this post.

---

### Post by hawaiiman on 2012-10-11
> **BkkBonanza said:**
> Almost all PCI network adapters should work out of the box without any user installed drivers. It would be very unusual if you had to do anything at all.
 
What you have above is source code files for compiling a driver it seems. 99.9% likely you don't need that at all.
 
You should just boot the linux disk and select install. It should detect and load any driver needed.
Unfortunately r8168, the driver for all realtek based 10/100/1000 nic cards as distributed by TP-Link and others isn't in the kernel, so nic won't work. The r8169 driver included in LTS kernels and all others supports only older 10/100 realtek chipsets. As the r8168 (currently r8168-032) driver supports legacy chipsets, I can't understand why it isn't in the kernel. These nics are among the most common worldwide. I'm, building a server using a second nic card and have to say, getting the ./autorun.sh to run to completion is a problem. Compiler packages and linux header packages seem to be required. BTW sudu apt-get dist-upgrade doesn't fix it. Servers frequently use a second nic, so this really needs fixing!
I am running 10.04 server,but have previously tried 12.04 server with the same frustrating result. Any guidance for my particular situation, of course, eagerly and gratefully accepted. Thanks

---


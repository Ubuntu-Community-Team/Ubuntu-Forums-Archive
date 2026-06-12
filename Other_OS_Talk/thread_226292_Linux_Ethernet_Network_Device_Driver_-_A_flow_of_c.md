---
title: "Linux Ethernet Network Device Driver - A flow of code"
date: 2006-07-31
forum: Other OS Talk
---

### Post by swamytk on 2006-07-31
Topic:
	This document talks about working of a ethernet card device driver in a bird's eyeview. This is aimed at people who are interested in understanding what is happening inside the driver. If a system administrator understands this document, he/she can understand the scope of command line (ifconfig) and device driver, so that he/she need not to break his/her head with command line for something which can only be done with kernel device driver. This document can make an developer to understand the existing network device driver to some extent. This document may motivate others to start learning kernel stuff.

Assumption:
	(a) You know that we talk here about kernel 2.4.X (not latest 2.6.X series kernel)
	(b) You know that this network device driver is a a modularized kernel module. It is assumed that it is not linked into the kernel.
	(c) The audience should have some basic "C" language and linux system administration skills.

Courtesy:
	I have learned about network device driver from the famous book (my favourite too!) Linux Device Drivers - 2nd Edition by Alessandro Rubini & Jonathan Corbet from O'reilly publication. This book has helped me in preparing this document. Thanks to Authors! This book is available under GPL license for download and hard copy of book is available in all leading book stores at reasonable cost.

Feedback:
	Your feedback is valuable since I too a newbie to kernel level stuff. This is my attempt to share my understanding with others, so that jointly we can fine tune this document, which can become a starting point for any network device driver programmer. You are welcome to mail me your suggestion to my mail id of "karuppuswamy" which is hosted in gmail dot com.

Enough with header....! Now let us kick start the exciting world of linux system internal of network device drivers. The following is the basic sequence and flow of code in a network driver. It does not talk in depth specific to hardware, but what ever explained here is common to all network device drivers.

1. Detecting Hardware Device: 
	Once a network driver is loaded into the kernel, the driver probes for the hardware device it supports (I/O ports and IRQ line). The device found are to be registered with kernel.

2. Registration with kernel: 
	Usually linux drivers register itself with kernel, once it is loaded. During the registration process it asks for its unique major/minor number. There will be a corresponding file in /dev directory with major/minor number allocated for that device (e.g.: /dev/hda - hard disk partition). But when a network driver is loaded into kernel, it does not ask for major/minor number as other drivers do. There is no "everything is a file" concept for network device (it means there is NO /dev/eth0 like file, similar to /dev/hda hard disk partition). Instead, the network driver inserts a data structure (struct net_device) for each newly detected interface into a global list of network devices. This structure describes the characteristics of the found device.

3. Filling up of net_device structure:
	Kernel takes care of some ethernet defaults through a function (ether_setup()), which fills several fields in the net_devie structure. Device specific fields are filled by this device driver.

4. Opening ("open" method) the device:
	(a) It requests and gets allocated its memory region and IRQs.
	(b) The hardware address ("MAC address" popularly known as) is copied from real hardware to net_device structure.
	(c) Transmit Queue of this device is started ("netif_start_queue") to accept packets for transmission.
	Note: Before the network device is used, it must be opened by the kernel in response to "ifconfig / ifup" command. With this command an IP address is assigned to the device and device is made up (ON). Assigning IP address is happening at OSI layer 3 (Network layer - IP), so this device driver (OSI layer 2 - MAC) has nothing to do with that. But to make this device up, IFF_UP flag of net_device structure is set. Kernel calls open method of this device to do the same.


5. Transmission of Packet ("hard_start_xmit" method):
	(a) Whenever the kernel needs to transmit a data packet, it calls the "hard_start_xmit" method to put the data on an outgoing queue.
	(b) Kernel put the data (packet) in the form of a structure called "socket buffer structure" (struct sk_buff).
	(c) Device driver does not modify this data and it does some sanity checks only. Then it transmits the data by calling highly hardware dependent routines of the device.
	Note1: The "hard_start_xmit" function is protected from concurrent calls by a spinlock (xmit_lock).
	Note2: The hardware interface (ethernet card) has limited memory for outgoing packets. When this memory is exhausted, the driver will tell the kernel ("netif_stop_queue") not to start any more transmissions until the hardware is ready to accept new data. Once the driver has stopped its queue, it must arrange to restart the queue at some point in the future, when it is again able to accept packets for transmission. To do so, it should call "netif_wake_queue" method.
	Note3: If the current system time exceeds the device's "trans_start" time (which is set while a packet is transmitted) by atleast the timeout period, the networking layer will eventually call the driver's "tx_timeout" method. That method's job is to clear up the problem and to ensure the proper completion of any transmissions that were already in progress.

6. Receiption of Packet:
	(a) When a packet is arrived at hardware, it trigges the corresponding interrupt. The interrupt handling routine of driver is called.
	(b) This routine receives a pointer to the data and its length (packet), which are already available in memory. Its responsibility is to send the packet to the upper layers of networking code.

7. Closing/Releasing/Stopping ("stop" method) the device:
	(a) It releases allocated memory and IRQs.
	(b) Trasmit Queue of this device is stopped ("netif_stop_queue") from accepting packets for transmission.
	Note: This method is called when we issue "ifdown <dev>" command.

8. Changes in Link state:
	The networking subsystem needs to know when network links go up or down, and it provides a few functions that the driver may use to convey that information. "netif_carrier_off", "netif_carrier_on" and "netif_carrier_ok" are such functions.

        --end of doc--

---


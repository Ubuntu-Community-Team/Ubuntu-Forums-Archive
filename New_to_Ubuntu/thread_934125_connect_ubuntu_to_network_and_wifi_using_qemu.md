---
title: "connect ubuntu to network and wifi using qemu?"
date: 2008-09-30
forum: New to Ubuntu
---

### Post by russian460 on 2008-09-30
Hi im using quemu to virtulise ubuntu on my laptop im trying to get it connected to the internet with wifi and a wired (tryig to get bouth working)

Now i know little about linux overall so il need a bit of help 

i have read the networking guides and understand the general concept you somehow bridge the ubuntu virtual network card to your real nic and all of the traffic goes to the ubuntu 


am i missing anything?
can i bridge my wifi card and use wifi?

my problem is how to do it exactly what commands do i use to make the bridge and where do i enter the commands? the ubuntu shell? or the cmd?

thx in advance =)

---

### Post by NESFreak on 2008-09-30
qemu probably uses a virtual (wired) network card. You should enable/config this somewhere in the qemu settings.

---

### Post by russian460 on 2008-10-01
i found something that ediscribes this but i still need a bit of help in the actual setup 

Another option is to make a vlan available through a device in the host OS. Any frames transmitted via this device will appear on a vlan in the qemu process (and thus received by another other interfaces on the vlan) and frames sent to the vlan will be received by the device.

                                    
 +-----------+                            +-------+
 |   Guest   |                            |  TAP  |
 |    OS     |                            | Device| 
 |   +---+   |                            |(qtap0)|
 |   |NIC|   |                            +---+---+
 +---+-+-+---+                                |   
       ^       +------+                   +---+-----+
       |       |      |                   | Kernel  |
       +------>+ VLAN +<-->   File    <-->+ TUN/TAP |
               |      |     Descriptor    | Driver  |
               +------+                   +---------+

  $> qemu -net nic -net tap,ifname=qtap0 ...

This works using the kernel's TUN/TAP device driver. This driver basically allows a user-space application to obtain a file descriptor which is connected to a network device. Any frames sent to the kernel over the file descriptor will be received by the device and any frames transmitted via the device will be received by the application. 


as far as i can tell this will connect my os to the network card and let me get online

---


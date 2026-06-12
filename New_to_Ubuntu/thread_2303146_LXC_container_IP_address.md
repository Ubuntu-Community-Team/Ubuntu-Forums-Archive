---
title: "LXC container IP address"
date: 2015-11-16
forum: New to Ubuntu
---

### Post by bobk48 on 2015-11-16
I install and run a new container on Ubuntu 15.10, with the ubuntu template, according to the excellent instructions here-
[www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/]("http://www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/")
and my home network does not see the IP address that is given by default, something like 10.0.3.1.
I have Googled how to set the bridged connection up so that I can access the container from my home network, 
but many of the instructions are either vague, or incomplete. It seems to me that such an elementary operation 
such as this, using the ubuntu template, should be very well documented, but I don't find that is true. 
After all, one of the primary purposes of deploying a container is to secure your computer by isolating specific
network traffic so that it only goes to the container.
Can anyone either point me to a direct, articulate, and applicable set of instructions that achieves connecting
the container through the host to my home network. 
Thanks!
Sincerely,
Robert M. Koretsky

---

### Post by sandyd on 2015-11-16
> **bobk48 said:**
> I install and run a new container on Ubuntu 15.10, with the ubuntu template, according to the excellent instructions here-
[www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/]("http://www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/")
and my home network does not see the IP address that is given by default, something like 10.0.3.1.
I have Googled how to set the bridged connection up so that I can access the container from my home network, 
but many of the instructions are either vague, or incomplete. It seems to me that such an elementary operation 
such as this, using the ubuntu template, should be very well documented, but I don't find that is true. 
After all, one of the primary purposes of deploying a container is to secure your computer by isolating specific
network traffic so that it only goes to the container.
Can anyone either point me to a direct, articulate, and applicable set of instructions that achieves connecting
the container through the host to my home network. 
Thanks!
Sincerely,
Robert M. Koretsky
You'll notice that lots of tutorials do not indicate how to do this because it is highly dependent on your home network setup.

By default, all the computers in the house are assigned an IP address from a subnet. The subnet is set in your internet gateway/router/etc.
As a result, computers only know how to access other IP addresses in the same subnet.

What you will need to do is add a route for 10.0.3.0/24 (not sure if this is the subnet you are using in LXC) so that computers on the network know that to get to IP addresses on the 10.0.3.0/24 network, they will need to pass the traffic to the computer running the LXC container.

That part is quite easy, the trouble comes with adding the routes for the subnet.

You can either
a) Add it to each computer manually
b) Add a route in the internet gateway/router/etc to route the traffic in that subnet to the computer hosting the container
c) Add an IP from 10.0.3.0/24 to each computer

Note that an easier method would be to create a network bridge with your host's ethernet card/wifi and place the LXC container on the bridge. Once the container is bridged, set the LXC container to get it's ip address from DHCP. The LXC container will get an IP from your network's DHCP server and will be in the same subnet.

Instructions on how to bridge interfaces and do the LXC bridging -> [https://wiki.debian.org/LXC/SimpleBridge](https://wiki.debian.org/LXC/SimpleBridge)

---

### Post by bobk48 on 2015-11-16
Much thanks, sandyd! The article you mention on LXC bridging was what I meant by information not clearly or completely specified. I have made several attempts using similar instructions (when I could understand what they were saying), watched several interesting YouTube videos, but none of them could be used to implement or to produce a working bridge.
I am intrigued by your suggestion b) to add something on the gateway/modem/router. I have an Actiontec PK5000, where you can configure it from a web browser. But nothing I can do, though, to my Actiontec will allow me to specify 10.0.3.1 as an IP address that will allow other computers on the network to access it. It doesn't seem as if any IPv4 address I can specify in any configuration file on the host or container will allow other nodes on the network to hookup to that address, say via ssh. I can ping the 10.0.3.1, from other places on the network, but that's about it.
FYI, and not to bash Ubuntu or LXC, but in VirtualBox you make one choice in setting up your guest, so that it has a bridged adapter, and that's it: Game Over. Also in FreeBSD and PC-BSD Jails, a very minor change as well. In Solaris Zones, same thing, very minor change. Particularly if you create the jail or zone from a .vdi or .ova file, those templates are already pre-built with the bridge DONE.

After about a week of trying to solve this problem, I'm pretty much at the same point as I started at. Trying various fixes from Google posts, posting on the lxc-users mailing list, etc.. Read sandyd's thoughtful and informative reply to my original thread, and you can see what I'm up against here- great overview, but no details. Last night I read through a very explicit and detailed, step-by-step procedure to get lxcbr0 bridged to eth0, and modify /etc/network/interfaces, lxc config files, on and on: none of it yielded a solution after many tries. Docker and Flockport offer automatic bridging solutions, and what I'm now going toward is Docker. I like how lightweight LXC is, and I liked the LXC web panel way of managing the containers! I was using the ubuntu template for my container, I've used Ubuntu Software Center to install LXC, and also alternatively this excellent tutorial source -
[www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/]("http://www.unixmen.com/setup-linux-containers-using-lxc-on-ubuntu-15-04/")
as I mentioned above. I still fail to see why such a fundamental part of container creation and use, like bridging it to your NIC, is not documented in an explicit and articulate way. When most experienced IT people or LXC users read that there are no docs, they get somewhat defensive, in my experience. Someone at lxc-users mailing list suggested that the default sub-net that all containers are put on, such as 10.0.3.1, is that way because of developer needs. I don't follow that. In other words, developers need the containers initially in a protected and secure place so that when they have been tested, then they can be unleashed via a DHCP assigned IP onto a network? I have given up on using pure LXC, and will try Docker or revert to VirtualBox. Just thought I'd put this rant on here to let other ordinary users know of my experiences with it.
Best of luck to you,
Sincerely,
Robert M. Koretsky

---


---
title: "Questions about Ubuntu 12.04 LTS Server"
date: 2012-11-25
forum: New to Ubuntu
---

### Post by zigwaldo on 2012-11-25
Good Morning,

Hopefully I'm in the right place, but figured I'd start here as to not get hazed (lol) for posting in the wrong place. I'll start by laying out the hardware, it's a dell SC1430 (tower server) with a quad-core xeon and 4gb ram, a 650gb 7200 rpm SATA drive where I store my media, a 250gb 7200 rpm SATA drive where I have Ubuntu 12.04 LTS headless running, 2 80gb 7200 rpm SAS drives mirrored as 1 VHD running windows server 2k8 r2 (don't laugh, not my first choice but I'm in the process of Server Administrator certs. for work), and 2 150gb 15000 rpm SAS drives mirrored as 1 VHD that I use for backups of my other systems, it's running dual NIC's, 1 Broadcom BCM5751 and 1 Intel 82572EI. What I'm trying to achieve is 3 virtual machines running on the 12.04 host, an Ubuntu 12.04 LTS for my media server (already have my mind made up about plex media server unless someone has a better suggestion), a Linux Mint 14 Cinnamon machine which will handle SMB and NFS shares, and a Centos 6 machine for my FTP.  DHCP and DNS are handled by my router which is flashed with DD-WRT Firmware and I have a static IP address with my cox business account. 

I've been dabbling with Linux for over a year now since my network administrator turned me onto it, but have never done a set up so involved. I've been scouring forums and google in general for about 2 weeks trying to get an idea of what I need to do to make this all work. So far I've got just about everything figured out except I'm running into one SNAFU that's hanging me up, creating the multiple bridged networks for my virtual machines (which I think I forgot to mention I'm using KVM). The way I have it figured out is I want the virtual ubuntu media server to run on eth1 which is the intel NIC, I want all other machines to run off eth0 which is the broadcom NIC. Ubuntu doesn't seem to recognize my broadcom card even though it has internet connection. How do I go about a) getting ubuntu to recognize my broadcom card and b) creating multiple bridges to the same NIC, I know how to configure a bridge but when I try to do multiple it won't let me do it. 

If anyone has any ideas on how I can accomplish this or any suggestions on the overall setup, I'm all ears! Greatly appreciate the help!

---

### Post by nwalkey on 2012-11-25
I think you can do it with bridge-utils and I believe this is how we're going to end up setting up our server (running ubuntu 12.04 server with 2 or 3 machines)

This is from here: [https://help.ubuntu.com/12.04/serverguide/network-configuration.html](https://help.ubuntu.com/12.04/serverguide/network-configuration.html)  (might be some other useful information there as well :))
 **Bridging**


         Bridging multiple interfaces is a more advanced configuration, but is very useful in multiple scenarios.         One scenario is setting up a bridge with multiple network interfaces, then using a firewall to filter traffic       between two network segments.  Another scenario is using bridge on a system with one interface to allow virtual       machines direct access to the outside network.  The following example covers the latter scenario.       
        Before configuring a bridge you will need to install the bridge-utils package.  To install the        package, in a terminal enter:       
 sudo apt-get install bridge-utils 
        Next, configure the bridge by editing /etc/network/interfaces:       
 auto lo iface lo inet loopback  auto br0 iface br0 inet static         address 192.168.0.10         network 192.168.0.0         netmask 255.255.255.0         broadcast 192.168.0.255         gateway 192.168.0.1         bridge_ports eth0         bridge_fd 9         bridge_hello 2         bridge_maxage 12         bridge_stp off 
                   Enter the appropriate values for your physical interface and network.         
       



        Now restart networking to enable the bridge interface:       
 sudo /etc/init.d/networking restart 
          The new bridge interface should now be up and running.  The brctl provides useful information         about the state of the bridge, controls which interfaces are part of the bridge, etc.  See man brctl          for more information.

---


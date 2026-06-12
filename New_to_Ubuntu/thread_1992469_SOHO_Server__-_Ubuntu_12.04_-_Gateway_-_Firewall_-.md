---
title: "SOHO Server  - Ubuntu 12.04 - Gateway - Firewall - DHCP Server"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by rubiconza on 2012-05-31
Hi guys

I've been toying with the idea of building myself a box which would do the following

[LIST]
[*]Gateway
[*]Firewall
[*]VPN Server
[*]File Server
[*]Web Server
[*]Mail Server
[/LIST]
I know there are distro's around like ClearOS, which I have tried, but I was not really satisfied with it's "feel" ... it felt bulky for some reason.

Obviously, as a beginner I want to feel empowered, as if I am learning something new, and I am going to try and share it as best I can so that other beginners could benefit from my experience (and my next to nothing experience in linux) to help them ease into the world that is ubuntu if they are like a Microsoft baby.

I decided to look towards ubuntu, I wiped Windows 7 from my PC and installed 12.04 desktop, then I went to work on the machine which I intended as my server and I started installing 12.04 on it.

So, here goes, in the order as above mentioned my steps to create my perfect box.

On the install I went for the normal regional settings and the default file system utilization.

At the point where you can select the services and servers which you want to run  I chose the following

OpenSSH

I wanted to install the packages myself and learn my way around the system

The system rebooted and I was faced CLI based login screen giving out my server name

I logged in with my admin user and the first thing I did was change into "sudo" mode, which is basically  an "administrator on steroids" account for executing certain commands.

To log into *sudo* mode do the following

Log in using your administrator account and then use the following command:

```
sudo -i
```

I entered my administrator password again and I was logged into the */root* directory

By default your primary interface card which you selected during installation will be configured to look for DHCP leases.

This is the first thing we want to change if we are going to use a fixed IP server in our environment. 

You will need to edit some files, a lot of people suggest *vi* as an editor, but I've been stuck on Norton Commander since it first made it's appearance on DOS, so I went for the linux substitute which is part of the Midnight Commander package, it's called *mcedit*

You can use other editors as well, but for me the easiest was *nano* and *mcedit*

To do your basic network configuration you can do the following

Make a copy of the **/etc/network/interfaces** file by using the following command:

```
cp /etc/network/interfaces /etc/network/interfaces.original
```

A breakup of what happened in that command is as follows

I used the copy (cp) command to make a copy of the *interfaces* file in the subdirectory *network* which resides under the *etc* directory which is in the " / " (root - top level of the filesystem) to a backup file in the same directory called *interface.original*.

I edited the file and deleted everything to change it to the following after playing around for a bit.

```
mcedit /etc/network/interfaces
```

The file looked like this:

> 
# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface (facing the Internet)
auto eth0
iface eth0 inet static
address 10.0.0.254
network 10.0.0.0
netmask 255.255.255.0
broadcast 10.0.0.255
gateway 10.0.0.2
dns-nameservers 8.8.8.8

# Secondary Network Card (facing Local Area Network - LAN)
auto eth1
iface eth1 inet static
address 192.168.0.1
network 192.168.0.0
netmask 255.255.255.0
broadcast 192.168.0.255


You can use the exact same configuration if you want, but personally I suggest in making it smaller once you have planned out your network.

In a perfect world I would slap my external facing network card in a /30 subnet so that you only have 2 usable IP's in that range, and of course you will have to make sure of your broadcast address, your network address and your default gateway when changing it.

Now your Server is on it's way to becoming a gateway

You can also now return to your workstation/desktop and use either PuTTy or ssh from your linux terminal window to access your server with the following command given that both you and the server are connected on the same network, my IP was 10.0.0.12 and the server got a lease from my router on 10.0.0.10

```
ssh masterofdisaster@10.0.0.10
```
(ssh) the application (masterofdisaster) the user (@10.0.0.10) the server

I recommend getting your **Firewall** up and running now.  Lucky for us the folks developing ubuntu made it pretty simple for us with *ufw* which stands for *uncomplicated firewall*

By default I deny everything with the following command

```
ufw default deny
```

Then I allow for SSH

```
ufw allow ssh
```

Then I turn the logging on with

```
ufw logging on
```

And now I enable the firewall

```
ufw enable
```

Now time to dish out some IP's for your internal "customers" in this case, everything connected "behind" your firewall

To get the DHCP server up and running do the following to quickly update and upgrade the system so that you have the latest packages available

```
apt-get update
```

and

```
apt-get upgrade
```

apt-get is the way we tell ubuntu to now look at the repositories on the Internet for the files we want.

After this we are going to install the *isc-dhcp-server* by using the following command

```
apt-get install isc-dhcp-server
```

Copy your **/etc/dhcp/dhcpd.conf** file to the same directory with just another name by running the following command

```
cp /etc/dhcp/dhcpd.conf /etc/dhcp/dhcpd.orignal
```

Now edit it

```
mcedit /etc/dhcp/dhcpd.conf
```

Delete everything inside the file and replace with the following example

> 
ddns-update-style none;
default-lease-time 3600;
max-lease-time 7200;
authoritative;
log-facility local7;

subnet 192.168.0.0 netmask 255.255.255.0 {
 range 192.168.0.11 192.168.0.100;
 option routers 192.168.0.1;
 option domain-name-servers 8.8.8.8;
}


Save and Quit

Now copy your /etc/default/isc-dhcp-server file to the same directory with just another name by running the following command:

```
cp /etc/default/isc-dhcp-server /etc/default/isc-dhcp-server.original
```

After this edit your /etc/default/isc-dhcp-server file and add the interface you want between then "" by running the following command:

In our case we are running the dhcp for our internal clients on the LAN port which in our case is defined as eth1

```
mcedit /etc/default/isc-dhcp-server
```

The section of the file should read like this

> INTERFACES="eth1"

Now Save and Quit

This binds the DHCP service to you NIC called eth1

Now run the following command

```
service isc-dhcp-server start
```

Now to enable your IPv4 packet forwarding by making a backup of the** /etc/sysctl.conf** file by running the following command ...

```
cp /etc/sysctl.conf /etc/sysctl.original
```

... and then by editing the file by running the following command ...

```
mcedit /etc/sysctl.conf
```

and then removing the # infront of net.ipv4.ip_forward=1 line on the file ...

> 
#net.ipv4.ip_forward=1


so that it displays as such:

> 
net.ipv4.ip_forward=1


Please note, uncommenting or to uncomment means to remove the # at the start of the line

Now Save and Quit

Now run the following command

```
sysctl -w net.ipv4.ip_forward=1
```

Now you will need to allow iptables rules for NAT to work at statup

Make a copy of the original into the same directory just with another name by running the following command:

```
cp /etc/rc.local /etc/rc.local.original
```

Now edit the file by running the following command:

```
mcedit /etc/rc.local
```

Enter the following commands just before the exit 0 line of the file

> 
/sbin/iptables -P FORWARD ACCEPT
/sbin/iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE


Now Save and Quit

Now run the following commands

```

iptables -P FORWARD ACCEPT
sudo iptables --table nat -A POSTROUTING -o eth0 -j MASQUERADE

```

Please note that this is a very basic setup, and I am not even sure if this is the best way to do it, but it worked for me, and maybe it can help you get started.

I'll do some more investigation into the rest of the server setup and I will ask around for advice from the community but I hope to get back to you soon with a workable, and fairly safe small office/home (SOHO) server solution

---

### Post by dougcumiskey123 on 2012-06-02
I read your heading with interest as I am looking to do something similar myself, however I am to much of a (Unbuntu 12.04) novice to tackle such a project yet.

In the past I have used an old desktop in XP to act as a internet/printer server via a ethernet switch for 2 other computers running Unbuntu, now I am ready to go one step further and have Unbuntu running on the old desktop but as yet have not found a way of getting it to share with the 2 other machines also running unbuntu.

Regards and good luck.

---

### Post by Muk on 2012-12-30
these are great instructions :D

though i am having some trouble getting the actual dhcp to work.

i tried connecting to the server with my win 7 via lan but am not getting any ip's for my laptop. not sure what i am doing wrong.

---

### Post by crashdogy on 2013-03-15
> **Muk said:**
> these are great instructions :D

though i am having some trouble getting the actual dhcp to work.

i tried connecting to the server with my win 7 via lan but am not getting any ip's for my laptop. not sure what i am doing wrong.

Total life saver works thank you

---


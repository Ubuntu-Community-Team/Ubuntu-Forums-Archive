---
title: "How to : OpenVZ Ubuntu Host"
date: 2007-11-19
forum: Outdated Tutorials &amp; Tips
---

### Post by bodhi.zazen on 2007-11-19
[size=4]**[center]Introduction[/center][/size]**

[color=green]OK, I think it is finished now. Please report any problems[/color]

[size=2]**Contents**[/size]

_Post _1 : Introduction

_Post 2_ : Install OpenVZ

_Post 3_ : Post-install configuration
[indent]**Basic network options NAT & Bridge**[/indent]

_Post 4_ : Running OpenVZ ~ AKA a walkthrough

_Post 5_ : Fixes / Tools
[indent]**How to mount a NFS share on a VE**
**Install VMWare server**
**Install VirtualBox**
**Install a kernel in the VE**[/indent]

_Post 6_ : Digital Blasphemy ~ How to forward X

_Post 7_ : How to make OS templates.

_ Attachments_ : I will attach a link to my newest Ubuntu template.:

[ubnuntu-7.10-i386-minimal](http://cafelinux.org/Downloads/bodhi.zazen/OpenVZ/)

[list][*]Save the template to /vz/template/cache/
[*]This template uses sys V (rather then upstart).
[*]I had problems with networking on this machine, so I restart the network in /etc/rc.local[/list]

--------------------------------------------------------------

OpenVZ is not true virtualization, it more akin to a sophisticated chroot. Open VZ is ideal for a server environment and the guest (templates) are minimal.

_Terminology_:

The host OS is often referred to as the "Node"

The guest OS is referred to as a "VE" AKA Virtual Environment.

_What to expect_ : VE are very small. For example, my Ubuntu-7.10 template is 37 Mb. Thus you can dedicate one VE to a single task with low overhead. For example, rather then running a "mega server" with with several instances of apache and a FTP server you can run a dedicated VE for each instance of apache/web site or a dedicated FTP server. This can potentially enhance security as each server is independent and if you are cracked, the cracker has access to a very limited resources (a 37 Mb version of Ubuntu does not have as  many tools available to crackers).

VE templates are pre-packaged machines and configuration files stored in a .tar.gz . To install a machine you unpack a template (using vzctl). You can deploy multiple cloned machines very rapidly.

*If you want to run X be prepared to install it or convert a physical installation*

[http://www.debianhelp.co.uk/openvz.htm](http://www.debianhelp.co.uk/openvz.htm)
[How to forge : OpenVZ On Debian Etch For Webservers](http://www.howtoforge.com/debian_etch_openvz)

Advantages:[list=number][*] Guests (VE) utilize your hardware directly.
[*] Speed.
[*] It is very easy to convert a hard drive install to a virtual machine.
[*] Guests are very easy to make / install.[/list]

Disadvantages:[list=number][*]There is NO GUI to configure or run your guests.
[*] OpenVZ will not run windows or FreeBSD.
[*] OpenVZ has not been ported to Ubuntu. Development has been most robust on rpm systems (Centos), although there is a Debian repo and I am hoping development is underway for Ubuntu.
[*] You have compile your own kernel (although a binary is available, see below).[/list]

If you would like to try OpenVZ, I highly recommend taking one of the live CD's for a spin (you do not need to reboot if you already have VMWare installed, just boot the iso and you can run VZ guests within your VMWare host).

[OpenVZ Live CD download  page](http://download.openvz.org/livecd/)

[font=times][size=4][i]As always, have fun,[/size][/font]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color][/i]

---

### Post by bodhi.zazen on 2007-11-19
[center]**[size=4]Install Openvz[/size]**[/center]

You have two options:[list=number][*]Download the OpenVZ patch and recompile your kernel[*]Install a pre-compiled binay[/list]

I did not have much success with compiling my own kernel, but here is a link if you would like to try it :

[http://wiki.openvz.org/Installation_on_Debian](http://wiki.openvz.org/Installation_on_Debian)

Also on that link is information on how to install the OpenVZ kernel from the Debian Repos's. The Debian kernel works just fine, but it was built without drivers (no sound, no nvidia).

I advise you install from here :

[http://debian.systs.org/howto/install-openvz-on-debian-etch/](http://debian.systs.org/howto/install-openvz-on-debian-etch/)

I had the best success with the "forzza" kernel

> root@Gutsy:~# uname -r
2.6.18-fza-5-686

Installation is quite easy.

Kernel source : [http://debian.systs.org/debian/pool/openvz/l/](http://debian.systs.org/debian/pool/openvz/l/)

[indent]_Note_: Be sure to use the **"fza" kernel appropriate to your cpu**. For me this was the 686 kernel : [http://debian.systs.org/debian/pool/openvz/l/linux-source-2.6.18-fza-5-686/](http://debian.systs.org/debian/pool/openvz/l/linux-source-2.6.18-fza-5-686/)[/indent]

Open a terminal and :

```
# I like to keep such things in my home directory under "src"
# You can choose an alternate location if you like

mkdir -P src/openvz
cd src/openvz
wget linux-image-2.6.18-fza-5-686_028stab048.1_i386.deb
wget linux-headers-2.6.18-fza-5-686_028stab048.1_i386.deb
sudo dpkg -i linux-image-2.6.18-fza-5-686_028stab048.1_i386.deb
sudo dpkg -i linux-headers-2.6.18-fza-5-686_028stab048.1_i386.deb

# Update grub to be sure your new kernel is included in the menu
sudo update-grub
```

**REBOOT** and select the new kernel, on my system :

>  Ubuntu 7.10, kernel 2.6.18-fza-5-68

**YOU CAN NOT COMPLETE THE INSTALLATION IF YOU ARE NOT RUNNING AN OPENVZ KERNEL**

edit, by any means, your sources adding the OpenVZ repository. I use vim.

```
sudo vim /etc/apt/sources.list
```

Add this repo:

> #OpenVZ
deb [http://debian.systs.org/](http://debian.systs.org/) etch openvz 
# deb [http://download.openvz.org/debian/](http://download.openvz.org/debian/) etch openv

Install OpenVZ:

```
sudo apt-get update
sudo apt-get install vzctl vzquota vzdump vzctl-ostmpl-debian
```

---

### Post by bodhi.zazen on 2007-11-19
[center][size=4]**Post install configuration[/center]**[/size]

1. For compatibility, make a link :

```
sudo ln -s /var/lib/vz /vz
```
 [list][*]OpenVZ on Centos uses /vz as the default directory[/list]

[size=4]Networking[/size]


1.  If you have a **public IP** (ie direct connection to internet) directly configure your IP address with vzctrl :

sudo vzctrl set <#VE> --ip <ip_address> --hostname <hostname> --nameserver <IP> --save
[list][*]Those are doubble - - in --ip --hostname --nameserver amd --save
[*]<#VE> = VE # ie 101
{*}<hostname> = your desired VE hostname
[*]<IP> i= IP address of your nameserver[/list]

Example:

```
sudo vzctrl 101 --ip 111.222.3.4 --hostname MyServer --nameserver xxx.yyy.z.z --save
```




2. If you use a **Private IP**, ie router, you will need to ues **either** NAT or bridge to allow your VE to access the internet.

++++++++++++++++++++

**NAT**

There is a "bug" in procps : 

[https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537)

It is no so much a bug as a change in the syntax for /etc/sysctl.conf to enable NAT forwarding.

This is the configuration I use :

File /etc/sysctl.conf:

>  # /etc/sysctl.conf - Configuration file for setting system variables
# See sysctl.conf (5) for information.
#

#kernel.domainname = example.com
#net/ipv4/icmp_echo_ignore_broadcasts=1

# the following stops low-level messages on console
kernel.printk = 4 4 1 7

# enable /proc/$pid/maps privacy so that memory relocations are not
# visible to other users.
kernel.maps_protect = 1

##############################################################3
# Functions previously found in netbase
#

# Uncomment the next line to enable Spoof protection (reverse-path filter)
net.ipv4.conf.default.rp_filter=1

# Uncomment the next line to enable TCP/IP SYN cookies
#net.ipv4.tcp_syncookies=1

# Uncomment the next line to enable packet forwarding for IPv4
# This line did not work, see bug below
# net.ipv4.conf.default.forwarding=1


# Uncomment the next line to enable packet forwarding for IPv6
#net.ipv6.conf.default.forwarding=1

#-- OpenVZ begin --#

# On Hardware Node we generally need
# packet forwarding enabled and proxy arp disabled
# Added the next line from [https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537](https://bugs.launchpad.net/ubuntu/+source/procps/+bug/84537)
**net.ipv4.conf.all.forwarding=1** # <-- Added to enable NAT 

net.ipv4.ip_forward = 1 # <-- This line enables NAT forwarding
net.ipv4.conf.default.proxy_arp = 0

# Enables source route verification
# Enabled above
# net.ipv4.conf.all.rp_filter = 1

# Enables the magic-sysrq key
kernel.sysrq = 1

# TCP Explict Congestion Notification
#net.ipv4.tcp_ecn = 0

# we do not want all our interfaces to send redirects
net.ipv4.conf.default.send_redirects = 1
net.ipv4.conf.all.send_redirects = 0

#-- OpenVZ end --

To see if NAT is enabled enter this command (you should see a the number "1" :

```

bodhi@GutsyVZ:~$ cat /proc/sys/net/ipv4/ip_forward
1
```

Enable NAT with :

```
iptables -t nat -A POSTROUTING -s src_net -o eth0 -j SNAT --to ip_address
```

src_net = range of guest ip addresses (ie 10.0.0.0/8 )
--to ip_address = ip address of your host OS

Example :

> iptables -t nat -A POSTROUTING -s 10.0.0.0/8 -o eth0 -j SNAT --to 192.168.1.25

[http://wiki.openvz.org/Using_NAT_for_VE_with_private_IPs](http://wiki.openvz.org/Using_NAT_for_VE_with_private_IPs)

++++++++++++++++++++

**Bridge**

To bridge my network card.

Install bridge utilities :

```
 apt-get install bridge-utils
```

Bridge your network card :

[color=red]**During these steps you will temporarily lose your Internet connection**[/color]

_Note_: I use eth0 as my network card, you may need to substitute your card (list your card with ifconfig). Also I use DHCP to assign IP addresses and again you will need to adapt if you use a static IP (for host or guest).

Edit /etc/network/interfaces changing it to this :

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
# Use these settings for NAT
# auto eth0
# iface eth0 inet dhcp

# Bridge
#Use these settings for Bridging
# Bridging can be used with both QEMU or VirtualBox
brctl addbr br0
auto br0
iface br0 inet dhcp
bridge_ports eth0

Restart your network 

```
sudo /etc/init.d/network restart
```

You will temporarily loose your network, it will come back momentarily ...

list your interfaces

```
sudo ifconfig
```

You should see both eth0 and br0


You should also have Internet access restored on the host.

Configure your guest. Again I am using 101 in this example, substitute your VE # as necessary.

```
sudo vzctl set 101 --netif_add eth0 --save

# The VE must be running to add the interface to the bridge
sudo  brctl addif br0 veth101.0
sudo vzctl exec 101 dhclient eth0
```

You should now have internet access on your guest.

You can download a script to do this automatically (see the OpenVZ link below "Using_private_IPs_for_Hardware_Nodes")


[center][size=4]**Firewalls : You must configure your firewall on both host and guest.**[/center][/size]


**NAT**

Here is a sample iptables :

> # Generated by iptables-save v1.3.5 on Sat Nov 17 17:13:41 2007
*nat
:PREROUTING ACCEPT [8:672]
:POSTROUTING ACCEPT [8:576]
:OUTPUT ACCEPT [6:408]
-A POSTROUTING -s 10.0.0.0/255.255.255.0 -o eth0 -j SNAT --to-source **192.168.1.25 #<---CHANGE THIS TO YOUR HOST IP** 
COMMIT
# Completed on Sat Nov 17 17:13:41 2007
# Generated by iptables-save v1.3.5 on Sat Nov 17 17:13:41 2007
*mangle
:PREROUTING ACCEPT [432:83374]
:INPUT ACCEPT [262:69094]
:FORWARD ACCEPT [170:14280]
:OUTPUT ACCEPT [282:22203]
:POSTROUTING ACCEPT [468:39573]
COMMIT
# Completed on Sat Nov 17 17:13:41 2007
# Generated by iptables-save v1.3.5 on Sat Nov 17 17:13:41 2007
*filter
:INPUT ACCEPT [0:0]
:FORWARD ACCEPT [0:0]
:OUTPUT ACCEPT [290:22763]
:RH-Firewall-1-INPUT - [0:0]
-A INPUT -j RH-Firewall-1-INPUT 
-A FORWARD -j RH-Firewall-1-INPUT 
-A RH-Firewall-1-INPUT -i lo -j ACCEPT 
-A RH-Firewall-1-INPUT -p icmp -m icmp --icmp-type any -j ACCEPT 
-A RH-Firewall-1-INPUT -p esp -j ACCEPT 
-A RH-Firewall-1-INPUT -p ah -j ACCEPT 
-A RH-Firewall-1-INPUT -d 224.0.0.251 -p udp -m udp --dport 5353 -j ACCEPT 
-A RH-Firewall-1-INPUT -p udp -m udp --dport 631 -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m tcp --dport 631 -j ACCEPT 
-A RH-Firewall-1-INPUT -m state --state RELATED,ESTABLISHED -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 21 -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 2049 -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 22 -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 443 -j ACCEPT 
-A RH-Firewall-1-INPUT -p tcp -m state --state NEW -m tcp --dport 80 -j ACCEPT 
-A RH-Firewall-1-INPUT -p udp -m state --state NEW -m udp --dport 53 -j ACCEPT 
-A RH-Firewall-1-INPUT -j REJECT --reject-with icmp-host-prohibited 
COMMIT
# Completed on Sat Nov 17 17:13:41 2007


Save this as a file in /home.

Load it with:
```
sudo iptables-restore < /path_to_file
```

This will not be permanent and will be undone when you reboot. To make it stick```
iptables-save
```


[size=2]**Firestarter**[/size]

used primarily with a bridge

**Host** :

In Preferences go to Network Settings

1. Under **Internet connected network device**

Detected Device(s) -> Select "Unknown device (br0) form the pull down menu..

2. Under **Local network connected device**

Again, Detected Device(s) -> Select "Unknown device (br0) form the pull down menu..

Now tic off the "Enable internet connection sharing".

**Guest**: Install firestarter as you would normally or use IPTables.


_References_ :

[Virtualbox How-to : Bridge network card](http://doc.gwos.org/doku.php/doc:office:virtualbox#bridging_your_network_card)

[OpenVZ wiki how to bridge network](http://wiki.openvz.org/Using_private_IPs_for_Hardware_Nodes)

---

### Post by bodhi.zazen on 2007-11-19
[center]**[size=4]Running OpenVZ[/center]**[/size]

A guest is referred to as a VE. The machines are downloaded as "os templates" and started from the command line.

Example : 

In this example I will use the [Pre-created Ubuntu (i386) template](http://download.openvz.org/template/precreated/ubuntu-7.10-i386-minimal.tar.gz). You can download additional guest templates from here 

[http://openvz.org/download/template/cache/](http://openvz.org/download/template/cache/)

FYI: Link to my template : [ubuntu-7.10-i386-minimal.tar.gz](http://cafelinux.org/Downloads/bodhi.zazen/OpenVZ/) "ubuntu-7.10-i386-minimal.tar.gz" in Community submitted templates (size = 45 Mb was submitted by me :)

Direct link : [http://download.openvz.org/template/precreated/contrib/ubuntu-7.10-i386-minimal.tar.gz](http://download.openvz.org/template/precreated/contrib/ubuntu-7.10-i386-minimal.tar.gz) [color=blue]<- This one is the one I made (in the OpenVZ Community Submitted Templates)[/color]

You can make your own, I have used the [Debian Template](http://wiki.openvz.org/Debian_template_creation) although there is now an [Ubuntu Template](http://wiki.openvz.org/Ubuntu_Gutsy_template_creation) as well (I advise you use the Ubuntu Template instructions, I will work through them as well and the wiki can be updated). [Additional templates](http://wiki.openvz.org/Category:Templates) are also available.

[color=red]**If you use one of the Ubuntu 7-10 templates, see the "fixes" section as each as a "small" bug.**[/color]

Save the os templates in : /vz/template/cache/

_*Note_: It is easier to manage guests as root.*```
sudo -i
```

The utility to manage VE (guests) is ***vzctl***

The general format is 

vzctrl <command> <VE #> <options>

Lets take a walk through :


> **[COLOR="Blue"]# Create a new VE :[/COLOR]**
root@GutsyVZ:~# vzctl create 201 --ostemplate ubuntu-7.10-i386-minimal
Creating VE private area (ubuntu-7.10-i386-minimal)
Performing postcreate actions
VE private area was created

**[COLOR="Blue"]# Setup ~ Add a virtual eth0, add nameserver, add hostname[/COLOR]**
root@GutsyVZ:~# vzctl set 201  --netif_add eth0 --nameserver 192.168.1.1 --hostname Gutsy --save
Saved parameters for VE 201

**[COLOR="Blue"]# List all VE[/COLOR]**
root@GutsyVZ:~# vzlist -a
      VEID      NPROC STATUS  IP_ADDR         HOSTNAME                        
       101          - stopped 10.1.1.10       Debian                          
       201          - stopped -               Gutsy                           

**[COLOR="Navy"]# Start the VE[/COLOR]**
root@GutsyVZ:~# vzctl start 201
Starting VE ...
VE is mounted
Setting CPU units: 1000
Configure meminfo: 49152
Set hostname: Gutsy
File resolv.conf was modified
Configure veth devices: veth201.0 
VE start in progress...

[B][COLOR="Blue"]#Add the virtual ethernet card to your bridge
# This can not be done if the VE is not running[/COLOR][/B]

root@GutsyVZ:~# brctl addif br0 veth201.0

**[COLOR="Blue"]#configure VE virtual ethernet card with dhcp[/COLOR]**
root@GutsyVZ:~# vzctl exec 201 dhclient eth0
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:18:51:3f:a3:63
Sending on   LPF/eth0/00:18:51:3f:a3:63
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPOFFER from 192.168.1.5 [color=blue]<- Note offer from Host IP[/color]
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.5
bound to 192.168.1.9 -- renewal in 37881 seconds.

[B][COLOR="Blue"]# Demonstration of connection with ping
# Ping VE[/COLOR][/B]
root@GutsyVZ:~# ping 192.168.1.9
PING 192.168.1.9 (192.168.1.9) 56(84) bytes of data.
64 bytes from 192.168.1.9: icmp_seq=1 ttl=64 time=0.808 ms
64 bytes from 192.168.1.9: icmp_seq=2 ttl=64 time=0.069 ms

--- 192.168.1.9 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1000ms
rtt min/avg/max/mdev = 0.069/0.438/0.808/0.370 ms

# Ping google from VE
root@GutsyVZ:~# vzctl exec 201 ping google.com
PING google.com (72.14.207.99) 56(84) bytes of data.
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=1 ttl=240 time=133 ms
64 bytes from eh-in-f99.google.com (72.14.207.99): icmp_seq=2 ttl=240 time=132 ms

**[COLOR="Blue"]# Enter VE[/COLOR]**
root@GutsyVZ:~# vzctl enter 201
entered into VE 201
root@Gutsy:/#

[color=blue]You are not logged into the VE as root. You can do what you will (This is a command line interface).[/color]

**[COLOR="Blue"]# Exit VE[/COLOR]**
root@Gutsy:/# exit
logout
exited from VE 201

**[COLOR="DarkOrange"]# Stop VE[/COLOR]**
root@GutsyVZ:~# vzctl stop 201
Stopping VE ...
VE was stopped
VE is unmounted
root@GutsyVZ:~#

**[COLOR="Red"]# Delete VE ~ There is no "undo"[/COLOR]**
root@GutsyVZ:~# vzctl destroy 201
Destroying VE private area: /var/lib/vz/private/201
VE private area was destroyed
root@GutsyVZ:~

To save a VE , stop the VE and use tar :

```
sudo vzctl stop 201
cd /vz/private/201
sudo tar -zcf /vz/template/cache/<new_name>.tar.gz .
```

[list][*]Don't forget the . at the end
[*]Re-name the VE what you will (Change <new_name> to something like Ubuntu-7.10-server.tar.gz[/list]

---

### Post by bodhi.zazen on 2007-11-19
[size=4]**[center]Fix VE[/size]**[/center]

[size=2]**Upstart is incompatible with previous versions of OpenVE (this has been fixed).**[/size]

One problem is that the Ubuntu upstart boot process is incompatible with OpenVZ (vzctrl to be exact). **This has apparently been fixed as of vzctl-3.0.19 or later**.

_Edit ~ UPDATE_: If you followed this how-to you installed *vzctl version 3.0.18-1dso1* you will need to install sysvinit on your Ubuntu VE (this will remove upstart).

If you are running an earlier version of vzctl, the" easy fix" is to install sysvinit in your VE template. Either chroot or use vzctl enter <VE#> to enter your VE,

[color=red]**DO NOT RUN THIS COMMAND ON YOUR HOST[/color]**

```
sudo apt-get install sysvinit
```

Alternate solutions would be to install from source, attempt to use Alien (to install the zvctl .rpm), or wait for an updated .deb.

_Note_: I have done this already in the Ubuntu-7.10 template I submitted (size = 37 Mb) and in "Community". I have not noticed any problems ...


=============================


[size=2]**Problem with ssh**[/size]

To ssh into the VE you need to first set a root password (or create a non-root user).

```
vzctl exec 101 passwd
```


+++++++++++++++++++

[center][size=4]**Useful "how-to's"**[/size][/center]

[size=2]**Mount a nfs share to a VE[/size]**

1. Mount the nfs share on the host, in this example I will assume the nfs share is mounted at /media/nfs

2. Use mount --bind

```
sudo mkdir -P /vz/root/media/nfs
mount --bind /media/nfs /vz/root/media/nfs
```


[size=2]**Install VMWare server[/size]**

The "fza" kernel was compiled on gxx 4.1. Download and install gcc from the Feisty repository, install VMWare, then restore the gutsy gcc with :

```
sudo apt-get upgrade #you will get error messages here
sudo apt-get install -f #This will correct them
``` 


[size=2]**Install VirtualBox[/size]**

The open source edition installs, but no kernel module is available. Use the "Personal Use and Evaluation License (PUEL)." edition.


[size=2]**Install a kernel in the VE[/size]**

If for some reason you wish to install a kernel in the VE :

Add the following file  cat /etc/kernel-img.conf

> do_symlinks = yes
relative_links = yes
do_bootloader = no
do_bootfloppy = no
do_initrd = yes
link_in_boot = no
postinst_hook = /bin/true
postrm_hook   = /bin/true

[color=darkred]Thank you to rednul from the Montana LUG for that fix[/color]

---

### Post by bodhi.zazen on 2007-11-19
[center][size=4]**Digital Blasphemy**[/size]
[size=2]How to forward X[/size][/center]

**************************
[size=2]**First we must install X in the VE[/size]**

[indent]* Installing X will obviously be distro dependent[/indent]

1. Enable your Repositories.

[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

2. Install a window manager. I advise Fluxbox or Openbox, although in this post I will use XFCE as an example (XFCE is very easy to use).

Ubuntu : [https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

Debian : [http://wiki.debian.org/DebianXFCE](http://wiki.debian.org/DebianXFCE)

Fedora : ```
yum groupinstall 'X Window System'
yum groupinstall XFCE
```

+++++++++++++++++++++

[size=2]**Xephyr**[/size]

1. Install Xephyr 

```
sudo apt-get install xserver-xephyr
```

2. Start Xephyr

```
Xephyr -ac -screen 1280x1024 2> /dev/null  :1 &
```
[list][*]The ":1" = your display (displays are numbered starting with 0)
[*]-ac =  disable access control restrictions= allow you to forward X
[*]-screen 1280x1024 = screen size
[*]2> /dev/unll redirects error messages[/list]

3. Set your display (for X)

```
DISPLAY=:1.0
```

4. ssh into the VE

```
ssh -XfC -c blowfish 10.0.0.1 xfce4-session
```
[list][*]-X = forward X
[*]-f = puts your ssh session into the background
[*]-C = use compression -c blowfish = use blowfish (I am told this is the fastest)
[*]Substitute your window manager for "xfce4-session[/list] 

5. Now you should have a terminal within a window on the host. 


[[img]http://cafelinux.org/OptickleArt/albums/userpics/normal_Xephyr.png[/img]](http://cafelinux.org/OptickleArt/albums/userpics/Xephyr.png)

(It's big)

+++++++++++++++++++++++

**[size=2]Direct from a terminal in X or console**[/size]

1. Enable your system to start a new X session from with a X session (otherwise you need to run these commands from the Console [at Ctrl-Alt-F1])

edit by any means /etc/X11/Xwrapper.config

```
sudo nano /etc/X11/Xwrapper.config
```

Change:> allowed_users=console
To:```
allowed_users=anybody
```

[Documentation](http://www.fifi.org/cgi-bin/man2html/usr/share/man/man5/Xwrapper.config.5.gz)

See also : [http://ubuntuforums.org/showthread.php?t=271674](http://ubuntuforums.org/showthread.php?t=271674)

2. Start a (new) X session:

```
xinit -ssh -XC -c blowfish 10.0.0.1 -- :1
```

3. Log in and start a new XFCE session as above :)

4. You "old" or host X session is at ***Ctrl-Alt-F7*** and the "new" or VE session at ***Ctrl-Alt-F8***

~ Enjoy

---

### Post by bodhi.zazen on 2007-11-19
[size=4][center]**How-to VE Templates**[/size][/center]

In general the OpenVZ wiki is the best source of information. This post is limited to comments on the wiki.

[size=2]**Build you own Ubuntu VE**[/size]

[OpenVZ wiki : Ubuntu Gutsy template creation](http://wiki.openvz.org/Ubuntu_Gutsy_template_creation)
[OpenVZ wiki : Ubuntu template (6.06 AKA LTS)](http://wiki.openvz.org/Ubuntu_template)

* I went through the Gutsy template creation and it works well. I encountered only two small problems:
[list=number][*]The new vzctl is not yet available for Debian/Ubuntu. Install sysvinit [color=red]IN THE VE NOT THE HOST[/color]:```
apt-get install sysvinit
```[indent]Alternately you could try installing a newer version of vzctl from source or with alien[/indent]
[*]The network does not start when booting the VE. Add > /etc/init.d/networking restart to /etc/rc/local [color=red]IN THE VE[/color] [/list]

=======================

[size=2]**How to convert a physical installation -> VE**[/size]

Converting a physical installation is very easy and, IMO, is a major advantage of OpenVZ. This method works with live CD as well.

[http://wiki.openvz.org/Physical_to_VE](http://wiki.openvz.org/Physical_to_VE)

1. Don't forget to install the ssh server.```
sudo apt-get install openssh-server
```

---

### Post by r3ddr on 2007-12-26
> **bodhi.zazen said:**
> [center]**[size=4]Running OpenVZ[/center]**[/size]

To save a VE , stop the VE and use tar :

```
sudo vzctl stop 201
cd /vz/private/201
sudo tar -zcf /vz/template/cache/<new_name>.tar.gz .
```

[list][*]Don't forget the . at the end
[*]Re-name the VE what you will (Change <new_name> to something like Ubuntu-7.10-server.tar.gz[/list]

using vzdump is a better way to save your VE data :KS

```
       vzdump is an utility to make consistent snapshots of running OpenVZ
       VEs. It basically creates a tar archive of the VE private area, which
       also includes the VE configuration files.

       There are several ways to provide consistency:

       - stop the VE during backup (very long downtime)

       - use rsync and suspend/resume (minimal downtime).

       - use LVM2 (no downtime, but needs LVM2 and 500m free space on the corâ
       responding volume group to create the LVM snapshot)

```

plus they recommend you should **not** access VE data from the Host (outside VE) :!:

---

### Post by bodhi.zazen on 2007-12-26
Thanks for the information r3ddr.

I will update/add in this information.

---

### Post by edmnc on 2007-12-30
> **bodhi.zazen said:**
> 
OK, I think it is finished now. Please report any problems


I'm having trouble booting into OpenVZ kernel. I do have a bit complicated setup: 64bit Ubuntu on Intel Xeon, RAID1 + LVM. The problem seems to be that initrd made by OVZ install does not include the necessary drivers for LVM. Even if I manually load LVM in Buisybox (like described in this bug: [https://bugs.launchpad.net/ubuntu/+bug/147216](https://bugs.launchpad.net/ubuntu/+bug/147216)) the network doesnt work in the booted HW node (network cards are not found -- probably a driver problem).

Any ideas where I could go with this? One option I guess would be to not put the root (/) on LVM. Maybe this would also magically solve missing NICs. Although I would prefer building a proper initrd, but update-initramfs doesn't seem to do that :(

---

### Post by incubus on 2008-01-22
Hello there.

I'm very excited about trying OpenVZ, but I'm waiting for the availability of a Kernel in the repositories.  I was looking around and I found this page:

[http://wiki.openvz.org/Ubuntu_Hardy_TODO](http://wiki.openvz.org/Ubuntu_Hardy_TODO)

Anybody knows if there's other places where I can follow the development status?  I couldn't find much on launchpad.  I think it would be nice to have a few people testing it.

incubus

---

### Post by bodhi.zazen on 2008-01-28
Moved to Tips and Tutorials.

---

### Post by rampras on 2008-01-29
Thanks for the excellent post. I was able to setup VZ in a few mins thanks to you.

I want to run multiple VE on my ubuntu box .. but I am running into problem with bridge (I created two bridges to use with two VEs. Once bridge is able to get dhcp IP, but the other is not able to).

Could you post some tips on creating and running multiple VEs ?

- Ram

---

### Post by bodhi.zazen on 2008-01-30
> **rampras said:**
> Thanks for the excellent post. I was able to setup VZ in a few mins thanks to you.

I want to run multiple VE on my ubuntu box .. but I am running into problem with bridge (I created two bridges to use with two VEs. Once bridge is able to get dhcp IP, but the other is not able to).

Could you post some tips on creating and running multiple VEs ?

- Ram

OK, scroll up and set up your bridge ....

Now, assuming your bridge is up, let me give you an example :

1. Create two new VE:

```
root@GutsyVZ:~ #vzctl create 401 --ostemplate debian-4.0-i386-minimal
Creating VE private area (debian-4.0-i386-minimal)
Performing postcreate actions
VE private area was created

root@GutsyVZ:~ #vzctl create 402 --ostemplate debian-4.0-i386-minimal
Creating VE private area (debian-4.0-i386-minimal)
Performing postcreate actions
VE private area was created
```


2. Create a virtual eth0 on each VE :

```
root@GutsyVZ:~vzctl set 401 --netif_add eth0 --hostname Debian1 --nameserver 19--2.1.1.1 --save
Saved parameters for VE 401

root@GutsyVZ:~vzctl set 402 --netif_add eth0 --hostname Debian2 --nameserver 19--2.1.1.1 --save
Saved parameters for VE 402
```


3. Start your VE :
[indent]NOTE THE NAME OF THE veth (bold)[/indent]

```
root@GutsyVZ:~ #vzctl start 401
Starting VE ...
VE is mounted
Setting CPU units: 1000
Configure meminfo: 49152
**Configure veth devices: veth401.0**
VE start in progress...

root@GutsyVZ:~ #vzctl start 402
Starting VE ...
VE is mounted
Setting CPU units: 1000
Configure meminfo: 49152
**Configure veth devices: veth402.0** 
VE start in progress...
```


4. Add the veth to your bridge :

```
root@GutsyVZ:~brctl addif br0 **veth401.0**
root@GutsyVZ:~ #brctl addif br0 **veth402.0**
```


5. Obtain an ip via dhclient

```
root@GutsyVZ:~vzctl exec 401 dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:51:93:2b:dc
Sending on   LPF/eth0/00:18:51:93:2b:dc
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPOFFER from 192.168.1.5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.5
bound to 192.168.1.9 -- renewal in 39643 seconds.

root@GutsyVZ:~ #vzctl exec 402 dhclient eth0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:18:51:bb:8a:b9
Sending on   LPF/eth0/00:18:51:bb:8a:b9
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 192.168.1.5
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.5
bound to 192.168.1.10 -- renewal in 40010 seconds.
```


6. Test internet connection with a ping :

```
root@GutsyVZ:~ #vzctl exec 401 ping -c 4 www.google.com
PING www.l.google.com (209.85.173.103) 56(84) bytes of data.
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=1 ttl=241 time=78.7 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=2 ttl=241 time=78.5 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=3 ttl=241 time=79.5 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=4 ttl=241 time=79.3 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3000ms
rtt min/avg/max/mdev = 78.563/79.070/79.545/0.454 ms


root@GutsyVZ:~ #vzctl exec 402 ping -c 4 www.google.com
PING www.l.google.com (209.85.173.103) 56(84) bytes of data.
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=1 ttl=241 time=79.7 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=2 ttl=241 time=79.2 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=3 ttl=241 time=80.2 ms
64 bytes from mh-in-f103.google.com (209.85.173.103): icmp_seq=4 ttl=241 time=78.3 ms

--- www.l.google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3001ms
rtt min/avg/max/mdev = 78.303/79.395/80.285/0.731 ms
```

HTH

[font=times][size=4][i]Peace be with you,[/size][/font]

[img]http://img381.imageshack.us/img381/4226/xubuntulogo2small0lj.png[/img][size=4] [color=navy][font=times]bodhi.[/color][color=darkgray]zazen[/font][/size][/color][/i]

---

### Post by incredibile10 on 2008-10-04
Hi,
thanks for how to, is excellent :)

but I have a problem with **xorg** inside the VE...:(

output the command **startx** inside the VE is:

```
xauth:  creating new authority file //.Xauthority
xauth:  creating new authority file //.Xauthority

X: warning; process set to priority -1 instead of requested priority 0

This is a pre-release version of the X server from The X.Org Foundation.
It is not supported in any way.
Bugs may be filed in the bugzilla at http://bugs.freedesktop.org/.
Select the "xorg" product for bugs you find in this release.
Before reporting bugs in pre-release versions please check the
latest version in the X.Org Foundation git repository.
See http://wiki.x.org/wiki/GitPage for git access instructions.

X.Org X Server 1.4.0.90
Release Date: 5 September 2007
X Protocol Version 11, Revision 0
Build Operating System: Linux Ubuntu (xorg-server 2:1.4.1~git20080131-1ubuntu9.2)
Current Operating System: Linux test1 2.6.24-19-openvz #1 SMP Thu Aug 21 04:18:17 UTC 2008 i686
Build Date: 13 June 2008  01:08:21AM
 
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  4 16:59:04 2008
(==) Using config file: "/etc/X11/xorg.conf"

Fatal server error:
xf86OpenConsole: Cannot open /dev/tty0 (No such file or directory)

giving up.
xinit:  Connection reset by peer (errno 104):  unable to connect to X server
xinit:  No such process (errno 3):  Server error.

```

you know how solve? :confused:

P.S. Sorry for my English  :oops:

---

### Post by bodhi.zazen on 2008-10-04
This guide is a *little* outdated.

For X connections see :

[How to Xephyr ~ AKA Multiple, nested X sessions - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?p=3816948#post3816948")

---

### Post by avel on 2008-11-12
Are there any news on an intrepid-friendly OpenVZ kernel?

I see that Debian have a 2.6.26 kernel with openvz patches here:
[http://packages.debian.org/sid/linux-image-openvz-686](http://packages.debian.org/sid/linux-image-openvz-686)

Would these debs work without weird issues?

---

### Post by bodhi.zazen on 2008-11-12
> **avel said:**
> Are there any news on an intrepid-friendly OpenVZ kernel?

I see that Debian have a 2.6.26 kernel with openvz patches here:
[http://packages.debian.org/sid/linux-image-openvz-686](http://packages.debian.org/sid/linux-image-openvz-686)

Would these debs work without weird issues?

I filed a "bug report" at Launchpad asking this question, no joy as of yet.

I am hoping OpenVZ will be supported in Ubuntu moving forward.

---

### Post by vladandrei on 2009-03-30
Hello, I've followed all the steps and now I have encountered a problem: my first kernel is: kernel **/boot/vmlinuz-2.6.27-11-generic root=UUID=33955edc-fec5-404b-86fe-752e43531ca1** ro quiet splash and boots ok.
I've tried setting the default kernel to:
kernel /**boot/vmlinuz-2.6.18-14-ovz-686 root=UUID=33955edc-fec5-404b-86fe-752e43531ca1** ro quiet splash. When this kernel boots, I get the ubuntu image, and then it stops loading, redirects me to /bin/sh with the following error: **/dev/disk/by-uuid/33955edc-fec5-404b-86fe-752e43531ca1 does not exist. Dropping to a shell.**
Now, I've checked /dev/disk/by-uuid/33955edc-fec5-404b-86fe-752e43531ca1 (which is the same for both kernels), and it points to /dev/sda1, which is my primary hdd, so, theoretically, it should boot.
My hardware is a Fujitsu Siemens laptop, with a SATA harddrive (might this be the problem?), and the OS is Kubuntu 8.10.
Could you please tell me if I'm doing something wrong?

---

### Post by bodhi.zazen on 2009-03-30
My guess is that the openvz kernel does not have the drivers for your hard drive.

You could try changing the kernel line to 

root=/dev/sda1

---

### Post by vladandrei on 2009-03-31
> **bodhi.zazen said:**
> My guess is that the openvz kernel does not have the drivers for your hard drive.

You could try changing the kernel line to 

root=/dev/sda1

Thanks for the idea, but could you please be a little more specific? In which file should I add this line? Or, how exactly do I make this change?

If this doesn't work, what are my options? To wait for openvz to create drivers for my harddrive? Should I try another virtualization solution?

---

### Post by bodhi.zazen on 2009-03-31
To make that change, you edit /boot/grub/menu.lst

You can do so with 

```
gksu gedit /boot/grub/menu.lst
```

or

```
sudo -e /boot/grub/menu.lst
```

If that fails, you would need to compile a custom kernel. I would use the ubuntu openzv kernel (download the source).

Look at the options in a working kernel and apply those to the config file for your openvz kernel.

[https://help.ubuntu.com/community/Kernel/Compile](https://help.ubuntu.com/community/Kernel/Compile)

---

### Post by starfry on 2009-06-15
Hello,

I've been using OpenVZ for various things for a few weeks now and am getting on well with it. I do have an issue with networking though... It would appear, at least on my Hardy box, that the OpenVZ containers do not start with networking when the host is booted (they do start, but networking does not work). Restarting the container and everything is fine.

I wondered if perhaps the OpenVZ stuff is starting too soon? (My install has this at /etc/rc3.d/S20vz I think)

Any thoughts ?

---

### Post by bodhi.zazen on 2009-06-15
Could you post a few more details ?

How did you set up networking ?

---

### Post by starfry on 2009-06-15
Hi, I did nothing special. Standard install just using venet0. Standard Hardy Desktop (64 bit) with Hardy Minimal 32 bit containers.

I installed Hardy, OpenVZ, etc. Set up some containers and all works fine. Reboot, all works fine except the containers aren't visible on the network. Restart the containers and all is fine.

I have another machine running an "alternate install" hardy environment (i.e, an older machine based on OpenBox without the Gnome Desktop bloat). That one works fine off the bat. There are no differences to how I set up OpenVZ on both.

I am actually in the middle of changing it so I can use veth but I am having trouble adding a bridge (via /etc/network/interfaces) because of network manager. But that is another story :)

---

### Post by bodhi.zazen on 2009-06-15
Not sure.

If you wish to use a bridge, remove network manager and configure your network manually.

A bridge is not required with openvz and I would not bother unless you need a bridge for something else.

Personal 8.04 seems soo dated, I switched to Proxmox.

[http://pve.proxmox.com/wiki/Main_Page](http://pve.proxmox.com/wiki/Main_Page)

---

### Post by starfry on 2009-06-15
I need to use a bridge because I need to use veth because I need to support multicast (DLNA upnp server, samba, etc). Unless I am wrong?

Since my last post, I removed network-manager and, lo, everything started working, including my new bridge.

Re the use of hardy, The host is a desktop environment as well. I know some may frown but the machine is more than capable and I want it to end up the only physical machine I have in daily use.

I'll upgrade when the next LTS comes out or the next release that supports OpenVZ out of the box.

---

### Post by bodhi.zazen on 2009-06-15
I made this mistake as well when starting with openvz. You do not need to use bridged networking with those services and OpenVZ (which is different from other virtualization technology). You will need to configure iptables.

Somehow I am not surprised the problem is with network manager, lol. IMO network manager is only helpful on laptops.

There is nothing wrong with using 8.04. I was in need of a more up-to-date version of kvm.

---

### Post by starfry on 2009-06-16
That's very interesting Bodhi - so are you saying that things that use multicast will work on venet0 if iptables is configured appropriately?

Do you have any material on that to explain what to do? I'd like to investigate it.

The OpenVZ Wiki seems to say that things like DHCP, Samba server domain broadcasts, etc,  require veth .

[http://wiki.openvz.org/DHCP](http://wiki.openvz.org/DHCP)
[http://wiki.openvz.org/Differences_between_venet_and_veth](http://wiki.openvz.org/Differences_between_venet_and_veth)

---

### Post by bodhi.zazen on 2009-06-16
> **starfry said:**
> That's very interesting Bodhi - so are you saying that things that use multicast will work on venet0 if iptables is configured appropriately?

Do you have any material on that to explain what to do? I'd like to investigate it.

The OpenVZ Wiki seems to say that things like DHCP, Samba server domain broadcasts, etc,  require veth .

[http://wiki.openvz.org/DHCP](http://wiki.openvz.org/DHCP)
[http://wiki.openvz.org/Differences_between_venet_and_veth](http://wiki.openvz.org/Differences_between_venet_and_veth)

Well, we are talking apples and oranges. You are speaking about a type of virtual interface.

I am saying you do not need to manually create a bridge the way you have.

[http://wiki.openvz.org/Veth](http://wiki.openvz.org/Veth)

That page goes through setting up Veth. You need to assign an ip address and mac, but it does not appear you need to bridge your network card.

That page has the iptables rules on it.

I have not worked through that page mind you ;)

---

### Post by jia103 on 2009-07-19
Hello, all,

I've been following bits and pieces of several guides in order to set up OpenVZ on Ubuntu 9.04 (Jaunty Jackalope); it seems most guides are based on prior versions of Ubuntu.

I've got everything working using the following instructions. The only problem I have now is that [COLOR="Red"]some things are not persistent[/COLOR]; thus, [COLOR="Red"]after each reboot, I need to run a few commands[/COLOR] before everything works again. I was hoping some kind user could offer assistance.

**_Problems:_**

Upon each reboot, I have the following problems:

[LIST=1]
[*]The bridge, br0, only contains the hosts' eth0; it does not contain the VE's eth0, veth*NNN*.0 where *NNN* is the ID of the VE.

[*]The VE does not have networking started.

[*]I cannot access anything beyond my LAN.
[/LIST]


**_Work-around:_**

After booting up, I run the following as root on the host:

[FONT="Courier New"]
   # brctl addif br0 veth*NNN*.0
   # vzctl exec *NNN* dhclient eth0
   # route add default gw 192.168.0.1
[/FONT]


**_Configuration:_**

I started with a typical home network setup with a wireless router behind amy Internet connection, and a laptop connected via a CAT5/Ethernet cable (not Wi-Fi) to the router. To be specific, there is a switch between the router and the laptop.

The laptop runs Ubuntu 9.04, except the kernel now being used is the OpenVZ kernel specified below.

I want a VE connected to the network using a bridge on the laptop host, rather than NAT. My router is already set up with static DHCP for all clients; I want VEs to be additional clients on the network.


**_Notation:_**

[LIST]
[*]Commands prefixed with a "#" indicate those commands run as a privileged user (e.g. root or via sudo).

[*]Commands prefixed with a ">" indicate those commands run as a non-privileged user.

[*]Commands prefixed with "VPS#" indicate those commands run as the VE's root user *inside* the VE, i.e. after running:
[/LIST]

[FONT="Courier New"]
   # vzctl enter *NNN*
[/FONT]


**_Details Instructions:_**

From [http://blog.jetienne.com/2009/07/installing-openvz-on-ubuntu-904.html:](http://blog.jetienne.com/2009/07/installing-openvz-on-ubuntu-904.html:)

[INDENT]

[FONT="Courier New"]
   # apt-get install vzctl vzquota
   > wget [http://ftp.fr.debian.org/debian/pool/main/l/linux-2.6/linux-image-2.6.26-2-openvz-686_2.6.26-17_i386.deb](http://ftp.fr.debian.org/debian/pool/main/l/linux-2.6/linux-image-2.6.26-2-openvz-686_2.6.26-17_i386.deb)
   # dpkg -i linux-image-2.6.26-2-openvz-686_2.6.26-17_i386.deb
[/FONT]

   Modify /boot/grub/menu.lst if desired to set "default" kernel to be the openvz kernel.

   Reboot, bring up Grub menu, select openvz kernel to boot. After booting:

[FONT="Courier New"]
   > uname -r
   2.6.26-2-openvz-686
[/FONT]

[/INDENT]

Done with installation. Now create VE.


From [https://help.ubuntu.com/community/OpenVZ:](https://help.ubuntu.com/community/OpenVZ:)

[INDENT]

   Skip editing /etc/sysctl.conf for now since we're more interested in a bridge configuration rather than NAT.

[FONT="Courier New"]
   # ln -s /var/lib/vz /vz
[/FONT]

   Download PGP public key from [http://wiki.openvz.org/Package_signatures](http://wiki.openvz.org/Package_signatures)

   Download template:

[FONT="Courier New"]
   > wget [http://download.openvz.org/template/precreated/ubuntu-9.04-x86.tar.gz.asc](http://download.openvz.org/template/precreated/ubuntu-9.04-x86.tar.gz.asc)
   > wget [http://download.openvz.org/template/precreated/ubuntu-9.04-x86.tar.gz](http://download.openvz.org/template/precreated/ubuntu-9.04-x86.tar.gz)
[/FONT]

   Verify signature:

[FONT="Courier New"]
   > gpg --import RPM-GPG-Key-OpenVZ.txt
   > gpg --verify ubuntu-9.04-x86.tar.gz{.asc,}
[/FONT]

   Install template:

[FONT="Courier New"]
   # mv */path/to*/ubuntu-9.04-x86.tar.gz /var/lib/vz/template/cache
   # vzctl create  *NNN* --ostemplate ubuntu-9.04-x86
[/FONT]

   *NNN* is the unique VEID of the VPS; a good guideline is to use the last octet of the IP address.

   Test:

[FONT="Courier New"]
   # vzctl start *NNN*
   # vzctl enter *NNN*
   VPS# exit
[/FONT]

[/INDENT]

No network yet; set up networking before resuming.


Set up DHCP from [http://ubuntuforums.org/showthread.php?t=617225](http://ubuntuforums.org/showthread.php?t=617225)

[INDENT]

   Additional resources:[LIST]
[*][http://ubuntuforums.org/showthread.php?t=434369](http://ubuntuforums.org/showthread.php?t=434369)
[*]   [http://wiki.openvz.org/Common_Networking_HOWTOs](http://wiki.openvz.org/Common_Networking_HOWTOs)
[*]   [http://wiki.openvz.org/DHCP](http://wiki.openvz.org/DHCP)
[*]   [http://wiki.openvz.org/Common_Networking_HOWTOs](http://wiki.openvz.org/Common_Networking_HOWTOs)
[/LIST]

[FONT="Courier New"]
      # vzctl set *NNN* --netif_add eth0 --save
      # apt-get install bridge-utils
      # vi /etc/network/interfaces
[/FONT]

   Add:

[FONT="Courier New"]
      brctl addbr br0
      auto br0
      iface br0 inet dhcp
      bridge_ports eth0 veth*NNN*.0
[/FONT]

   Restart networking:

[FONT="Courier New"]
      # /etc/init.d/networking restart
[/FONT]

   Check interfaces:

[FONT="Courier New"]
      > ifconfig -a
[/FONT]

   Confirm both br0 and eth0 are present.

   Configure the guest:

[FONT="Courier New"]
      # brctl addif br0 veth*NNN*.0
      # vzctl exec *NNN* dhclient eth0

      # vzctl enter *NNN*
      [VPS]# vi /etc/network/interfaces
[/FONT]

      [INDENT]

         Add:

[FONT="Courier New"]
            auto eth0
            iface eth0 inet dhcp

      VPS# exit

      [/INDENT]
[/FONT]

   Test it out:

[FONT="Courier New"]
      # vzctl enter *NNN*
      VPS# ifconfig eth0
[/FONT]

      Ping various hosts; ping the host; ping a site outside (e.g. Yahoo or Google).

[FONT="Courier New"]
      VPS# exit
[/FONT]

      Ping various hosts; ping the VE; ping a site outside (e.g. Yahoo or Google).

   Problem pinging from host to sites outside the LAN.

[FONT="Courier New"]
      # route add default gw 192.168.0.1
[/FONT]

   Reboot.

   Try the ping test again. Run "brctl show". This shows the problems listed above.

[/INDENT]


**_Question:_**

[COLOR="Red"]How can I make the settings persistent so I don't have to run the work-around steps upon each boot-up?[/COLOR]

Thanks!

---

### Post by bodhi.zazen on 2009-07-20
Sweet =)

A work around would be to add your commands to a boot script or /etc/rc.local .

Personally my advice is to use Ubuntu 8.04, Proxmox, or Centos rather then Ubuntu 9.04.

---

### Post by jia103 on 2009-07-20
Thanks for the feedback. I guess I need to come up with a better question now. :)

Yes, I could add the commands to a boot script; however, I wanted to ask if I was doing anything incorrectly.

For instance, why would I suddenly need to add a gateway via the bridge configuration when I didn't need to before? [COLOR="Red"]Is there anything I'm doing incorrectly[/COLOR], or will this be the way it has to be?

Regarding Ubuntu 9.04, that's what's on my laptop, on which I'm just trying this out. Once I learn enough and get it to work, I plan to run this on my desktop, which I just confirmed is running [COLOR="Red"]Ubuntu 8.04[/COLOR].

Thanks again!

---

### Post by bodhi.zazen on 2009-07-20
I have found the openvz kernel is not optimal for a desktop.

If I run openvz on a desktop, I run it in a guest in KVM or Virtualbox or VMware.

In terms of your problem, I have not had that problem in Ubuntu 8.04, Centos, or Proxmox.

---

### Post by starfry on 2009-08-25
> **bodhi.zazen said:**
> I have found the openvz kernel is not optimal for a desktop.

That's interesting. Can you elaborate?

I run 8.04 desktop and use OpenVZ. It appears to be fine so far...

---

### Post by bodhi.zazen on 2009-08-25
Well, openvz is a patch that is compiled into the kernel. So it depends on how you did this. If you compiled a kernel yourself you can tune it for your hardware.

If you are downloading any of the various pre-compiled kernels you may have problems as the kernels tend to be minimal and optimized for servers and not desktops. In addition it can be problematic with wireless, sound, nvidia, and ATI (to name a few).

The Ubuntu openvz kernel in 8.04 is fairly generic and not as "problematic" or "optimized" as others.

It is not a huge performance hit and if your hardware works, then no problem. However, in general, more people aer going to have problems if they install the openvz kernel on desktops and expect video, sound, wireless, etc to be working out of the box.

---


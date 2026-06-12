---
title: "an ip scanner, any ip scanner"
date: 2021-06-22
forum: New to Ubuntu
---

### Post by winston61 on 2021-06-22
Hello to all

Getting Ubuntu Desktop setup on my Pi 4. I would like to have an ip scanner. I tried several install methods, none work. Any old ip scanner, nothing fancy. Can someone please help?

---

### Post by TheFu on 2021-06-22
What is an "ip scanner?"

Are you looking to search for copyright or patent documents with specific intellectual property keywords?  Some sort of research organization tool?

---

### Post by winston61 on 2021-06-22
an ip scanner, like advanced ip scanner, angry ip scanner. A utility to show ips associated with my network

---

### Post by him610 on 2021-06-22
Maybe nmap?
```

apt show nmap
Package: nmap
Version: 7.80+dfsg1-2build1
Priority: extra
Section: universe/net
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Debian Security Tools <team+pkg-security@tracker.debian.org>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 4,499 kB
Depends: nmap-common (= 7.80+dfsg1-2build1), libc6 (>= 2.29), libgcc-s1 (>= 3.0), liblinear4 (>= 2.01+dfsg), liblua5.3-0, libpcap0.8 (>= 1.5.1), libpcre3, libssl1.1 (>= 1.1.0), libstdc++6 (>= 5.2), lua-lpeg (>= 1.0.2), zlib1g (>= 1:1.1.4)
Suggests: ncat, ndiff, zenmap
Homepage: https://nmap.org/
Download-Size: 1,662 kB
APT-Manual-Installed: yes
APT-Sources: http://us.archive.ubuntu.com/ubuntu focal/universe amd64 Packages
Description: The Network Mapper
 Nmap is a utility for network exploration or security auditing. It
 supports ping scanning (determine which hosts are up), many port
 scanning techniques, version detection (determine service protocols
 and application versions listening behind ports), and TCP/IP
 fingerprinting (remote host OS or device identification). Nmap also
 offers flexible target and port specification, decoy/stealth scanning,
 sunRPC scanning, and more. Most Unix and Windows platforms are
 supported in both GUI and commandline modes. Several popular handheld
 devices are also supported, including the Sharp Zaurus and the iPAQ.

```

---

### Post by sudodus on 2021-06-23
1. Check which network interface that you use

```

**ip a**

```

In my case the network interface is **eno1**

2. [Install and] run **arp-scan**

```

sudo apt install arp-scan  # install from the repository universe, if not already installed

**sudo arp-scan -l -I eno1**

```

The options are 'minus ell' and 'minus upper-case I' and use the interface that **you** found with **ip a**

See more details with

```

man arp-scan

```

---

### Post by TheFu on 2021-06-23
Ah.  Never heard of any of those scanners in the OP, but nmap is THE standard 
```
sudo nmap -sT 192.168.1.0/24
```
There are thousands of different nmap commands, depending on what you seek and what protections the other systems might have automated to block scanning. 

If the systems have already been in contact over ethernet, then a simple **arp** will show the arp table for IPv4. On IPv6, there's a show neighbors command of some sort. Sorry, I don't know what it is, just that it replaces the arp in IPv4.
```
ip neigh
```
seems similar to arp. arp does a DNS lookup, but *ip neigh* does not.

---

### Post by ActionParsnip on 2021-06-23
Nmap

---

### Post by him610 on 2021-06-23
In addition to the investigative tools discussed above, there are other network tools you may be unaware of since you seem to be new to *buntu. These are some that I have noted over the years from reading these very informative forums...
> 
# Network tools
ifconfig - configure a network interface
ip - show / manipulate routing, network devices, interfaces and tunnels
iwconfig - configure a wireless network interface
iwlist - Get more detailed wireless information from a wireless interface
mtr - combines the functionality of the traceroute and ping programs in a single network
nmcli - command-line tool for controlling NetworkManager
nmtui - Text User Interface for controlling NetworkManager
rfkill - tool for enabling and disabling wireless devices
netplan - YAML network configuration abstraction for various backends
lspci -vk |perl -lne 'print if /Ethernet|Network/ .. /^[\w]*$/' 

#Turn on network adapter
rfkill unblock wifi
nmcli radio wifi on

You can use the 'man' pages to find out detailed information as to how to use each tool.

---

### Post by scorp123 on 2021-06-23
> **winston61 said:**
> I tried several install methods, none work.

Such as? Weird that you say "none work". Unless you did something really weird all the scan programs can easily be installed via the **"Software"** app or the **"apt"** package manager.

Might also want to read this:
[https://www.maketecheasier.com/best-linux-port-scanners/]("https://www.maketecheasier.com/best-linux-port-scanners/")

---

### Post by TheFu on 2021-06-23
```
sudo apt update
sudo apt install nmap
```
done.

How new to Linux are you?  nmap isn't a GUI tool. The most powerful tools on Unix-like OSes seldom have GUIs.  GUIs are hard to automate, but CLI programs can be automated to infinite needs.

Seems really odd to me that someone doesn't know the IPs on their network.  How can that happen if the person is the network admin?

---

### Post by scorp123 on 2021-06-24
> **TheFu said:**
>  Seems really odd to me that someone doesn't know the IPs on their network.  How can that happen if the person is the network admin?

New job maybe? And previous guy suddenly left / had to be let go / had an accident etc. and did a really poor job documenting anything at all?  I've been in that boat and in that ocean too. Not a fun ride.

---

### Post by TheFu on 2021-06-24
> **scorp123 said:**
> New job maybe? And previous guy suddenly left / had to be let go / had an accident etc. and did a really poor job documenting anything at all?  I've been in that boat and in that ocean too. Not a fun ride.

Pi 4? Desktop? Work?  I'd hope not, but we were all new at some point. Learning at home with a Pi isn't a bad thing at all. I fear the desktop experience will be really poor, however.

As with all Unix stuff, there are often 50 different ways to solve any issue.
[http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) is a book that should cover most things, though on my Pis, conman is used to handle network connectivity and Ubuntu doesn't use that.  It is so much easier to setup a static IP and never worry about this stuff again.

---


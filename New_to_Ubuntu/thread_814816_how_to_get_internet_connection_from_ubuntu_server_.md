---
title: "how to get internet connection from ubuntu server command lines"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by kalidj on 2008-06-01
i am new to ubuntu, but i am searching around, and i installed ubuntu server on a pc i thought would act as a server, but i now found out that i do need to insert the cd everytime i needed updates, ... i mean i was looking for some ways to get direct connection to the internet from the command line of the server, and be able to download any package i need from the internet. Is there a means to do this.

i am asking cuz when i tried to install an ldap package from the cd after the server installation, it tells me that the server cd doesnt have the migrationtools package which i was looking for ldap. i think i need to get to the internet to download the package, don't i?

---

### Post by cariboo on 2008-06-01
if you have a network card installed you should be all ready to go. Ubuntu automatically sets up most peripherals during installation. If your connecting through a router you should get something like this when you run ifconfig:

```
jimk@intrepid:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:17:9c:84:b5  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:17ff:fe9c:84b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:782830 errors:0 dropped:0 overruns:0 frame:0
          TX packets:521054 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:972325753 (927.2 MB)  TX bytes:44539592 (42.4 MB)
          Interrupt:20 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:5068 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5068 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:253400 (247.4 KB)  TX bytes:253400 (247.4 KB)

jimk@intrepid:~$ 
```

As you can see in the second line below eth0 my ip address is 192.168.1.100, this address was assigned by my router.

After you have made sure you're connected you should be able to do updates and upgrades using either apt or aptitude (still after all these years I hate using aptitude). Aptitude is a ncurses interface for apt. To use aptitude on the command line just type:

```
sudo aptitude
```

to use apt on the command line type:

```
sudo apt-get update
```

Then to upgrade to the latest packages type

```
sudo apt-get upgrade
```

To install packages type:

```
sudo apt-get install "package name"
```

Have fun

Jim

---

### Post by wormser on 2008-06-01
Do you get an insert CD error when trying to install software?  If this is the case then you need to edit /etc/apt/sources.list.  Then comment (#) out the CD line.

```
sudo nano /etc/apt/sources.list
```Then save the file and run:
```
sudo apt-get update
```

---

### Post by kalidj on 2008-06-01
ya, thats the thing that was giving me hard time. i got insert CD error when trying to install software. so now i have commented out the cd line, but still cant get to download the package i want.

is it from me? i cant download migrationtools package to my server. the line    *sudo apt-get install migrationtools* tells me the package doesn't exist.

---

### Post by Monicker on 2008-06-01
> **kalidj said:**
> ya, thats the thing that was giving me hard time. i got insert CD error when trying to install software. so now i have commented out the cd line, but still cant get to download the package i want.

is it from me? i cant download migrationtools package to my server. the line    *sudo apt-get install migrationtools* tells me the package doesn't exist.

What is the output of the following commands when run from the server?

```
ifconfig
netstat -rn
lshw -C network
```

---

### Post by kalidj on 2008-06-01
ifconfig shows
eth0      Link encap:Ethernet  HWaddr 00:13:72:84:94:A5  
          inet addr:10.140.50.82  Bcast:10.140.50.255  Mask:255.255.255.0
          inet6 addr: fe80::213:72ff:fe84:94a5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:69 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7721 (7.5 KB)  TX bytes:4502 (4.3 KB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

---

### Post by moffa on 2008-06-01
It seems that your internet connection is working.

Did you uncomment the deb lines in /etc/apt/sources.list?

Try uncommenting the restricted and multiverse lines and then running apt-get update

---

### Post by kalidj on 2008-06-01
netstat shows:-

```
kernel  IP routing table
Destination     Gateway     Genmask      Flags    Mss  Window   irtt  Iface
10.140.50.0     0.0.0.0     255.255.255.0  U       0    0        0     eth0
0.0.0.0         10.140.50.1 0.0.0.0        UG      0    0        0   eth0
```
 
lshw -c network shows: -
```
Hardware Lister (lshw) - B.02.10
usage: lshw [-format] [-options ...]
       lshw -version

        -version        print program version (B.02.10)

format can be
        -html           output hardware tree as HTML
        -xml            output hardware tree as XML
        -short          output hardware paths
        -businfo        output bus information

options can be
        -class CLASS    only show a certain class of hardware
        -C CLASS        same as '-class CLASS'
        -disable TEST   disable a test (like pci, isapnp, cpuid, etc. )
        -enable TEST    enable a test (like pci, isapnp, cpuid, etc. )
        -quiet          don't display status
```

---

### Post by spiderbatdad on 2008-06-01
how about```
cat /etc/resolv.conf
```?? Could you post that, please?

---

### Post by kalidj on 2008-06-01
cat /etc/resolv/conf

```
search mc.aau.edu.et
nameserver 10.140.5.25
nameserver 10.141.5.25
```

---

### Post by spiderbatdad on 2008-06-01
> **kalidj said:**
> cat /etc/resolv/conf

```
search mc.aau.edu.et
nameserver 10.140.5.25
nameserver 10.141.5.25
```
 You might verify those against another computer. Normally I have seen 3 listed. The first is primary, then secondary, then tertiary. I have used just two. not sure what the 'search mc.aau.edu.et' is all about. I guess I would try changing the order and put that line below the others, unless it has a # mark that you did not include in the post.

---

### Post by cariboo on 2008-06-01
What happens when you try ```
sudo apt-get update
```
Jim

---

### Post by louieb on 2008-06-01
> **moffa said:**
> It seems that your internet connection is working.
Did you uncomment the deb lines in /etc/apt/sources.list?
Try uncommenting the restricted and multiverse lines and then running apt-get update

Have you done this yet? Sure sounds like this is what you need to do. What happens?

---


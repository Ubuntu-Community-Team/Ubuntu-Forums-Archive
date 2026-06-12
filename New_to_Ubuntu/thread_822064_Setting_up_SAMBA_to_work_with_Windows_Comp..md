---
title: "Setting up SAMBA to work with Windows Comp."
date: 2008-06-07
forum: New to Ubuntu
---

### Post by AdrianStrays on 2008-06-07
I followed a guide on here, but still neither computer recognizes one another.  I'm really out of my league when it comes to this kind of thing, and I know there have been a million threads to this effect, I'd really appreciate some help setting up SAMBA properly.

---

### Post by Rocket2DMn on 2008-06-07
Here is a very useful guide on setting up samba - [https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

If you have any specific questions regarding the tutorial, please ask.

---

### Post by AdrianStrays on 2008-06-07
My computer can't even detect the other computers on the network.  I need help, not a guide. I've set up a static-ip address on my Vista desktop and I know the internal IP-Address of my Ubuntu laptop.  Neither can connect to each other, despite the fact that they are in the same work group on the same network.  I need to troubleshoot, and documentation isn't helping.

---

### Post by Rocket2DMn on 2008-06-07
The purpose of providing documentation is to ensure that Samba is setup correctly on your Ubuntu machine before starting a wild goose chase.  So, now assuming that Samba is setup correctly, when you go to Places->Network, can you see "Windows Network"?  If so, is it empty?
If so, I have found that if you hav firestarter installed, opening it and stopping the firewall helps.  Otherwise you may need to configure iptables.
For this, see:
[http://ubuntuforums.org/showthread.php?t=159661](http://ubuntuforums.org/showthread.php?t=159661)
If this isn't helping to solve your problem, you should consider searching the Networking and Wireless forum and making a request for help there if needed (since this is an Absolute Beginner forum)
[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)
Feel free to post back, and good luck.

---

### Post by Prospero2006 on 2008-06-08
Please tell us the ip addresses you have assigned to all machines on your network.

Also, on your linux machines give us the output of ifconfig

This will help

---

### Post by AdrianStrays on 2008-06-08
I disabled firewalls, no effect

Vista: 192.168.1.101
Linux: 192.168.1.102

```
eth0      Link encap:Ethernet  HWaddr 00:1c:23:89:2f:27  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1b:fc:6d:3f:34  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:fcff:fe6d:3f34/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:63095 errors:0 dropped:0 overruns:0 frame:0
          TX packets:48177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:79589585 (75.9 MB)  TX bytes:6874197 (6.5 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:948 errors:0 dropped:0 overruns:0 frame:0
          TX packets:948 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:53492 (52.2 KB)  TX bytes:53492 (52.2 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-FC-6D-3F-34-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

---

### Post by fenian on 2008-06-08
First start with a clean samba: in synaptic package manager mark all the samba stuff for complete removal then after it uninstalls reinstall those same packages.

Next go to the menu System>Administration>Users and Groups
click unlock
click properties 
click the user privelages tab and and make sure the share files with network box is checked.
click ok

Next if the other computer will use a username and password different than your ubuntu username/passwd add a user for that account...
Clickthe add user button and enter the desired username and password
as you did above click the user privelages tab and and make sure the share files with network box is checked.
click ok
close the user settings window

Next setup the smb.conf file
open a terminal and enter...

> sudo gedit /etc/samba/smb.conf

Under Share Definitions change the line...

;browseable = no
to
browseable = yes

and change the line...

;read only = yes
to
read only = no

save the file and close.

Next add all the users to samba
First add the main ubuntu user...
open a terminal and enter

> sudo smbpasswd -L -a username

  (username=your ubuntu username when prompted for password use your ubuntu password)
 the in the terminal enter...
> 
sudo smbpasswd -L -e username

  (as above username=your ubuntu username when prompted for password use your ubuntu password)

repeat those two commands for each user you want to have access to shared files substituting appropriate usernames and passwords.

finally  restart samba with this command...

> sudo /etc/init.d/samba restart

---

### Post by fenian on 2008-06-08
The instructions I posted above are for Hardy (8.04)

also to share a folder or file simply right click th fle/oder and select sharing options and check the appropriate box(es)

---

### Post by AdrianStrays on 2008-06-08
Done, no effect.

---

### Post by fenian on 2008-06-08
First make sure that the windows machine is set to connect to the right workgroup MSHOME is the default workgroup.

Also it can sometimes take quite a while for the shares to be seen on the network I've had it take up to 20 minutes.

---

### Post by AdrianStrays on 2008-06-08
It is, although there is a space in both the Vista and Ubuntu workgroup, which I think may be a problem.

---

### Post by fenian on 2008-06-08
Also make sure your smb.conf is set to MSHOMEopen a terminal and enter...

> sudo gedit /etc/samba/smb.conf 

under global settings the first lines should look like this...

#======================= Global Settings =======================

[global]

## Browsing/Identification ###

# Change this to the workgroup/NT-domain name your Samba server will part of
   workgroup = MSHOME
......

---

### Post by AdrianStrays on 2008-06-08
Im not using Mshome as a work group on either comp.

---

### Post by kamaji792 on 2008-06-08
Try and ping each machine

Windows:
```
ping 192.168.1.102
```
Linux:
```
ping -c 4 192.168.1.101
```

all the best

---

### Post by Stefanie on 2008-06-08
when i set up sambe, i had a problem that seems similar to yours. when i clicked places -> network, i saw my windows network, but when i clicked it the other computers didn't show up. i got it working by typing the ip-address of the other computer in the nautilus location bar:

```
smb://192.168.1.101
```
(it's possible that you have to type smb:/// instead of smb:// , i'm not sure)

---

### Post by Prospero2006 on 2008-06-08
It looks to me like eth0 may be your primary device. Eth1 is currently set.

```

ifconfig eth1 down
ifconfig eth0 192.168.1.101 up
ifconfig eth0 netmask 255.255.255.0
route add default gw [COLOR="Red"]ip_address_of_gateway[/COLOR]
ping 192.168.1.102

```

?

---

### Post by AdrianStrays on 2008-06-08
From Vista:
```
Pinging 192.168.1.102 with 32 bytes of data:
Reply from 192.168.1.102: bytes=32 time=1ms TTL=64
Reply from 192.168.1.102: bytes=32 time=2ms TTL=64
Reply from 192.168.1.102: bytes=32 time=2ms TTL=64
```

From Ubuntu:
```

adrian@Alpha-60-Workstation:~$ ping -c 4 192.168.1.101
PING 192.168.1.101 (192.168.1.101) 56(84) bytes of data.
64 bytes from 192.168.1.101: icmp_seq=2 ttl=128 time=1.31 ms
64 bytes from 192.168.1.101: icmp_seq=4 ttl=128 time=3.40 ms

--- 192.168.1.101 ping statistics ---
4 packets transmitted, 2 received, 50% packet loss, time 3000ms
rtt min/avg/max/mdev = 1.319/2.361/3.403/1.042 ms
adrian@Alpha-60-Workstation:~$ 
```

> smb://192.168.1.101

I can access my folders from Windows in Ubuntu by doing that, but I'd prefer not to have to enter that everytime I'd like to connect, and it also doesn't help me with Windows.

---

### Post by fenian on 2008-06-08
You may need to set up your shares-admin to the workgroup you are using,it defaults to MSHOME and you say you want to use something else.To do this open a terminal and enter...

> shares-admin

in the window that opens click unlock then click the General Properties tab change the Domain/Workgroup to whatever yours is named.

---

### Post by kamaji792 on 2008-06-09
I wonder if you have a problem with your network connection.  The ping result for ubuntu showed 50% packet loss!

Are you using a hub/switch or a crossover wire?

---


---
title: "HowTo: ProFTPD Behind NAT"
date: 2005-06-05
forum: Outdated Tutorials &amp; Tips
---

### Post by Beernut on 2005-06-05
This HowTo should be pretty short and sweet.  I searched all over trying to figure out how to get PASV FTP to work behind a NAT router like a Linksys or any similar home networking router.  It really isn't that hard just a couple of commands to the configuration file and some port forwarding on the router. 

Well let's get started first you need to have ProFTPD installed so in a terminal on the server type the following commands.

```
sudo apt-get install proftpd
```

That will install the two packages you need to run ProFTP.  Now we need to edit the configuration file so that the FTP server will work behind NAT.  So still in the terminal on the server enter the following command.

```
sudo nano /etc/proftpd.conf
```

That will bring up the configuration file, at the end of the file add the following lines.

```
PassivePorts 60000 60100

MasqueradeAddress YourSiteName.com
MasqueradeAddress xxx.xxx.xxx.xxx
```

The PassivePorts command we entered there allows 100 concurrent connection which should be enough for most home users.  Those are the ports we are going to have to forward to the FTP server on the router.  Replace the xxx.xxx.xxx.xxx with the routers public IP address you can usually find this on the routers status page or you can simply go to [http://www.ipchicken.com/](http://www.ipchicken.com/) which will tell you your public IP address.

Still in the terminal on the server we have to restart ProFTPD so that the configuration changes will take effect.  Enter the following on the command line.

```
sudo /etc/rc.d/init.d/proftpd restart
```

Now we have to forward the PassivePorts on the router.  Login to your router click on the advanced tab then the forwarding tab.  Enter in the port range we specified in the configuration file then check the TCP box UDP does not need to be enabled then enter the IP address of the FTP server and click enable.  Click the "Apply button and your done on the router.  Note if you are using a different brand router the process should be similar this is the setup on a Linksys router.

That should do it your FTP server should work behind your NAT router.  There is one drawback to this if you have a dynamic IP address from your ISP you will need to update the address in your configuration file whenever it changes.

---

### Post by traherom on 2005-07-09
Thanks, works for me. Almost all the people I host access through passive FTP, so this is invaluable in my move from a Windows host to Ubuntu.

---

### Post by hbomb on 2006-05-18
thanks for the code, this solved my proftp nat issue! :D

---

### Post by baldercm on 2006-11-22
Hi!

I've setup my ftp server and everything works ok... but only in mi local LAN.
I've dynamic IP address, and I've got a dyndns domain with ddclient.
My ftp port and passive ports are open in my router configuration, and I added
```

MasqueradeAddress mydomain.serveftp.org
PassivePorts 60000 60100
```
to the proftpd.conf file.
When I start proftp I get
```
balder@PortatilBalder:~$ sudo /etc/init.d/proftpd restart
Password:
 * Stopping ftp server proftpd                                                                                                          [ ok ]
 * Starting ftp server proftpd
- IPv6 getaddrinfo 'PortatilBalder' error: Name or service not known
PortatilBalder - 127.0.1.1:2000 masquerading as 192.168.1.2 [ ok ]
```
Is that an error or it's ok?
My ftp site can't be accessed from outside my NAT right now and I really need it to work as soon as possible.](*,)
Thanks

---

### Post by chaplinux on 2006-12-24
It reads:
less /usr/share/doc/proftpd/README.Debian

- add your servername in line:
sudo vi /etc/hosts  

127.0.0.1       localhost
127.0.1.1       my-server

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback my-server
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by Big_Rog on 2007-03-08
Please update for Edgy?

Apparently "sudo /etc/rc.d/init.d/proftpd restart" doesn't work, as there are only /etc/rc#, not /etc/rc.d entries.  Could you also put in the updates for using inetd/xinetd, or at least a reference to what does/doesn't need to be done?

thanks!

---

### Post by neutrino15 on 2008-05-22
I followed your instructions and set up my masqueradeaddress to be my domain name (dyndns).
I am using a weird port (4221) for login, and ports 4290 through 4299 for ftp pasv.

When I start the server, it tells me
```
ubuntu-server - 127.0.1.1:4221 masquerading as my.external.ip
```
Which should be ok.
When I try to log in to my server, however, at [ftp://ftp.my.dyndns.domain:4221](ftp://ftp.my.dyndns.domain:4221) the client times out after trying to connect for a good minute.

My config is attached.

It's not dyndns' fault. I use apache and azureus' webUI with no problems. SSH works as well.
I am using Hardy Heron


Thanks in advance!

---

### Post by djliamtate on 2009-10-22
Hi,

I have followed the instructions to setup ProFTPD to work behind a NAT and have so far only managed to connect from local machines. I am currently using a local file server with Ubuntu Server installed so I can access all my music locally but I also need to be able to FTP to the server when I am away from the home network.

Now currently, I have PassivePorts directive set to 60000 60100 and the Port directive to 1980. I have my Masquerade address set to xxxxxxxxxx.homeftp.net and am using a Netgear WRN2000 Router for my home network. I have a static IP assigned to the server although all other devices have their IP addresses assigned Dynamically by the router. When I try to connect using the DynDNS hostname in CrossFTP or from a Finder folder on my Mac I get no joy but if I connect using FTP with the 192.xxx.xxx.xxx private address it seems to be fine.

Any clues anyone, I have been reading the net all day.

Thanks in advance.

Liam

---

### Post by djliamtate on 2009-10-23
> **djliamtate said:**
> Hi,

I have followed the instructions to setup ProFTPD to work behind a NAT and have so far only managed to connect from local machines. I am currently using a local file server with Ubuntu Server installed so I can access all my music locally but I also need to be able to FTP to the server when I am away from the home network.

Now currently, I have PassivePorts directive set to 60000 60100 and the Port directive to 1980. I have my Masquerade address set to xxxxxxxxxx.homeftp.net and am using a Netgear WRN2000 Router for my home network. I have a static IP assigned to the server although all other devices have their IP addresses assigned Dynamically by the router. When I try to connect using the DynDNS hostname in CrossFTP or from a Finder folder on my Mac I get no joy but if I connect using FTP with the 192.xxx.xxx.xxx private address it seems to be fine.

Any clues anyone, I have been reading the net all day.

Thanks in advance.

Liam

I changed all the directories but because I "cut and paste" I forgot to change something. How annoying is it when you don't read something properly and it takes you hours to figure it out huh?

---

### Post by aytacd on 2009-11-07
I'm also trying to make a ftp server 
 
My modem is Zyxel P-661HW-D1 
i used proftpd and try to set up the conf file. 
i've added 
PassivePorts 60000 60100

MasqueradeAddress 85.103.159.187
but that doesn't work. 

local ip of the  computer is 192.168.1.33 and the ip of the router is 85.103.159.187
i don't have a dns server so i didn't add the dns part of the masquerade is it wrong? 

Can you help me about that? 
i've attached the conf file.

---


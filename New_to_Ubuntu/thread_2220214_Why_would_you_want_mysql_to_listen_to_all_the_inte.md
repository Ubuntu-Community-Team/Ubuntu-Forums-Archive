---
title: "Why would you want mysql to listen to all the interfaces ?"
date: 2014-04-27
forum: New to Ubuntu
---

### Post by Adonosonix on 2014-04-27
Hi, 

This really has to be a noob question, but I can't help it.
I just finished setup my web server for production using the howtoforge perfect server 12.04 LTS tutorial (apache version).

During the setup they tell:

> [COLOR=#000000][FONT=verdana]We want MySQL to listen on all interfaces, not just localhost, therefore we edit [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]*/etc/mysql/my.cnf*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] and comment out the line [/FONT][/COLOR][COLOR=#000000][FONT=Courier New]*bind-address = 127.0.0.1*[/FONT][/COLOR][COLOR=#000000][FONT=verdana]:[/FONT][/COLOR]

As a result:

> [COLOR=#000000][FONT=Courier New]*netstat -tap | grep mysql*[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*tcp        0      0 *:mysql                 *:*                     LISTEN      21298/mysqld*[/FONT][/COLOR]

Can I (should I) protect my SQL server by letting only process running on the server access it?
Right now, NMAP tells me my port 3306 is open to the world.

---

### Post by steeldriver on 2014-04-27
It depends where you want to access it from and what other firewall(s) / NAT you have in place - is it really "open to the world" or just open to other hosts on your LAN?

---

### Post by Adonosonix on 2014-04-27
Well, the server is hosted by a hosting company, but it has its own IP address, of course. And I can see the port is open from my computer, which is half a world away from the server.

I guess, since it is a single server, there should be no need for mysql to be accessed from elsewhere than localhost. So why on earth would they make their guide change this setting, on a single server? Is there some reason I can't grasp ?

---

### Post by SeijiSensei on 2014-04-27
The only reason to have MySQL bind to an address other than localhost is to access it with a remote client.  For instance, I have a PostgreSQL server on a Linode host that I sometimes connect to with LibreOffice base from my office.  So I need to be able to see the server's PG port from here.

Just having it listen on a public-facing interface is not a good way to go about this, of course.  If you're running on a virtual host, as your comment suggests, you do have an iptables firewall in place, yes?  One that blocks everything except the few ports like 80 that you need to have open to the world?  What about rules that restrict access to the server from all IP addresses except your own?  

I avoid this problem entirely by having an [OpenVPN static-key tunnel]("http://openvpn.net/static.html") set up between my office and the remote machine.  Then I see the remote SQL server using the server's private address on its end of the tunnel.  I would never expose a database server to the world without a lot of security in place first.

If you do have a server exposed to the public, make absolutely sure there are no "wildcard" user definitions like 'root'@'%'.  Always tie the MySQL users to specific hostnames or IP addresses.

---

### Post by Adonosonix on 2014-04-28
Thank you very much for your reply. My server is a dedicated server: a "real" computer un a data center somewhere. I did a scan, and currently open ports are:

[COLOR=#000000][FONT=Helvetica]**22, 25, 80, 110, 143, 443, 465, 587, 993, 995, 3306, 8080, 8081**
[/FONT][/COLOR]
I have ISPConfig installed (8080). I need **22, 25, 80, 110, 143, 443, 465, 587, 993, 995** for **SSH, HTTP/HTTPS** and **e-mail **services. 
In an other thread, I try to get rid of 8080 for ISPConfig (I would like to use **[https://mywebsite.tld/ispconfig](https://mywebsite.tld/ispconfig)**) but for some reason, I can't make it work.

I am unsure about 8081. I don't know what its purpose is.
I have blocked mysql's port (3306) from the firewall. The server runs OK.

I am planning on installing an IPSec vpn (tunnel mode) so I can easily connect to it from my office computer (MAC), but that's an other question&#8230; All other ports are firewall blocked.

---

### Post by SeijiSensei on 2014-04-28
> **Adonosonix said:**
> I am planning on installing an IPSec vpn (tunnel mode) so I can easily connect to it from my office computer (MAC), but that's an other question… All other ports are firewall blocked.

I'd use [OpenVPN]("http://openvpn.net/static.html") for this task.  It's remarkably simple to configure.  IPSec, not so much.

---

### Post by Adonosonix on 2014-04-28
Thank you for your reply. I tried OpenVPN on my NAS two years ago (MyBook Live, custom debian lenny). It was a nightmare to setup. Kernel modules were missing, I had to recompile them. Then there was something about tun/tap to setup (I don't remember what). I spent one week to make it work. In the end:

– I got a working VPN, but each time I activated the server through ssh (I didn't want to run it always), I had to run a script (about tun/tap).
– I had to resort to tunnelblick on my MAC
– It was slow like hell (using TCP) and sometimes unresponsive. I ended up dropping everything.

I couldn't setup an IPSec VPN on the NAS because of missing components in the kernel that could not be compiled as modules. And since the kernel was actually stored in flash (UBoot setup) there wasn't much I could do… without risking bricking the device.

---

### Post by SeijiSensei on 2014-04-29
I use CentOS on servers.  It has an openvpn package in the repositories, just like Ubuntu does.  You install the package, put a configuration file in /etc/openvpn, and run it as a service at boot with chkconfig.  I don't use appliances other than a wifi router.  On a regular Linux box, OpenVPN is pretty much a snap to configure.  On my virtual server at Linode I have this configuration:
```

dev tun
ifconfig 10.1.1.1 10.1.1.2
up /etc/openvpn/add_routes
secret /etc/openvpn/keys/mykey
port 12345
user nobody
group nobody
ping-restart 45
ping-timer-rem
persist-tun
persist-key
comp-lzo
ping 15                                                                                            

```
The office client has this configuration:
```

dev tun
remote myserver.at.linode
ifconfig 10.1.1.2 10.1.1.1
port 12345
secret /etc/openvpn/keys/mykey
up /etc/openvpn/add_routes
user nobody
group nobody
ping-restart 45
ping-timer-rem
persist-tun
persist-key
comp-lzo
ping 15

```
On Ubuntu, I believe you need to use "group nogroup".  "add_routes" is a script I wrote that runs a couple of "ip route" commands after the tunnel is established.  I used the command "openvpn --genkey" to create the key on one machine, then copied it to the other with scp.

Because OpenVPN punches through firewalls with SSL, you only need to let the office machine see the designated UDP port on the server, 12345 in the example here.

---


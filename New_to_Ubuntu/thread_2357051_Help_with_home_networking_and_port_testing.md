---
title: "Help with home networking and port testing"
date: 2017-03-29
forum: New to Ubuntu
---

### Post by karentutor1 on 2017-03-29
Hi

I wish to test is port 7443 is open on my new ubuntu 16.04 LTs server.

I have two computers connected each to an Ethernet wire at home (the other is a fedora25 desktop)

I have installed netcat on the ubuntu and have entered netcat -l 7443 

I have also installed netcat (nc) on the fedora.

I am a little at a loss as to how to ping the ubuntu server from my fedora to see if the port is open. (Or if this is the best way to test).  

Thanks!
Karen

---

### Post by SeijiSensei on 2017-03-29
Install **[nmap](http://nmap.org/)** from the Ubuntu repositories.  To probe port 7443 you would use
```
sudo nmap -sT -p 7443 server_name_or_ip
```
That attempts a TCP connection ("-sT") to port 7443.  

If you don't specify a port or protocol ("sudo nmap server"),  nmap will scan about 1500 well-known ports using TCP and print out a list like this:
```

22/tcp   open  ssh
25/tcp   open  smtp
53/tcp   open  domain
80/tcp   open  http
110/tcp  open  pop3
143/tcp  open  imap
993/tcp  open  imaps
995/tcp  open  pop3s
2049/tcp open  nfs

```

There are many other types of scans available as well.  See the manual page at "[man nmap]("https://linux.die.net/man/1/nmap")" for details.

---

### Post by karentutor1 on 2017-03-29
ok I'll give that a try thanks!!

---

### Post by SeijiSensei on 2017-03-29
It depends on how your network is configured.  If you simply plugged the server into a router and obtained an IP address automatically via the DHCP protocol, then it's possible the router asked the server for its hostname and added it to its DNS tables.  Otherwise you would have had to assign the name manually.

First, on the server, enter the command "hostname" and you will get back whatever name you assigned it at installation.  Now try using "ping hostname" on the Fedora box and see if it can identify the server's address.
```

$ ping server
PING server.example.com (10.10.10.10) 56(84) bytes of data.
64 bytes from server.example.com (10.10.10.10): icmp_seq=1 ttl=64 time=0.028 ms
64 bytes from server.example.com (10.10.10.10): icmp_seq=2 ttl=64 time=0.032 ms
64 bytes from server.example.com (10.10.10.10): icmp_seq=3 ttl=64 time=0.030 ms

```

If not, run "ifconfig" on the server to determine its IP address.  Now on the Fedora machine, edit the file /etc/hosts (as root) and add the line
```

ip.addr.of.server     servername

```
e.g.,
```
10.10.10.10   myhomeserver
```
Now you can use "myhomeserver" in place of 10.10.10.10.

Since this is a server, you'd be well-served to [assign it a "static" IP address]("https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing") rather than letting the router do it.

---

### Post by karentutor1 on 2017-03-29
Hi sorry still confused.  

At the most basic level, If two computers are attached to Ethernet wires at home, how can I ping or see the other one?

---

### Post by SeijiSensei on 2017-03-29
You mean you just have one wire connecting the two machines?

Whether that will work depends on the physical adapters.  In the past, you would need to use a special type of Ethernet cable called a "crossover."  It connects the transmit pair on one end to the receive pair on the other end, and vice versa.  Newer adapters have auto-sensing circuitry that work with ordinary Ethernet cables.  So the first step is to make sure both machines' network cards have their lights on when connected with the cable.  If they do not light up, you'll need a different method, either a [crossover cable]("https://www.newegg.com/Product/Product.aspx?Item=N82E16812119153") or a [network hub or switch]("https://www.neweggbusiness.com/Product/Product.aspx?Item=9B-33-122-005").  With the latter you just plug both computers into the switch and let it manage the physical connection.

If you have an Internet connection with a router, you can use the Ethernet ports on the back of that device.  Most routers come with a four-port Ethernet switch built in.  Use the "LAN" ports; the "WAN" port connects upstream to the Internet.  The router will assign addresses to the machines automatically using something called DHCP.

If you don't have a router involved, the two machines will need to have IP addresses assigned manually to their network connections in the same IP "subnet."  Use a private address space like 10 or 192.168.  So on the server you could assign it the address 10.10.10.1 and assign the Fedora box 10.10.10.2.  You can then ping each end by IP address.  Ubuntu and Fedora use different methods for assigning static addresses.  I gave you a link to the Ubuntu documentation above; on Fedora I believe you can use the command-line "setup" utility, or edit the files /etc/sysconfig/network and /etc/sysconfig/network-scripts/ifup-eth0.

To see which IP address each machine has, enter "ifconfig" at the command prompt.  You'll see something like this:

```
eth0      Link encap:Ethernet  HWaddr 38:2c:4a:c5:70:6c  
          inet addr:192.168.101.1  Bcast:192.168.101.255  Mask:255.255.255.0
          inet6 addr: fe80::3a2c:4aff:fec5:706c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

```

This says the Ethernet adapter on this machine, called "eth0," has been assigned the address 192.168.101.1.  The "broadcast (Bcast)" and "netmask (Mask)" addresses are usually determined automatically.

You can also use ifconfig to assign addresses temporarily, though they won't be preserved by a reboot.  To assign eth0 192.168.101.1 you would use
```
sudo ifconfig eth0 192.168.101.1
```

If this doesn't make sense, please describe how the computers are connected now.  Do you have a router?  Are you just wiring them together directly?

---

### Post by karentutor1 on 2017-03-29
Hi sorry 

I have two different computers.  They are in different rooms.  Each has its own Ethernet cable.

I would like to be able to ping one from the other and "see the other computer" from the first.

If this is complicated, I would be happy to have suggested reading or link?

---

### Post by SeijiSensei on 2017-03-29
To what are those cables connected now?

---

### Post by vidtek on 2017-03-29
> **karentutor1 said:**
> Hi sorry still confused.  

At the most basic level, If two computers are attached to Ethernet wires at home, how can I ping or see the other one?

Karen-

As Ssei says, you first need to assign a static IP (v4) address to each one.  The actual address you assign will depend on the router to which they are attached.

Go to a command prompt at each machine and type in ifconfig -a, or if you have a gui network control interface, that will show you.

That will tell you what ip addresses are already assigned (probably by the router)

They will be in the range 192.168.*.*  or 10.10.*.* dependent on the manufacturer of your router. 

At this stage you don't have to worry about ipv6 addresses.  

If your router was supplied by your ISP (most are) there will be a web interface where you can access the settings.

If you are unsure about which setting to change if any, come back to us with the make and model number and we will assist.

Most routers have a facility for assigning a single ip address to a particular computer or peripheral, that way you can avoid having to set each individual machine.

A couple of things to note:

You may get frustrated by the ip not changing in the interface or refusing to be assisgned a different address.  This is because they have what is called "ttl" or time to live.
Once a machine address has been recognised on the network, even if it is switched off it will persist as a phantom for up to 20 minutes.  To overcome this, switch everything off that is network connected for a couple of mins, then restart, the router being the first to be switched on.

For a network newbie, it is easier to set an assigned ip at the web interface of your router, as you don't need to mess about or know your gateway address or dns addresses, that becomes automatic.

To answer your last question, how do you ping, get the addresses set up first and you will be able to see the other computers.

Cheers, Tony.

---

### Post by karentutor1 on 2017-03-29
Hi ok in the ifconfig -a command.

I see the data.

The first computer is a desktop so I have GUI and the second is an ubuntu server with only terminal.

I am comfortable with terminal commands.

Pls note both  my systems are using 192.168.x.x which I understand is non routable.

What commands to set up the static ip and how to chose numbers to assign?

Thanks a lot!!
Karen

---

### Post by ajgreeny on 2017-03-29
So from the desktop machine use command ping 192.168.x.x where that IP is for the server that you found from the ifconfig command.

This is assuming both machines are attached to the same router. 
I am not quite sure what you mean by "my systems are using 192.168.x.x which I understand is non routable."
More explanation please.

---

### Post by SeijiSensei on 2017-03-29
If both machines are plugged into the same router, they will automatically get addresses from DHCP.  If you run ifconfig on both machines, you should be able to determine which addresses they have.  Suppose the Ubuntu box has 192.168.1.50.  Then you should be able to run "ping 192.168.1.50" on the Fedora box and see the replies.

If you need static addressing, please consult my postings earlier.  The first one points to documentation for Ubuntu; in my second post I suggest methods for Fedora.  Only the server really needs a static address so any machines on your network can reliably find it.  

> I am not quite sure what you mean by "my systems are using 192.168.x.x which I understand is non routable."
I think she means that machines have [RFC1918 private addresses]("https://tools.ietf.org/html/rfc1918").  They are "routable" within the local network, but they won't work on the Internet without a NAT router of some kind in between.

---

### Post by vidtek on 2017-03-29
Karen-

We need the model number and make of the router

---

### Post by karentutor1 on 2017-03-29
Hi I'm at work and won't be able to pick this up again until tomorrow noon GMT

I'll review and progress then 

Thanks to you all!!

---

### Post by yancek on 2017-03-29
You indicate that each computer has it's own ethernet cable, what you don't say is what the other end of the cables are attached to.  Do you have a router?  If you have a router and you have your different computers booted, you can get the IP addresses of any/all of them with a command similar to the one below.  This would be for a network in the range:  192.168.0:  

```
nmap -sP 192.168.0.*
```

You can get the router ip with:  route -n if you don't know it.

There should be no problem networking locally with that type address but as stated above, you can't access that ip from outside the LAN.  If you want to do more than ping, you need to have something like nfs installed which probably is by default with a server version.

---

### Post by karentutor1 on 2017-03-30
Hi all

Reviewing the above, I think I have enough info to do this.

If I have further questions, they will be more specific, so I will indicate answered on this thread.

Thank you all so very much for your time! :)

Best regards
Karen

---


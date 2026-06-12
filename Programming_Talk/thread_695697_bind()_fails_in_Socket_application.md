---
title: "bind() fails in Socket application"
date: 2008-02-13
forum: Programming Talk
---

### Post by tunelabguy on 2008-02-13
I'm using sockets to develop a simple LAN server, but I'm having trouble calling **bind()**.  When I do this:

  [INDENT]my_addr.sin_family = AF_INET;
  my_addr.sin_port = htons(2001);
  my_addr.sin_addr.s_addr = **inet_addr("192.168.0.230")**;
  rc = bind(sock, (struct sockaddr *)&my_addr, sizeof my_addr);[/INDENT]

I get rc = -1 (error return).  But if I do this:

[INDENT]  my_addr.sin_family = AF_INET;
  my_addr.sin_port = htons(2001);
  my_addr.sin_addr.s_addr = **INADDR_ANY;**
  rc = bind(sock, (struct sockaddr *)&my_addr, sizeof my_addr);[/INDENT]

then rc = 0, so bind() succeeds, but when I check the bound address with this:

 [INDENT]   struct sockaddr_in sa;
    unsigned int len = sizeof(sa);
  getsockname(sock, (sockaddr*)&sa, &len);
  BoundAddr = ntohl(sa.sin_addr.s_addr);
  BoundPort = ntohs(sa.sin_port);
[/INDENT]
I get BoundAddr = 00000000.  BoundPort does turn out correct at 2001.  But I need to make the IP address a LAN address, such as 192.168.0.1.  How can I bind to a known fixed IP address?  The server is for a custom client that I am developing on the other end of the Ethernet cable.

Robert Scott
Ypsilanti, Michigan

---

### Post by ruy_lopez on 2008-02-13
Try htonl():

```

#include <netinet/in.h>

my_addr.sin_addr.s_addr = htonl("192.168.0.230");
```

htonl changes host byte ordering to network byte ordering. 

INADDR_ANY is typically zero.

I can't remember if you use quotes with it, so try with/without.

---

### Post by tunelabguy on 2008-02-13
I think **inet_addr**("192.168.0.230") already delivers network order.

Robert Scott
Ypsilanti, Michigan

---

### Post by lnostdal on 2008-02-13
you gotta clear the struct with *memset*, like this:

```

my_addr.sin_family = AF_INET;
my_addr.sin_port = htons(2001);
my_addr.sin_addr.s_addr = inet_addr("192.168.0.230");
memset(my_addr.sin_zero, '\0', sizeof(my_addr.sin_zero));
rc = bind(sock, (struct sockaddr *)&my_addr, sizeof my_addr);

```

also, when you get an error (in this case signified by *-1* as return value from *bind*) you can check what it actually is by using *errno* and *strerror* (see the man pages)
edit: or maybe *perror* is simpler in this case .. =)

---

### Post by public_void on 2008-02-13
Try using
```
 
int inet_aton(const char *cp, struct in_addr *inp)

```For example:
```

my_addr.sin_family = AF_INET;
my_addr.sin_port = htons(2001);
inet_aton("192.168.0.230", &my_addr.sin_addr);
rc = bind(sock, (struct sockaddr *)&my_addr, sizeof my_addr);

```

Probably better than inet_addr because inet_addr can return -1 which is "255.255.255.255".

---

### Post by tunelabguy on 2008-02-13
> Try using
```
 
...
inet_aton("192.168.0.230", &my_addr.sin_addr);
...

```


bind() still fails.  Perhaps it is the way my ubuntu is set up?  I have eth0 (the wired LAN card I want to use) and eth0 (a separate wi-fi card linked to my home hotspot for Internet access).  In Network properties I set up eth0 for a static IP address of 192.168.0.230.  I was hoping that INADDR_ANY would assign that address, but no luck.  INADDR_ANY results in IPaddr = 0.0.0.0.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by ruy_lopez on 2008-02-13
I think inet_pton is the way I did it before:

```
#include <arpa/inet.h>

inet_pton(AF_INET, "192.168.1.3", &my_addr.sin_addr);
```

You don't have to zero this afterwards. Just zero the whole sockaddr_in struct after it's declared.

```
bzero(&my_addr, sizeof(my_addr));
```

However, unless you have a special reason, INADDR_ANY usually does the trick.

---

### Post by tunelabguy on 2008-02-13
> ...However, unless you have a special reason, INADDR_ANY usually does the trick.

Yes, that's what I wanted to do at first.  But I don't know what IP address gets assigned if I use INADDR_ANY.  I tried to find out with the call to getsockname() after the bind, and it said the assigned address was 0.0.0.0, which is obviously wrong.  So I guess the real question is, where in my ubuntu system do I assign the IP address that will get used when INADDR_ANY is specified?  I must know this in order to write the client software that will talk to this server.  Keep in mind I have eth0 and eth1 on my system.

By the way, thanks for the quick response.  This forum is phenomenal!

Robert Scott
Ypsilanti, Michigan USA

---

### Post by ruy_lopez on 2008-02-13
0.0.0.0 is the ip address for INADDR_ANY, which means **any** address you have assigned to an interface.

If your server's network interface uses 192.168.0.230, then that's what the client will connect to.

You can specify the address if you want, using inet_pton. It doesn't make much difference.

Start your server, then run ```
netstat -antp
```. You should see 0.0.0.0:PORT for Local Address and Foreign Address, and the name of the server. 

When you connect to the server from the client, it cannot connect to 0.0.0.0, since that's not a valid address. You supply the ip address according to the ip assigned to the servers interface, not the 0.0.0.0 which the socket listens on (that's just a wildcard). Run ```
ifconfig
``` to find out what IP address is assigned to your server's interface.

Once you've connected successfully, run the netstat command again.

You can even connect the client and server using the same machine. Run the server in one window, then open another. Then give the client this address: 127.0.0.1. That's the loopback interface. It's useful for testing, so you can run both server and client on the same system. (that's why INADDR_ANY is better, when you are testing, otherwise you'll be shuttling back and forth between systems.)

---

### Post by tunelabguy on 2008-02-13
> **ruy_lopez said:**
> ..Run ifconfig to find out what IP address is assigned to your server's interface...

Maybe that is the problem.  When I run ifconfig I get:
```

eth0      Link encap:Ethernet  HWaddr 00:14:2A:1E:CA:CC  
          inet6 addr: fe80::214:2aff:fe1e:cacc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:103 errors:0 dropped:0 overruns:0 frame:0
          TX packets:67 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:25404 (24.8 KB)  TX bytes:10575 (10.3 KB)
          Interrupt:17 Base address:0xdc00 

```

I don't see my address of 192.168.0.230 anywhere in here, even though that is the static IP address that I entered in the system network configuration for this port.  Also my client is failing to connect, so I can't follow your next step of running netstat after establishing a connection.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by Zwack on 2008-02-13
Ruy is correct...

Most daemons listen on ANY address, which means that if you have five network cards on your system then it listens on port X on all five.

If you want it to only listen on one network card then you need to bind it to the address of that card.  

0.0.0.0 is acceptable, your client can talk to the server if it talks on the right port.  If there is a reason that you want to listen only on a specific card then set the IP address, otherwise listen on all cards.


Following up on your response to that, if you don't see that card with that IP address I am suspicious of your network configuration... particularly as you claim that both of your cards are eth0.

Only one should be eth0... did you disable your wired card?  
Z.

---

### Post by ruy_lopez on 2008-02-13
> I don't see my address of 192.168.0.230 anywhere in here, even though that is the static IP address that I entered in the system network configuration for this port. Also my client is failing to connect, so I can't follow your next step of running netstat after establishing a connection.

You'll need to assign an ip address using the network config gui: System -> Network.

Or just practice getting the code running using the loopback interface.

Best of luck

---

### Post by tunelabguy on 2008-02-13
OK, I used Network Tools to look at eth0, and at first it only had a IPv6 address entry, but after I re-entered the IPv4 address, it now shows up, and ifconfig also shows:

          inet addr:192.168.0.230  Bcast:192.168.0.255  Mask:255.255.255.0

But my client still will not connect.  It is running on a Windows machine, so I can't use the loopback port.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by tunelabguy on 2008-02-13
OK, I have used tcpdump to monitor activity on eth0, and the problem may be with my Windows client program.  Here is what happens:

I have been using the Windows hosts file to define the IP address for a named host, and then my client program references that named host.  But when I make my client program attempt to connect to a named host that is not in the hosts file, then tcpdump on my Linux machine shows attempted address resolution activity on eth0.  But when the client program tries to connect to a host that is named in the Windows  hosts file (and given the IP address of 192.168.0.230) then I see NO activity at all on eth0 (according to TCP dump).

However, when I tried this same experiment, substituting for the Linux server machine, another device with a similar address (192.168.0.1) then the client program reports a successful connection.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by ruy_lopez on 2008-02-13
Can't you supply the client with a simple IP address to connect to? Does it require a hostname? 

I know next to nothing about Windows, except how to fix my niece's system when it gets infested with spyware.

I'm pretty sure that the problem isn't to do with the code. You could try posting in the Networking & Wireless forum.

Can you ping the server system from the client? (Does Windows even have ping?) As soon as you said it was a windows system, I knew I couldn't help you.

Best of luck.

---

### Post by Zwack on 2008-02-13
does netstat show the daemon listening on the port now?

If it's not listening then there is your problem...

If it is listening try using telnet to connect to the port...

You might not be able to type the protocol but your linux box should be able to connect to itself on that port and telnet will show it connected...

I hope that this helps,

Z.

---

### Post by tunelabguy on 2008-02-13
> **Zwack said:**
> does netstat show the daemon listening on the port now?

Yes, but it shows:
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 *:2001                  *:*                     LISTEN   

> 
If it is listening try using telnet to connect to the port...


..have done so using telnet command "o 192.168.0.230 2001".  Connection failed there too.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by tunelabguy on 2008-02-14
Well, everything is working now.  I think I forgot to turn off the ZoneAlarm firewall on the Windows machine running the client.  It really doesn't like port 2001.  I should have known something was basically wrong when I couldn't get PING to work in either direction.  Now it does.  In any case, using INADDR_ANY for the bind() address worked just fine.  Bind() worked.  Accept() worked.  And Recv() worked.  Sorry for all the trouble.  But I sure have learned a lot about network debugging tools.  Thanks to everyone who contributed.

Robert Scott
Ypsilanti, Michigan USA

---

### Post by Zwack on 2008-02-14
Glad to be of help...

I'm confused as to how your telnet connection failed to work...  I was suggesting that on the linux box you telnet to the appropriate port on itself.  If that connection is refused then it's a problem with the listener... if that one works then it's not...

i.e. if Linux box can talk to itself problem is not on the linux box end.  If it can't then problem is elsewhere.  

Z.

---


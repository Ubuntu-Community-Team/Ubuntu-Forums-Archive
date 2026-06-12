---
title: "find machine ip address"
date: 2009-04-24
forum: Programming Talk
---

### Post by ggreco on 2009-04-24
I've the following code that works on every linux variant I tried (including various debian servers) except with ubuntu (tried with 8.04 and 9.04), what's wrong with it:

```

in_addr_t get_local_address()
{
    char ac[80];
    struct hostent *phe;

    if (gethostname(ac, sizeof(ac)) == SOCKET_ERROR)
        return INADDR_NONE;
   
    std::cerr << "Hostname: <" << ac << ">\n";

    if ((phe = gethostbyname(ac) )== 0) 
        return INADDR_NONE;

    std::cerr << "Available addresses:\n";
    for (int i = 0; phe->h_addr_list[i] != 0; ++i) {
	in_addr_t addr;
	memcpy(&addr, phe->h_addr_list[i], sizeof(addr));
        struct in_addr a;
        a.s_addr = addr;

        std::cerr << "Address " << i << " - " << inet_ntoa(a) << '\n';

        // avoid local addresses
        if (((unsigned char *)&addr)[0] != 127)
            return addr;
    }    
    return INADDR_NONE;
}

```

ifconfig returns the correct address (192.168.8.40) that I'd like to grab with the previous function:

```

eth0      Link encap:Ethernet  HWaddr 00:13:49:25:73:b4  
          inet addr:192.168.8.40  Bcast:192.168.8.255  Mask:255.255.255.0
          inet6 addr: fe80::213:49ff:fe25:73b4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:302772 errors:0 dropped:0 overruns:0 frame:0
          TX packets:234818 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:171691551 (171.6 MB)  TX bytes:58548246 (58.5 MB)
          Interrupt:18 Base address:0xf600 

eth1      Link encap:Ethernet  HWaddr 00:1c:25:4e:17:54  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Base address:0xdead 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8338 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8338 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1498751 (1.4 MB)  TX bytes:1498751 (1.4 MB)

```

I suppose the problem is that /etc/hosts contains only the local address reference for "nevada" (the hostname returned also by gethostname()) and that gethostbyname() doesn't check the DNS since it finds an answer in /etc/hosts.

```

127.0.0.1	localhost
127.0.1.1	nevada

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

The problem is that this behaviour is the default one with a "fresh install", so I cannot rely on the fact users has a "correct" /etc/hosts...

There is another way to get the current ip address used for outbound TCP/IP communications without doing ugly things like grepping ifconfig or route command output?

---

### Post by rlzyoner on 2009-04-24
I'm not too sure but you may get more luck in the programming thread

---


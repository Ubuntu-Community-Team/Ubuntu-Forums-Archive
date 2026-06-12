---
title: "[SOLVED] Socket - Get IP of server and client"
date: 2007-11-07
forum: Programming Talk
---

### Post by rockballad on 2007-11-07
Hi,

I'm trying to program socket C/C++ on Linux, using Ubuntu GG. I have some questions:

- gethostbyname("mylaptop") returns 127.0.1.1 instead of 192.126.1.11 (as I expect). How can I get the latter IP? "mylaptop" is the computer name. Because my client will run on another computer (Windows XP), the LAN IP is needed, isn't it?

- how to get IP of connected client?

Thanks in advance!

---

### Post by PaulFr on 2007-11-07
1. AFAIK, you have to get a socket, then do a SIOCGIFCONF ioctl on it to get all the addresses available on the local system, then you have to loop over the returned structures to eliminate the loopback addresses and the 127. addresses. **man netdevice** for details, or google for "enumerating interfaces in Linux".

2. **getpeername** should give you the info.

---

### Post by rockballad on 2007-11-07
Thank you, PaulFr, but I'm not yet familiar with such a concept as SIOCGIFCONF ioctl. I do a quick search but still confused. I just wonder how to get the LAN IP (192.168.x.x), not the local IP (127.x.x.x). Could you give me a sample, please? I just learn about socket recently. In Windows, it works as I expected.

---

### Post by the_unforgiven on 2007-11-07
> **rockballad said:**
> Hi,

I'm trying to program socket C/C++ on Linux, using Ubuntu GG. I have some questions:

- gethostbyname("mylaptop") returns 127.0.1.1 instead of 192.126.1.11 (as I expect). How can I get the latter IP? "mylaptop" is the computer name. Because my client will run on another computer (Windows XP), the LAN IP is needed, isn't it?

- how to get IP of connected client?

Thanks in advance!
As per the manpage of [gethostbyname()]("http://linux.die.net/man/3/gethostbyname"), the member h_addr_list of struct hostent is a NULL-terminated **list** of IP addresses.
So, I guess, you can just do something like:
```
char* ptr;
int counter = 0;
while((ptr = hosts.h_addr_list[counter++]))
{
	if(strstr(ptr, "127.") == ptr)
	{
		// ptr begins with 127. - localnet
		// skip it.
	}
	else
	{
		printf("IP: %s\n", ptr);
	}
}

``` where hosts is the struct hostent* returned by gethostbyname().
HTH ;)

---

### Post by rockballad on 2007-11-07
Thanks, **the_unforgiven!** Your solution should work. But when I try to ping another computer, it returns "unknown host"! I get IP from "www.google.com", and it's okay. I can also browse to another computer on my LAN (menu Places -> Network), but I can't ping using these hosts. It may now turn to my Ubuntu problem. Why I can't ping to another computer like that (did notice about upper/lower case)

---

### Post by the_unforgiven on 2007-11-07
> **rockballad said:**
> Thanks, **the_unforgiven!** Your solution should work. But when I try to ping another computer, it returns "unknown host"! I get IP from "www.google.com", and it's okay. I can also browse to another computer on my LAN (menu Places -> Network), but I can't ping using these hosts. It may now turn to my Ubuntu problem. Why I can't ping to another computer like that (did notice about upper/lower case)
These two are different issues.
Resolving a hostname using gethostbyname() is a DNS affair whereas ping is a different thing in itself.
[Ping]("http://en.wikipedia.org/wiki/Ping") uses an ICMP "echo request" which can be blocked at the firewall level. In fact, many hosts do block ICMP echo request-responses.

So, you could check up your own firewall settings if it's allowing ICMP echo (ping) requests to go out of your computer - or maybe your LAN firewall is blocking all ICMP traffic?

Are you able to manually ping any host on the internet - say google.com?
If that succeeds, then the firewall config should be OK - allowing ping traffic. Then, the problem might be something else.

---

### Post by rockballad on 2007-11-07
yeah, I can ping google.com, 

64 bytes from cf-in-f103.google.com (74.125.19.103): icmp_seq=1 ttl=239 time=642 ms
64 bytes from cf-in-f103.google.com (74.125.19.103): icmp_seq=3 ttl=239 time=766 ms
...
I just set some first steps on Ubuntu, So what's the problem when I couldn't ping other computer on LAN? It's a big problem to me.

---

### Post by the_unforgiven on 2007-11-08
> **rockballad said:**
> yeah, I can ping google.com, 

64 bytes from cf-in-f103.google.com (74.125.19.103): icmp_seq=1 ttl=239 time=642 ms
64 bytes from cf-in-f103.google.com (74.125.19.103): icmp_seq=3 ttl=239 time=766 ms
...
I just set some first steps on Ubuntu, So what's the problem when I couldn't ping other computer on LAN? It's a big problem to me.
Looks like your LAN configuration doesn't honour ping requests - it's possible to drop ping requests at the firewall level as I said earlier.
So, your gateway might be configured to drop ICMP echo requests to any LAN machine.

This is just a guess - you need to figure out where the ICMP echo requests to the LAN are getting dropped (or ask your network admin :))

---

### Post by rockballad on 2007-11-08
oops! I found one thing: 

I can ping my other computer (both on LAN), it's name is HOME01, it's IP is 192.168.1.5: command "ping 192.168.1.5" ok. But command "ping HOME01" returns "unknown host HOME01", although command "net lookup HOME01" returns "192.168.1.5".

OK, I'll investigate it later. Now I'd like to turn to the my old question, how to get my computer IP on the LAN in C/C++. All ways above doesn't work yet. 

Note: I found out how to get connected client IP:

```

struct sockaddr_in m_addr;
socklen_t len;

en = sizeof m_addr;
getpeername(m_sock, (struct sockaddr*)&m_addr, &len);
printf("Peer IP address: %s\n", inet_ntoa(m_addr.sin_addr));

```

Thank PaulFr! HIH for someone!

---

### Post by PaulFr on 2007-11-09
Please try out the following code for the SIOCGIFCONF ioctl: ```
#include <stdio.h>
#include <sys/ioctl.h>
#include <sys/socket.h>
#include <net/if.h>
#include <netinet/in.h>
  
int main(int ac, char** av)
{
      struct ifreq   buffer[32];
      struct ifconf  intfc;
      struct ifreq  *pIntfc;
      int            i, fd, num_intfc;
  
      intfc.ifc_len = sizeof(buffer);
      intfc.ifc_buf = (char*) buffer;
  
      if ((fd = socket(AF_INET, SOCK_DGRAM, 0)) < 0)
      {
          perror("socket() failed");
          return 1;
      }
  
      if (ioctl(fd, SIOCGIFCONF, &intfc) < 0)
      {
          perror("ioctl SIOCGIFCONF failed");
          return 1;
      }
  
      pIntfc    = intfc.ifc_req;
      num_intfc = intfc.ifc_len / sizeof(struct ifreq);
  
      for (i = 0; i < num_intfc; i++)
      {
          struct ifreq *item = &(pIntfc[i]);
          printf("Interface # %d -> %s: IP %s\n",
               i, item->ifr_name,
                 inet_ntoa(((struct sockaddr_in *)&item->ifr_addr)->sin_addr));
      }
      return 0;
}
```You can change 32 to the maximum number of interfaces you expect.

---

### Post by rockballad on 2007-11-09
> **PaulFr said:**
> Please try out the following code for the SIOCGIFCONF ioctl: ```
#include <stdio.h>
#include <sys/ioctl.h>
#include <sys/socket.h>
#include <net/if.h>
#include <netinet/in.h>
  
int main(int ac, char** av)
{
      struct ifreq   buffer[32];
      struct ifconf  intfc;
      struct ifreq  *pIntfc;
      int            i, fd, num_intfc;
  
      intfc.ifc_len = sizeof(buffer);
      intfc.ifc_buf = (char*) buffer;
  
      if ((fd = socket(AF_INET, SOCK_DGRAM, 0)) < 0)
      {
          perror("socket() failed");
          return 1;
      }
  
      if (ioctl(fd, SIOCGIFCONF, &intfc) < 0)
      {
          perror("ioctl SIOCGIFCONF failed");
          return 1;
      }
  
      pIntfc    = intfc.ifc_req;
      num_intfc = intfc.ifc_len / sizeof(struct ifreq);
  
      for (i = 0; i < num_intfc; i++)
      {
          struct ifreq *item = &(pIntfc[i]);
          printf("Interface # %d -> %s: IP %s\n",
               i, item->ifr_name,
                 inet_ntoa(((struct sockaddr_in *)&item->ifr_addr)->sin_addr));
      }
      return 0;
}
```You can change 32 to the maximum number of interfaces you expect.


**GREAT!** It makes the **difference!!!** 

I investigated for it all day long but got no success. Now you help me out! Thanks very very much! =D>

Wish you all the best!

Cheers :KS

---


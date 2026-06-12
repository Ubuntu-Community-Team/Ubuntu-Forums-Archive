---
title: "Get IP for localhost"
date: 2009-01-01
forum: Programming Talk
---

### Post by nebu on 2009-01-01
i am trying to get my IP address with this code in c++


```

#inlcude <netdb.h>

void getMyIP()
{
    hostent* localHost = gethostbyname("localhost");
    char* localIP = inet_ntoa(*(struct in_addr *)*localHost->h_addr_list);
    printf("MyIP: %s(%s)\n",localIP,localHost->h_name);
}

```

why is this giving me 127.0.0.1......

how do i get my lan IP through this??

---

### Post by pp. on 2009-01-01
localhost ***is*** 127.0.0.1

---

### Post by Reiger on 2009-01-01
Localhost is the domain name of the special loop-back device which routes any and all TCP requests to 127.0.0.1 (its IP address) from your machine back to it. This is/can be used for things like IPC, so some of your OS services can send messages to each other back and forth using special port addresses in a platform independent manner, without requiring prior knowledge of the Process ID's of each other (which is how Pipes work).

It is completely detached from *any* network you may be connected to and does not function as your IP address within any such network. If you must retrieve your own IP address the easiest way would be to parse the output of an "ifconfig" call to the system -- provided that you are on a Linux/Unix like environment.

EDIT: The equivalent call in Windows would be "ipconfig /all".

---

### Post by nebu on 2009-01-01
> **Reiger said:**
> Localhost is the domain name of the special loop-back device which routes any and all TCP requests to 127.0.0.1 (its IP address) from your machine back to it. This is/can be used for things like IPC, so some of your OS services can send messages to each other back and forth using special port addresses in a platform independent manner, without requiring prior knowledge of the Process ID's of each other (which is how Pipes work).

It is completely detached from *any* network you may be connected to and does not function as your IP address within any such network. If you must retrieve your own IP address the easiest way would be to parse the output of an "ifconfig" call to the system -- provided that you are on a Linux/Unix like environment.

EDIT: The equivalent call in Windows would be "ipconfig /all".
@reiger
how do i do that in c++??

is there no way for me to get my IP for the internal lan network using the code i wrote??

---

### Post by Reiger on 2009-01-01
Not sure but if you use:
```
ifconfig <device-name>
```
Like so:
```
ifconfig wlan0
```
You get output such as this:
```

wlan0     Link encap:Ethernet  HWaddr [Your MAC address]
          inet addr:[Your IPv4 address]  Bcast:192.168.2.255  Mask:[Your Net Mask]
          inet6 addr: [Your IPv6 address] Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:114691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:76745 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:115993168 (110.6 MB)  TX bytes:10451360 (9.9 MB)
          Interrupt:18 Memory:f89f0000-f8a00000

```

Those [You ... addresss/mask] have all a distinct pattern.

---

### Post by nebu on 2009-01-01
thats fine.... what i wanted to know was that how do i extract the inet_addr from the output of ifconfig and use it in a c/c++ program.....

---

### Post by dwhitney67 on 2009-01-01
I wrote and posted a C++ solution a while back on this forum on how to use pipe() to obtain the results from a system command, such as 'ifconfig'.

Alternatively, you could just open and examine the /proc/net/rt_cache file.  You will need to know the (ethernet) interface you are interested in (e.g. eth0).

Here's a silly program that solves this approach:
[php]
#include <boost/tokenizer.hpp>
#include <fstream>
#include <string>
#include <iostream>
#include <cstdlib>


int main(int argc, char** argv)
{
  if (argc < 2)
  {
    std::cerr << "Usage: " << argv[0] << " <interface>" << std::endl;
    return 1;
  }

  if (std::string("lo") == argv[1] || std::string("localhost") == argv[1])
  {
    std::cout << "ip address for " << argv[1] << ": 127.0.0.1" << std::endl;;
    return 0;
  }

  std::fstream file("/proc/net/rt_cache", std::ios::in);

  if (file)
  {
    std::string line;
    bool        done = false;

    while (getline(file, line) && !done)
    {
      typedef boost::tokenizer< boost::char_separator<char> > Tokenizer;
      boost::char_separator<char> sep("\t ");

      Tokenizer info(line, sep);

      Tokenizer::iterator it = info.begin();

      if (*it == argv[1])
      {
        for (int i = 0; i < 7; ++i, ++it);

        if (*it != "")
        {
          done = true;

          // get the ip address
          const std::string ipaddr = *it;

          std::cout << "ip address for " << argv[1] << ": ";

          // resulting ipaddr string is in reverse order; make it presentable
          for (int i = 3; i >= 0; --i)
          {
            std::string val = "0x";
            val += ipaddr[i*2];
            val += ipaddr[i*2 + 1];

            std::cout << strtod(val.c_str(), 0);

            if (i > 0)
              std::cout << ".";
          }
          std::cout << std::endl;
        }
      }
    }

    if (!done)
    {
      std::cout << "ip address for " << argv[1] << ": unknown" << std::endl;
    }
  }
  else
  {
    std::cerr << "Unable to open /proc/net/rt_cache" << std::endl;
    return 1;
  }

  return 0;
}
[/php]

P.S.  I just thought about something... I have no idea if /proc/net/rt_cache exists on an Ubuntu system!  I wrote the application above on my Fedora system.

---

### Post by The Cog on 2009-01-02
You could see if there is a call like gethostname(), and use that to find the name to pass into gethostbyname(). I'm sure there must be such a call.

"localhost" is guaranteed to be there on all machines, and always gives the loopback address of 127.0.0.1 or ::1.

---

### Post by eckertd on 2009-01-02
gethostname() is provided by unistd.h (see 'man 2 gethostname')

---

### Post by dwhitney67 on 2009-01-02
The OP asked the following question, which it not obtainable with gethostname() nor gethostbyname().
> **nebu said:**
> ...
how do i get my lan IP through this??

---

### Post by eckertd on 2009-01-02
> **dwhitney67 said:**
> The OP asked the following question, which it not obtainable with gethostname() nor gethostbyname().

I made an assumption (perhaps wrong) that since he was looking up localhost with gethostbyname, he just might have an entry in /etc/hosts (or DNS) that would resolve his hostname to his LAN interface IP.  Sorry about that.

Anyway, scroll down [[COLOR="Red"]here[/COLOR] ]("http://kasperd.net/~kasperd/comp.os.linux.development.faq#IP") to Frank Becker's code for a method that works quite well.

---

### Post by dwhitney67 on 2009-01-02
> **eckertd said:**
> ...

Anyway, scroll down [[COLOR="Red"]here[/COLOR] ]("http://kasperd.net/~kasperd/comp.os.linux.development.faq#IP") to Frank Becker's code for a method that works quite well.

Thanks for the link.  The example (first one in Section 30) works quite well.  The OP will hopefully be happy with that.  It's a lot better than the example I provided earlier.

Would you by chance know of a way to obtain the IP address that is assigned by an ISP?  I am behind a Linksys router, so although I can obtain the LAN IP address, it might be useful to obtain the one assigned to my router.

---

### Post by pp. on 2009-01-02
> **dwhitney67 said:**
> I am behind a Linksys router, so although I can obtain the LAN IP address, it might be useful to obtain the one assigned to my router.

I think the Linksys routers might understand both snmp and telnet. Hence, you might be able to ask the router for that and other items of data. 

Otherwise, there's still the web interface which presumably can show a web page showing the required data.

---


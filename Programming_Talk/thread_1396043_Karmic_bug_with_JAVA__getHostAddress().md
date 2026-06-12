---
title: "Karmic bug with JAVA  getHostAddress() ?"
date: 2010-02-01
forum: Programming Talk
---

### Post by n45w73 on 2010-02-01
hi,

im trying to get the LAN address from Karmic

myIp = InetAddress.getLocalHost();
str = myIp.getHostAddress();

but I only get the local 127.0.0.1 instead of the dhcp address the network manager should have  something like  192.168.0.x

getHostAddress()  on PC, Mac an another linux distro return the right thing ....  is there some bug in karmic.
btw i tried both java package,  openJDK and sunJRE with the same result...

so it isn't java,  it might be /etc/hosts  not being updated ?

:confused:

---

### Post by TennTux on 2010-02-01
I'm not positive what your issue is but I see a couple of possibilities.

1) A system can have several addresses. As an example you could have a local area net connected to the internet, another that is for internal purposes only  and you could have a loop back address. All of which are valid addresses for your computer. [I suspect this is not your issue]

2) After reviewing the documentation. I see that INetAddress.getLocalHost() has a note saying:
> If there is a security manager, its checkConnect method is called with the local host name and -1 as its arguments to see if the operation is allowed. If the operation is not allowed, an InetAddress representing the loopback address is returned.

You likely have a permissions issue.

---

### Post by dwhitney67 on 2010-02-01
TennTux is right; a system can have multiple interfaces, each supporting an IPv4 and IPv6 address.

Here's some code that can be used to get the IP addresses assigned to all interfaces, or from a specific interface.
```

import java.net.*;
import java.util.*;

public class GetHost
{
   public static void main(String[] args)
   {
      try
      {
         Enumeration<NetworkInterface> nis = NetworkInterface.getNetworkInterfaces();

         // option 1
         while (nis.hasMoreElements())
         {
            System.out.println("network interface: " + nis.nextElement().toString());
         }

         // option 2 (not recommended)
         System.out.println("eth0 interface: " + NetworkInterface.getByName("eth0"));
      }
      catch (SocketException e)
      {
         System.out.println(e.toString());
      }
   }
}

```
I marked option 2 above as "not recommended" because not everyone will have the same interface aliases.  Although "eth0" is a common alias used by many distros, it may not be (and I'm sure it's not) used by Windoze.

---


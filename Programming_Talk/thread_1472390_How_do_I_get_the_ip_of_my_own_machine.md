---
title: "How do I get the ip of my own machine?"
date: 2010-05-04
forum: Programming Talk
---

### Post by guest_user on 2010-05-04
I am writing a program and I need to get the ip address of my own machine, how do I do it? preferable for it to be IPv6

---

### Post by Portmanteaufu on 2010-05-04
If you want your internal IP (the one issued by your local router), type: ```
ifconfig
```
If you want the IP address issued to you by your ISP, the one you would need to access your home network from elsewhere in the world, try going to a site like [http://ipchicken.com]("http://ipchicken.com").

ifconfig will give you your IPv4 and IPv6 internal addresses. In order to get an IPv6 external address, you might have to make sure your browser requests the webpage using IPv6. (Not sure about that, anyone know?)

---

### Post by Queue29 on 2010-05-04
```

wget www.whatismyip.com/automation/n09230945.asp -O - -o /dev/null

```

---

### Post by Portmanteaufu on 2010-05-04
> **guest_user said:**
> I am writing a program and I need to get the ip address of my own machine, how do I do it? preferable for it to be IPv6

Alternatively, if you're just trying to connect to your own box (i.e. from the same box), you can always use ```
127.0.0.1
```as your IP address or ```
localhost
``` as your hostname.

---

### Post by guest_user on 2010-05-04
what I mean is what kind of function calls do I make to get the actual ip(NOT 127.0.0.1) of my machine or the network interface my application is using?

---

### Post by VernonA on 2010-05-04
You need to specify which programming language you are writing your application in, as the specific function call is language-dependent.

---

### Post by Portmanteaufu on 2010-05-04
> **guest_user said:**
> what I mean is what kind of function calls do I make to get the actual ip(NOT 127.0.0.1) of my machine or the network interface my application is using?

Ahh.

This is a good example of why providing details in the original post is such a fine idea.

What language?

---

### Post by Charlietje on 2010-05-04
> **guest_user said:**
> I am writing a program and I need to get the ip address of my own machine, how do I do it? preferable for it to be IPv6

does this help you?

```
ip -6 a

```

---

### Post by lavinog on 2010-05-04
Attached is a python script I wrote that has different ways of getting the ip4 address.  Haven't done anything with ip6 yet.

---

### Post by soltanis on 2010-05-05
Look into the socket.getaddrinfo function. This function will look complicated; to see why it is, read Beej's guide to Network Programming on the getaddrinfo() C function. The Python interface is obviously much easier than the C one.

In particular, I wouldn't be concerned with whether you get an IPv6 address or v4 address. Don't try to coerce one into another; use the one that getaddrinfo() gives you, because this one is intended to be correct.

---

### Post by guest_user on 2010-05-05
> **portmanteaufu said:**
> ahh.

This is a good example of why providing details in the original post is such a fine idea.

What language?

c/c++

---

### Post by dwhitney67 on 2010-05-05
Long ago I copied this code from a thread posted on this forum (or perhaps it was from LinuxQuestions.org); perhaps it may help you.

```

/*
 *
 * This program is free software, distributed under the terms of
 * the GNU General Public License Version 2. See the LICENSE file
 * at the top of the source tree.
 */

/*! \file
 *
 * \brief getIP address 
 * 
 * \ingroup applications
 */

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <net/if.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <sys/ioctl.h>

char* getIP(const char* interface);

char* getIP(const char* interface)
{
   int iSocket = 0;
   char* IP = 0;

   // Con questa chiamata creiamo la socket per la comunicazione con la ioctl().    
   // create a socket to be used when calling ioctl().
   if ((iSocket = socket(PF_INET, SOCK_DGRAM, 0)) < 0)
   {
      perror("socket");
      return 0;
   }

   // if_nameindex - return all network interface names and indexes    
   struct if_nameindex* pIndex  = if_nameindex();
   struct if_nameindex* pIndex2 = pIndex;
   
   while ((pIndex != NULL) && (pIndex->if_name != NULL))
   {
      struct ifreq req;

      strncpy(req.ifr_name, pIndex->if_name, IFNAMSIZ);

      // ioctl - control a STREAMS device
      if (ioctl(iSocket, SIOCGIFADDR, &req) < 0)
      {
         if (errno == EADDRNOTAVAIL)
         {
            pIndex++;
            continue;
         }
         perror("ioctl");
         close(iSocket);
         return 0;
      }
    
      if (strncmp(interface, pIndex->if_name, strlen(interface)) == 0)
      {
         IP = strdup(inet_ntoa(((struct sockaddr_in*)&req.ifr_addr)->sin_addr));
         break;
      }
      ++pIndex;
   }
    

   // if_freenameindex - free memory allocated by if_nameindex
   if_freenameindex(pIndex2);
    
   close(iSocket);

   return IP;
}

int main(void)
{
   char* IP = getIP("eth0");

   printf("%s\n", IP);

   free(IP);

   return 0;
}

```

---


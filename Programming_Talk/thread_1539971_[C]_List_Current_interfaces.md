---
title: "[C] List Current interfaces"
date: 2010-07-27
forum: Programming Talk
---

### Post by SpinningAround on 2010-07-27
What would be the simplest way to list current active interfaces with C, basically the interfaces that show up when using ifconfig.

---

### Post by VH-BIL on 2010-07-27
Check out [http://www.adamrisi.com/?p=84](http://www.adamrisi.com/?p=84)

---

### Post by SpinningAround on 2010-07-27
> **VH-BIL said:**
> Check out [http://www.adamrisi.com/?p=84](http://www.adamrisi.com/?p=84)

Very interesting code, but it's slightly to complex for me, is there possible any simpler or a guide where the basics are taught?

---

### Post by VH-BIL on 2010-07-27
I don't know. Study the code, it does make sense.

---

### Post by dwhitney67 on 2010-07-27
> **SpinningAround said:**
> Very interesting code, but it's slightly to complex for me, is there possible any simpler or a guide where the basics are taught?

Here's another spin on the reference provided by VH-BIL, however I'm unsure if it handles IPv6...
```

#include <stdio.h>
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <net/if.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <sys/ioctl.h>

int main(void)
{
   int    iSocket = -1;
   struct if_nameindex* pIndex = 0;
   struct if_nameindex* pIndex2 = 0;

   if ((iSocket = socket(PF_INET, SOCK_DGRAM, 0)) < 0)
   {
      perror("socket");
      return -1;
   }

   pIndex = pIndex2 = if_nameindex();

   while ((pIndex != NULL) && (pIndex->if_name != NULL))
   {
      struct ifreq req;

      printf("%d: %s\n", pIndex->if_index, pIndex->if_name);

      strncpy(req.ifr_name, pIndex->if_name, IFNAMSIZ);

      if (ioctl(iSocket, SIOCGIFADDR, &req) < 0)
      {
         if (errno == EADDRNOTAVAIL)
         {
            printf("\tN/A\n");
            ++pIndex;
            continue;
         }

         perror("ioctl");
         close(iSocket);
         return -1;
      }

      printf("\t %s\n", inet_ntoa(((struct sockaddr_in*)&req.ifr_addr)->sin_addr));
      ++pIndex;
   }

   if_freenameindex(pIndex2);

   close(iSocket);
   return 0;
}

```

---

### Post by WitchCraft on 2010-07-27
> **SpinningAround said:**
> What would be the simplest way to list current active interfaces with C, basically the interfaces that show up when using ifconfig.

Open ifconfig with popen, then parse the resulting pointer until EOF, then pclose ifconfig.

---


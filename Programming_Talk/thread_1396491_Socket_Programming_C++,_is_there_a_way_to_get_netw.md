---
title: "Socket Programming C++, is there a way to get network devices(i.e eth0) without bash?"
date: 2010-02-02
forum: Programming Talk
---

### Post by TMagic*04 on 2010-02-02
Technology: C++ / Socket programming
OS: FC11

Hi,

I'm writing a network client, and at startup I want the app to get a collection of any type which contains all of the connected network devices (specifically eth0 and wlan0) for the machine, and the machines corresponding hardware address for each network connection.

My current idea is a bit inelegant and involves piping output from ifconfig through a series of regexes before writing the information I want to a text file. Ideally (and i'm quite certian there is one somewhere) there is some function within the numerous networking libraries of C++ that will return it (or some object I can pull it from) for me, or if any gurus out there know where in the kernel the struct is which holds this information, I may be able to query it for myself.

If anyone could advise me or give me tips on a good solution to this issue, or just point in the right direction regarding where I can investigate further it would be much appreciated.

---

### Post by Some Penguin on 2010-02-02
Just took a look at the sources in [http://packages.debian.org/source/stable/net-tools](http://packages.debian.org/source/stable/net-tools)

Started looking at ifconfig.c; that led me to a for_all_interfaces macro which was defined in interface.c.  Turns out that it calls an 'if_readlist', which uses if_readlist_proc and if_readconf... and if_readlist_proc reads /proc/net/dev line by line.

Judging from that, there might not be a neat syscall.

---

### Post by dwhitney67 on 2010-02-02
Someone recently posted the following code (in C) here on this forum; you may (will) need to modify it if all you are after is a specific network interface, and not just a listing of all of them.
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

### Post by dwhitney67 on 2010-02-02
Here's another take:
```

/* display info about network interfaces */

#define _BSD_SOURCE

#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>
#include <string.h>
#include <errno.h>
#include <sys/ioctl.h>
#include <sys/types.h>
#include <net/if.h>
#include <net/if_arp.h>
#include <arpa/inet.h>

#define inaddrr(x) (*(struct in_addr *) &ifr->x[sizeof sa.sin_port])
#define IFRSIZE   ((int)(size * sizeof (struct ifreq)))

static int
get_addr(int sock, char * ifname, struct sockaddr * ifaddr) {

  struct ifreq *ifr;
  struct ifreq ifrr;
  struct sockaddr_in sa;

  ifr = &ifrr;
  ifrr.ifr_addr.sa_family = AF_INET;
  strncpy(ifrr.ifr_name, ifname, sizeof(ifrr.ifr_name));

  if (ioctl(sock, SIOCGIFADDR, ifr) < 0) {
    printf("No %s interface.\n", ifname);
    return -1;
  }

  *ifaddr = ifrr.ifr_addr;
  printf("Address for %s: %s\n", ifname, inet_ntoa(inaddrr(ifr_addr.sa_data)));
  return 0;
}

int
main(void)
{
  unsigned char      *u;
  int                sockfd, size  = 1;
  struct ifreq       *ifr;
  struct ifconf      ifc;
  struct sockaddr_in sa;

  if (0 > (sockfd = socket(AF_INET, SOCK_DGRAM, IPPROTO_IP))) {
          fprintf(stderr, "Cannot open socket.\n");
    exit(EXIT_FAILURE);
  }

  ifc.ifc_len = IFRSIZE;
  ifc.ifc_req = NULL;

  do {
    ++size;
    /* realloc buffer size until no overflow occurs  */
    if (NULL == (ifc.ifc_req = realloc(ifc.ifc_req, IFRSIZE))) {
      fprintf(stderr, "Out of memory.\n");
      exit(EXIT_FAILURE);
    }
    ifc.ifc_len = IFRSIZE;
    if (ioctl(sockfd, SIOCGIFCONF, &ifc)) {
      perror("ioctl SIOCFIFCONF");
      exit(EXIT_FAILURE);
    }
  } while  (IFRSIZE <= ifc.ifc_len);

  /* this is an alternate way to get info... */
  {
    struct sockaddr ifa;
    get_addr(sockfd, "ppp0", &ifa);
  }

  ifr = ifc.ifc_req;
  for (;(char *) ifr < (char *) ifc.ifc_req + ifc.ifc_len; ++ifr) {

    if (ifr->ifr_addr.sa_data == (ifr+1)->ifr_addr.sa_data) {
      continue;  /* duplicate, skip it */
    }

    if (ioctl(sockfd, SIOCGIFFLAGS, ifr)) {
      continue;  /* failed to get flags, skip it */
    }

    printf("Interface:  %s\n", ifr->ifr_name);
    printf("IP Address: %s\n", inet_ntoa(inaddrr(ifr_addr.sa_data)));

    /*
      This won't work on HP-UX 10.20 as there's no SIOCGIFHWADDR ioctl. You'll
      need to use DLPI or the NETSTAT ioctl on /dev/lan0, etc (and you'll need
      to be root to use the NETSTAT ioctl. Also this is deprecated and doesn't
      work on 11.00).

      On Digital Unix you can use the SIOCRPHYSADDR ioctl according to an old
      utility I have. Also on SGI I think you need to use a raw socket, e.g. s
      = socket(PF_RAW, SOCK_RAW, RAWPROTO_SNOOP)

      Dave

      From: David Peter <dave.peter@eu.citrix.com>
     */

    if (0 == ioctl(sockfd, SIOCGIFHWADDR, ifr)) {

      /* Select which  hardware types to process.
       *
       *    See list in system include file included from
       *    /usr/include/net/if_arp.h  (For example, on
       *    Linux see file /usr/include/linux/if_arp.h to
       *    get the list.)
       */
      switch (ifr->ifr_hwaddr.sa_family) {
      default:
        printf("\n");
        continue;
      case  ARPHRD_NETROM:  case  ARPHRD_ETHER:  case  ARPHRD_PPP:
      case  ARPHRD_EETHER:  case  ARPHRD_IEEE802: break;
      }

      u = (unsigned char *) &ifr->ifr_addr.sa_data;

      if (u[0] + u[1] + u[2] + u[3] + u[4] + u[5]) {
        printf("HW Address: %2.2x.%2.2x.%2.2x.%2.2x.%2.2x.%2.2x\n",
             u[0], u[1], u[2], u[3], u[4], u[5]);
      }
    }

    if (0 == ioctl(sockfd, SIOCGIFNETMASK, ifr) &&
        strcmp("255.255.255.255", inet_ntoa(inaddrr(ifr_addr.sa_data)))) {
      printf("Netmask:    %s\n", inet_ntoa(inaddrr(ifr_addr.sa_data)));
    }

    if (ifr->ifr_flags & IFF_BROADCAST) {
      if (0 == ioctl(sockfd, SIOCGIFBRDADDR, ifr) &&
          strcmp("0.0.0.0", inet_ntoa(inaddrr(ifr_addr.sa_data)))) {
        printf("Broadcast:  %s\n", inet_ntoa(inaddrr(ifr_addr.sa_data)));
      }
    }

    if (0 == ioctl(sockfd, SIOCGIFMTU, ifr)) {
      printf("MTU:        %u\n",  ifr->ifr_mtu);
    }

    if (0 == ioctl(sockfd, SIOCGIFMETRIC, ifr)) {
      printf("Metric:     %u\n",  ifr->ifr_metric);
    }
    printf("\n");
  }

  close(sockfd);
  return EXIT_SUCCESS;
}

```

---

### Post by TMagic*04 on 2010-02-02
Thanks very much dwhitney67, after a bit of tinkering I managed to get exactly what I needed out of it.

---


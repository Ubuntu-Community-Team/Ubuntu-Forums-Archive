---
title: "C code: how get IP adress"
date: 2010-01-18
forum: Programming Talk
---

### Post by erotavlas on 2010-01-18
Hi all,

can you help me to find a C code that retrieve IP address? I'm not expert programmer about socket and network.
I need simple code that can get the etho address not 127.0.0.1

Thank in advance

---

### Post by Majorix on 2010-01-18
This maybe helps:
[http://forums.debian.net/viewtopic.php?f=8&t=31673](http://forums.debian.net/viewtopic.php?f=8&t=31673)

---

### Post by Neezer on 2010-01-18
> **erotavlas said:**
> Hi all,

can you help me to find a C code that retrieve IP address? I'm not expert programmer about socket and network.
I need simple code that can get the etho address not 127.0.0.1

Thank in advance

Are you looking for your LAN IP address, or your external IP address? I have a script that is written in Python that checks my external IP. If you want I can post it here and maybe you can adapt it to C.

---

### Post by dwhitney67 on 2010-01-18
> **erotavlas said:**
> Hi all,

can you help me to find a C code that retrieve IP address? I'm not expert programmer about socket and network.
I need simple code that can get the etho address not 127.0.0.1

Thank in advance

There is no easy way to do this.  However, it is not impossible.  Two ways I know of involve reading/parsing.

One way is to examine /proc/net/tcp.  If you run your code with root-privileges, then you could alternatively look at /proc/net/arp.  In either case, the file would need to be opened, say using fopen(), and then each line read and parsed for the relevant information that you want.

Another way is to run the command "ifconfig eth0" using popen().  After successfully opening the pipe to the command results, reading/parsing is done very as if you were reading a file.

A third option, of which I have my doubts would work for you, is to try using getaddrinfo().

P.S.  It probably would have been best to ask up front why you need to get the IP address?  Do you need to display it, or are you merely using it for something related to socket programming?

---

### Post by erotavlas on 2010-01-18
> **dwhitney67 said:**
> There is no easy way to do this.  However, it is not impossible.  Two ways I know of involve reading/parsing.

One way is to examine /proc/net/tcp.  If you run your code with root-privileges, then you could alternatively look at /proc/net/arp.  In either case, the file would need to be opened, say using fopen(), and then each line read and parsed for the relevant information that you want.

Another way is to run the command "ifconfig eth0" using popen().  After successfully opening the pipe to the command results, reading/parsing is done very as if you were reading a file.

A third option, of which I have my doubts would work for you, is to try using getaddrinfo().

P.S.  It probably would have been best to ask up front why you need to get the IP address?  Do you need to display it, or are you merely using it for something related to socket programming?

I need C code not python. Not I'm not under root privileges. I find a code that use the third way getaddrinfo(). I need IP to configure SIP program and VLC player.

---

### Post by dwhitney67 on 2010-01-18
> **erotavlas said:**
> I need IP to configure SIP program and VLC player.

This is a vague statement; in what capacity do you need an IP address for these applications?  Could you just not use '/sbin/ifconfig eth0' to view the IP address of your system and then enter it as a preference setting?

Or is this for VLC running on a remote system trying to access a server that you manage?  For this case, register a DNS name for the server.  An easy out is to rely on 'ddclient' to acquire your IP address and associate it with your DynDNS registered DNS name.

---

### Post by erotavlas on 2010-01-19
> **dwhitney67 said:**
> This is a vague statement; in what capacity do you need an IP address for these applications?  Could you just not use '/sbin/ifconfig eth0' to view the IP address of your system and then enter it as a preference setting?

Or is this for VLC running on a remote system trying to access a server that you manage?  For this case, register a DNS name for the server.  An easy out is to rely on 'ddclient' to acquire your IP address and associate it with your DynDNS registered DNS name.


I'm writing a code that use VLC and SIPp and so I have to know the IP address for configuring it. I can make a system call with ifconfig, but it is no elegant...
If there are no other ways I will use this solution.

Whit this code i have partial solved 

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
#include <string.h>
#include <errno.h>
#include <unistd.h>
#include <net/if.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <sys/ioctl.h>

char * getIP();

char * getIP()
{
   int iSocket;
    char * IP;
   // if_nameindex - return all network interface names and indexes    
   struct if_nameindex *pIndex; //, *pIndex2;
   
   // Con questa chiamata creiamo la socket per la comunicazione con la ioctl().    
   if ((iSocket = socket(PF_INET, SOCK_DGRAM, 0)) < 0)
   {
      perror("socket");
      //return -1;
   }

   //pIndex  = pIndex2 = if_nameindex();
   pIndex  = if_nameindex();
   while ((pIndex != NULL) && (pIndex->if_name != NULL))
   {
      struct ifreq req;
      //printf("%d: %s\n", pIndex->if_index, pIndex->if_name);
      strncpy(req.ifr_name, pIndex->if_name, IFNAMSIZ);
      // ioctl - control a STREAMS device
      if (ioctl(iSocket, SIOCGIFADDR, &req) < 0)
      {
         if (errno == EADDRNOTAVAIL)
         {
            printf("N/A\n");
            pIndex++;
            continue;
         }
         perror("ioctl");
         close(iSocket);
         //return -1;
      }
    
    //printf("\t %s\n", inet_ntoa(((struct sockaddr_in*)&req.ifr_addr)->sin_addr));
      
    
        if (pIndex->if_index == 2) {
          //a = *inet_ntoa(((struct sockaddr_in*)&req.ifr_addr)->sin_addr);


    IP = inet_ntoa(((struct sockaddr_in*)&req.ifr_addr)->sin_addr);
    }
        pIndex++;
   }
    

   // if_freenameindex - free memory allocated by if_nameindex
   //if_freenameindex(pIndex2);
    
   close(iSocket);
return IP;

}

int main() {


char * IP = getIP();
printf("%s\n", IP);

return 0;
}
```I have a problem: if the code is compiled a stand-alone program it work well while inside my complex original program i get segmentation fault.

I can't know why...

---

### Post by dwhitney67 on 2010-01-19
I cannot begin to guess how you called your getIP() function in your "real" application; nevertheless, below is a working program with a modified getIP() address function.

Note how I defined a parameter which one can use to specify the interface (eg. eth0) that they are interested in.  Also note that I utilized strdup() to return a bonafide copy of the IP address, so that I can follow up with the safe destruction of the if_nameindex object(s).

In theory, you should be able to place the getIP() prototype in a header file, and reference this header file in your "real" application.  As for the implementation of getIP(), place this in its own module so that you can compile it and then link it with the "real" application.

Here's the modified code:
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
   int iSocket = -1;
   char* IP = 0;
    
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
            ++pIndex;
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

   if (IP)
   {
      printf("%s\n", IP);

      free(IP);
   }

   return 0;
}

```

---

### Post by erotavlas on 2010-01-19
Thank for your help, but the problem is still there...

Both code (my and your) work well as stand-alone program but inside the "real" application produce error.

There are  very strange compilation warning:

```
In file included from stream.c:6:
getIP.h: In function &#8216;getIP&#8217;:
getIP.h:66: warning: implicit declaration of function &#8216;__dont__use__inet_ntoa__use__ast_inet_ntoa__instead__&#8217;
getIP.h:66: warning: passing argument 1 of &#8216;strdup&#8217; makes pointer from integer without a cast
/usr/include/string.h:173: note: expected &#8216;const char *&#8217; but argument is of type &#8216;int&#8217;


```this is the header file getIP.h. Inside "real" application i call it.

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
   int iSocket = -1;
   char* IP = 0;
    
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
            ++pIndex;
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
```

---

### Post by dwhitney67 on 2010-01-19
Can you please show me how you are compiling the code?

P.S.  If you do not have plans to create a separate header file for the getIP() function, you do not need to declare the function prototype.

---

### Post by WitchCraft on 2010-01-19
Aren't all those functions a bit overcomplicated for something that simple?
I think I remember something about getHostName(byte[]), or whatever it is called.


OK, looked it up:
man 3 gethostbyname
for IPv6 use gethostbyname2
ps: #include <netdb.h>
```

    Print out the hostname associated with a specific IP address:

           const char *ipstr = "127.0.0.1";
           struct in_addr ip;
           struct hostent *hp;

           if (!inet_aton(ipstr, &ip))
                   errx(1, "can't parse IP address %s", ipstr);

           if ((hp = gethostbyaddr((const void *)&ip,
               sizeof ip, AF_INET)) == NULL)
                   errx(1, "no name associated with %s", ipstr);

           printf("name associated with %s is %s\n", ipstr, hp->h_name);

```


reverse:
```

include <iostream>
#include <netdb.h>
#include <sys/param.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <fstream>
#include <time.h>
using namespace std;

#define MST (-7)

int main(int argc, char *argv[])
{
	if(argc != 2)
	{
		printf("usage: %s <hostname>\n", argv[0], argv[1]);
		exit(1);
	}
		
	hostent * record = gethostbyname(argv[1]);
	if(record == NULL)
	{
		printf("%s is unavailable\n", argv[1]);
		exit(1);
	}
	in_addr * address = (in_addr * )record->h_addr;
	string ip_address = inet_ntoa(* address);

	// get the current time
	time_t rawtime;
	tm * ptm;
	time ( &rawtime );
	ptm = gmtime ( &rawtime );
	
	cout << argv[1] << " (" << ip_address << ")\n";
	
	// log this information to ipaddr.log
	ofstream ipaddr_log("ipaddr.log", ios::app);
	ipaddr_log << (ptm->tm_hour+MST%24) << ":" << (ptm->tm_min) << " " << argv[1] << " (" << ip_address << ")" << endl;
	ipaddr_log.close();
	return 0;
}

```

---

### Post by dwhitney67 on 2010-01-19
> **WitchCraft said:**
> Aren't all those functions a bit overcomplicated for something that simple?
I think I remember something about getHostName(byte[]), or whatever it is called.


Nice work slick; unfortunately it does not yield the desired results.

The OP wants the IP address assigned to his Network Interface Card (NIC).  Your app only works to retrieve an IP address based on a 'hostname' that may or may not be in the /etc/hosts file.

---

### Post by WitchCraft on 2010-01-19
> **dwhitney67 said:**
> Nice work slick; unfortunately it does not yield the desired results.

The OP wants the IP address assigned to his Network Interface Card (NIC).  Your app only works to retrieve an IP address based on a 'hostname' that may or may not be in the /etc/hosts file.


Well, then the simplest thing is to ifconfig eth0 and read the IP out there using popen.
It would be best to use a simple regex library.
The external you get by downloading ip-adress.com and parse everything out that isn't your IP.

---

### Post by PandaGoat on 2010-01-19
At one point I also needed to retrieve my IP.  Here is what I ended up with:

[php]
guint32 utilities_get_my_ip (const gchar * device)
{
  gint fd;
  struct ifreq ifr;
  
  fd = socket (AF_INET, SOCK_DGRAM, 0);
  ifr.ifr_addr.sa_family = AF_INET;  
  g_strlcpy (ifr.ifr_name, device, IFNAMSIZ-1);
  
  ioctl (fd, SIOCGIFADDR, &ifr);
 
  close (fd);
  return ((struct sockaddr_in *)&ifr.ifr_addr)->sin_addr.s_addr;
}
[/php]

ioctl is the main component here.

**edit** I forgot to mention this requires the network device's name of which you wish to retrieve the IP.  For example, if you are using wireless interner, the name will most likely be wlan0, and if you are using wired internet, the name will most likely be eth0.

---

### Post by erotavlas on 2010-01-20
> **dwhitney67 said:**
> Can you please show me how you are compiling the code?

P.S.  If you do not have plans to create a separate header file for the getIP() function, you do not need to declare the function prototype.

The real application is open source iPBX Asterisk. I'm trying to enhance the capabilities of module appConference. The module is app_conference.so

The Makefile is the following

```

# $Id: Makefile 889 2007-08-09 14:42:48Z sbalea $

#
# Makefile, based on the Asterisk Makefile, Coypright (C) 1999, Mark Spencer
#
# Copyright (C) 2002,2003 Junghanns.NET GmbH
#
# Klaus-Peter Junghanns <kapejod@ns1.jnetdns.de>
#
# This program is free software and may be modified and
# distributed under the terms of the GNU Public License.
#

.EXPORT_ALL_VARIABLES:

#
# app_conference defines which can be passed on the command-line
#

INSTALL_PREFIX :=
INSTALL_MODULES_DIR := $(INSTALL_PREFIX)/usr/lib/asterisk/modules

ASTERISK_INCLUDE_DIR ?= ../asterisk/include

REVISION = $(shell svnversion -n .)

# turn app_conference debugging on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DEBUG ?= 0

# 0 = OFF 1 = astdsp 2 = speex
SILDET := 2

# turn app_conference Dummy User on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DU ?= 1

#
# app_conference objects to build
#

OBJS = app_conference.o conference.o member.o frame.o cli.o 
TARGET = app_conference.so


#
# standard compile settings
#

PROC = $(shell uname -m)
INSTALL = install

INCLUDE = -I$(ASTERISK_INCLUDE_DIR)
DEBUG := -g

CFLAGS = -pipe -Wall -Wmissing-prototypes -Wmissing-declarations -MD -MP $(DEBUG)

CPPFLAGS = $(INCLUDE) -D_REENTRANT -D_GNU_SOURCE -DREVISION=\"$(REVISION)\"
#CFLAGS += -O2
#CFLAGS += -O3 -march=pentium3 -msse -mfpmath=sse,387 -ffast-math
# PERF: below is 10% faster than -O2 or -O3 alone.
#CFLAGS += -O3 -ffast-math -funroll-loops
# below is another 5% faster or so.
#CFLAGS += -O3 -ffast-math -funroll-all-loops -fsingle-precision-constant
#CFLAGS += -mcpu=7450 -faltivec -mabi=altivec -mdynamic-no-pic
# adding -msse -mfpmath=sse has little effect.
#CFLAGS += -O3 -msse -mfpmath=sse
#CFLAGS += $(shell if $(CC) -march=$(PROC) -S -o /dev/null -xc /dev/null >/dev/null 2>&1; then echo "-march=$(PROC)"; fi)
CFLAGS += $(shell if uname -m | grep -q ppc; then echo "-fsigned-char"; fi)
CFLAGS += -fPIC
CPPFLAGS += -DCRYPTO

# Uncomment for Asterisk 1.6
CFLAGS += -DAST16

#
# Uncomment this if you want G.729A support (need to have the actual codec installed
#
CPPFLAGS += -DAC_USE_G729A



ifeq ($(APP_CONFERENCE_DEBUG), 1)
CPPFLAGS += -DAPP_CONFERENCE_DEBUG
endif


ifeq ($(APP_CONFERENCE_DU), 1)
LDFLAGS += -lMagickWand
OBJS += stream.o
endif

#
# additional flag values for silence detection
#

ifeq ($(SILDET), 2)
OBJS += libspeex/preprocess.o libspeex/misc.o libspeex/smallft.o
CPPFLAGS += -Ilibspeex -DSILDET=2
endif

ifeq ($(SILDET), 1)
CPPFLAGS += -DSILDET=1
endif

OSARCH=$(shell uname -s)
ifeq (${OSARCH},Darwin)
SOLINK=-dynamic -bundle -undefined suppress -force_flat_namespace
else
SOLINK=-shared -Xlinker -x
endif

DEPS += $(subst .o,.d,$(OBJS))

#
# targets
#

all: $(TARGET)

.PHONY: clean
clean:
    $(RM) $(OBJS) $(DEPS)

.PHONY: distclean
distclean: clean
    $(RM) $(TARGET)

$(TARGET): $(OBJS)
    $(CC) -pg $(SOLINK) $(LDFLAGS) -o $@ $(OBJS)


vad_test: vad_test.o libspeex/preprocess.o libspeex/misc.o libspeex/smallft.o
    $(CC) $(PROFILE) -o $@ $^ -lm

install:
    $(INSTALL) -m 755 $(TARGET) $(INSTALL_MODULES_DIR)




#config: all
#    cp conf.conf /etc/asterisk/

-include $(DEPS)
# $Id: Makefile 889 2007-08-09 14:42:48Z sbalea $

#
# Makefile, based on the Asterisk Makefile, Coypright (C) 1999, Mark Spencer
#
# Copyright (C) 2002,2003 Junghanns.NET GmbH
#
# Klaus-Peter Junghanns <kapejod@ns1.jnetdns.de>
#
# This program is free software and may be modified and
# distributed under the terms of the GNU Public License.
#

.EXPORT_ALL_VARIABLES:

#
# app_conference defines which can be passed on the command-line
#

INSTALL_PREFIX :=
INSTALL_MODULES_DIR := $(INSTALL_PREFIX)/usr/lib/asterisk/modules

ASTERISK_INCLUDE_DIR ?= ../asterisk/include

REVISION = $(shell svnversion -n .)

# turn app_conference debugging on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DEBUG ?= 0

# 0 = OFF 1 = astdsp 2 = speex
SILDET := 2

# turn app_conference Dummy User on or off ( 0 == OFF, 1 == ON )
APP_CONFERENCE_DU ?= 1

#
# app_conference objects to build
#

OBJS = app_conference.o conference.o member.o frame.o cli.o 
TARGET = app_conference.so


#
# standard compile settings
#

PROC = $(shell uname -m)
INSTALL = install

INCLUDE = -I$(ASTERISK_INCLUDE_DIR)
DEBUG := -g

CFLAGS = -pipe -Wall -Wmissing-prototypes -Wmissing-declarations -MD -MP $(DEBUG)

CPPFLAGS = $(INCLUDE) -D_REENTRANT -D_GNU_SOURCE -DREVISION=\"$(REVISION)\"
#CFLAGS += -O2
#CFLAGS += -O3 -march=pentium3 -msse -mfpmath=sse,387 -ffast-math
# PERF: below is 10% faster than -O2 or -O3 alone.
#CFLAGS += -O3 -ffast-math -funroll-loops
# below is another 5% faster or so.
#CFLAGS += -O3 -ffast-math -funroll-all-loops -fsingle-precision-constant
#CFLAGS += -mcpu=7450 -faltivec -mabi=altivec -mdynamic-no-pic
# adding -msse -mfpmath=sse has little effect.
#CFLAGS += -O3 -msse -mfpmath=sse
#CFLAGS += $(shell if $(CC) -march=$(PROC) -S -o /dev/null -xc /dev/null >/dev/null 2>&1; then echo "-march=$(PROC)"; fi)
CFLAGS += $(shell if uname -m | grep -q ppc; then echo "-fsigned-char"; fi)
CFLAGS += -fPIC
CPPFLAGS += -DCRYPTO

# Uncomment for Asterisk 1.6
CFLAGS += -DAST16

#
# Uncomment this if you want G.729A support (need to have the actual codec installed
#
CPPFLAGS += -DAC_USE_G729A



ifeq ($(APP_CONFERENCE_DEBUG), 1)
CPPFLAGS += -DAPP_CONFERENCE_DEBUG
endif


ifeq ($(APP_CONFERENCE_DU), 1)
LDFLAGS += -lMagickWand
OBJS += stream.o
endif

#
# additional flag values for silence detection
#

ifeq ($(SILDET), 2)
OBJS += libspeex/preprocess.o libspeex/misc.o libspeex/smallft.o
CPPFLAGS += -Ilibspeex -DSILDET=2
endif

ifeq ($(SILDET), 1)
CPPFLAGS += -DSILDET=1
endif

OSARCH=$(shell uname -s)
ifeq (${OSARCH},Darwin)
SOLINK=-dynamic -bundle -undefined suppress -force_flat_namespace
else
SOLINK=-shared -Xlinker -x
endif

DEPS += $(subst .o,.d,$(OBJS))

#
# targets
#

all: $(TARGET)

.PHONY: clean
clean:
    $(RM) $(OBJS) $(DEPS)

.PHONY: distclean
distclean: clean
    $(RM) $(TARGET)

$(TARGET): $(OBJS)
    $(CC) -pg $(SOLINK) $(LDFLAGS) -o $@ $(OBJS)


vad_test: vad_test.o libspeex/preprocess.o libspeex/misc.o libspeex/smallft.o
    $(CC) $(PROFILE) -o $@ $^ -lm

install:
    $(INSTALL) -m 755 $(TARGET) $(INSTALL_MODULES_DIR)




#config: all
#    cp conf.conf /etc/asterisk/

-include $(DEPS)


```The getIP.h is included inside stream.c

---

### Post by dwhitney67 on 2010-01-20
Your Makefiles look ok; and since I do not have the luxury to download the iPBX Asterisk package to experiment with, I think it would be best to revisit the compiler errors you posted earlier.

Let's begin by examining the error that produced this message/advice:
```

__dont__use__inet_ntoa__use__ast_inet_ntoa__instead__

```
In the getIP.h, please replace the call to inet_ntoa() with ast_inet_ntoa().

This error seemed to create a cascade of other errors, so hopefully this will resolve the issue.

---

### Post by erotavlas on 2010-01-20
> **dwhitney67 said:**
> Your Makefiles look ok; and since I do not have the luxury to download the iPBX Asterisk package to experiment with, I think it would be best to revisit the compiler errors you posted earlier.

Let's begin by examining the error that produced this message/advice:
```

__dont__use__inet_ntoa__use__ast_inet_ntoa__instead__

```In the getIP.h, please replace the call to inet_ntoa() with ast_inet_ntoa().

This error seemed to create a cascade of other errors, so hopefully this will resolve the issue.

thank you very much :popcorn:

After i have changed from inet_ntoa() to ast_inet_ntoa() it work :D
(I saw a strange message and I have not read :()

---


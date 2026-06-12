---
title: "C - getopt problem - help"
date: 2009-10-06
forum: Programming Talk
---

### Post by ApEkV2 on 2009-10-06
This program is for testing my webserver against denial of service attacks.
I'm having problems with getopt in this code, the program works if no other arguments are inputed.
This is the normal output with "sudo a.out 192.168.1.101 80"

aflag = 0, bflag = 0, cvalue = (null)
Using custom TCP header:
Successful fork
Sent 1 to 192.168.1.101 at 80...
Sent 1 to 192.168.1.101 at 80...
Successful fork
Sent 1 to 192.168.1.101 at 80...
Sent 1 to 192.168.1.101 at 80...

However, it doesn't work when I use -a or any other options, I get

aflag = 1, bflag = 0, cvalue = (null)
Using custom TCP header:
Successful fork
sendto() Failed
sendto() Failed
Successful fork
sendto() Failed
sendto() Failed

Why are the options messing up the program? I'm sure it is something I missed.
```
#include <sys/wait.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>
#include <ctype.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <unistd.h>
#include <netdb.h>
#include <netinet/in.h>
#include <netinet/tcp.h>
#include <netinet/ip.h>
#include <limits.h>

struct ipheader {
unsigned char      iph_ihl:5,
                   iph_ver:4;

unsigned char      iph_tos;
unsigned short int iph_len;
unsigned short int iph_ident;
unsigned char      iph_flags;
unsigned short int iph_offset;
unsigned char      iph_ttl;
unsigned char      iph_protocol;
unsigned short int iph_chksum;
unsigned int       iph_sourceip;
unsigned int       iph_destip;
	};

unsigned long zcount,zstop;

struct tcpheader {
unsigned short int   tcph_srcport;
unsigned short int   tcph_destport;
unsigned int         tcph_seqnum;
unsigned int         tcph_acknum;
unsigned char        tcph_reserved:4, tcph_offset:4;
unsigned int

	tcp_res1:4,
	tcph_hlen:4,
	tcph_fin:1,
	tcph_syn:1,
	tcph_rst:1,
	tcph_psh:1,       
	tcph_ack:1,
	tcph_urg:1,
	tcph_res2:2;

unsigned short int   tcph_win;
unsigned short int   tcph_chksum;
unsigned short int   tcph_urgptr;
	};

unsigned short csum (unsigned short *buf, int nwords) {
unsigned long sum;
for (sum = 0; nwords > 0; nwords--)

	sum += *buf++;
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);

      return (unsigned short)(~sum);
}

int main(int argc, char *argv[])
{

[color=red] int aflag = 0; int bflag = 0; char *cvalue = NULL; int c;
	while ((c = getopt (argc, argv, "abc:")) != -1)
	switch (c) {
           case 'a':
             aflag = 1;
             break;
           case 'b':
             bflag = 1;
             break;
           case 'c':
             cvalue = optarg;
             break;
           case '?':
             if (optopt == 'c')
               fprintf (stderr, "Option -%c requires an argument.\nExit 1\n", optopt);
             else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
             else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
             return 1;
  }  printf ("aflag = %d, bflag = %d, cvalue = %s\n", aflag, bflag, cvalue); [/color]

    int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);
if (s == -1) {
		perror("[open_sockraw] socket()");
		exit(-1);
	}
    char datagram[4096];
    struct ipheader *iph = (struct ipheader *) datagram;
    struct tcpheader *tcph = (struct tcpheader *) datagram + sizeof (struct ipheader);
    struct sockaddr_in sin;
if (argc < 3) {
		fprintf(stderr,"usage %s Hostname Port\n", argv[0]);
		exit(-1);
	}
    unsigned int destport = atoi(argv[2]);
    sin.sin_family = AF_INET;
    sin.sin_port = htons(destport);
    sin.sin_addr.s_addr = inet_addr(argv[1]);

	memset(datagram, 0, 4096);
	iph->iph_ihl = 5;
	iph->iph_ver = 4;
	iph->iph_tos = 0;

    iph->iph_len = sizeof (struct ipheader) + sizeof (struct tcpheader);

    iph->iph_ident = htonl (54321);
    iph->iph_offset = 0;
    iph->iph_ttl = 64;
    iph->iph_protocol = 4;
    iph->iph_chksum = 0;
    iph->iph_sourceip = inet_addr ("127.0.0.1");
    iph->iph_destip = sin.sin_addr.s_addr;
    tcph->tcph_srcport = htons (6600);
    tcph->tcph_destport = htons (destport);
    tcph->tcph_seqnum = random();
    tcph->tcph_acknum = 0;
    tcph->tcph_res2 = 0;
    tcph->tcph_offset = 0;
    tcph->tcph_syn = 0x02;
    tcph->tcph_win = htonl (65535);
    tcph->tcph_chksum = 0;
    tcph-> tcph_urgptr = 0;

    iph-> iph_chksum = csum ((unsigned short *) datagram, iph-> iph_len >> 1);

    int tmp = 1;
    int pid;
    const int *val = &tmp;
if(setsockopt (s, IPPROTO_IP, IP_HDRINCL, val, sizeof (tmp)) < 0) {
	printf("Error: setsockopt() - Cannot set HDRINCL:\n");
	exit(-1);
    }
else
	printf("Using custom TCP header:\n");
	usleep(250);

waitpid(-1, NULL, WNOHANG);
	if(pid == NULL)
	pid = fork();
	printf("Successful fork\n");
		if (pid < 0)
			error("ERROR on fork\n");
while(1) {
	if(sendto(s,
		datagram,
		iph->iph_len,
		0,
		(struct sockaddr *) &sin,
		sizeof (sin)) < 0)
		[color=red] printf("sendto() Failed\n"); [/color]
	else
		printf("Sent 1 to %s at %u...\n", argv[1], destport);
		zstop = zcount++;
		if(zstop >= 1) {
			break;
		}
	}
      return 0;
} 
```

---

### Post by lloyd_b on 2009-10-06
Your problem lies here:```
   unsigned int destport = [COLOR="Red"]atoi(argv[2])[/COLOR];
    sin.sin_family = AF_INET;
    sin.sin_port = htons(destport);
    sin.sin_addr.s_addr = [COLOR="Red"]inet_addr(argv[1])[/COLOR];
```Without the "-a", host is argv[1], port is argv[2].  But *with* the "-a", host is pushed up to argv[2], and port to argv[3].  Net result - you're getting garbage in the address and port elements of "sin".

Use the external variable set by getopt called "optind" to determine where the host and port are, rather than hard-coded values...

Lloyd B.

---

### Post by ApEkV2 on 2009-10-07
Thanks lloyd, I am trying to get this working, and I don't know why this isn't working.
Here is the output with -a included.

aflag = 1, bflag = 0, cvalue = (null)
argc = 4
        ARGV[2] = <192.168.1.101>

The port 85322264 and dest is 24

        ARGV[3] = <80>

```
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>

int main(int argc, char *argv[])
{

int aflag = 0; int bflag = 0; char *cvalue = NULL; int c;
extern int optind, opterr, optopt;
	while ((c = getopt (argc, argv, "abc:")) != -1)
	switch (c) {
           case 'a':
             aflag = 1;
             break;
           case 'b':
             bflag = 1;
             break;
           case 'c':
             cvalue = optarg;
             break;
           case '?':
             if (optopt == 'c')
               fprintf (stderr, "Option -%c requires an argument.\nExit 1\n", optopt);
             else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
             else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
             return 1;
  }  printf ("aflag = %d, bflag = %d, cvalue = %s\n", aflag, bflag, cvalue);

printf("argc = %d\n", argc);

[color=red]while (optind < (argc - 2))
	{ optind++; break; } [/color]

printf("\tARGV[%d] = <%s>\n\n", optind, argv[optind]);

[color=red]char d_addr = argv[optind];
unsigned int d_port = argv[optind++]; [/color]

printf("The port %d and dest is %d\n\n", d_port, d_addr);
printf("\tARGV[%d] = <%s>\n\n", optind, argv[optind]);
	return 0;
} 
```
[color=red]I should've added an * after char, and then changed the printf format, but I still can't get d_port correct
Changes[/color]
```
[color=red]char [color=blue]*[/color]d_addr = argv[optind];
unsigned int d_port = argv[optind++]; 

printf("The port %d and dest is [color=blue]%s[/color]\n\n", d_port, d_addr);[/color]
```
[color=blue]This yields the following: ( I do get a warning for line 43:"initialization makes integer from pointer without a cast" when I build it)
Line 43 is "unsigned int d_port = argv[optind++];"

aflag = 1, bflag = 0, cvalue = (null)
argc = 4
	ARGV[2] = <192.168.1.101>

The port 947124760 and dest is 192.168.1.101

	ARGV[3] = <80>[/color]

---

### Post by lloyd_b on 2009-10-08
Okay, I see two problems, both with the port assignment.

First, argv[?] is a string pointer.  You're assigning it to an "int", which is where that large number for the port is coming from.  You need an "atoi()" here to convert the string to an integer.

Second, "argv[optind++]" isn't doing what you think it's doing.  Specifically, having the "++" *after* the variable means that the variable is not incremented until after the rest of the statement is performed.  What you need in this case is "argv[++optind]", to increment optind so that it's pointing to the port *before* making use of that value.

In this case, it might be easier to avoid optind entirely, and just use relative values of argc:```
char *d_addr = argv[argc - 2];
unsigned int d_port = atoi(argv[argc - 1]);
``` will work, since you're relying on the host and port being the last two parameters, regardless of what options are used.

(Note: You should really have some error checking on these.  For instance, put a sanity check on the port to see if it's in the range 1-64k.  For the address, you should check the return value from inet_addr() to see if what you had was actually something that the function could convert).

Lloyd B.

---

### Post by ApEkV2 on 2009-10-08
Thanks again lloyd for helping me out. I did get optind to work correctly now (I think).
Ok then, I thought I got it, but it still doesn't work. I get no errors when it's run, but wireshark shows no traffic.
[color=blue]I think I'm going to start a new thread maybe, (title's outdated)
For some reason it is working now (wireshark can now see it)
However the packets are all messed up (IP protocol instead of TCP, etc)
Also not to mention it is IPv6 for some reason.[/color]

[color=red]The getopt problem is solved, so I'm going to start a new thread later.[/color]

```
#include <netinet/in.h>
#include <netinet/tcp.h>
#include <netinet/ip.h>
#include <ctype.h>
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h> 
#include <limits.h>
#include <sys/wait.h>
#include <string.h>
#include <signal.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netdb.h>

#define TH_FIN 0x02
struct ipheader {
unsigned char      iph_ihl:5, iph_ver:4;

unsigned char      iph_tos;
unsigned short int iph_len;
unsigned short int iph_ident;
unsigned char      iph_flags;
unsigned short int iph_offset;
unsigned char      iph_ttl;
unsigned char      iph_protocol;
unsigned short int iph_chksum;
unsigned int       iph_sourceip;
unsigned int       iph_destip;
	};

struct tcpheader {
unsigned short int   tcph_srcport;
unsigned short int   tcph_destport;
unsigned int         tcph_seqnum;
unsigned int         tcph_acknum;
unsigned char        tcph_reserved:4, tcph_offset:4;
unsigned int

	tcp_res1:4,
	tcph_hlen:4,
	tcph_fin:1,
	tcph_syn:1,
	tcph_rst:1,
	tcph_psh:1,       
	tcph_ack:1,
	tcph_urg:1,
	tcph_res2:2;

unsigned short int   tcph_win;
unsigned short int   tcph_chksum;
unsigned short int   tcph_urgptr;
	};

unsigned short csum (unsigned short *buf, int nwords) {
unsigned long sum;
for (sum = 0; nwords > 0; nwords--)

	sum += *buf++;
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);
      return (unsigned short)(~sum);
}

int main(int argc, char *argv[])
{

int aflag = 0; int bflag = 0; char *cvalue = NULL; int c;
extern int optind, opterr, optopt;
	while ((c = getopt (argc, argv, "abc:")) != -1)
	switch (c) {
           case 'a':
             aflag = 1;
             break;
           case 'b':
             bflag = 1;
             break;
           case 'c':
             cvalue = optarg;
             break;
           case '?':
             if (optopt == 'c')
               fprintf (stderr, "Option -%c requires an argument.\nExit 1\n", optopt);
             else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
             else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
             return 1; }
printf ("aflag = %d, bflag = %d, cvalue = %s, argc = %d\n ", aflag, bflag, cvalue, argc);
while (optind < (argc - 2))
	{ optind++; break; }

printf("\tARGV[%d] = <%s>  ", optind, argv[optind]);
char *d_addr = argv[optind];
unsigned int d_port = atoi(argv[++optind]);
if (d_addr == NULL, d_port < 1^ d_port > 64000)
	{ printf("range broken\n"); return -1; }
printf("\tARGV[%d] = <%s>\n", optind, argv[optind]);

int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);
if (s == -1)
	{ perror("[open_sockraw] socket()");
	exit(-1); }

char datagram[4096];
struct ipheader *iph = (struct ipheader *) datagram;
struct tcpheader *tcph = (struct tcpheader *) datagram + sizeof (struct ipheader);
struct sockaddr_in sin;

    sin.sin_family = AF_INET;
    sin.sin_port = htons (d_port);
    sin.sin_addr.s_addr = inet_addr (d_addr);
	memset(datagram, 0, 4096);

	iph->iph_ihl = 5;
	iph->iph_ver = 4;
	iph->iph_tos = 0;
iph->iph_len = sizeof (struct ipheader) + sizeof (struct tcpheader);
	iph->iph_ident = htonl (54321);
	iph->iph_offset = 0;
	iph->iph_ttl = 64;
	iph->iph_protocol = 4;
	iph->iph_chksum = 0;
	iph->iph_sourceip = inet_addr ("127.0.0.1");
	iph->iph_destip = sin.sin_addr.s_addr;
	tcph->tcph_srcport = htons (6600);
	tcph->tcph_destport = htons (d_port);
	tcph->tcph_seqnum = random();
	tcph->tcph_acknum = 0;
	tcph->tcph_res2 = 0;
	tcph->tcph_offset = 0;
	tcph->tcph_syn = 0x02;
	tcph->tcph_win = htonl (65535);
	tcph->tcph_chksum = 0;
	tcph-> tcph_urgptr = 0;
iph->iph_chksum = csum ((unsigned short *) datagram, iph->iph_len >> 1);

unsigned int tmp = 1, zcount = 0;
const int *val = &tmp;
if(setsockopt (s, IPPROTO_IP, IP_HDRINCL, val, sizeof (tmp)) < 0)
	{ printf("Error: setsockopt() - Cannot set HDRINCL:\n");
	exit(-1); }
	usleep(250);

while(1) {
	if(sendto(s, datagram, iph->iph_len, 0, (struct sockaddr *) &sin, sizeof (sin)) < 0)
		printf("sendto() Failed\n");
	else
		printf("Sent 1 to %s at %u...\n", d_addr, d_port);
		++zcount;
		if (zcount >= 4) {
			break;
		}

	}
	return 0;
}
```

---

### Post by dwhitney67 on 2009-10-08
Out of mere curiosity, why are you using raw sockets?  Could your application not just use regular sockets to send whatever data needs to be sent?

Also, I can see from your code that you understand how to define/implement functions.  Would your code not look better, and more modular, if you were to implement functions for each section of your main() function, rather than just run it all together?

Lastly, and I hope you don't think I am being insensitive to your development efforts, but what is the purpose of the getopt() anyhow?  You do not appear to be using any of the flags that could be set if a particular command-line arg is passed to the program.

---

### Post by ApEkV2 on 2009-10-08
Raw sockets are being used because I want to make custom ip/tcp headers.  
More so, I want to make a packet with Syn Fin flags and be able to fragment it (the dream).
I actually started learning C about five days ago. (previously knew bash)
I'm planning on using the options later for changing aspects of the headers.

Basically right now I'm trying to figure out why my packets are screwed up.
I tried to get a tcp syn connect packet (IPv4), but instead got an Ipv6, ip protocol, the best packet known to man.
I'm going to freaking backflip punch this code in the face!!

---

### Post by dwhitney67 on 2009-10-09
Where did you lift this portion of the tcpheader from?
```

...
unsigned int

	tcp_res1:4,
	tcph_hlen:4,
	tcph_fin:1,
	tcph_syn:1,
	tcph_rst:1,
	tcph_psh:1,       
	tcph_ack:1,
	tcph_urg:1,
	tcph_res2:2;
...

```
Here's the wiki on the standard TCP header: [http://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_segment_structure](http://en.wikipedia.org/wiki/Transmission_Control_Protocol#TCP_segment_structure)

The other thing, you do not need to define your own struct for ipheader, unless you plan on expanding it.  It's basic form is defined in /usr/netinet/ip.h, and there are two versions available, the non-BSD version (struct iphdr) and the BSD-version (struct ip). 

You can customize the IP and/or TCP headers, however don't expect Wireshark to be able to interpret your header(s) correctly.  It will attempt to interpret your data based on its concept of the IP and TCP headers, not yours.  Fortunately, you can (manually) interpret the raw bytes to discern if the data is correct.  Easier yet would be to have a server that is ready to receive this modified datagram, and display it.


P.S.  I have never worked with raw sockets using TCP, however I have minimal experience using UDP.  Here's an example of a UDP client application that I wrote that uses raw sockets:
```

/*
# Copyright (C) 2008 David M. Whitney (aka "dwhitney67")
#
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
# this program. If not, see <http://www.gnu.org/licenses/>.
*/

#include "IpDataDisplayer.h"

#include <Socket/UDPSocket.hpp>
#include <Socket/SocketUtility.h>

#include <string>
#include <iostream>
#include <iomanip>
#include <stdexcept>
#include <cstdlib>
#include <cstring>
#include <cassert>


typedef std::basic_string<unsigned char> RawData;

RawData BuildUdpDatagram(const std::string& servAddr, unsigned short servPort, const RawData& msg);


int main(int argc, char** argv)
{
  const std::string    servAddr = (argc > 1 ? argv[1] : "127.0.0.1");
  const unsigned short servPort = (argc > 2 ? atoi(argv[2]) : 9000);

  const unsigned char  data[]   = { 0xCA, 0xFE, 0xBA, 0xBE };
  const RawData        msg(data, sizeof(data));

  std::cout << "UDP client, using servAddr = " << servAddr << std::endl;
  std::cout << "UDP client, using servPort = " << servPort << std::endl;

  try
  {
    // Build the raw IP/UDP message
    RawData rd = BuildUdpDatagram(servAddr, servPort, msg);

    // Create the socket
    socketpp::UDPSocket sock(PF_INET, SOCK_RAW);

    // We no longer need root privileges
    setuid(getuid());

    // Send the raw data
    sock.send((const char*) rd.data(), rd.size(), servAddr, servPort);

    std::cout << "\nThis data was sent...\n"
              << IpDataDisplayer(rd)
              << std::endl;
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << std::endl;
    return 1;
  }
}


RawData BuildUdpDatagram(const std::string& servAddr, unsigned short servPort, const RawData& msg)
{
  // Obtain the destination and source addresses to be inserted into the IP header
  sockaddr_in dst_sin;
  sockaddr_in src_sin;

  int dst_rtn = socketpp::fillAddress(PF_INET, servAddr.c_str(), servPort, &dst_sin);
  int src_rtn = socketpp::fillAddress(PF_INET, "127.0.0.1", 1234, &src_sin);
  assert(dst_rtn == 0 && src_rtn == 0);

  // this buffer will contain IP header, UDP header, and payload. we'll point an ip
  // header structure at its beginning, and a UDP header structure after that to write
  // the header values into it.
  unsigned char* datagram = new unsigned char[sizeof(ip) + sizeof(udphdr) + msg.size()];

  // setup offsets to mark our header and data regions
  ip* iph    = reinterpret_cast<ip*>(datagram);
  int ip_len = sizeof(ip) + sizeof(udphdr) + msg.size();

  iph->ip_hl         = sizeof(ip) >> 2;       // 5 words (20 bytes), but could be more!
  iph->ip_v          = 4;                     // IPv4
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);         // the total length of the datagram
  iph->ip_id         = htons(54321);          // the value doesn't matter here
  iph->ip_off        = 0;
  iph->ip_ttl        = 255;
  iph->ip_p          = IPPROTO_UDP;
  iph->ip_sum        = 0;                      // set to 0; compute checksum later
  iph->ip_src.s_addr = src_sin.sin_addr.s_addr;
  iph->ip_dst.s_addr = dst_sin.sin_addr.s_addr;
  //iph->ip_src.s_addr = inet_addr(servAddr.c_str());
  //iph->ip_dst.s_addr = inet_addr("127.0.0.1");

  // compute checksum for the IP header (this is optional)
  iph->ip_sum = socketpp::headerChecksum(reinterpret_cast<uint16_t*>(iph), iph->ip_hl << 2);

  // now obtain our other data pointers
  udphdr*        udph = reinterpret_cast<udphdr*>(datagram + (iph->ip_hl << 2));
  unsigned char* data = datagram + (iph->ip_hl << 2) + sizeof(udphdr);

  // assign the message data
  memcpy(data, msg.data(), msg.size());

  // we'll now fill in the UDP header values (note that the 'source' and 'check' are optional)
  udph->source = 0;
  udph->dest   = htons(servPort);
  udph->len    = htons(sizeof(udphdr) + msg.size());
  udph->check  = socketpp::udpHeaderChecksum((const uint16_t*) datagram, ip_len);

  RawData rd(datagram, datagram + ip_len);

  delete [] datagram;

  return rd;
}

```
Some of the details are missing from the code, but hopefully this will help you.

---

### Post by ApEkV2 on 2009-10-10
Thanks for the input, this will definitely keep me busy. 
I was originally trying to learn from Hping's code, but there are tons of source files to look through.
I'll probably make another thread once I eventually get started on this.

---


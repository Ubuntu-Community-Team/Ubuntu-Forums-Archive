---
title: "C - raw socket - tcp/ip header problem"
date: 2009-10-15
forum: Programming Talk
---

### Post by ApEkV2 on 2009-10-15
I finished this code today and I'm having trouble with the tcp/ip headers. 
They are all messed up, and wireshark doesn't even pick them up.
The input for the program is "192.168.1.100 80"
I think I might have htons and htonl mixed up a lot.
Any and all help would be awesome! (strace does show that sendto is being called)
[php]#include <arpa/inet.h>
#include <ctype.h>
#include <limits.h>
#include <netdb.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>
#include <signal.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/wait.h>
#include <unistd.h>

struct pseudohdr {
	unsigned long saddr;
	unsigned long daddr;
	char useless;
	unsigned char protocol;
	unsigned short length;
};
#define PSEUDO sizeof(struct pseudohdr)
#define TCPHDR sizeof(struct tcphdr)
#define Z_NL 4294967295
unsigned short c_sum(unsigned short *buf, int nwords) {
unsigned long sum;
for (sum = 0; nwords > 0; nwords--)
	sum += *buf++;
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);
	return (unsigned short)(~sum); }

int main(int argc, char *argv[])
{

int h = 0, x = 0, c, s_port; char *zvalue = NULL;
extern int optind, opterr, optopt;
while ((c = getopt (argc, argv, "hxz:")) != -1)
	switch (c) {
		case 'h':
		h = 1;
	break;
		case 'x':
		x = 1;
	break;
		case 'z':
		zvalue = optarg;
	break;
		case '?':
	if (optopt == 'z')
               fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
	else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
		return 1; }

while (optind < (argc - 2)) {
	optind++; }
char *d_addr = argv[optind];
unsigned int d_port = atoi(argv[++optind]);
if ((d_addr == NULL || d_port < 1 || d_port > 64000) && h == 0)
	{ printf("Error:\n"); h = 1; }

if (h > 0) {
	printf(
"Usage: [command] [host] [port] [options]\n"
" -h = show help  "
" -x = Not used  "
" -z = Not used\n"
	); return 0; }

srand((unsigned)time(NULL)); 
s_port = (int)(rand()/(((double)RAND_MAX + 1)/64000));
int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);
if (s == -1) {
	perror("[open_sockraw] socket()");
	return 1; }

char p_data[4096];
struct ip *iph = (struct ip *) p_data;
struct tcphdr *tcph = (struct tcphdr *) p_data + sizeof(struct ip);
struct sockaddr_in sin;
struct pseudohdr pseudo;
sin.sin_family = AF_INET;
sin.sin_port = htons(d_port);
sin.sin_addr.s_addr = inet_addr(argv[--optind]);
memset(p_data, 0, 4096);

	    iph->ip_hl = sizeof(struct ip) >> 2;
	iph->ip_v = 4;
    iph->ip_tos = 0;
    iph->ip_len = sizeof(struct ip) + sizeof(struct tcphdr);
    iph->ip_id = htons((int)(rand()/(((double)RAND_MAX + 1)/14095)));
    iph->ip_off = 0;
    iph->ip_ttl = 64;
    iph->ip_p = IPPROTO_TCP;
    iph->ip_sum = htons((c_sum((unsigned short *) p_data, iph->ip_len >> 1)));
    iph->ip_src.s_addr = inet_addr("192.168.1.105");
    iph->ip_dst.s_addr = sin.sin_addr.s_addr; 

    tcph->source = htons(s_port);
    tcph->dest = htons(d_port);
    tcph->seq = htonl((int)(rand()/(((double)RAND_MAX + 1)/Z_NL)));
    tcph->ack_seq = htonl(0);
    tcph->res1 = 0;
    tcph->doff = 5;
    tcph->fin = 1;
    tcph->syn = 1;
    tcph->rst = 0;
    tcph->psh = 0;
    tcph->ack = 0;
    tcph->urg = 0;
    tcph->res2 = 0;
    tcph->window = htons(512);

    pseudo.saddr = inet_addr("127.0.0.1");
    pseudo.daddr = sin.sin_addr.s_addr;
    pseudo.useless = htons(0);
    pseudo.protocol = IPPROTO_TCP;
    pseudo.length = htons(TCPHDR);

    tcph->check = htons((c_sum((unsigned short *) &pseudo, PSEUDO+TCPHDR)));
    tcph->urg_ptr = htons(0);

int tmp = 1, z_stop = 0; const int *val = &tmp;
if (setsockopt(s, IPPROTO_IP, IP_HDRINCL, val, sizeof(tmp)) < 0) {
	printf("Error: setsockopt() - Cannot set HDRINCL:\n");
	return 1; }

while (z_stop < 2) {
	if (sendto(s, p_data, iph->ip_len, 0, (struct sockaddr *) &sin, sizeof(sin)) < 0) {
		printf("Error: sendto()\n");
		break; }
	else
		++z_stop;
	}

	return 0;
}[/php]
And this is the strace of sendto.
```
sendto(3, "E\0(\0\302\5\0@\377\6\244\220\177\0\0\1\300\250\1d\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 40, 0, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("192.168.1.100")}, 16) = 40
```

And this is the strace of sendto for Hping3 (with -SF)
```
sendto(3, "E\0\0(\370F\0\0@\6\0\0\300\250\1i\300\250\1d\0062\0P0B\35l8C\243\10P"..., 40, 0, {sa_family=AF_INET, sin_port=htons(11111), sin_addr=inet_addr("192.168.1.100")}, 16) = 40
```

---

### Post by dwhitney67 on 2009-10-16
I created an app on my system that sets up a raw socket that uses TCP, and I was able to successfully send messages... and more importantly, monitor the messages using WireShark.

Here's a snippet of the code I wrote (which is in C++); extract the relevant part for your C program.
```

RawData BuildTcpDatagram(const std::string& servAddr, unsigned short servPort, const RawData& msg)
{
  // Obtain the destination and source addresses to be inserted into the IP header
  sockaddr_in dst_sin;
  sockaddr_in src_sin;

  int dst_rtn = socketpp::fillAddress(PF_INET, servAddr.c_str(), servPort, &dst_sin);
  int src_rtn = socketpp::fillAddress(PF_INET, "127.0.0.1", 1234, &src_sin);
  assert(dst_rtn == 0 && src_rtn == 0);

  // this buffer will contain IP header, TCP header, and payload. we'll point an ip
  // header structure at its beginning, and a TCP header structure after that to write
  // the header values into it.
  unsigned char* datagram = new unsigned char[sizeof(ip) + sizeof(tcphdr) + msg.size()];

  // setup offsets to mark our header and data regions
  ip* iph    = reinterpret_cast<ip*>(datagram);
  int ip_len = sizeof(ip) + sizeof(tcphdr) + msg.size();

  iph->ip_hl         = sizeof(ip) >> 2;       // 5 words (20 bytes), but could be more!
  iph->ip_v          = 4;                     // IPv4
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);         // the total length of the datagram
  iph->ip_id         = htons(54321);          // the value doesn't matter here
  iph->ip_off        = 0;
  iph->ip_ttl        = 255;
  iph->ip_p          = IPPROTO_TCP;
  iph->ip_sum        = 0;                      // set to 0; compute checksum later
  iph->ip_src.s_addr = src_sin.sin_addr.s_addr;
  iph->ip_dst.s_addr = dst_sin.sin_addr.s_addr;
  //iph->ip_src.s_addr = inet_addr(servAddr.c_str());
  //iph->ip_dst.s_addr = inet_addr("127.0.0.1");

  // compute checksum for the IP header (this is optional)
  iph->ip_sum = socketpp::headerChecksum(reinterpret_cast<uint16_t*>(iph), iph->ip_hl << 2);

  // now obtain our other data pointers
  tcphdr*        tcph = reinterpret_cast<tcphdr*>(datagram + (iph->ip_hl << 2));
  unsigned char* data = datagram + (iph->ip_hl << 2) + sizeof(tcphdr);

  // assign the message data
  memcpy(data, msg.data(), msg.size());

  // we'll now fill in the TCP header values
  tcph->source  = 0;
  tcph->dest    = htons(servPort);
  tcph->seq     = 1;
  tcph->ack_seq = 0;
  tcph->res1    = 0;
  tcph->doff    = sizeof(tcphdr) >> 2;
  tcph->fin     = 0;
  tcph->syn     = 0;
  tcph->rst     = 0;
  tcph->psh     = 0;
  tcph->ack     = 0;
  tcph->urg     = 0;
  tcph->res2    = 0;
  tcph->window  = 0;
  tcph->check   = 0;
  tcph->urg_ptr = 0;

  RawData rd(datagram, datagram + ip_len);

  delete [] datagram;

  return rd;
}

```

Btw, I sent the message to the localhost (127.0.0.1), port 12345.

---

### Post by ApEkV2 on 2009-10-16
Thanks for posting an example, unfortunately after a couple of hours trying to "extract", I tried to follow a tut.
[http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt](http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt)
I updated the code above, and now if ip header length ( iph->ip_hl = 5; ) is above 16 bytes, it yields a sendto error.
sendto(blablabla) = -1 EPERM (Operation not permitted)

---

### Post by dwhitney67 on 2009-10-16
> **ApEkV2 said:**
> Thanks for posting an example, unfortunately after a couple of hours trying to "extract", I tried to follow a tut.
[http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt](http://packetstormsecurity.nl/programming-tutorials/raw_socket.txt)
I updated the code above, and now if ip header length ( iph->ip_hl = 5; ) is above 16 bytes, it yields a sendto error.
sendto(blablabla) = -1 EPERM (Operation not permitted)

I don't understand what you are saying.  When iph->ip_hl is set to 5, this implies that the header has a size of 20 bytes.  It is used to denote how many long-words are in the header.

20 >> 2 = 5

or better yet...

sizeof(struct ip) >> 2 = 5

---

### Post by ApEkV2 on 2009-10-16
My bad........(me and words)....if ip header length is GREATER than 16 bytes, it gives me that error

[color=red]EDIT - so for *example* if I use iph->ip_hl = 5; (20bytes) it gives an error
, but if I use iph->ip_hl = 4; (16bytes) it works (although the packet is invalid)[/color]

Here is the strace
```
sendto(3, "E\0(\0\3241\0\0\377\6\277\306\177\0\0\1\300\250\1d\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 40, 0, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("192.168.1.100")}, 16) = -1 EPERM (Operation not permitted)
```

---

### Post by dwhitney67 on 2009-10-16
Well, unless you have extended the IP header, it should be 20 bytes long.

Therefore, if you use 5 (20 >> 2) as your IP header length, and you get an error performing the sendto(), the issue lies elsewhere.

The code I posted earlier worked for me, although WireShark was annoyed that I posted multiple packets with the same sequence number.

Just moments ago I augmented my code to include the checksum in the TCP header; what a pain that was.  The formula is the same as used for the IP header, however the data that is used is "weird" because it involves creating a temporary pseudo header for the packet.  This pseudo header includes the source address, destination address, the IP protocol, and the length of the TCP header and the data that follows.

---

### Post by ApEkV2 on 2009-10-16
I've updated the code in the first post.  Is there a way to use GDB for debugging this? (or anything other than strace)

---

### Post by dwhitney67 on 2009-10-16
> **ApEkV2 said:**
> I've updated the code in the first post.  Is there a way to use GDB for debugging this? (or anything other than strace)

Yes, just compile your code with the '-g' option.  Then when you debug, use a statement similar to the following:
```

sudo gdb myapp

```
After you see the GDB prompt, then you enter your command-line parameters.  For example:
```

gdb> b main
gdb> r 192.168.1.100 80

```

---

### Post by ApEkV2 on 2009-10-16
Well I give up on gdb for now (can't really get anything useful out of it).
I used sudo gdb --args a.out [192.168.1.100 80], but I just don't know what to do with it.
Right now I'm about to pass out from lack of sleep. Any other ideas for debugging?

EDIT - I'm getting closer to Hping's sendto.  The differences are in red
Hping3 (with -SF)
```
sendto(3, "E\0\0(\370F\0\0@\6\0\0\300\250\1i\300\250\1d\[color=red]0062\0P0B\35l8C\243\10P[/color]"..., 40, 0,
```
And my program - the tcp header isn't working
```
sendto(3, "E\0(\0\0177\0\0@\6\0\0\300\250\1i\300\250\1d\[color=red]0\0\0\0\0\0\0\0\0\0\0\0\0[/color]"..., 40, 0,
```

---

### Post by ApEkV2 on 2009-10-17
Well it turns out that the problem with the sendto was firestarter, once I turned firestarter off, it worked.
However, Wireshark says that the IP header is fine, but the tcp header doesn't have anything in it. (it's empty)
What the heck? Here is a screen shot of wireshark.

---

### Post by dwhitney67 on 2009-10-17
Can you please post your code again?  I am not psychic, and there's nothing in the world that will help me analyze your code by merely viewing a WireShark screen shot.  :p

_

---

### Post by ApEkV2 on 2009-10-17
[php]#include <arpa/inet.h>
#include <ctype.h>
#include <limits.h>
#include <netdb.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>
#include <signal.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/wait.h>
#include <unistd.h>

struct pseudohdr {
	unsigned long saddr;
	unsigned long daddr;
	char useless;
	unsigned char protocol;
	unsigned short length;
};
#define PSEUDO sizeof(struct pseudohdr)
#define TCPHDR sizeof(struct tcphdr)
#define Z_NL 4294967295
unsigned short c_sum(unsigned short *buf, int nwords) {
unsigned long sum;
for (sum = 0; nwords > 0; nwords--)
	sum += *buf++;
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);
	return (unsigned short)(~sum); }

int main(int argc, char *argv[])
{

int h = 0, x = 0, c, s_port; char *zvalue = NULL;
extern int optind, opterr, optopt;
while ((c = getopt (argc, argv, "hxz:")) != -1)
	switch (c) {
		case 'h':
		h = 1;
	break;
		case 'x':
		x = 1;
	break;
		case 'z':
		zvalue = optarg;
	break;
		case '?':
	if (optopt == 'z')
               fprintf (stderr, "Option -%c requires an argument.\n", optopt);
	else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
	else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
		return 1; }

while (optind < (argc - 2)) {
	optind++; }
char *d_addr = argv[optind];
unsigned int d_port = atoi(argv[++optind]);
if ((d_addr == NULL || d_port < 1 || d_port > 64000) && h == 0)
	{ printf("Error:\n"); h = 1; }

if (h > 0) {
	printf(
"Usage: [command] [host] [port] [options]\n"
" -h = show help  "
" -x = Not used  "
" -z = Not used\n"
	); return 0; }

srand((unsigned)time(NULL)); 
s_port = (int)(rand()/(((double)RAND_MAX + 1)/64000));
int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);
if (s == -1) {
	perror("[open_sockraw] socket()");
	return 1; }

char p_data[4096];
struct ip *iph = (struct ip *) p_data;
struct tcphdr *tcph = (struct tcphdr *) p_data + sizeof(struct ip);
struct sockaddr_in sin;
struct pseudohdr pseudo;
sin.sin_family = AF_INET;
sin.sin_port = htons(d_port);
sin.sin_addr.s_addr = inet_addr(argv[--optind]);
memset(p_data, 0, 4096);

    iph->ip_hl = sizeof(struct ip) >> 2;
    iph->ip_v = 4;
    iph->ip_tos = 0;
    iph->ip_len = sizeof(struct ip) + sizeof(struct tcphdr);
    iph->ip_id = htons((int)(rand()/(((double)RAND_MAX + 1)/14095)));
    iph->ip_off = 0;
    iph->ip_ttl = 64;
    iph->ip_p = IPPROTO_TCP;
    iph->ip_sum = htons((c_sum((unsigned short *) p_data, iph->ip_len >> 1)));
    iph->ip_src.s_addr = inet_addr("192.168.1.105");
    iph->ip_dst.s_addr = sin.sin_addr.s_addr; 

    tcph->source = htons(s_port);
    tcph->dest = htons(d_port);
    tcph->seq = htonl((int)(rand()/(((double)RAND_MAX + 1)/Z_NL)));
    tcph->ack_seq = htonl(0);
    tcph->res1 = 0;
    tcph->doff = sizeof(struct tcphdr) >> 2;
    tcph->fin = 1;
    tcph->syn = 1;
    tcph->rst = 0;
    tcph->psh = 0;
    tcph->ack = 0;
    tcph->urg = 0;
    tcph->res2 = 0;
    tcph->window = htons(512);

    pseudo.saddr = inet_addr("192.168.1.105");
    pseudo.daddr = sin.sin_addr.s_addr;
    pseudo.useless = htons(0);
    pseudo.protocol = IPPROTO_TCP;
    pseudo.length = htons(TCPHDR);

    tcph->check = htons((c_sum((unsigned short *) &pseudo, PSEUDO+TCPHDR)));
    tcph->urg_ptr = htons(0);

int tmp = 1, z_stop = 0; const int *val = &tmp;
if (setsockopt(s, IPPROTO_IP, IP_HDRINCL, val, sizeof(tmp)) < 0) {
	printf("Error: setsockopt() - Cannot set HDRINCL:\n");
	return 1; }

while (z_stop < 1) {
	if (sendto(s, p_data, iph->ip_len, 0, (struct sockaddr *) &sin, sizeof(sin)) < 0) {
		printf("Error: sendto()\n");
		break; }
	else
		++z_stop;
	}

	return 0;
}[/php]

---

### Post by dwhitney67 on 2009-10-17
I took your code, blended in my code (which I believe works), and came up with the app below.

I removed some of the non-essentials from your code; so feel free to add them in at your leisure.

```

#include <arpa/inet.h>
#include <ctype.h>
#include <limits.h>
#include <netdb.h>
#include <netinet/in.h>
#include <netinet/ip.h>
#include <netinet/tcp.h>
#include <stdlib.h>
#include <string.h>
#include <stdio.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <sys/wait.h>
#include <unistd.h>
#include <time.h>
#include <errno.h>

struct PseudoHdr
{
  unsigned long  saddr;
  unsigned long  daddr;
  char           reserved;
  unsigned char  protocol;
  unsigned short length;
};

#define PSEUDO sizeof(struct pseudohdr)
#define TCPHDR sizeof(struct tcphdr)
#define Z_NL   4294967295

unsigned short c_sum(unsigned short* data, int nbytes)
{
  unsigned long sum = 0;

  for (; nbytes > 1; nbytes -= 2)
  {
    sum += *data++;
  }

  if (nbytes == 1)
  {
    sum += *(unsigned char*) data;
  }

  sum  = (sum >> 16) + (sum & 0xffff);
  sum += (sum >> 16);

  return ~sum;
}

int fillAddress(int domain, const char* address, unsigned short port, struct sockaddr_in* sin);

unsigned char* buildTCPDatagram(struct sockaddr_in* src_sin, struct sockaddr_in* dst_sin, const unsigned char* msg, unsigned int msgSize);

unsigned int buildPseudoHdrBuffer(unsigned int src_addr, unsigned int dst_addr, unsigned int protocol,
                                  const unsigned char* hdrData, unsigned int hdrBytes,
                                  const unsigned char* msgData, unsigned int msgBytes,
                                  unsigned short** buffer);

int main(int argc, char** argv)
{
  const char*          dest_ip   = (argc > 1 ? argv[1] : "127.0.0.1");   // destination IP
  const unsigned short dest_port = (argc > 2 ? atoi(argv[1]) : 80);      // destination port

  srand(time(0));

  // root-privileges needed for the following operation
  int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);

  if (s <= 0)
  {
    perror("[open_sockraw] socket()");
    return 1;
  }

  int enable = 1;
  if (setsockopt(s, IPPROTO_IP, IP_HDRINCL, &enable, sizeof(enable)) < 0)
  {
    printf("Error: setsockopt() - Cannot set HDRINCL:\n");
    return 1;
  }

  // We no longer need root privileges
  setuid(getuid());

  // build up out source and destination sock addresses
  struct sockaddr_in src_sin;
  struct sockaddr_in dst_sin;

  fillAddress(PF_INET, "127.0.0.1", 1234, &src_sin);
  fillAddress(PF_INET, dest_ip, dest_port, &dst_sin);


  // build our TCP datagram
  char*          msg          = "Hello World";
  unsigned char* datagram     = buildTCPDatagram(&src_sin, &dst_sin, (unsigned char*) msg, strlen(msg));
  unsigned int   datagramSize = sizeof(struct ip) + sizeof(struct tcphdr) + strlen(msg);

  for (int i = 0; i < 3; ++i)
  {
    if (sendto(s, datagram, datagramSize, 0, (struct sockaddr*) &dst_sin, sizeof(dst_sin)) < 0)
    {
      printf("Error with sendto() -- %s (%d)\n", strerror(errno), errno);
      break;
    }
  }
  free(datagram);

  return 0;
}  


int fillAddress(int domain, const char* address, unsigned short port, struct sockaddr_in* sin)
{
  if (!address)
  {
    memset(sin, 0, sizeof(struct sockaddr_in));

    sin->sin_family      = domain;
    sin->sin_addr.s_addr = htonl(INADDR_ANY);
    sin->sin_port        = htons(port);
  }
  else
  {
    struct addrinfo  hints;
    struct addrinfo* host_info = 0;

    memset(&hints, 0, sizeof(hints));

    hints.ai_family = domain;

    if (getaddrinfo(address, 0, &hints, &host_info) != 0  ||
        !host_info || !host_info->ai_addr || host_info->ai_family != domain)
    {
      if (host_info) freeaddrinfo(host_info);
      return -1;
    }

    memcpy(sin, host_info->ai_addr, sizeof(struct sockaddr_in));
    sin->sin_port = htons(port);

    freeaddrinfo(host_info);
  }

  return 0;
}


unsigned char* buildTCPDatagram(struct sockaddr_in* src_sin, struct sockaddr_in* dst_sin, const unsigned char* msg, unsigned int msgSize)
{
  const int      ip_len   = sizeof(struct ip) + sizeof(struct tcphdr) + msgSize;
  unsigned char* datagram = calloc(1, ip_len);

  if (!datagram) return 0;

  // setup useful pointers to locations within the datagram
  struct ip*     iph  = (struct ip*) datagram;
  struct tcphdr* tcph = (struct tcphdr*)(datagram + sizeof(struct ip));
  unsigned char* data = datagram + sizeof(struct ip) + sizeof(struct tcphdr);

  // build IP header
  iph->ip_hl         = sizeof(struct ip) >> 2;
  iph->ip_v          = 4;
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);
  iph->ip_id         = htons((int)(rand()/(((double)RAND_MAX + 1)/14095)));
  iph->ip_off        = 0;
  iph->ip_ttl        = 64;
  iph->ip_p          = IPPROTO_TCP;
  iph->ip_sum        = 0;
  iph->ip_src.s_addr = src_sin->sin_addr.s_addr;
  iph->ip_dst.s_addr = dst_sin->sin_addr.s_addr;

  // now we compute the checksum for the IP header (albeit this is optional)
  iph->ip_sum = c_sum((unsigned short*) iph, sizeof(struct ip));

  // build TCP header
  tcph->source  = htons(src_sin->sin_port);
  tcph->dest    = htons(dst_sin->sin_port);
  tcph->seq     = htonl((int)(rand()/(((double)RAND_MAX + 1)/Z_NL)));
  tcph->ack_seq = htonl(0);
  tcph->res1    = 0;
  tcph->doff    = sizeof(struct tcphdr) >> 2;
  tcph->fin     = 1;
  tcph->syn     = 1;
  tcph->rst     = 0;
  tcph->psh     = 0;
  tcph->ack     = 0;
  tcph->urg     = 0;
  tcph->res2    = 0;
  tcph->window  = htons(512);
  tcph->check   = 0;
  tcph->urg_ptr = htons(0);

  // now we compute the TCP header checksum, across a pseudo message buffer, not the actual TCP header
  unsigned short* buffer = 0;
  unsigned int    bufferSize = buildPseudoHdrBuffer(src_sin->sin_addr.s_addr, dst_sin->sin_addr.s_addr, IPPROTO_TCP,
                                                    (const unsigned char*) tcph, sizeof(struct tcphdr),
                                                    msg, msgSize, &buffer);

  tcph->check = c_sum(buffer, bufferSize);
  free(buffer);

  // add message data (if any)
  if (msgSize > 0)
  {
    memcpy(data, msg, msgSize);
  }

  return datagram;
}


unsigned int buildPseudoHdrBuffer(unsigned int src_addr, unsigned int dst_addr, unsigned int protocol,
                                  const unsigned char* hdrData, unsigned int hdrBytes,
                                  const unsigned char* msgData, unsigned int msgBytes,
                                  unsigned short** buffer)
{
  struct PseudoHdr pseudoHdr;

  pseudoHdr.saddr    = src_addr;
  pseudoHdr.daddr    = dst_addr;
  pseudoHdr.reserved = 0;
  pseudoHdr.protocol = protocol;
  pseudoHdr.length   = htons(hdrBytes + msgBytes);

  unsigned int   bufSize = sizeof(struct PseudoHdr) + hdrBytes + msgBytes;
  unsigned char* buf     = calloc(1, bufSize);
  int            offset  = 0;

  memcpy(buf + offset, &pseudoHdr, sizeof(struct PseudoHdr)); offset += sizeof(struct PseudoHdr);
  memcpy(buf + offset, hdrData, hdrBytes); offset += hdrBytes;
  memcpy(buf + offset, msgData, msgBytes);

  *buffer = (uint16_t*) buf;

  return bufSize;
}

```

---

### Post by ApEkV2 on 2009-10-17
Holy thanks for helping me out, however I had to move the declaration of "i" outside of the for loop.
And once I changed the destination address, wireshark sees three successful packets with both tcp/ip headers intact (plus the cool message).
Now I just gotta see what I am doing wrong in my code.  Thanks again for the example.

---

### Post by dwhitney67 on 2009-10-18
> **ApEkV2 said:**
> Holy thanks for helping me out, however I had to move the declaration of "i" outside of the for loop.
And once I changed the destination address, wireshark sees three successful packets with both tcp/ip headers intact (plus the cool message).
Now I just gotta see what I am doing wrong in my code.  Thanks again for the example.
You're welcome.

I use the GCC option -std=gnu99 when compiling C source code, thus allowing me to declare variables pretty much wherever I please, including within the initialization section of for-loop constructs.

---

### Post by ApEkV2 on 2009-10-18
I found the problem in mine......get ready......My Dear Aunt Sally.  An order of operations mistake.
```
struct tcphdr *tcph = [color=red](struct tcphdr *) p_data + sizeof(struct ip)[/color];
```
Now corrected, the tcp header is now being filled.
```
struct tcphdr *tcph = (struct tcphdr *) [color=red]([/color]p_data + sizeof(struct ip)[color=red])[/color];
```
Now all I have to fix is the tcp checksum, (cause it's bad)
And for the record, I wouldn't have seen the problem if dwhitney hadn't of posted his code.

---


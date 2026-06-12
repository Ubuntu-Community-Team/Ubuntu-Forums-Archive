---
title: "C - incompatible types in assignment"
date: 2009-10-15
forum: Programming Talk
---

### Post by ApEkV2 on 2009-10-15
Hey there, I just finished this code, and couldn't (didn't know how) fix the two errors: incompatible types in assignment.
The lines with the error are 97 and 98.  And I probably did everything wrong, so any and all help is awesome.
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

#define Z_MAX 64000
unsigned short csum (unsigned short *buf, int nwords) {
unsigned long sum;
for (sum = 0; nwords > 0; nwords--)
	sum += *buf++;
	sum = (sum >> 16) + (sum & 0xffff);
	sum += (sum >> 16);
	return (unsigned short)(~sum); }

int main(int argc, char *argv[])
{

int h, x, c, s_port, z_key, zstop; char *zvalue = NULL;
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
               fprintf (stderr, "Option -%c requires an argument.\nExit 1\n", optopt);
	else if (isprint (optopt))
               fprintf (stderr, "Unknown option `-%c'.\n", optopt);
	else
               fprintf (stderr, "Unknown option character `\\x%x'.\n", optopt);
	default:
		return 1; }
while (optind < (argc - 2))
	{ optind++; break; }

if (h > 0) {
	printf(
"Usage: [command] [host] [port] [options]\n"
" -h = show help\n"
" -x = Not used\n"
" -z = Not used\n"
	); return 0; }

char *d_addr = argv[optind];
unsigned int d_port = atoi(argv[++optind]);
if (d_addr == NULL || d_port < 1 || d_port > 64000)
	{ printf("Error Invalid\n"); return 1; }

srand((unsigned)time(NULL)); 
s_port = (int)(rand()/(((double)RAND_MAX + 1)/ Z_MAX));
z_key = (int)(rand()/(((double)RAND_MAX + 1)/ Z_MAX));
if (s_port > 40000 && z_key > 40000)
	s_port -= 10000;

int s = socket(PF_INET, SOCK_RAW, IPPROTO_TCP);
if (s == -1) {
	perror("[open_sockraw] socket()");
	return 1; }

char p_data[4096];
struct ip *iph = (struct ip *) p_data;
struct tcphdr *tcph = (struct tcphdr *) p_data + sizeof(struct ip);
struct sockaddr_in sin;

sin.sin_family = AF_INET;
sin.sin_port = htons(d_port);
sin.sin_addr.s_addr = inet_addr(argv[--optind]);
memset(p_data, 0, 4096);

    iph->ip_hl = 4;
    iph->ip_v = 4;
    iph->ip_tos = 0;
    iph->ip_len = sizeof(struct ip) + sizeof(struct tcphdr);
    iph->ip_id  = htonl(54321);
    iph->ip_off = 0;
    iph->ip_ttl = MAXTTL;
    iph->ip_p = 4;
    iph->ip_sum = 0;
/* 97 */    iph->ip_src = inet_addr("127.0.0.1");   /* Incompatible types in assignment */
/* 98 */    iph->ip_dst = sin.sin_addr.s_addr;      /* Incompatible types in assignment */

    tcph->source = htons(s_port);
    tcph->dest = htons(d_port);
    tcph->seq = random();
    tcph->ack_seq = 0;
    tcph->res1 = 4;
    tcph->doff = 4;
    tcph->fin = 1;
    tcph->syn = 1;
    tcph->rst = 0;
    tcph->psh = 0;
    tcph->ack = 0;
    tcph->urg = 0;
    tcph->res2 = 2;
    tcph->window = TCP_MAXWIN;
    tcph->check = 0;
    tcph->urg_ptr = 0;

    iph->ip_sum = csum((unsigned short *) p_data, iph->ip_len >> 1);

    int tmp = 1;
    const int *val = &tmp;
if (setsockopt(s, IPPROTO_IP, IP_HDRINCL, val, sizeof (tmp)) < 0) {
	printf("Error: setsockopt() - Cannot set HDRINCL:\n");
	return 1; }

while (zstop < 3) {
	if (sendto(s, p_data, iph->ip_len, 0, (struct sockaddr *) &sin, sizeof(sin)) < 0)
	    printf("Error: sendto()\n");
	else
		++zstop; usleep(250);
	}

	return 0;
}[/php]

---

### Post by dwhitney67 on 2009-10-15
Try:
```

iph->ip_src**.s_addr** = inet_addr("127.0.0.1");
iph->ip_dst**.s_addr** = sin.sin_addr.s_addr;

```

---

### Post by ApEkV2 on 2009-10-15
That worked. Thanks a lot!
Now since all the errors are ironed out, when I run it, wireshark picks nothing up, and no traffic.
I think it's a problem in the tcp/ip headers.  Are there any ways to debug this?
Probably going to make a different thread.

---

### Post by dwhitney67 on 2009-10-15
What evidence do you have that sendto() was ever called?

You should start your investigative efforts by examining the value of 'zstop'.  It could be that I am losing my eyesight, but no where in the code could I see where you set it to any particular value.

---

### Post by ApEkV2 on 2009-10-15
Sendto was called, I used strace to make sure.
here is zstop on line 29
```
int h, x, c, s_port, z_key, [color=red]zstop[/color]; char *zvalue = NULL; 
```

---

### Post by dwhitney67 on 2009-10-15
> **ApEkV2 said:**
> Sendto was called, I used strace to make sure.

Wonderful; the sendto() was called by shear luck.

> 
here is zstop on line 29
```
int h, x, c, s_port, z_key, [color=red]zstop[/color]; char *zvalue = NULL; 
```
I see where you defined it; but where did you initialize it to a value less than 3?  (hint:  nowhere!)

---

### Post by ApEkV2 on 2009-10-15
That doesn't change the fact that zstop isn't the problem.

---

### Post by dwhitney67 on 2009-10-15
> **ApEkV2 said:**
> That doesn't change the fact that zstop isn't the problem.
Well, I haven't a clue what the problem is because 1) I don't know what parameters you are passing to the application, 2) I don't know if you have the raw socket datagram setup correctly, and 3) whether or not you are using wireshark correctly?

Nevertheless, it still stands that 'zstop' is an uninitialized value and thus you should fix it.

---

### Post by ApEkV2 on 2009-10-15
I fixed zstop before my last post, and I'm only using 192.168.1.100 80 as arguments.
I believe I've already said where I think the problem is (in the tcp/ip headers).

---

### Post by dwhitney67 on 2009-10-15
When you used strace, what was the return value from the call to sendto()?

---

### Post by ApEkV2 on 2009-10-15
This is what I get
```
sendto(3, "E\0(\0\0\0\0\0\377\4R\354\177\0\0\1\300\250\1d\0\0\0\0\0\0\0\0\0\0\0\0\0"..., 40, 0, {sa_family=AF_INET, sin_port=htons(80), sin_addr=inet_addr("192.168.1.100")}, 16) = 40
```

This is a normal sendto by hping3 (-SF)
```
sendto(3, "E\0\0(\370F\0\0@\6\0\0\300\250\1i\300\250\1d\0062\0P0B\35l8C\243\10P"..., 40, 0, {sa_family=AF_INET, sin_port=htons(11111), sin_addr=inet_addr("192.168.1.100")}, 16) = 40
```

[color=red]EDIT: I'm probably going to start a different thread [/color]

---


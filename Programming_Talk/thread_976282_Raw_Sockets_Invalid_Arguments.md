---
title: "Raw Sockets: Invalid Arguments ?"
date: 2008-11-09
forum: Programming Talk
---

### Post by souljumper on 2008-11-09
hi,

i've trouble with raw sockets. i try to create a simple udp package and send it. Everytime i come to the "sendto()" - call i get an "invalid arguments" error.

i don't know what i'm doing wrong i read and compared almost everyside in the internet regarding udp and raw sockets. i don't get what my mistake is...

maybe someone can lend me a helping hand a review my code:
```

#define __USE_BSD	/* use bsd'ish ip header */
#include <sys/socket.h>	/* these headers are for a Linux system, but */
#include <netinet/ip.h>
#include <netinet/udp.h>
#include <sys/types.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <unistd.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

unsigned short in_cksum(unsigned short *ptr, int nbytes)
{
  register long sum =0;
  u_short oddbyte = 0;
  
  while(nbytes > 1)
  {
    sum += *ptr++;
    nbytes -=2;
  }
  
  if(nbytes == 1)
  {
     *((u_char *) &oddbyte) = *(u_char*) ptr;
     sum += oddbyte;
  }
  
  sum = (sum>>16) + (sum & 0xffff);
  sum += (sum>>16);
  
  return (u_short)~sum;
}


int main(int argc, char **argv)
{

  int uid = geteuid();
  if ( uid != 0)
  {
	  printf("You're not root ! %i", uid);
	  exit(1);
  }
  
  

 unsigned int headersize = sizeof(struct ip) + sizeof(struct udphdr);
 unsigned int payload = 512;
 unsigned int packetsize = headersize + payload;
 unsigned char packet[packetsize]; 
 memset(packet,0,packetsize);
  
 
 int rawsock=0;
 if ((rawsock = socket(AF_INET, SOCK_RAW, IPPROTO_UDP)) < 0)
 {
	 perror("socket() - failed");
 	exit(1);
 }

 
 /* Eigenen IP-Header verwenden, Kernel-Header unterdrücken */
 int on=1;
 if (setsockopt(rawsock, IPPROTO_IP, IP_HDRINCL, (const char* )&on, sizeof(on)) < 0 )
 {
   perror("IP_HDRINCL failed!\n");
   exit(1);
 }
 
 struct sockaddr_in sin;
 memset(&sin, 0, sizeof(struct sockaddr_in));
 sin.sin_addr.s_addr = inet_addr("127.0.0.1");
 sin.sin_port = htons(1235);
 sin.sin_family = AF_INET;
 
 /* IP Header*/
  struct ip *iph     = (struct ip*) packet;
 iph->ip_v 		       	= 4; //IPv4
 iph->ip_hl		    	= 5;
 iph->ip_tos           	= 0x0;
 iph->ip_len		  	= htons(packetsize); 
 iph->ip_len			= 0;
 iph->ip_ttl        	= 100;
 iph->ip_sum	 		= 0;    
 iph->ip_p		 		= IPPROTO_UDP;
 iph->ip_src.s_addr 	= inet_addr("127.0.0.1");
 iph->ip_dst.s_addr 	= inet_addr("192.168.2.103");
 iph->ip_id 			= htons(random());
 iph->ip_id 			= 0;

 /* UDP Header  */
 struct udphdr *udp     = (struct udphdr *) (packet + sizeof(struct ip));
 udp->uh_sport			= htons(1234);
 udp->uh_dport			= htons(1235);
 udp->uh_ulen			= htons(packetsize - sizeof(struct ip));
 udp->uh_sum			= 0;
 
 printf("Checksumme, Headersize \n");
 iph->ip_sum = in_cksum((unsigned short*) &iph, sizeof(struct ip));
 printf("Calculated Checksumme: %i\n", iph->ip_sum);

 
 if (sendto(rawsock, packet, packetsize, 0, (struct sockaddr*) &sin,
                                             sizeof(sin)) < 0 )
    perror("sendto() failed");
    
 close(rawsock);
 
 
 return 0;
}
```

---

### Post by dwhitney67 on 2008-11-09
I ran a variation of your code, and it appeared to work fine on my system (Fedora 9).

What system are you using?  I've noticed that to use (and compile) the BSD-style udphdr your code uses, one needs to define __FAVOR_BSD prior to the include of netinet/udp.h.

I checked the header file /usr/include/netinet/udp.h, on both my Fedora and Ubuntu 8.04 systems to confirm that this is true.  Using __USE_BSD did not work on my Fedora system.

For my test, I changed the following in your code:

1. I replaced the hard-coded IP addresses to the aliases as they appear in my /etc/hosts file; and I moved the statement that calls in_cksum() up a few lines:
[php]
...
  iph->ip_src.s_addr = inet_addr("localhost");
  iph->ip_dst.s_addr = inet_addr("bluediamond");
  iph->ip_id         = htons(random());
  iph->ip_id         = 0;
  iph->ip_sum        = in_cksum((unsigned short*) &iph, sizeof(struct ip));
...
[/php]

2.  I elected to use different port numbers (9000 for the source, 9001 for the destination).
[php]
  /* UDP Header  */
  struct udphdr* udp = (struct udphdr*) (packet + sizeof(struct ip));
  udp->uh_sport = htons(9000);
  udp->uh_dport = htons(9001);
  udp->uh_ulen  = htons(packetsize - sizeof(struct ip));
  udp->uh_sum   = 0;
[/php]

Anyhow, as you can see, the changes were very cosmetic.  The sendto() call did not fail as you had indicated in your post.  I could not verify if it succeeded because I did not have a client readily available to receive the data.

P.S.  You should avoid declaring a variable-length array as you did for "packet".  Consider allocating the memory for the packet buffer, and then after you have used it, free the memory.

---

### Post by souljumper on 2008-11-10
hm i changed my code and the error doesn't appear anymore...thanks so far :-).

i use the tool wireshark to capture my packet and it appears like my header checksums (udp and ip) are total trash. i wonder what im doing wrong:

IP-Checksum
```

unsigned short checksum(unsigned short *buffer, int size)
{
  unsigned long cksum=0;

  while (size > 1)
  {
    cksum += *buffer++;
    size -= sizeof(unsigned short);
  }

  if (size)
  {
    cksum += *(unsigned char*)buffer;
  }

  cksum = (cksum >> 16) + (cksum & 0xffff);
  cksum += (cksum >> 16);

  return (unsigned short)(~cksum);
}

```

and my udp-checksum
```


uint16_t udp_chk(const void * buff, size_t len, in_addr_t src_addr, in_addr_t dest_addr)
{
	const uint16_t *buf=buff;
	uint16_t *ip_src=(void *)&src_addr, *ip_dst=(void *)&dest_addr;
	uint32_t sum;
	size_t length=len;
	
	// Calculate the sum                                            //
	sum = 0;
	while (len > 1)
	{
	sum += *buf++;
	if (sum & 0x80000000)
	  sum = (sum & 0xFFFF) + (sum >> 16);
	len -= 2;
	}
	
	if ( len & 1 )
	// Add the padding if the packet lenght is odd          //
	    sum += *((uint8_t *)buf);
	
	// Add the pseudo-header                                        //
	sum += *(ip_src++);
	sum += *ip_src;
	sum += *(ip_dst++);
    sum += *ip_dst;

    sum += htons(IPPROTO_UDP);
    sum += htons(length);

         // Add the carries                                              //
	while (sum >> 16)
                sum = (sum & 0xFFFF) + (sum >> 16);

    // Return the one's complement of sum                           //
	return ( (uint16_t)(~sum)  );
 }

```

here my call of the above functions:
```

 iph->ip_sum	 		= checksum((unsigned short*) &iph, sizeof(struct ip));
/*-------cut---------*/
//and my udp call (that wasn't in the code of my first post)
 udp->uh_sum			= udp_chk(packet,packetsize - sizeof(struct ip), inet_addr("1.2.3.4"), inet_addr("127.0.0.1"));

```

anyone see whats my problem here ?

---

### Post by dwhitney67 on 2008-11-10
Here you can find the wiki-definition of a checksum:  [http://en.wikipedia.org/wiki/Checksum](http://en.wikipedia.org/wiki/Checksum)

I have used checksums in past projects, and one thing I learned/observed is that there are many ways for one to compute a checksum.  In other words, there are many algorithms.

If your algorithm is not exhibiting a symptom resembling a fault that causes a crash in the program, there is not much I can do to help you.  Unless of course you specify in plain English words what the algorithm is supposed to do (with the data).

At first glance I see that checksum() function is summing two-bytes (a short) at a time into a 4-byte storage area.  When the summing is done, you take the high-order word and add it to the low-order word of the 4-byte storage area.  Then you add the high-order word again (???).  Finally you return the complement of that result.

Is this what you intended?  Below are some more comments that you are free to disagree with.

[php]
// (IMO) Your buffer is declared as an unsigned short, thus the size should
// reflect how many words are in the buffer, not the number of bytes.
unsigned short checksum(unsigned short *buffer, int size)
{
  ...

  // (IMO) You should never need the following if-statement.
  // If your data is not word-aligned, then make it so before calling
  // this function.
  if (size)
  {
    cksum += *(unsigned char*)buffer;
  }

  ...

  // What is the purpose of this operation?
  cksum += (cksum >> 16);

  ...
}
[/php]

You other function, udp_chk(), is a wee-bit more complicated to digest.  Once again, it would be helpful if you provided an English description of what you intended this function to perform.

---


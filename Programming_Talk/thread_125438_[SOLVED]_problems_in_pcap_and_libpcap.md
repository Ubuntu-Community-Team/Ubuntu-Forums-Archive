---
title: "[SOLVED] problems in pcap and libpcap"
date: 2006-02-03
forum: Programming Talk
---

### Post by nuttycat on 2006-02-03
Hello everyone,
I am new to the world of Linux Programming. 
As part of learning to use the pcap library, I downloaded a basic libpcap program.
The program is a very basic one, just looks at the available network devices  and prints some info on them.

The program goes like this. 
```

/* ldev.c
   Martin Casado
   Looks for an interface, and lists the network ip
   and mask associated with that interface.
*/
#include <stdio.h>
#include <stdlib.h>
#include <pcap.h>  /* GIMME a libpcap plz! */
#include <errno.h>
#include <sys/socket.h>
#include <netinet/in.h>
#include <arpa/inet.h>

int main(int argc, char **argv)
{
  char *dev; /* name of the device to use */ 
  char *net; /* dot notation of the network address */
  char *mask;/* dot notation of the network mask    */
  int ret;   /* return code */
  char errbuf[PCAP_ERRBUF_SIZE];
  bpf_u_int32 netp; /* ip          */
  bpf_u_int32 maskp;/* subnet mask */
  struct in_addr addr;

  /* ask pcap to find a valid device for use to sniff on */
  [COLOR="Blue"]dev = pcap_lookupdev(errbuf);
[/COLOR]
  /* error checking */
  if(dev == NULL)
  {
   printf("%s\n",errbuf);
   exit(1);
  }

  /* print out device name */
  printf("DEV: %s\n",dev);

  /* ask pcap for the network address and mask of the device */
  [COLOR="Blue"]ret = pcap_lookupnet(dev,&netp,&maskp,errbuf);[/COLOR]

  if(ret == -1)
  {
   printf("%s\n",errbuf);
   exit(1);
  }

  /* get the network address in a human readable form */
  addr.s_addr = netp;
  net = inet_ntoa(addr);

  if(net == NULL)/* thanks Scott :-P */
  {
    perror("inet_ntoa");
    exit(1);
  }

  printf("NET: %s\n",net);

  /* do the same as above for the device's mask */
  addr.s_addr = maskp;
  mask = inet_ntoa(addr);
  
  if(mask == NULL)
  {
    perror("inet_ntoa");
    exit(1);
  }
  
  printf("MASK: %s\n",mask);

  return 0;
}

```

I saved the file as lcap.c, rather than ldev.c as mentioned by the original author.
On trying to compile with gcc , I get this:
```

suneil@Family:~/Desktop/code$ gcc -o lcap lcap.c
/tmp/ccGCEcAx.o: In function `main':
[COLOR="Blue"]lcap.c:(.text+0x2a): undefined reference to `pcap_lookupdev'
lcap.c:(.text+0x82): undefined reference to `pcap_lookupnet'[/COLOR]
collect2: ld returned 1 exit status
suneil@Family:~/Desktop/code$

```

but that error doesn't make sense, because in the pcap.h header file, the two functions are defined: (scroll down a bit, the defn's are highlighted)
```

#ifndef lib_pcap_h
#define lib_pcap_h

#include <sys/types.h>
#include <sys/time.h>

#include <net/bpf.h>

#include <stdio.h>

#ifdef __cplusplus
extern "C" {
#endif

#define PCAP_VERSION_MAJOR 2
#define PCAP_VERSION_MINOR 4

#define PCAP_ERRBUF_SIZE 256

/*
 * Compatibility for systems that have a bpf.h that
 * predates the bpf typedefs for 64-bit support.
 */
#if BPF_RELEASE - 0 < 199406
typedef	int bpf_int32;
typedef	u_int bpf_u_int32;
#endif

typedef struct pcap pcap_t;
typedef struct pcap_dumper pcap_dumper_t;
typedef struct pcap_if pcap_if_t;
typedef struct pcap_addr pcap_addr_t;

/*
 * The first record in the file contains saved values for some
 * of the flags used in the printout phases of tcpdump.
 * Many fields here are 32 bit ints so compilers won't insert unwanted
 * padding; these files need to be interchangeable across architectures.
 *
 * Do not change the layout of this structure, in any way (this includes
 * changes that only affect the length of fields in this structure).
 *
 * Also, do not change the interpretation of any of the members of this
 * structure, in any way (this includes using values other than
 * LINKTYPE_ values, as defined in "savefile.c", in the "linktype"
 * field).
 *
 *
 */
struct pcap_file_header {
	bpf_u_int32 magic;
	u_short version_major;
	u_short version_minor;
	bpf_int32 thiszone;	/* gmt to local correction */
	bpf_u_int32 sigfigs;	/* accuracy of timestamps */
	bpf_u_int32 snaplen;	/* max length saved portion of each pkt */
	bpf_u_int32 linktype;	/* data link type (LINKTYPE_*) */
};

/*
 * Each packet in the dump file is prepended with this generic header.
 * This gets around the problem of different headers for different
 * packet interfaces.
 */
struct pcap_pkthdr {
	struct timeval ts;	/* time stamp */
	bpf_u_int32 caplen;	/* length of portion present */
	bpf_u_int32 len;	/* length this packet (off wire) */
};

/*
 * As returned by the pcap_stats()
 */
struct pcap_stat {
	u_int ps_recv;		/* number of packets received */
	u_int ps_drop;		/* number of packets dropped */
	u_int ps_ifdrop;	/* drops by interface XXX not yet supported */
};

/*
 * Item in a list of interfaces.
 */
struct pcap_if {
	struct pcap_if *next;
	char *name;		/* name to hand to "pcap_open_live()" */
	char *description;	/* textual description of interface, or NULL */
	struct pcap_addr *addresses;
	u_int flags;		/* PCAP_IF_ interface flags */
};

#define PCAP_IF_LOOPBACK	0x00000001	/* interface is loopback */

/*
 * Representation of an interface address.
 */
struct pcap_addr {
	struct pcap_addr *next;
	struct sockaddr *addr;		/* address */
	struct sockaddr *netmask;	/* netmask for that address */
	struct sockaddr *broadaddr;	/* broadcast address for that address */
	struct sockaddr *dstaddr;	/* P2P destination address for that address */
};

typedef void (*pcap_handler)(u_char *, const struct pcap_pkthdr *,
			     const u_char *);

[COLOR="Blue"]char	*pcap_lookupdev(char *);
int	pcap_lookupnet(char *, bpf_u_int32 *, bpf_u_int32 *, char *);[/COLOR]
pcap_t	*pcap_open_live(char *, int, int, int, char *);
pcap_t	*pcap_open_dead(int, int);
pcap_t	*pcap_open_offline(const char *, char *);
void	pcap_close(pcap_t *);
int	pcap_loop(pcap_t *, int, pcap_handler, u_char *);
int	pcap_dispatch(pcap_t *, int, pcap_handler, u_char *);
const u_char*
	pcap_next(pcap_t *, struct pcap_pkthdr *);
int	pcap_stats(pcap_t *, struct pcap_stat *);
int	pcap_setfilter(pcap_t *, struct bpf_program *);
int	pcap_getnonblock(pcap_t *, char *);
int	pcap_setnonblock(pcap_t *, int, char *);
void	pcap_perror(pcap_t *, char *);
char	*pcap_strerror(int);
char	*pcap_geterr(pcap_t *);
int	pcap_compile(pcap_t *, struct bpf_program *, char *, int,
	    bpf_u_int32);
int	pcap_compile_nopcap(int, int, struct bpf_program *,
	    char *, int, bpf_u_int32);
void	pcap_freecode(struct bpf_program *);
int	pcap_datalink(pcap_t *);
int	pcap_snapshot(pcap_t *);
int	pcap_is_swapped(pcap_t *);
int	pcap_major_version(pcap_t *);
int	pcap_minor_version(pcap_t *);

/* XXX */
FILE	*pcap_file(pcap_t *);
int	pcap_fileno(pcap_t *);

pcap_dumper_t *pcap_dump_open(pcap_t *, const char *);
void	pcap_dump_close(pcap_dumper_t *);
void	pcap_dump(u_char *, const struct pcap_pkthdr *, const u_char *);

int	pcap_findalldevs(pcap_if_t **, char *);
void	pcap_freealldevs(pcap_if_t *);

/* XXX this guy lives in the bpf tree */
u_int	bpf_filter(struct bpf_insn *, u_char *, u_int, u_int);
int	bpf_validate(struct bpf_insn *f, int len);
char	*bpf_image(struct bpf_insn *, int);
void	bpf_dump(struct bpf_program *, int);

#ifdef __cplusplus
}
#endif

#endif

```

Am i doing something wrong in my compile process? Help/Suggestions please on how to get this working.
Thanks,
Nuttycat

EDIT:
Just for info:
About 10 mins before I ran the compile process, I got the libpcap devl lib using apt-get
suneil@Family:/$ sudo apt-get install libpcap-dev

This installed without any errors.

I am cross posting this into the sub forum "Packaging and Compiling Programs" also. Cause I am not sure where this query actually belongs. Can someone give me a head's up on this also?

---

### Post by hod139 on 2006-02-23
I was browsing the unanswered programming quesions and saw this. If you still care, you need to tell gcc to link against the pcap libraries
```
gcc -lpcap -o lcap lcap.c
```

---

### Post by nuttycat on 2006-02-23
Thanks for the reply.
-Nuttycat

---


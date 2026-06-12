---
title: "Problem Sending/Receiving Packets Into/From Network"
date: 2010-12-24
forum: Programming Talk
---

### Post by GEFORCEXTREME on 2010-12-24
Hi guys,

I've been looking into packet sniffing with libpcap and sending packets with raw packets.

I edited the code I got from a raw packet guide/tutorial. However I've failed to verify that I'm actually sending out the packets with another program written with libpcap and also Wireshark ([www.wireshark.org](www.wireshark.org)), a packet sniffer.

The code is as follow.

```

// Must be run by root lol! Just datagram, no payload/data

#include <unistd.h>
#include <stdio.h>
#include <sys/socket.h>
#include <netinet/ip.h>
#include <netinet/udp.h>

#define PCKT_LEN 8192 // The packet length

// Can create separate header file (.h) for all headers' structure

// The IP header's structure
struct ipheader
{
    unsigned char      iph_ihl:5, iph_ver:4;
    unsigned char      iph_tos;
    unsigned short int iph_len;
    unsigned short int iph_ident;
    unsigned char      iph_flag;
    unsigned short int iph_offset;
    unsigned char      iph_ttl;
    unsigned char      iph_protocol;
    unsigned short int iph_chksum;
    unsigned int       iph_sourceip;
    unsigned int       iph_destip;
};

// UDP header's structure
struct udpheader
{
    unsigned short int udph_srcport;
    unsigned short int udph_destport;
    unsigned short int udph_len;
    unsigned short int udph_chksum;
};
// total udp header length: 8 bytes (=64 bits)

// Function for checksum calculation. From the RFC,
// the checksum algorithm is:
//  "The checksum field is the 16 bit one's complement of the one's
//  complement sum of all 16 bit words in the header.  For purposes of
//  computing the checksum, the value of the checksum field is zero."
unsigned short csum(unsigned short *buf, int nwords)
{       //
        unsigned long sum;

        for(sum=0; nwords>0; nwords--)
                sum += *buf++;

        sum = (sum >> 16) + (sum &0xffff);

        sum += (sum >> 16);

        return (unsigned short)(~sum);
}

#define SOURCE_PORT 1884
#define SPOOF_IP_ADDRESS "192.168.1.199"

// Source IP, source port, target IP, target port from the command line arguments
int main(int argc, char *argv[])
{
    int sd;

    // No data/payload just datagram
    char buffer[PCKT_LEN];

    // Our own headers' structures
    struct ipheader *ip = (struct ipheader *)buffer;
    //struct tcpheader *tcp = (struct tcpheader *) (buffer + sizeof(struct ipheader));
    struct udpheader *udp = (struct udpheader *)(buffer + sizeof(struct ipheader));

    // Source and destination addresses: IP and port
    struct sockaddr_in sin, din;

    int one = 1;
    const int *val = &one;

    memset(buffer, 0, PCKT_LEN);

    if(argc != 3)
    {
        printf("- Invalid parameters!!!\n");
        //printf("- Usage %s <source hostname/IP> <source port> <target hostname/IP> <target port>\n", argv[0]);
	printf("- Usage %s <target hostname/IP> <target port>\n", argv[0]);
        exit(-1);
    }

    // Create a raw socket with UDP protocol
    sd = socket(PF_INET, SOCK_RAW, IPPROTO_UDP);
    if(sd < 0)
    {
        perror("socket() error");
        // If something wrong just exit
        exit(-1);
    }
    else
        printf("socket() - Using SOCK_RAW socket and UDP protocol is OK.\n");

    // The source is redundant, may be used later if needed

    // The address family
    sin.sin_family = AF_INET;
    din.sin_family = AF_INET;

    // Port numbers
    sin.sin_port = htons(SOURCE_PORT);
    din.sin_port = htons(atoi(argv[2]));

    // IP addresses
    sin.sin_addr.s_addr = INADDR_ANY; // get my IP
    din.sin_addr.s_addr = inet_addr(argv[1]);

#if 1
    // Fabricate the IP header or we can use the
    // standard header structures but assign our own values.
    ip->iph_ihl = 5; // header length in bytes
    ip->iph_ver = 4; // IPv4
    ip->iph_tos = 16; // type of service, low delay
    ip->iph_len = sizeof(struct ipheader) + sizeof(struct udpheader);
    ip->iph_ident = htons(54321);
    ip->iph_ttl = 64; // hops
    ip->iph_protocol = 17; // UDP
#endif

    // Source IP address, can use spoofed address here!!! cool!!!!!
    ip->iph_sourceip = inet_addr(argv[1]);
    // The destination IP address
    ip->iph_destip = inet_addr(argv[1]);
#if 1
    // Fabricate the UDP header. Source port number, redundant
    udp->udph_srcport = htons(SOURCE_PORT);
    // Destination port number
    udp->udph_destport = htons(atoi(argv[2]));

    udp->udph_len = htons(sizeof(struct udpheader));
#endif
    // Calculate the checksum for integrity
    ip->iph_chksum = csum((unsigned short *)buffer, sizeof(struct ipheader) + sizeof(struct udpheader));

    // Inform the kernel do not fill up the packet structure. we will build our own...
    if(setsockopt(sd, IPPROTO_IP, IP_HDRINCL, val, sizeof(one)) < 0)
    {
        perror("setsockopt() error");
        exit(-1);
    }
    else
        printf("setsockopt() is OK.\n");

    // Send loop, send for every 2 second for 100 count
    printf("Trying...\n");
    printf("Using raw socket and UDP protocol\n");
    printf("Using Target IP: %s port: %u.\n", argv[1], atoi(argv[2]));

    int count;
    for(count = 1; count <=20; count++)
    {
        if(sendto(sd, buffer, ip->iph_len, 0, (struct sockaddr *)&din, sizeof(din)) < 0) // Verify
        {
            perror("sendto() error");
            exit(-1);
        }
        else
        {
            printf("Count #%u - sendto() is OK.\n", count);
            sleep(2);
        }
    }

    close(sd);

    return 0;
}
```

If anyone understands why, please tell me. Thanks.

---


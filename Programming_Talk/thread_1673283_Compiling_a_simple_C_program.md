---
title: "Compiling a simple C program"
date: 2011-01-22
forum: Programming Talk
---

### Post by SteelCore on 2011-01-22
I'm trying to compile this simple C program on 10.04 but without success. The code is from a C programming book. I get the following error messages:
```
$ gcc program2_11.c 
program2_11.c:3:65: error:  limits.h : No such file or directory
program2_11.c: In function ‘main’:
program2_11.c:9: error: ‘CHAR_MIN’ undeclared (first use in this function)
program2_11.c:9: error: (Each undeclared identifier is reported only once
program2_11.c:9: error: for each function it appears in.)
program2_11.c:9: error: ‘CHAR_MAX’ undeclared (first use in this function)
program2_11.c:11: error: ‘UCHAR_MAX’ undeclared (first use in this function)
program2_11.c:13: error: ‘SHRT_MIN’ undeclared (first use in this function)
program2_11.c:13: error: ‘SHRT_MAX’ undeclared (first use in this function)
program2_11.c:15: error: ‘USHRT_MAX’ undeclared (first use in this function)
program2_11.c:16: error: ‘INT_MIN’ undeclared (first use in this function)
program2_11.c:16: error: ‘INT_MAX’ undeclared (first use in this function)
program2_11.c:17: error: ‘UINT_MAX’ undeclared (first use in this function)
program2_11.c:19: error: ‘LONG_MIN’ undeclared (first use in this function)
program2_11.c:19: error: ‘LONG_MAX’ undeclared (first use in this function)
program2_11.c:21: error: ‘ULONG_MAX’ undeclared (first use in this function)
program2_11.c:23: error: ‘LLONG_MIN’ undeclared (first use in this function)
program2_11.c:23: error: ‘LLONG_MAX’ undeclared (first use in this function)
program2_11.c:25: error: ‘ULLONG_MAX’ undeclared (first use in this function)
```
any help is appreciated. Thank you.

---

### Post by gyussz on 2011-01-22
The problem is with the include of the limits.h header file.
Original code:
```
#include < limits.h >
```
After removing the spaces It should compile fine.

---

### Post by SteelCore on 2011-01-22
It did. Thank you again.

---

### Post by meson2439 on 2011-01-22
I've checked it. Apparently you forgot to convert type. I've edited the file a little bit, enough to show you what's going wrong. I assume you need the limits.h for something.

Hope it helps

---

### Post by greenmonkeey on 2011-02-14
:p hi ubuntu geeks.


wana ur help....i m writing a packet sniffer....when i run this code ,compiler shw me some errors in it...
well i think the prob will be because of switching my lapy.before i was using p4 and nw i m using 64 bit core i-3.....can u tell me wat can be the prob in code i m providing u tat code....:o

regards
drv

---

### Post by greenmonkeey on 2011-02-14
....drv cont..
oops here is the code...
#include<stdio.h>
#include<stdlib.h>
#include<sys/socket.h>
#include<features.h>
#include<linux/if_packet.h>
#include<linux/if_ether.h>
#include<errno.h>
#include<sys/ioctl.h>
#include<net/if.h>
#include<linux/ip.h>
#include<linux/tcp.h>
#include<netinet/in.h>


int CreateRawSocket(int protocol_to_sniff)
{
    int rawsock;

    if((rawsock = socket(PF_PACKET, SOCK_RAW, htons(protocol_to_sniff)))== -1)
    {
        perror("Error creating raw socket: ");
        exit(-1);
    }

    return rawsock;
}

int BindRawSocketToInterface(char *device, int rawsock, int protocol)
{
    
    struct sockaddr_ll sll;
    struct ifreq ifr;

    bzero(&sll, sizeof(sll));
    bzero(&ifr, sizeof(ifr));
    
    /* First Get the Interface Index  */


    strncpy((char *)ifr.ifr_name, device, IFNAMSIZ);
    if((ioctl(rawsock, SIOCGIFINDEX, &ifr)) == -1)
    {
        printf("Error getting Interface index !\n");
        exit(-1);
    }

    /* Bind our raw socket to this interface */

    sll.sll_family = AF_PACKET;
    sll.sll_ifindex = ifr.ifr_ifindex;
    sll.sll_protocol = htons(protocol); 


    if((bind(rawsock, (struct sockaddr *)&sll, sizeof(sll)))== -1)
    {
        perror("Error binding raw socket to interface\n");
        exit(-1);
    }

    return 1;
    
}

void PrintPacketInHex(unsigned char *packet, int len)
{
    unsigned char *p = packet;

    printf("\n\n---------Packet---Starts----\n\n");
    
    while(len--)
    {
        printf("%.2x ", *p);
        p++;
    }

    printf("\n\n--------Packet---Ends-----\n\n");

}


PrintInHex(char *mesg, unsigned char *p, int len)
{
    printf(mesg);

    while(len--)
    {
        printf("%.2X ", *p);
        p++;
    }

}


ParseEthernetHeader(unsigned char *packet, int len)
{
    struct ethhdr *ethernet_header;

    if(len > sizeof(struct ethhdr))
    {
        ethernet_header = (struct ethhdr *)packet;

        /* First set of 6 bytes are Destination MAC */

        PrintInHex("Destination MAC: ", ethernet_header->h_dest, 6);
        printf("\n");
        
        /* Second set of 6 bytes are Source MAC */

        PrintInHex("Source MAC: ", ethernet_header->h_source, 6);
        printf("\n");

        /* Last 2 bytes in the Ethernet header are the protocol it carries */

        PrintInHex("Protocol: ",(void *)&ethernet_header->h_proto, 2);
        printf("\n");

        
    }
    else
    {
        printf("Packet size too small !\n");
    }
}

ParseIpHeader(unsigned char *packet, int len)
{
    struct ethhdr *ethernet_header;
    struct iphdr *ip_header;

    /* First Check if the packet contains an IP header using
       the Ethernet header                                */

    ethernet_header = (struct ethhdr *)packet;

    if(ntohs(ethernet_header->h_proto) == ETH_P_IP)
    {
        /* The IP header is after the Ethernet header  */
        
        if(len >= (sizeof(struct ethhdr) + sizeof(struct iphdr)))
        {
            ip_header = (struct iphdr*)(packet + sizeof(struct ethhdr));
            
            /* print the Source and Destination IP address */

            printf("Dest IP address: %s\n", inet_ntoa(ip_header->daddr));
            printf("Source IP address: %s\n", inet_ntoa(ip_header->saddr));
    

        }
        else
        {
            printf("IP packet does not have full header\n");
        }

    }
    else
    {
        /* Not an IP packet */

    }
}



ParseTcpHeader(unsigned char *packet , int len)
{
    struct ethhdr *ethernet_header;
    struct iphdr *ip_header;
    struct tcphdr *tcp_header;

    /* Check if enough bytes are there for TCP Header */

    if(len >= (sizeof(struct ethhdr) + sizeof(struct iphdr) + sizeof(struct tcphdr)))
    {
        /* Do all the checks: 1. Is it an IP pkt ? 2. is it TCP ? */
        
        ethernet_header = (struct ethhdr *)packet;

        if(ntohs(ethernet_header->h_proto) == ETH_P_IP)
        {
            ip_header = (struct iphdr *)(packet + sizeof(struct ethhdr));

            if(ip_header->protocol == IPPROTO_TCP)
            {
                tcp_header = (struct tcphdr*)(packet + sizeof(struct ethhdr) + ip_header->ihl*4 );
                /* Print the Dest and Src ports */

                printf("Source Port: %d\n", ntohs(tcp_header->source));
                printf("Dest Port: %d\n", ntohs(tcp_header->dest));

            }
            else
            {
                printf("Not a TCP packet\n");
            }
        }
        else
        {
            printf("Not an IP packet\n");
        }    
        
    }
    else
    {
        printf("TCP Header not present \n");

    } 
}

int ParseData(unsigned char *packet, int len)
{
    struct ethhdr *ethernet_header;
    struct iphdr *ip_header;
    struct tcphdr *tcp_header;
    unsigned char *data;
    int data_len;

    /* Check if any data is there */

    if(len > (sizeof(struct ethhdr) + sizeof(struct iphdr) + sizeof(struct tcphdr)))
    {
        
        ip_header = (struct iphdr*)(packet + sizeof(struct ethhdr));

        
        data = (packet + sizeof(struct ethhdr) + ip_header->ihl*4 +sizeof(struct tcphdr));
        data_len = ntohs(ip_header->tot_len) - ip_header->ihl*4 - sizeof(struct tcphdr);

        if(data_len)
        {
            printf("Data Len : %d\n", data_len);
            PrintInHex("Data : ", data, data_len);
            printf("\n\n");        
            return 1;    
        }
        else
        {
            printf("No Data in packet\n");
            return 0;
        }
    }
    else
    {
        printf("No Data in packet\n");
        return 0;
    }     

}

int IsIpAndTcpPacket(unsigned char *packet, int len)
{
    struct ethhdr *ethernet_header;
    struct iphdr *ip_header;

    ethernet_header = (struct ethhdr *)packet;

    if(ntohs(ethernet_header->h_proto) == ETH_P_IP)
    {
        ip_header = (struct iphdr *)(packet + sizeof(struct ethhdr));

        if(ip_header->protocol == IPPROTO_TCP)
            return 1;
        else        
            return -1;
    }
    else
    {
        return -1;
    }
    
}

main(int argc, char **argv)
{
    int raw;
    unsigned char packet_buffer[2048]; 
    int len;
    int packets_to_sniff;
    struct sockaddr_ll packet_info;
    int packet_info_size = sizeof(packet_info);

    /* create the raw socket */

    raw = CreateRawSocket(ETH_P_IP);

    /* Bind socket to interface */

    BindRawSocketToInterface(argv[1], raw, ETH_P_IP);

    /* Get number of packets to sniff from user */

    packets_to_sniff = atoi(argv[2]);

    /* Start Sniffing and print Hex of every packet */
    
    while(packets_to_sniff--)
    {
        if((len = recvfrom(raw, packet_buffer, 2048, 0, (struct sockaddr*)&packet_info, &packet_info_size)) == -1)
        {
            perror("Recv from returned -1: ");
            exit(-1);
        }
        else
        {
            /* Packet has been received successfully !! */

            PrintPacketInHex(packet_buffer, len);

            /* Parse Ethernet Header */
            
            ParseEthernetHeader(packet_buffer, len);
            
            /* Parse IP Header */

            ParseIpHeader(packet_buffer, len);

            /* Parse TCP Header */

            ParseTcpHeader(packet_buffer, len);
            
            if(IsIpAndTcpPacket(packet_buffer, len))
            {
                if(!ParseData(packet_buffer, len))
                    packets_to_sniff++;
            }
            
        }
    }
    
    
    return 0;
}

---

### Post by Arndt on 2011-02-14
> **greenmonkeey said:**
> :p hi ubuntu geeks.


wana ur help....i m writing a packet sniffer....when i run this code ,compiler shw me some errors in it...
well i think the prob will be because of switching my lapy.before i was using p4 and nw i m using 64 bit core i-3.....can u tell me wat can be the prob in code i m providing u tat code....:o

regards
drv

1) start a new thread for your question; this one has already been marked as solved, which is confusing
2) put your code inside CODE tags (use the # symbol in the tool bar)
3) don't type as if you were hunted by wolves; take half a minute to read what you've written
4) show what error messages you are talking about

---

### Post by Zugzwang on 2011-02-14
> **greenmonkeey said:**
> :p hi ubuntu geeks.


wana ur help....i m writing a packet sniffer....when i run this code ,compiler shw me some errors in it...
well i think the prob will be because of switching my lapy.before i was using p4 and nw i m using 64 bit core i-3.....can u tell me wat can be the prob in code i m providing u tat code....:o

regards
drv

Three things:
[LIST]
[*]Please try to write proper English. Most of the people here simply won't understand the words "shw", "nw", "wat" and "tat", and it also took me several minutes to get some sense out of your writing. Note that most people here are *not* native English speakers.
[*]Secondly, try to embed your code in "Code"-tags and apply some formatting algorithm. This makes it much easier to read.
[*]You code compiles for me and does not produce any error, but no warnings (provided that it is meant to be C and not C++ code). Can copy *copy and paste* what you get as an error message when you compile here? Also include how you are are compiling. I'm getting:
```

me@my-computer:/tmp$ gcc test.c 
test.c: In function &#8216;BindRawSocketToInterface&#8217;:
test.c:34: warning: incompatible implicit declaration of built-in function &#8216;bzero&#8217;
test.c:40: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
test.c: In function &#8216;PrintInHex&#8217;:
test.c:83: warning: format not a string literal and no format arguments
test.c: In function &#8216;ParseIpHeader&#8217;:
test.c:145: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
test.c:146: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;

```
[/LIST]

---

### Post by greenmonkeey on 2011-02-14
okay i can understand ...i will b writing in full format from now onwards...
cool:p

so @zig i hv encountered these warnings ....
socket.c: In function &#8216;BindRawSocketToInterface&#8217;:
socket.c:34: warning: incompatible implicit declaration of built-in function &#8216;bzero&#8217;
socket.c:40: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
socket.c: In function &#8216;PrintInHex&#8217;:
socket.c:83: warning: format not a string literal and no format arguments
socket.c: In function &#8216;ParseIpHeader&#8217;:
socket.c:145: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;
socket.c:146: warning: format &#8216;%s&#8217; expects type &#8216;char *&#8217;, but argument 2 has type &#8216;int&#8217;


i hv also made some changes. somewht it is reduced.....
and i m using ubuntu 10.10 and i m compiling this code as

gcc -o socket socket.c

wat to do?

---

### Post by greenmonkeey on 2011-02-14
sry i m using 10.10 maverick

---

### Post by Zugzwang on 2011-02-14
The first thing is that what you are getting are *warnings* and not *errors*. That's not the same and mixing these when asking for help puts us on the wrong track here.

With respect to your first two warnings: "warning: incompatible implicit declaration of built-in function" means that you forgot to include the header files in which "bswap" and "strnlen" were declared. look up which these are (use google, for example), include them and the warnings should be gone. In recent versions, the GCC people have cleaned up their header files a bit, which is likely to have caused the difference.

Then, for the fourth and fifth warning: The "inet_ntoa" function does not seem to return a "char *" but rather an integer value. Find out where this comes from. Probably it is declared that way somewhere in the Linux headers you are using?

Finally, the third warning tells you that this statement might we wrong. In particular, if "mesg" contains a "%" symbol, your code will probably segfault because printf will then try to access values you don't prove. So instead of "printf(mesg);" the following might be better: "printf("%s",mesg);"

By the way: What do you mean by "somewht it is reduced"?

---


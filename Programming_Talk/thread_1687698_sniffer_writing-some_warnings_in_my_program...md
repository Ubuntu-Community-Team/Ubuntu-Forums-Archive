---
title: "sniffer writing-some warnings in my program.."
date: 2011-02-14
forum: Programming Talk
---

### Post by greenmonkeey on 2011-02-14
problem in writing a sniffer....

i m using ubuntu 10.10  i3-core os 64 bit and encountering some problems in running a sniffer program...these are the warnings below.....help guys...:p

socket.c: In function ‘BindRawSocketToInterface’:
socket.c:34: warning: incompatible implicit declaration of built-in function ‘bzero’
socket.c:40: warning: incompatible implicit declaration of built-in function ‘strncpy’
socket.c: In function ‘PrintInHex’:
socket.c:83: warning: format not a string literal and no format arguments
socket.c: In function ‘ParseIpHeader’:
socket.c:145: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’
socket.c:146: warning: format ‘%s’ expects type ‘char *’, but argument 2 has type ‘int’

---

### Post by greenmonkeey on 2011-02-14
reply me pls....

wat should i do....

---

### Post by Some Penguin on 2011-02-14
Read the error messages.

(1) Read the man page for bzero.  You're missing a header.
(2) Read the man page for strncpy.  You're missing a header.
(3) Add a string argument that contains the formatting parameters.
(4) Don't treat int like char*.
(5) Don't treat int like char*.

---

### Post by Zugzwang on 2011-02-14
First, avoid double-posts. That is simply not kind to the people answering your posts. So I'm repeating my [post]("http://ubuntuforums.org/showpost.php?p=10457911&postcount=11") from the other thread here. Also, *do* include your code to make sure that people are not simply guessing what is wrong. The following statements are based on the code that the OP wrote in the other thread.

With respect to your first two warnings: "warning: incompatible implicit declaration of built-in function" means that you forgot to include the header files in which "bswap" and "strnlen" were declared. look up which these are (use google, for example), include them and the warnings should be gone. In recent versions, the GCC people have cleaned up their header files a bit, which is likely to have caused the difference.

Then, for the fourth and fifth warning: The "inet_ntoa" function does not seem to return a "char *" but rather an integer value. Find out where this comes from. Probably it is declared that way somewhere in the Linux headers you are using?

Finally, the third warning tells you that this statement might we wrong. In particular, if "mesg" contains a "%" symbol, your code will probably segfault because printf will then try to access values you don't prove. So instead of "printf(mesg);" the following might be better: "printf("%s",mesg);"

---

### Post by greenmonkeey on 2011-02-14
still receiving these warnings...

 In function ‘BindRawSocketToInterface’:
socket.c:42: warning: incompatible implicit declaration of built-in function ‘strncpy’ is the prob in

i hv added #include<string.h>
wats can be the prob in BindRawSocket function.

---

### Post by greenmonkeey on 2011-02-14
[http://ubuntuforums.org/showthread.php?t=1673283](http://ubuntuforums.org/showthread.php?t=1673283)  
i already pasted my code their....i hv made changes in it which u told me still getting above 2 warnings..?

---

### Post by Zugzwang on 2011-02-14
> **greenmonkeey said:**
> [http://ubuntuforums.org/showthread.php?t=1673283](http://ubuntuforums.org/showthread.php?t=1673283)  
i already pasted my code their....i hv made changes in it which u told me still getting above 2 warnings..?

Sorry, whose code has been pasted?

Since adding the line "#include <string.h>" fixed the first two warnings for me, I would suggest, to rule out simple mistakes, that you copy&paste your new code here in "CODE" tags.

---

### Post by greenmonkeey on 2011-02-15
#include<strings.h>
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

       BindRawSocketToInterface(char *device, int rawsock, int protocol)
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
    printf("%s",mesg);

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

            printf("Dest IP address: %d\n", inet_ntoa(ip_header->daddr));
            printf("Source IP address: %d\n", inet_ntoa(ip_header->saddr));
    

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


uodated code and how u attach the file here i hv to paste whole code here....whn i attach any file it shws errors..

---

### Post by worksofcraft on 2011-02-15
change the first line to read:
```

#include <string.h>

```

so there is no "s" at the end of strings

p.s. if you compile it with -Wall -pedantic you get loads more warnings and also it doesn't actually run because it says:

```

$ ./a.out
Error creating raw socket: : Operation not permitted

```

p.s... some suggestions:
add the return type "int" on line 31 to read:
```

int BindRawSocketToInterface(char *device, int rawsock, int protocol)

```

add return type "void" on line 84 to read:
```

void PrintInHex(char *mesg, unsigned char *p, int len)

```

do likewise on line 97 and 128 and 168

then on line 276 specify the return type of main as int

---

### Post by greenmonkeey on 2011-02-15
omg tat was a silly mistake....thanks guys now there are no warnings but when i run this program as

./socket eht0 1

 Error creating raw socket: : Operation not permitted...:p

---

### Post by greenmonkeey on 2011-02-15
so wat should i do to run this program...and i dnt knw abt -wall- pedantic...i m just reading it now..

---

### Post by worksofcraft on 2011-02-15
> **greenmonkeey said:**
> omg tat was a silly mistake....thanks guys now there are no warnings but when i run this program as

./socket eht0 1

 Error creating raw socket: : Operation not permitted...:p

I suspect there are still more bugs...
```

$ sudo ./a.out
Segmentation fault

```

oh no my bad... it doesn't crash if I specify eth0 and it does apear to be sniffing at my internet connexion :)
```


$ sudo ./a.out eth0 1

```

---

### Post by greenmonkeey on 2011-02-15
> **greenmonkeey said:**
> omg tat was a silly mistake....thanks guys now there are no warnings but when i run this program as

./socket eht0 1

 Error creating raw socket: : Operation not permitted...:p
  i did the same as u told me...but when i run it as ./socket eth0 1 same error as above...no change.

"1"- number of packets to sniff

---

### Post by worksofcraft on 2011-02-15
> **greenmonkeey said:**
> i did the same as u told me...but when i run it as ./socket eth0 1 same error as above...no change.

"1"- number of packets to sniff

you need to run it with superuser privilege. Type "sudo" in front of the command... evidently mine compiled into a.out and yours is called socket but it's the same program

oh and your ethernet card is called eth0 not eht0 :popcorn:

---

### Post by greenmonkeey on 2011-02-15
> **worksofcraft said:**
> you need to run it with superuser privilege. Type "sudo" in front of the command... evidently mine compiled into a.out and yours is called socket but it's the same program

oh and your ethernet card is called eth0 not eht0 :popcorn:
ya that was a typing mistake here..i wrote eth0 only with sudo(super user privilege)...but it ask for the pass i give it and its in process bt not shwing any output...:p

---

### Post by worksofcraft on 2011-02-15
> **greenmonkeey said:**
> ya that was a typing mistake here..i wrote eth0 only with sudo(super user privilege)...but it ask for the pass i give it and its in process bt not shwing any output...:p

try the "ifconfig" command to confirm you are using eth0
I don't want to post any of the output I get because the information might be used to hack my computer.

---

### Post by greenmonkeey on 2011-02-15
> **worksofcraft said:**
> try the "ifconfig" command to confirm you are using eth0
I don't want to post any of the output I get because the information might be used to hack my computer.


ya ifconfig command is showing eth0,lo and others

i hv to put my interface into promiscous mode?

---

### Post by worksofcraft on 2011-02-15
> **greenmonkeey said:**
> ya ifconfig command is showing eth0,lo and others

i hv to put my interface into promiscous mode?

maybe... soz IDK it still seg faults sometimes and the warnings that the compiler gives may help find out why.

---

### Post by greenmonkeey on 2011-02-15
> **worksofcraft said:**
> may sbe... soz IDK it still seg faults sometimes and the warnings that the compiler gives may help find out why.

 
hey crafty

i have put my eth0 in promisc mode and still whn i run this program it waits and shows no output...my program is running on your system? Is it sniffing packets frm the network?

---

### Post by greenmonkeey on 2011-02-15
> **greenmonkeey said:**
> hey crafty

i have put my eth0 in promisc mode and still whn i run this program it waits and shows no output...my program is running on your system? Is it sniffing packets frm the network?


well thanks to all genius mind here....finally i run it, i was a prob of mode....thnks u ...:p

DRV

---

### Post by greenmonkeey on 2011-02-15
> **greenmonkeey said:**
> well thanks to all genius mind here....finally i run it, i was a prob of mode....thnks u ...:p

DRV

one more thing can u tell me best guides from where u hv learn networking programming?

---

### Post by worksofcraft on 2011-02-15
> **greenmonkeey said:**
> one more thing can u tell me best guides from where u hv learn networking programming?

Soz wuz AFK... I never did do much network programming, just a dabble once long ago but I tried to compile your code out of curiosity.

It's funny how styles have changed and to think that old code you dug up was considered professional back then :D

p.s. anyway I just booted my pc and ran this
```

$ sudo ./a.out eth0 10
[sudo] password for chris: 


---------Packet---Starts----

00 1f d0 ....

--------Packet---Ends-----

Destination MAC: ** ** ** ** ** ** 
Source MAC: ** ** ** ** ** ** ** 
Protocol: 08 00 
Dest IP address: **********
Source IP address: ***********
Not a TCP packet
Data Len : 121
Data : 0C 75 62....
etcetera...

```

You won't get anything until you actually do something on the networks... like post an update to the Ubuntu forum ;)

p.s. the *'s are where I manually censored sensitive information.

---

### Post by greenmonkeey on 2011-02-15
> **worksofcraft said:**
> Soz wuz AFK... I never did do much network programming, just a dabble once long ago but I tried to compile your code out of curiosity.

It's funny how styles have changed and to think that old code you dug up was considered professional back then :D

p.s. anyway I just booted my pc and ran this
```

$ sudo ./a.out eth0 10
[sudo] password for chris: 


---------Packet---Starts----

00 1f d0 ....

--------Packet---Ends-----

Destination MAC: ** ** ** ** ** ** 
Source MAC: ** ** ** ** ** ** ** 
Protocol: 08 00 
Dest IP address: **********
Source IP address: ***********
Not a TCP packet
Data Len : 121
Data : 0C 75 62....
etcetera...

```You won't get anything until you actually do something on the networks... like post an update to the Ubuntu forum ;)

p.s. the *'s are where I manually censored sensitive information.

ya bro i got the same output but with different addresses and packets lol.....obviously
:p

---


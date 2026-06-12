---
title: "no output in my sniffer prog"
date: 2011-02-21
forum: Programming Talk
---

### Post by greenmonkeey on 2011-02-21
#include<string.h>
#include<stdio.h>
#include<stdlib.h>
#include<sys/socket.h>
#include<features.h>
#include<linux/if_packet.h>
#include<linux/if_ether.h>
#include<errno.h>
#include<sys/ioctl.h>
#include<net/if.h>


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
        }
    }
    
    
    return 0;
}

hey i can compile it successfully but when i run it ,it gives no output on the screen...wat can be the problem?:KS:KS

---

### Post by Zugzwang on 2011-02-21
> **greenmonkeey said:**
> 
hey i can compile it successfully but when i run it ,it gives no output on the screen...wat can be the problem?:KS:KS

First thing: please surround your code in [CODE]-tags and make sure that the code indentation is proper. Otherwise no one will read your code, as it is too cumbersome.

---

### Post by Arndt on 2011-02-21
> **greenmonkeey said:**
> 
hey i can compile it successfully but when i run it ,it gives no output on the screen...wat can be the problem?:KS:KS

I don't know, but maybe you're running it as a normal user, not as root? Only root can sniff packets (if you're doing what I think you're doing).

In any case, look at all the return values, and detect error conditions. Otherwise it will be very hard to determine exactly why the program is failing.

---


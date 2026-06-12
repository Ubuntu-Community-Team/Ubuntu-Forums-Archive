---
title: "Using libpcap to capture and inject problems"
date: 2007-08-14
forum: Programming Talk
---

### Post by ADT on 2007-08-14
I have a question about the way libpcap works.

I have a computer C with two network interface cards. 
One interface is connected to a computer A.
The other interface is connected to a computer B. 

When I run my program it captures packets from both interfaces and then injects the captured packets to the opposite interfaces.

In otherwords computer A can send data to computer B through computer C and vice versa.

The problem I'm having is that all interface cards I am using are 100 Mbps but the max speed that I can reach between the Computer A and the Computer B is only 400Kbps.

How can I get pcap_capture and pcap_inject to process packets faster than 400 Kbps?


```

#include <pcap.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <pthread.h>
#include <arpa/inet.h>
#include <time.h>
#include <errno.h>

struct iface_settings {
	char ip [15];
	char client_dev [15];
    char server_dev [15];
	char filter [100];
    bpf_u_int32 dev_net;
    bpf_u_int32 dev_mask;
	int is_iface_client;
};

struct iface_list {
    struct iface_settings server;
    struct iface_settings client;
};

struct thread_list {
    pthread_t capture_loop_thread1;
    pthread_t capture_loop_thread2;
};

struct data_list {
    struct thread_list threads;
    struct iface_list ifaces;
};


void packet_injection ( u_char* user, 
                        const struct pcap_pkthdr* packet_header, 
                        const u_char* packet_data );

void *packet_capture ( void *arg );



int main ()
{
    printf ( "\nClient Internet Connector Program\n" );
    printf ( "====================================\n" );
    
    struct data_list wle;
        
    char errbuf [PCAP_ERRBUF_SIZE];
    
    /* Server Interface Settings */
    strncpy ( wle.ifaces.server.ip, "192.168.1.1", 15 );
    strncpy ( wle.ifaces.server.client_dev, "eth1", 15 );
    strncpy ( wle.ifaces.server.server_dev, "eth0", 15 );
    /*strncpy ( wle.ifaces.server.filter, "src host 192.168.1.1 and dst host 192.168.1.100", 100 );*/
    strncpy ( wle.ifaces.server.filter, "dst host 192.168.1.100", 100 );
    wle.ifaces.server.is_iface_client = 0;
    
    if ( ( pcap_lookupnet ( wle.ifaces.server.server_dev, &wle.ifaces.server.dev_net, 
                            &wle.ifaces.server.dev_mask, errbuf) ) == -1 )
    {
        printf ( "\n%s\n",errbuf );
        exit ( 1 );
    }
    
    
    /* Client Interface Settings */
    strncpy ( wle.ifaces.client.ip, "192.168.1.100", 15 );
    strncpy ( wle.ifaces.client.client_dev, "eth1", 15 );
    strncpy ( wle.ifaces.client.server_dev, "eth0", 15 );
    /*strncpy ( wle.ifaces.client.filter, "src host 192.168.1.100 and dst host 192.168.1.1", 100 );*/
    strncpy ( wle.ifaces.client.filter, "src host 192.168.1.100", 100 );
    wle.ifaces.client.is_iface_client = 1;
        
    if ( ( pcap_lookupnet ( wle.ifaces.client.client_dev, &wle.ifaces.client.dev_net,
                            &wle.ifaces.client.dev_mask, errbuf) ) == -1 )
    {
        printf ( "\n%s\n",errbuf );
        exit ( 1 );
    }
    
    
    if ( ( pthread_create ( &wle.threads.capture_loop_thread1, NULL,
                            &packet_capture, &wle.ifaces.client ) ) != 0 )
    {
        printf ( "\nError: Thread creation.\n" );
        exit ( 1 );
    }
    
    if ( ( pthread_create ( &wle.threads.capture_loop_thread2, NULL,
                            &packet_capture, &wle.ifaces.server ) ) != 0 )
    {
        printf ( "\nError: Thread creation.\n" );
        exit ( 1 );
    }
    
    
    pthread_join ( wle.threads.capture_loop_thread1, NULL );
    pthread_join ( wle.threads.capture_loop_thread2, NULL );
    
    
    return 0;
}


void *packet_capture ( void *arg )
{    
    struct iface_settings *iface = ( struct iface_settings* ) arg;
    struct bpf_program capture_filter;
    
    pcap_t *capture_int_desc;
    
    char errbuf [ PCAP_ERRBUF_SIZE ];
    char *capture_interface;
    char *inject_interface;
        
    struct in_addr dev_mask_addr;
    struct in_addr dev_net_addr;
    dev_mask_addr.s_addr = iface->dev_mask;
    dev_net_addr.s_addr = iface->dev_net;
    
    /* Check to see if client or server thread */
    if ( iface->is_iface_client == 1 )
    {
        capture_interface = iface->client_dev;
        inject_interface = iface->server_dev;
    }
    else if ( iface->is_iface_client == 0 )
    {
        capture_interface = iface->server_dev;
        inject_interface = iface->client_dev;
    }
    else
    {
        printf ( "\nError: The variable is_iface_client has an invalid value. %d\n", 
                 iface->is_iface_client );
        exit ( 1 );
    }
    
    /* Setup the Capture Interface */
    /*
    pcap_open_live (    Device:     The interface to capture packets on.
                        snaplen:    Max number of bytes to capture.
                        promisc:    Specifies whether the interface be put into promiscuous mode.
                        to_ms:      Timeout Milliseconds how long to wait before reading a packet.
                        errbuf:     Holds the error string if an error occurs.
    */
    if ( ( capture_int_desc = pcap_open_live ( capture_interface, BUFSIZ, 
                              1, -1, errbuf ) ) == NULL )
    {
        printf ( "\nError: %s\n", errbuf );
        exit ( 1 );
    }
    
    /* Setup the Capture Filter */
    pcap_compile ( capture_int_desc, &capture_filter, iface->filter, 0, iface->dev_mask );
    
    pcap_setfilter ( capture_int_desc, &capture_filter );
    
    
    
    /* Setup packet capture loop */
    pcap_loop ( capture_int_desc, -1, packet_injection, inject_interface );
    
    /* Close interfaces */
    pcap_close ( capture_int_desc );
    
    return NULL;
}


void packet_injection ( u_char* user, 
                       const struct pcap_pkthdr* packet_header,
                       const u_char* packet_data )
{
    char* inject_interface = user;
    char errbuf [ PCAP_ERRBUF_SIZE ];
    pcap_t* inject_int_desc;
     
    /* Setup the Injection Interface */
    if ( ( inject_int_desc = pcap_open_live ( inject_interface, BUFSIZ,
                             1, -1, errbuf ) ) == NULL )
    {
        printf ( "\nError: %s\n", errbuf );
        exit ( 1 );
    }
    
    /*
    packet_header->len  The lenght of the packet captured
    packet_header->ts   The time stamp the packet was captured
    */    
    
    /* To make the inject process sleep to emulate even slower network speeds */
    /* 
        struct timespec
            time_t tv_sec;  Seconds
            long tv_nsec;   nanoseconds ( must be in range of 0 to 999 999 999 )
    */
    double delay_time = 0;
    struct timespec tv;
    tv.tv_sec = ( time_t ) delay_time;
    tv.tv_nsec = ( long ) ( ( delay_time - tv.tv_sec ) * 1e+9 );
    nanosleep (&tv, &tv);
    
    pcap_inject ( inject_int_desc, packet_data, packet_header->len );
    
    pcap_close ( inject_int_desc );
}

```

---

### Post by ADT on 2007-08-15
bump

---

### Post by ADT on 2007-08-19
The reason that packet capturing and packet injecting is so slow is because libpcap can only process and capture about at about 2% of the networks capacity. This is because of the way the Linux kernel works. On BSD systems libpcap can capture 34% of a network packets from the live wire and on Windows 64%.

"Using Linux for packet capture is a very bad idea!"

The way around this problem is to either use BSD or use a version of libpcap called ncap which is optimised to capture packets at a faster rate.

Link where I found out about libpcap problems:
[http://tobi.oetiker.ch/tobjour/2004-09-30-11-08-f-1.html]("http://tobi.oetiker.ch/tobjour/2004-09-30-11-08-f-1.html")

nCap site
[http://www.nmon.net/nCap.html]("http://www.nmon.net/nCap.html")

---

### Post by dinopeso on 2009-01-08
im trying to compile this code because i want take yours as an example to do my job. i want to put ip packets on a tcp/ip stack of  a O.S. 

could someone help me? am i wrong?

gcc program.c -pthread -lpcap -o program

i got some errors listed below:

/tmp/ccALBdoJ.o: In function `packet_injection':
Teste.c:(.text+0x563): undefined reference to `pcap_inject'
collect2: ld returned 1 exit status

In your case, you are capturing packets of one device and injecting on another. I want only to inject some packets. Could anyone guide me?

---


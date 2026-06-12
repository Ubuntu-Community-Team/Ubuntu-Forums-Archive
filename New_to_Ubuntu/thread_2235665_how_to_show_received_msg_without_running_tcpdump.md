---
title: "how to show received msg without running tcpdump"
date: 2014-07-22
forum: New to Ubuntu
---

### Post by zerop2 on 2014-07-22
this program can only show received message when
tcpdump eth0 in another console

when tcpdump running, it will show extra character E, even if char[3] and memcpy(&a,&b[14], 3)

why it can not show received message without running tcpdump?

which is missing ?


i guess the buffer in somewhere is not full, so that it stop at somewhere and tcpdump help to flush this buffer
so that it can show received msg when running tcp dump

then i guess that i have to set mmap

both client and server i added code below , just different in 
    PACKET_TX_RING and 
    PACKET_RX_RING  and use DONTWAIT when sendto

but it return compile error, socket invalid option
```

//96/96 = 1, 1*1 = 1
tpacket_req req;
req.tp_block_size=96;
req.tp_frame_size=96;
req.tp_block_nr=1;
req.tp_frame_nr=(req.tp_block_size / req.tp_frame_size) * req.tp_block_nr;
if ( (setsockopt(s,
    SOL_PACKET,
    PACKET_TX_RING,
    (char *)&req,
    sizeof(req))) != 0 ) {
    perror("setsockopt()");
    close(s);
    return 1;
};
char* map=(char*)mmap(NULL, req.tp_block_size * req.tp_block_nr, PROT_READ|PROT_WRITE|PROT_EXEC, MAP_SHARED, s, 0);

```


```

#include <sys/socket.h>
#include <linux/if_packet.h>
#include <linux/if_ether.h>
#include <linux/if_arp.h>
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <netinet/in.h>
#include <ctype.h>
//#define ETH_FRAME_LEN 1518
// 14 + 46-1500 + 4
#define ETH_FRAME_LEN 60
char *trimwhitespace(char *str)
{
  char *end;

  // Trim leading space
  while(isspace(*str)) str++;

  if(*str == 0)  // All spaces?
    return str;

  // Trim trailing space
  end = str + strlen(str) - 1;
  while(end > str && isspace(*end)) end--;

  // Write new null terminator
  *(end+1) = 0;

  return str;
}
char *replace_str(char *str, char *orig, char *rep)
{
  static char buffer[4096];
  char *p;

  if(!(p = strstr(str, orig)))  // Is 'orig' even in 'str'?
    return str;

  strncpy(buffer, str, p-str); // Copy characters from 'str' start to 'orig' st$
  buffer[p-str] = '\0';

  sprintf(buffer+(p-str), "%s%s", rep, p+strlen(orig));

  return buffer;
}
int main()
{
int s; /*socketdescriptor*/

s = socket(AF_PACKET, SOCK_RAW, htons(ETH_P_ALL));
if (s == -1) { printf("socket error"); }

/*target address*/
struct sockaddr_ll socket_address;

/*buffer for ethernet frame*/
unsigned char* buffer = (unsigned char*)malloc(ETH_FRAME_LEN);

/*pointer to ethenet header*/
unsigned char* etherhead = (unsigned char*)buffer;
    
/*userdata in ethernet frame*/
unsigned char* data = (unsigned char*)(buffer);
    
/*another pointer to ethernet header*/
struct ethhdr *eh = (struct ethhdr *)etherhead;
 
int send_result = 0;

/*our MAC address*/
unsigned char src_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};

/*other host MAC address 10:78:d2:ad:90:cb*/
unsigned char dest_mac[6] = {0x10, 0x78, 0xd2, 0xad, 0x90, 0xcb};

/*prepare sockaddr_ll*/

/*RAW communication*/
socket_address.sll_family   = PF_PACKET;    
/*we don't use a protocoll above ethernet layer
  ->just use anything here*/
socket_address.sll_protocol = htons(ETH_P_IP);    

/*index of the network device
see full code later how to retrieve it*/
socket_address.sll_ifindex  = 2;

/*ARP hardware identifier is ethernet*/
socket_address.sll_hatype   = ARPHRD_ETHER;
    
/*target is another host*/
socket_address.sll_pkttype  = PACKET_OTHERHOST;

/*address length*/
socket_address.sll_halen    = ETH_ALEN;        
/*MAC - begin*/
socket_address.sll_addr[0]  = 0x10;        
socket_address.sll_addr[1]  = 0x78;        
socket_address.sll_addr[2]  = 0xd2;
socket_address.sll_addr[3]  = 0xad;
socket_address.sll_addr[4]  = 0x90;
socket_address.sll_addr[5]  = 0xcb;
/*MAC - end*/
socket_address.sll_addr[6]  = 0x00;/*not used*/
socket_address.sll_addr[7]  = 0x00;/*not used*/

int length=0;
int succeed = 0;
int i =0;
int j = 0;
while(true)
{
    length = recvfrom(s, buffer, ETH_FRAME_LEN, 0, NULL, NULL);

    if (length == -1 && succeed == 0) {
        printf("recv error\n");
        succeed = 2;
    }
    if(length > 0)
    {
        char buff[46] = "\0";
        memcpy(&buff, &buffer[14], 46);
        printf(trimwhitespace(buff));
    }
}
}

```

---


---
title: "Why am i getting these strange packets while running my packet capture module written"
date: 2013-02-11
forum: Programming Talk
---

### Post by arunpushkar on 2013-02-11
I have made an packet capture application running on intel machine, it   is capturing packets with src address- 17.0.0.0 destination ip-   66.0.0.0, source port- 0, destination port- 0, and protocol- 0 what does   these packets mean ?
The code written to interpreter captured  bytes is given below. Which  basically locate source address, destination  address, source port,  destination port, and protocol from various  headers from packet  captured. After it is done then only TCP and UDP  packets are stored  into a file. so it means only those packets having  protocol number 6,17  should be saved but when i go through the file the  packets with  protocol 0,20,255,100,8,66 are also saved more over strange  IP address  are also seen like.2.8.2.8, 17.0.0.0, 66.0.0.0, 0.0.0.0 etc  what are  these packets, am i correct in my approach.
```
inline u_int32_t hash_function(const u_char *packet, int pkt_len)  {   u_int32_t hash=0;   u_int8_t next_protocol;   u_int32_t src_ip,dst_ip;     u_short  src_p,dst_p;                unsigned short ip_hdr_len;          // Checking if it is a IPv4 or IPv6 packet     struct ether_header *eptr;  /* net/ethernet.h */     eptr = (struct ether_header *) packet;      if (ntohs (eptr->ether_type) == ETHERTYPE_IP) // means it is IPv4 pkt         {             struct iphdr *ip4h = (struct iphdr *)(packet  + sizeof(struct ethhdr) );         ip_hdr_len =ip4h->ihl*4;         next_protocol=ip4h->protocol;         pktFeatures.src_ip=ntohl(ip4h->saddr);         pktFeatures.dst_ip=ntohl(ip4h->daddr);         pktFeatures.pkt_len=pkt_len;         switch (next_protocol) //Check the Protocol and do accordingly...         {         case 6:  //TCP Protocol                {                 struct tcphdr *tcph=(struct tcphdr*)(packet + ip_hdr_len + sizeof(struct ethhdr));                 pktFeatures.src_p=ntohs(tcph->th_sport);                 pktFeatures.dst_p=ntohs(tcph->th_dport);                 pktFeatures.protocol=next_protocol;                 writeBytes((char *)&pktFeatures,sizeof(struct packet_features),WRITE_TO_FILE);             }             break;         case 17: //UDP Protocol             {                 struct udphdr *udph = (struct udphdr*)(packet + ip_hdr_len  + sizeof(struct ethhdr));                 pktFeatures.src_p=ntohs(udph->uh_sport);                 pktFeatures.dst_p=ntohs(udph->uh_sport);                 pktFeatures.protocol=next_protocol;                 writeBytes((char *)&pktFeatures,sizeof(struct packet_features),WRITE_TO_FILE);                              }             break;         default: //Some Other Protocol like ARP FTP etc.             {                 printf(" * Some Other Protocol \n");                                          }         }         int rm=0;         }/*else  if (ntohs (eptr->ether_type) == ETHERTYPE_IPV6) // means it is IPv6 pkt             {                              u_int32_t *s, *d;             struct ip6_hdr *ip6h = (struct ip6_hdr *)(packet  + sizeof(struct ethhdr) );             ip_hdr_len=320;             next_protocol=ip6h->ip6_un1_nxt; // is the next protocol type             s = (u_int32_t *) &ip6h->ip6_src, d = (u_int32_t *) &ip6h->ip6_dst;             hash=(s[0] + s[1] + s[2] + s[3] + d[0] + d[1] + d[2] + d[3]+ip6h->ip6_un1_nxt); // ip6_un1_nxt is the next protocol                                         type TCP/UDP can be extention header ? need to be catered for                           }else hash=0;          */            return hash;  } 
```

---

### Post by dwhitney67 on 2013-02-11
I looked around my office, and with all the various keyboards we have,  each has an "Enter" or "Return" key.

You should consider using this key on your keyboard more often when you develop software.  As is, I cannot read your code snip that has been posted as a single line.  Could you please reformat the code so that it is readable?

---

### Post by arunpushkar on 2013-02-11
sorry @dwhitney67 code is as follows

```

inline u_int32_t hash_function(const u_char *packet, int pkt_len)
{
   u_int32_t hash=0;
   u_int8_t next_protocol;
   u_int32_t src_ip,dst_ip;
   u_short  src_p,dst_p;
   unsigned short ip_hdr_len;          // Checking if it is a IPv4 or IPv6 packet
   struct ether_header *eptr;  /* net/ethernet.h */     
  eptr = (struct ether_header *) packet;      
  if (ntohs (eptr->ether_type) == ETHERTYPE_IP) // means it is IPv4 pkt         
  {             
       struct iphdr *ip4h = (struct iphdr *)(packet  + sizeof(struct ethhdr) );
       ip_hdr_len =ip4h->ihl*4;
       next_protocol=ip4h->protocol;
       pktFeatures.src_ip=ntohl(ip4h->saddr);
       pktFeatures.dst_ip=ntohl(ip4h->daddr);
       pktFeatures.pkt_len=pkt_len;
       switch (next_protocol) //Check the Protocol and do accordingly...         
       {        
          case 6:  //TCP Protocol                
          {                 struct tcphdr *tcph=(struct tcphdr*)(packet + ip_hdr_len + sizeof(struct ethhdr));
                            pktFeatures.src_p=ntohs(tcph->th_sport);
                            pktFeatures.dst_p=ntohs(tcph->th_dport);
                            pktFeatures.protocol=next_protocol; 
                           writeBytes((char *)&pktFeatures,sizeof(struct packet_features),WRITE_TO_FILE);
          }             
                break;        
          case 17: //UDP Protocol
           {                
                   struct udphdr *udph = (struct udphdr*)(packet + ip_hdr_len  + sizeof(struct ethhdr));
                   pktFeatures.src_p=ntohs(udph->uh_sport);
                   pktFeatures.dst_p=ntohs(udph->uh_sport);
                   pktFeatures.protocol=next_protocol;
                   writeBytes((char *)&pktFeatures,sizeof(struct packet_features),WRITE_TO_FILE);
           }             
                  break;         
           default: //Some Other Protocol like ARP FTP etc.
            {                 
                  printf(" * Some Other Protocol \n");
            }         
          }         
          int rm=0;         
          }
 return hash;  }
```

---

### Post by dwhitney67 on 2013-02-11
I must admit that I'm not familiar with the ether_header structure (until I looked at the header file today).  Also, I was unaware that there is data *prior *to the IP Header, which your code seems to imply.
```

struct iphdr *ip4h = (struct iphdr *)(packet  + sizeof(struct ethhdr) );

```

In the past, when I dabbled with raw sockets, I perused packets using struct ip, struct tcphdr (or udphdr).  I do not have experience working with raw data using IPv6.

Examining the layout of the IPv4 header (as shown [here]("http://en.wikipedia.org/wiki/IPv4")), I do not believe the struct ether_header should be mapped to the beginning of the packet as shown in your code.

Could you please explain where you found the information regarding the mapping of the header?

---

### Post by arunpushkar on 2013-02-11
I referred to the code given at this link 
[http://www.binarytides.com/packet-sniffer-code-c-libpcap-linux-sockets/](http://www.binarytides.com/packet-sniffer-code-c-libpcap-linux-sockets/)

---

### Post by Tony Flury on 2013-02-11
> **arunpushkar said:**
> I referred to the code given at this link 
[http://www.binarytides.com/packet-sniffer-code-c-libpcap-linux-sockets/](http://www.binarytides.com/packet-sniffer-code-c-libpcap-linux-sockets/)

That example is using the libcap library which takes data straight from a network device, and so will include the ethernet headers etc.

How is your program getting it's data - if you aren't using libcap then your code probably wont work.

---

### Post by arunpushkar on 2013-02-11
i am using PF_RING to get data. following is the brief how am i receiving the packet from pfring capturing is working fine.

```

char *hddr;
 struct pfring_pkthdr hdr;
 u_char *packet_data_buffer,*pktr;
 packet_data_buffer=(u_char *)malloc(snaplen*sizeof(u_char));
struct packet_load *pkt_load;

if(pfring_recv(pd, &packet_data_buffer, 0, &hdr, 1 /* wait_for_packet */) > 0)
        {
            tk=hdr.len-hdr.caplen;
            //caplen is the length of the data we have captured while len is the length of the  packet on the wire. We might capture only parts of the packet, that length will be 'caplen', while 'len' is the original length
           
 if(!(tk<0)&&!(hdr.caplen>snaplen)&&!(hdr.caplen<0)) // for checking invalid packets
            {
               pkt_load=(struct packet_load *)malloc(sizeof(struct packet_load));
               hddr=(char *)malloc(sizeof(struct pcap_disk_pkthdr));
                hddr=memcpy(hddr,(char *)&hdr,sizeof(struct pcap_disk_pkthdr));
                pkt_load->header=hddr;
                pkt_load->header_length=sizeof(struct pcap_disk_pkthdr);
                pktr=(u_char *)malloc(hdr.caplen*sizeof(u_char));
                pktr=memcpy(pktr,packet_data_buffer,(hdr.caplen*sizeof(u_char)));
                pkt_load->packet=pktr;
                pkt_load->packet_length=(hdr.caplen*sizeof(u_char));
                hash_function(pkt_load->packet,pkt_load->packet_length);

```

---


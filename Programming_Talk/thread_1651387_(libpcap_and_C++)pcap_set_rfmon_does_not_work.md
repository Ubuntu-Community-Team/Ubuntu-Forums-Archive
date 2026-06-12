---
title: "(libpcap and C++)pcap_set_rfmon does not work?"
date: 2010-12-23
forum: Programming Talk
---

### Post by cftmon on 2010-12-23
I am trying to set my device to monitor mode, and i  know its capable of being in monitor mode as doing a "iwconfig wlan0 mode  monitor" works, i run my code and i can capture packets from anywhere.
  The problem is that in libpcap it fails to set my device to monitor  mode at all(without entering the above-mentioned command line).I can't  capture any packets until i manually connect to a access point.
     ```
    pcap_t *handler = pcap_create("wlan0",errbuff);
       if(pcap_set_rfmon(handler,1)==0 )
       {
           std::cout << "monitor mode enabled" << std::endl;
       }
       handler=pcap_open_live ("wlan0", 2048,0,512,errbuff);
       int status = pcap_activate(handler); //it returns 0 here.
      pcap_loop(handler, 10 ,procPacket, NULL );

```  so is this a code problem, or the pcap library problem?Anybody  successfully set their device to monitor mode without using command  lines?I am using a Realtek2500/netbeans 6.9 btw.

---

### Post by cftmon on 2010-12-26
i gave out on this one and i instead use system calls to execute the iwconfig commands in my program.Not preety but it works.


I also noticed that tcpdump also won't allow me to run by adapter monitor mode, keeps complaining monitor mode can't be set.maybe this is a driver issue?


One question:anyone  knows how look at beacon frames and extract their source/destination and BSSID MAC addresses?The example codes shown does not work at all, i am thinking the casting was wrong: 
```

typedef struct mac_header{
unsigned char fc[2];
unsigned char id[2];
unsigned char add1[6];
unsigned char add2[6];
unsigned char add3[6];
unsigned char sc[2];
}mac_header;

typedef struct frame_control{
unsigned protocol:2;
unsigned type:2;
unsigned subtype:4;
unsigned to_ds:1;
unsigned from_ds:1;
unsigned more_frag:1;
unsigned retry:1;
unsigned pwr_mgt:1;
unsigned more_data:1;
unsigned wep:1;
unsigned order:1;
}frame_control;

//pcap handler callback function
void procPacket(u_char *arg, const struct pcap_pkthdr *pkthdr, const u_char *packet)
{
          struct mac_header *p = (struct mac_header *)(packet);//is this correct?
          struct frame_control *control = (struct frame_control *)(p->fc);
         //check if this is a beacon packet
         if ((control->protocol == 0) && (control->type == 0) && (control->subtype == 8))
         {
             // extract MAC address


         }


}
```

---


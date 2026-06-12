---
title: "Raw socket: unexpected IP header added when sending self-made IP/TCP packets"
date: 2015-10-22
forum: Programming Talk
---

### Post by esolve on 2015-10-22
I want to use raw socket to send TCP packets which is a full IP packet(so the packet has IP header, TCP header and TCP payload, but has no ethernet header. The IP source and destination addresses are in a WLAN, 192.168.0.105 and 192.168.0.103), with the following codes
  ```

        int on;
        on = 0;
        if ((sendfd = socket(AF_INET, SOCK_RAW, IPPROTO_RAW)) < 0) {
                perror("raw socket");
                exit(1);
        }
        if (setsockopt(sendfd, IPPROTO_IP, IP_HDRINCL, &on, sizeof(on)) < 0) {
                perror("setsockopt");
                exit(1);
        }
 
        nr_bytes = sendto(sendfd, packet, ip_len, 0, (struct sockaddr*)&client_addr, addr_len);

```    


I use TCPdump to capture the sent-out packet and notice it has added an additional IP header to the IP packet, and the IP protocol number is 255&#65288;ip->ip_p is 255&#65289;. So it has two IP headers(with same pair of src and dst IP), which is unexpected.


what are the problems? thank you!

---


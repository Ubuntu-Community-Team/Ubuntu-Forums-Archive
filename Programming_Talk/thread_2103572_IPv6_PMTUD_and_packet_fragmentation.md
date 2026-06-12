---
title: "IPv6 PMTUD and packet fragmentation"
date: 2013-01-10
forum: Programming Talk
---

### Post by crux2005 on 2013-01-10
Hello,

I am doing PMTUD in C++ using IPv6 and I need from the IPv6 stack/OS kernel to drop packets that are bigger than the link MTU or to signalize "this packet needs fragmentation" (using ancillary data or ICMPv6 reply). How can I achieve this behavior? 

I tried `setsockopt` with `IPV6_DONTFRAG` (defined it in my code `#define IPV6_DONTFRAG 62` because i get redefinition errors if I include the linux/in6.h header file), `setsockopt` with `IPV6_MTU_DISCOVER`, `int on = IPV6_PMTUDISC_DO` and `setsockopt` with `IPV6_RECVPATHMTU` (defined in my code #define IPV6_RECVPATHMTU 60).

But the OS is still sending packets bigger then the link MTU and I am not getting the `PACKET TOO BIG` reply or `ancillary data` with `cmsg_level == IPPROTO_IPV6` and `cmsg_type == IPV6_PATHMTU` when needed.

Part of my code:
```
/** sending ICMP packet*/
     if (((length = sendto(mysocket, packet, lengthBuff, 0, result->ai_addr, result->ai_addrlen)) < 0) && (errno == EMSGSIZE)){
            
         // works for IPv4, doesn't work with IPv6
         cout << "changing maxBuff and lengthBuff size" << endl;
         
            maxBuff = lengthBuff;
            lengthBuff = (minBuff + maxBuff) / 2;

            if (packet) {
                delete(packet);
                packet = NULL;
            }

            
        } else if (length < 0){
         
         cerr << "Error: sending data." << endl;

                freeaddrinfo(result);
                close(mysocket);

                if (packet) {
                    delete(packet);
                    packet = NULL;
                }

                exit(1);
        } else if(((recvmsg(mysocket, &msg, 0)) != -1) && (errno != EINTR)) {
            
            // reading ancillary dada as described in  *Unix-Linux Addison-Wesley - Stevens2003 - Unix Network Programming, page 736*
            cmsgh = CMSG_FIRSTHDR(&msg);    
            
            if(cmsgh != NULL) {
                cout << "getting msg " << endl;
                cout << "msg len " << msg.msg_controllen << endl;
            
            
                if(cmsgh->cmsg_level == IPPROTO_ICMPV6 && cmsgh->cmsg_type == IPV6_PATHMTU)
                {
                    cout << "CMSGHEADER - GOOD" << endl;
                    //mtustruct = CMSG_DATA(&msg); 

                maxBuff = lengthBuff;
                lengthBuff = (minBuff + maxBuff) / 2;

                if (packet) {
                    delete(packet);
                    packet = NULL;
                }

                }
                else{

                    cout << "different ancillary data. " << endl;
                    cout << " level " << cmsgh->cmsg_level << " type " << cmsgh->cmsg_type << endl;
                }
            }
         
        } else {
            
            cout << "no ERROR with sendto and no RESCVMSG" << endl;
        } 

        /** receiving ICMP data */
        tv.tv_sec = 3;
        tv.tv_usec = 0;
        
        int retval; // select

            FD_ZERO(&mySet);
            FD_SET(mysocket, &mySet);

            retval = select(mysocket + 1, &mySet, NULL, NULL, &tv);
            
            if (retval == -1) {
                cerr << "select failed" << endl;
                //break;
                exit(1);
            } else if (retval) {
                if ((length = recvfrom(mysocket, buffer, MAX, 0, result->ai_addr, &(result->ai_addrlen))) == -1) {
                    cerr << "Error: receiving data." << endl;
                } else {
                    icmpRec = (struct icmp6_hdr*) buffer;
                    
                    if((icmpRec->icmp6_type == ICMP6_PACKET_TOO_BIG)) {
                        
                        
                        cout << "next hop MTU: " << ntohl(icmpRec->icmp6_mtu) << endl;
                        maxBuff = ntohl(icmpRec->icmp6_mtu);                       
                       
                    } else if ((icmpRec->icmp6_type == ICMP6_ECHO_REPLY) && (ntohs(icmpRec->icmp6_id) == pid) && (ntohs(icmpRec->icmp6_seq) == (seq - 1))) {
                        cout << "code " << ntohs(icmpRec->icmp6_code) << endl;
                        cout << "ICMP ECHO REPLY" << endl;
                        minBuff = lengthBuff;
                    
                    }
                }
            }
```Im running Ubuntu 12.10 on VirtualBox 4.26 and GNS3 for the virtual  network. The virtual Cisco C3660 router has just basic configuration:  ip, ipv6 address, no shut and set MTU's.

What am I doing wrong? 
Thank you for any help.

---

### Post by crux2005 on 2013-01-12
I realized, setsockopt with IPV6_DONTFRAG is not working for me, but setsockopt with  IPV6_MTU_DISCOVER is working for the own interface. The eth1 interface MTU is 1500 (default) and if sendto wants to send packets with bigger size, errno is set to EMSGSIZE. After some time I get PACKET TOO BIG message for these not send messages from the **own kernel/OS**. 

**My real problem is, I am not receiving (Ubuntu 12.10 running on VirtualBox 4.2.6) PACKET TOO BIG messages from the virtual router (Cisco c3660) running on GNS3.**

---


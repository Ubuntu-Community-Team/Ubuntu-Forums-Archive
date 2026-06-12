---
title: "Sending Packets to class C private address"
date: 2010-03-11
forum: Programming Talk
---

### Post by TMagic*04 on 2010-03-11
I have four machines all with two network cards one (eth0) connected to internet, and the other (eth1) has a customly added private address (192.168.0.0). These added network cards are all connected by ethernet over a hub.

I'm trying to send packets to it on a specific port using packet sockets (I'm under the impression this is the best way) however when I want to bind to the socket  I get a perror bind:: Socket operation on non-socket
 

My link level header is: (where pa the address i'm sending to is 192.168.0.0:1337, with or without the port number appended I get the same problem)
```

llHeader.sll_family = AF_PACKET;
llHeader.sll_protocol = htons(ETH_P_ALL);
llHeader.sll_ifindex = if_nametoindex("eth1");
llHeader.sll_halen = 4;//IP_ADDR_LEN
if(inet_pton(AF_INET, pa, &llHeader.sll_addr)<0)
  perror("ptoning pa:");  

```and I'm binding like so:
```

if (packet_socket = socket(AF_PACKET, SOCK_RAW, htons(ETH_P_ALL))<0)
      perror("socket:");
  
if(bind(packet_socket, (struct sockaddr *)&llHeader, addrlen) < 0)
    perror("bind:");  

```If anyone could give me some advice as to what the problem is , or if there's simply a better way of unicasting to a private address then I'd be very thankful, as I'm well and truly stumped right now.

I'm thinking it could be a problem with binding to a private address? But if the interface is enable with the address and is up  then I don't understand why there should be a problem.

---

### Post by psusi on 2010-03-11
The only reason to use packet sockets is to do funky things like spoof your address.  What exactly are you trying to do?

---

### Post by TMagic*04 on 2010-03-11
I'm trying to implement a mesh client, vis a vis 80211s. I'm pretty close to, and as all the machines have a logical connection, I was under the impression that this should work.

---

### Post by TMagic*04 on 2010-03-11
As an update by changing the protocol type to IPPROTO_UDP, I've managed to get rid of the bind error, and it appears to be working in that the receive loop sets up fine, and on the other machine the packet is sent off successfully. However I never see the message being received...odd

This is my receiving loop
```

while(1)
{
receiver = recvfrom(packet_socket, &pkt, sizeof(pkt), 0, (struct sockaddr *)&llHeader, &addrlen);
   if(receiver < 0)
   {
     perror("receiver:");
    // return -1;
   }                      
   else if(receiver > 1)
   {
     //deal with it
  }
}

```and my sending code..
```

if(sendto(packet_socket, &pkt, sizeof(pkt), MSG_DONTROUTE, (struct sockaddr *)&llHeader, sizeof(llHeader)) < 0)
      perror("sendto");
  

```

Once again, any help really would be much appreciated.

---


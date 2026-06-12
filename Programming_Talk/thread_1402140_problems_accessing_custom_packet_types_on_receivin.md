---
title: "problems accessing custom packet types on receiving them"
date: 2010-02-08
forum: Programming Talk
---

### Post by TMagic*04 on 2010-02-08
Language: C/C++

Hi,

As part of an over all network client i'm writing, I'm trying to send my own variation of ARP packets, then receive them on another box and take the data out etc.

I seem to be able to send it alright, and I do receive it. How i'm receiving it is as so:

      receiver = recvfrom(rcvMulticastDescriptor, message, sizeof(message), MSG_WAITALL, (struct sockaddr *)&mcastAddress, &addrlen);    

where message is my buffer and is of type char. 
and the packet sent is of this form:
struct arp_packet 
{
 // u_char targ_hw_addr[ETH_HW_ADDR_LEN];
 // u_char src_hw_addr[ETH_HW_ADDR_LEN];
  u_short frame_type;
  u_short hw_type;
  u_short prot_type;
  char hw_addr_size;
  char prot_addr_size;
  u_short op;
  char sndr_hw_addr[ETH_HW_ADDR_LEN];
 // u_char sndr_ip_addr[IP_ADDR_LEN];
  char rcpt_hw_addr[ETH_HW_ADDR_LEN];
 // u_char rcpt_ip_addr[IP_ADDR_LEN];
  char padding[18];
};

Logically I know it's not right that a custom struct is in a char array and a direct cast won't work, but I'm not sure exactly how I can go from my message buffer to the appropriate type.

If anyone has done something similar in the past or knows somewhere where I can possibly find more about recasting packets from the buffer I'd be very thankful.

---

### Post by TMagic*04 on 2010-02-08
I just solved my own problem, for some reason I failed to realise that I don't have to use a char buffer and just used my the struct as the buffer

---

### Post by Some Penguin on 2010-02-09
> **TMagic*04 said:**
> I just solved my own problem, for some reason I failed to realise that I don't have to use a char buffer and just used my the struct as the buffer

Provided that you're using identical or near-identical systems.  This is problematic, however, if you have systems with different sizes or byte orderings for the same C types.

---

### Post by TMagic*04 on 2010-02-09
Do you think it would be better to parse it all to a string for the transmission?

---

### Post by Some Penguin on 2010-02-09
It'd be fairly traditional to decide how many bytes go in each field (which is normally going to be one for the chars, and probably two for the shorts) and to have multi-byte numbers be in network-byte order (i.e. most-significant-byte first).

Then the client needs to read the specified number of bytes for each field, and swap byte orderings if needed.  You can use the fixed-size types (defined in sys/types.h for instance) for additional paranoia.  Doing it this way means that you also shouldn't be seeing wacky problems from byte alignment.

e..g.

```

#include <sys/types.h>
...
u_short  some_number = ...
u_int8_t octet_MSB = (some_number >> 8) % 256;
u_int8_t octet_LSB = (some_number % 256);

// then ensure that t_octet_MSB precedes t_octet_LSB in the array that's sent

```

In general, you can usually assume that a C 'char' means 8 bits, which keeps things less ugly.  It's guaranteed to be at least 8 bits and doesn't have to be, but 8 is usual. 

If you don't care about bloat or mimicking actual ARP, and if you had more complex types, it might be interesting to look at serialization frameworks.  Those are mostly for conveniently sending complex objects and the like, however.

---


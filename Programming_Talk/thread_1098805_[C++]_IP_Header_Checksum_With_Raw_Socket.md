---
title: "[C++] IP Header Checksum With Raw Socket"
date: 2009-03-17
forum: Programming Talk
---

### Post by dwhitney67 on 2009-03-17
I am computing and then setting the checksum for an IP header just prior to sending out a packet across a raw socket.

When the packet arrives at the destination, all of the data is identical to what I had sent, except for the checksum.  Why is the kernel setting the IP header checksum to a different value than what was sent?  Is my value incorrect?  If so, then why was the message delivered to the destination?

Here's the code I use to compute the checksum:
```

uint16_t Checksum(const uint16_t* buf, unsigned int nbytes)
{
  uint32_t sum = 0;

  for (; nbytes > 1; nbytes -= 2)
  {
    sum += *buf++;
  }

  if (nbytes == 1)
  {
    sum += *(unsigned char*) buf;
  }

  sum  = (sum >> 16) + (sum & 0xFFFF);
  sum += (sum >> 16);

  return ~sum;
}

```

---

### Post by cabalas on 2009-03-17
The first thing that springs to mind is that the TTL field should have changed this changing will produce a different checksum.

When you say the data hasn't changed from what you sent worries me a little as the TTL field changes each hop from source to destination even if it is going from your machine to your router and back again the TTL is meant to change.

Aside from that at first glance the code for computing looks right but I haven't gone and tested it.  Have you checked it against an checksum calculator just to make sure the calculations are right [http://mna.nlanr.net/Software/HEC/hec.html](http://mna.nlanr.net/Software/HEC/hec.html)

---

### Post by dwhitney67 on 2009-03-17
The documentation does indicate that the TTL field will be changed at each hop, however in my case, I am working on the same system (i.e. client on 127.0.0.1 sending to server at same IP).  Thus I do not know if this is considered a "hop".

The thing that really perplexes me is that I have no way to verify if I am indeed computing/inserting the correct checksum.  The kernel is inserting its own checksum, even though I setup the socket using code similar to the following:
```

  const int          optVal = 1;
  const unsigned int optLen = sizeof(optVal);

  if (setsockopt(sd, IPPROTO_IP, IP_HDRINCL, (void*) &optVal, optLen) < 0)
  {
    // error...
  }

```

As for the TTL, the sent value is identical as to what is received.  In fact, all values, both in the IP header, the UDP header, and the message data itself are identical... all except for the IP header checksum.

---

### Post by slavik on 2009-03-17
just to reinforce the above point, if the packet goes through a NAT, the header will get changed so that to the outside, the NAT is requesting data, not you.

but I am interested ... why are you writing raw data on sockets?

EDIT: I retract my statement above about NAT since it's not applicable. my only other thought is that maybe the kernel is ignoring what you put in ...

---

### Post by dwhitney67 on 2009-03-17
> **slavik said:**
> ...
but I am interested ... why are you writing raw data on sockets?
...
It's the only way I have found that I can programatically set the ToS field in the header.  I need to be able to modify the ToS on a per message transaction vs. just setting the entire socket at a particular ToS setting.

EDIT:  Actually, the setsockopt() function was recommended (by a colleague) of an alternative way to set the ToS.  I ended up using this method rather than play around with raw sockets, which is a pain, and affects the application's performance.
```

int           sd   = socket(AF_INET, SOCK_DGRAM, IPPROTO_UDP);
unsigned char dscp = 0x30;  // CS6
...
setsockopt(sd, IPPROTO_IP, IP_TOS, (void*) &dscp, sizeof(dscp));
...

```

---

### Post by slavik on 2009-03-17
interesting ^^

---

### Post by dwhitney67 on 2009-03-18
Well, I sorted out the problem.  The checksum I am computing is correct; the issue was how I was inserting it into the raw IP header.

I was under the impression that all values that are 16-bits long had to be assigned using htons().  Apparently when assigning the checksum-value, it is exempt from this rule.  Of course, I am running my client and my server on an Intel architecture, so it would be nice to know if this is true if dealing with dissimilar architectures.

---

### Post by muralig on 2009-10-29
Hey, just wanted to say that was perhaps the shortest/best example of how to calculate a checksum.  There are a lot of bad / lengthy examples out there.

---

### Post by dwhitney67 on 2009-10-30
> **muralig said:**
> Hey, just wanted to say that was perhaps the shortest/best example of how to calculate a checksum.  There are a lot of bad / lengthy examples out there.
Thanks, but unfortunately I cannot take credit for it.  I lifted the algorithm from some place that I Googled.  You're right though... it is sweet and simple.

---

### Post by sopordave on 2011-03-22
When in doubt, consult the original RFC: [http://www.faqs.org/rfcs/rfc1071.html](http://www.faqs.org/rfcs/rfc1071.html)

The RFCs are usually pretty easy to read. In addition to having an example implementation in C, it has a a discussion on the effects of endianness (none!).

---

### Post by slavik on 2011-03-23
dead threads stay dead

---


---
title: "Berkeley Packet Filter - pcapy and impacket"
date: 2010-07-30
forum: Programming Talk
---

### Post by wconstantine on 2010-07-30
I'm trying to create a packet filter for pcapy. It says I need to use BPF (Berkeley Packet Filter). I'm at loss as how to use Ethernet in a BPF filter string.

I know that the ARP type is repsented by 0x0806 in an Ethernet frame. I think the offset is 16, it's more if you should include the preamble and start of frame delimiter... Don't know if those are to be included.

If I want, say, to filter only udp packets. That's easy. The filter string would look like this: "ip[9] = 0x11". However, I need to know how I do the same but for Ethernet. I've found no documentation nor examples of this. 

**ether[21:2] = 0x0806**

Is this somewhat near what I'm looking for? I've tried the filter string using tcpdump. I've verified with Wireshark that I'm receiving ARP packets.

Edit: More pondering;

The ethernet frame should look like this:

Preamble (7 bytes) Start-of-frame (1 byte) SRC MAC (6 bytes) DST MAC (6 bytes) Ethertype (2 bytes)

The offset should be 21 then? And Ether type spans two bytes so ether[21:2] should be correct?

Edit2: Solved. All that was needed was the word ARP. :evil:

---


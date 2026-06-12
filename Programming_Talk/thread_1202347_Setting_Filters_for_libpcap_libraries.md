---
title: "Setting Filters for libpcap libraries"
date: 2009-07-02
forum: Programming Talk
---

### Post by codingfreak on 2009-07-02
Hi

I am trying to write a sniffer application using "libpcap" libraries.

I have some problems with filtering packets of specific protocol. When I try to give filter as "port 23" i.e for telnet packets I am even capturing other packets from ports 2893, 1065, 2892.

Are these telnet packets ???

Can anyone help me out what type packets are necessary for processing in HTTP, FTP and TELNET as there are different packets like SYN, ACK and so on. ....

---

### Post by smartbei on 2009-07-02
Note that the fact that a packet is headed for port 23 doesn't in fact mean that it is COMING from port 23. It could be coming from any port in fact. So are you sure your filters are failing? Try it out. start sniffing, open telnet, send something indicative, and see if it is in one of the packets returned after the filter.

---

### Post by codingfreak on 2009-07-03
Thank you [smartbei]("http://ubuntuforums.org/member.php?u=192213") for the fast reply.

Filter I am trying to give in my sniffer application is "**ip and tcp and dst port 23**"

I have taken some screen captures and placed at

```
http://3.bp.blogspot.com/_MQa_rKnACRw/Sk38BpS947I/AAAAAAAABvo/ogZ8NuT0qDE/s1600-h/02.PNG
http://1.bp.blogspot.com/_MQa_rKnACRw/Sk371fdgYWI/AAAAAAAABvg/Ru-1xe-zRQg/s1600-h/01.PNG

```In those screen shots areas I marked in RED blocks ... I do see some TCP communication going through port 23 and from source port with different port number.

Can you please suggest me any sniffing tool source which is written for Linux or UNIX specific and doesnt have GUI coding within .... As i want to learn How to dissect various network packets I am capturing through my application. Please dont say WIRESHARK it is very hard for a NEWBIE like me to understand its internals.

[IMG]http://1.bp.blogspot.com/_MQa_rKnACRw/Sk371fdgYWI/AAAAAAAABvg/Ru-1xe-zRQg/s1600-h/01.PNG[/IMG]

[IMG]http://3.bp.blogspot.com/_MQa_rKnACRw/Sk38BpS947I/AAAAAAAABvo/ogZ8NuT0qDE/s1600-h/02.PNG[/IMG]

---

### Post by smartbei on 2009-07-03
To me it looks like the filter is working fine. Note that all the packets you recieved are indeed TCP, IP, and are to the port 23.

You don't really need the source for sniffing tools in order to dissect packets. Rather, check out the various RFCs for the protocols you want to dissect. Heck, even wikipedia is pretty good - check out [http://en.wikipedia.org/wiki/Transmission_Control_Protocol](http://en.wikipedia.org/wiki/Transmission_Control_Protocol). From there you should be able to get to any common relevant protocol.

---

### Post by codingfreak on 2009-07-03
I do have information of each and every protocol theoretically ....

Thing is I am really eager to learn a robust way to dissect through packets practically ......  so the source code do might help me to learn faster and in best way ......

have you ever tried out libpcap libraries ???

---

### Post by smartbei on 2009-07-03
What language are you using? Is there a specific framework you have in mind for other parts of the application?

I have a bit of experiance using libpcap with python.

In C, for example, you might start by creating structs that represent the packet formats. Then, given the data, you could just cast the pointer to it as a pointer to the relevant struct, and your (mostly) done.

In Python, you would probably want to use something like ctypes' Structure, which allows you to define c-like structures and have them automatically parse the data.

---

### Post by codingfreak on 2009-07-03
Hi

At present I am trying out in C and in future there are chances for C++.

Since I using C .... I dont have any 3rd party framework [If any 3rd party framework 's available do reply me ...] for my application. But I have designed my own one ....

Dont think me as outstanding progammer in C .. but I am trying to get my basics in right direction .. so decided to implement a full fledged coding in C.

I am trying out with various structures but really dont have any expertise in how to parse through packets in a more robust way ....

---

### Post by pokerbirch on 2009-07-03
The Python library pcapy makes life easy. You can write a packet sniffer in about 10 lines of code.

---

### Post by codingfreak on 2009-07-06
> **pokerbirch said:**
> The Python library pcapy makes life easy. You can write a packet sniffer in about 10 lines of code.

Its not about how fastly you can develop a sniffer. It is about how much I learn in doing so .....

With the help of pcapy library in python you might require just 10 lines but I really doubt how much you learn the network internals.

---

### Post by monraaf on 2009-07-06
> **codingfreak said:**
> Its not about how fastly you can develop a sniffer. It is about how much I learn in doing so .....

With the help of pcapy library in python you might require just 10 lines but I really doubt how much you learn the network internals.

If your goal is to learn network internals, I suggest reading a good book on the subject. TCP/IP Illustrated, Volume 1 is an excellent book to start with.

---

### Post by jon zendatta on 2009-07-06
tcp/ip illustrated w.richard stevens  :KS
(addison-wesley professional computing series)

---

### Post by PandaGoat on 2009-07-06
If you want to analyze sniffed packets, you take the pointer to the beginning of the array of bytes that represents the entire packet and cast it into structures that are human-readable.  

Ip/tcp packets have three different headers and then the payload:
* ethernet header ([http://fxr.watson.org/fxr/source/net/ethernet.h](http://fxr.watson.org/fxr/source/net/ethernet.h))
* ip header ([http://en.wikipedia.org/wiki/Ip_%28struct%29](http://en.wikipedia.org/wiki/Ip_%28struct%29))
* tcp header ([http://en.wikipedia.org/wiki/Tcphdr](http://en.wikipedia.org/wiki/Tcphdr))
* payload -- like for games to fill with information about the state of the server and send to clients

```

ethhdr = (struct ether_header*)raw_packet;

iphdr = (struct ip*)(raw_packet + sizeof(struct ether_header));

tcphdr = (struct tcphdr*)(raw_packet + sizeof(struct ether_header) + iphdr->ip_hl * 4);

payload = (unsigned char*)(raw_packet + sizeof(struct ether_header) + iphdr->ip_hl * 4 + tcphdr->doff * 4);

```

raw_packet is what pcap will give you.

If you are looking at non-tcp packets, then you get the iphdr and look at iphdr->ip_p to see what protocol it uses.  But if you add the tcp part to the pcap filter, you can assume the packet uses tcp.

---

### Post by codingfreak on 2009-07-07
> **PandaGoat said:**
> If you want to analyze sniffed packets, you take the pointer to the beginning of the array of bytes that represents the entire packet and cast it into structures that human-readable.  

Ip/tcp packets have three different headers and then the payload:
* ethernet header ([http://fxr.watson.org/fxr/source/net/ethernet.h](http://fxr.watson.org/fxr/source/net/ethernet.h))
* ip header ([http://en.wikipedia.org/wiki/Ip_%28struct%29](http://en.wikipedia.org/wiki/Ip_%28struct%29))
* tcp header ([http://en.wikipedia.org/wiki/Tcphdr](http://en.wikipedia.org/wiki/Tcphdr))
* payload -- like for games to fill with information about the state of the server and send to clients

```

ethhdr = (struct ether_header*)raw_packet;

iphdr = (struct ip*)(raw_packet + sizeof(struct ether_header));

tcphdr = (struct tcphdr*)(raw_packet + sizeof(struct ether_header) + iphdr->ip_hl * 4);

payload = (unsigned char*)(raw_packet + sizeof(struct ether_header) + iphdr->ip_hl * 4 + tcphdr->doff * 4);

```raw_packet is what pcap will give you.

If you are looking at non-tcp packets, then you get the iphdr and look at iphdr->ip_p to see what protocol it uses.  But if you add the tcp part to the pcap filter, you can assume the packet uses tcp.

Hi all

Thanks for the links and suggestions

I am using libpcap libraries and able to capture the packets and traverse through the header until TCP

Can you please help me out in displaying the content in payload[data] part in TCP header.

I am accessing TCP header as shown below.

```
tcp = (struct tcphdr *)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl));
```TCP header is of size 20 bytes. Then I have no clue how to display the payload part in TCP header.

---

### Post by PandaGoat on 2009-07-08
There isn't a payload in the tcp header.  Packets consist of headers (you can safely say always an ip header) and then a payload.  The payload comes after all of the headers.

If 
```

tcp = (struct tcphdr *)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl));

```

Then the payload will be 
```

payload = (unsigned char*)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl) **+ (4*tcphdr->doff) **)

```

Reread my previous post; I'm repeating myself I believe.  I may not understand your question.

---

### Post by codingfreak on 2009-07-08
> **PandaGoat said:**
> There isn't a payload in the tcp header.  Packet consist of headers (you can safely say always an ip header) and then a payload.  The payload comes after all of the headers.

If 
```

tcp = (struct tcphdr *)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl));

```Then the payload will be 
```

payload = (unsigned char*)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl) **+ (4*tcphdr->doff) **)

```Reread my previous post; I'm repeating myself I believe.  I may not understand your question.

@PandaGoat - I got you and I was doing the same thing as you were saying before.

I feel that a Ethernet packet will have the following structure

```
**<ETHERNETHEADER 14bytes><IPHEADER 20bytes><TCPHEADER 20bytes><DATA><Ethernetchecksum 4bytes>**
```If the total packet size in above representation is 60 bytes then size of the <DATA> part would be 2 BYTES (60-(14+20+20+4)=2).

So now inorder to display the data part I am trying out as shown below [Sorry of poor programming skills in C .... I am still working out on it]

```
unsigned char *ch = (unsigned char *)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl) + 4*tcp->doff);

  for(i = 0 ; i< ((pkthdr->len)-len) ; i++) 
  {
        printf("%c",(isgraph(*ch) ? *ch : ' '));
        *ch++;
  }
  printf("\n");
```Where (pkthdr->len)-len is similar to (60-(14+20+20+4)=2)
Simply Junk data is getting printed on the screen [Even for TELNET]. Is there any better way to display the content in a more meaningful way.

---

### Post by PandaGoat on 2009-07-08
I believe your code should look like this to get the intended result.  The important changes are in bold:
```

unsigned char *ch = (unsigned char *)( packet + sizeof(struct ether_header) + (4*iphdr->ip_hl) + 4*tcp->doff);

for(i = 0; i < ((pkthdr->len)-len); i++) 
{
      printf("%c",(isgraph(*ch) ? *ch : ' '));
      **ch++;**
}
printf("\n");

```

Get rid of the asterisk, since you want to increment the pointer, not the value the pointer points to.  I would bet that the junk being printed is sequential bytes starting at the first *ch.

I don't know what isgraph() does, and I'm assuming len equals 
```
sizeof(struct ether_header) + (4*iphdr->ip_hl) + 4*tcp->doff
```

Also, you might want to print out the hexadecimal representation of the payload, as it might be easier to compare with wireshark so you can check if what you print is correct.  To do this, change %c to %X (or %x if you prefer lower case letters).

---

### Post by codingfreak on 2009-07-09
Thank you @[PandaGoat]("http://ubuntuforums.org/member.php?u=257349")

It really worked out great .... with your suggestions.

---


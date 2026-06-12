---
title: "raw sockets funny problems"
date: 2009-03-27
forum: Programming Talk
---

### Post by stonerhash on 2009-03-27
Hi there, I'm gonna describe a ridiculous problem.

I m writing some code based on raw sockets crafting a TCP packet.

The same code runs flawlessly in Ubuntu 8.04 i686 but in Ubuntu 8.10 i686 works like crap. Comparing the printed packet (befora calling sendto) and the capture by Wireshark packet one can see lots of altered bits, and even if I change the hard coded values for example destination port, all newly captured packets remain altered the same way.
 
I also tried to send some ICMP ECHO if I correctly remember ICMP ECHO has type 8 the value shown in captured packet by wireshark is 68

I have disabled IPv6 in both versions.
I know that you would ask for the code but I dont think that will help same code should run the same way on both version unless there is a bug  , I hope that someone can make a speculation about this or guide me to find out why this thing happens.

Both Ubuntu versions run on Vmware vm

Thanx

---

### Post by croto on 2009-03-28
Unless the code does not comply to specifications. I suspect the code has bugs that trigger undefined behavior.

---

### Post by efexD on 2009-03-28
Code would be nice.

---

### Post by stonerhash on 2009-03-28
I'm sending you a  link of a pinger based on ICMP with raw sockets.

[http://cboard.cprogramming.com/networking-device-communication/107801-linux-raw-socket-programming.html#post793989](http://cboard.cprogramming.com/networking-device-communication/107801-linux-raw-socket-programming.html#post793989)

I 've tested it on 8.04 and works fine in 8.10 the packet captured by Wireshark has corrupted ICMP type.

I would be glad if someone else could test it also.

I also have to mention that I use wireshark in sender's side not the receiver's. The problems also occur in lo interface two.

---

### Post by dwhitney67 on 2009-03-28
I took a look at the example code from the link you provided.  There was a minor issue when compiling it (maybe a warning?), but it was easy to correct.  When I ran the application and monitored the packet transmission from wireshark, a "malformed packet" warning was issued.

I looked into the code to see if I could adapt it using my socket library, and although there were some issues which I have not fully resolved yet, I was able to piece together a raw packet that I could send out without having Wireshark complain about the "malformed packet.".

Here's the function I used to create the raw packet, which is written in C++ syntax... sorry, I avoid C whenever I can.  It is very similar to the example you provided, although with some cleanup.
```

RawData BuildPingDatagram(const std::string& servAddr)
{
  // this buffer will contain IP header, UDP header, and payload. we'll point an ip
  // header structure at its beginning, and a UDP header structure after that to write
  // the header values into it.
  unsigned char* datagram = new unsigned char[sizeof(ip) + sizeof(icmphdr)];

  // setup offset to mark our IP header region
  ip* iph    = reinterpret_cast<ip*>(datagram);
  int ip_len = sizeof(ip) + sizeof(icmphdr);

  iph->ip_hl         = sizeof(ip) >> 2;       // 5 words (20 bytes), but could be more!
  iph->ip_v          = 4;                     // IPv4
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);         // the total length of the datagram
  iph->ip_id         = htons(54321);          // the value doesn't matter here
  iph->ip_off        = 0;
  iph->ip_ttl        = 255;
  iph->ip_p          = IPPROTO_ICMP;
  iph->ip_src.s_addr = inet_addr(servAddr.c_str());
  iph->ip_dst.s_addr = inet_addr("192.168.1.104");

  // compute checksum for the IP header (this is optional)
  iph->ip_sum = socketpp::HeaderChecksum(reinterpret_cast<const uint16_t*>(iph), iph->ip_hl << 2);

  // setup the ICMP header pointer to the appropriate offset within the datagram
  icmphdr* icmph = reinterpret_cast<icmphdr*>(datagram + (iph->ip_hl << 2));

  // fill in the ICMP header values
  icmph->type             = ICMP_ECHO;
  icmph->code             = 0;
  icmph->un.echo.id       = 0;
  icmph->un.echo.sequence = 0;
  icmph->checksum         = socketpp::HeaderChecksum(reinterpret_cast<const uint16_t*>(icmph),
                                                     sizeof(icmphdr));

  RawData rd(datagram, datagram + ip_len);

  delete [] datagram;

  return rd;
}

```
This function returns a RawData object, which is an std::basic_string<unsigned char>.  With this object, I have a pointer to the raw data and the size of that data.  It would not be too difficult to come up with a similar structure in C.

Now, the only thing I was unable to do is receive a response (an ICMP_ECHOREPLY) from the system I was pinging.  I don't know why.

P.S.  What data were you observing via WireShark that appeared erroneous?

---

### Post by stonerhash on 2009-03-28
In other words you too have observed unexpected results.

Using the code I gave you results in a corrupted ICMP type (Wireshark says obsolete ICMP type). No ICMP replies except from 127.0.0.1. I also updated the system + kernel but no results.


I'm gonna try the 9.04 beta just for the facts.

---

### Post by dwhitney67 on 2009-03-28
Ok, I sorted out the "issue" I was having.  Apparently it was with an erroneous ICMP header checksum that my app was computing.  The algorithm I employed is correct, however I had neglected to blank-out the ICMP header with zeroes prior to setting up the data within it and then computing the checksum.

Here's the code that now works on my Fedora 10 and Ubuntu 8.10 systems.
```

#include <sys/socket.h>
#include <netinet/ip.h>
#include <netinet/ip_icmp.h>
#include <arpa/inet.h>
#include <iostream>
#include <iomanip>
#include <cstring>
#include <cassert>

uint16_t Checksum(const uint16_t* buf, const size_t nbytes);
void     DisplayRaw(const unsigned char* buf, size_t bufSize);

int main()
{
  int sd = socket(PF_INET, SOCK_RAW, IPPROTO_ICMP);
  assert(sd > 0);

  setuid(getuid());

  int          opt    = 1;
  unsigned int optLen = sizeof(opt);

  int rtn = setsockopt(sd, IPPROTO_IP, IP_HDRINCL, (void*) &opt, optLen);
  assert(rtn == 0);

  unsigned char datagram[sizeof(ip) + sizeof(icmphdr)];
  const int     ip_len = sizeof(ip) + sizeof(icmphdr);
  ip*           iph    = reinterpret_cast<ip*>(datagram);
  icmphdr*      icmph  = reinterpret_cast<icmphdr*>(datagram + sizeof(ip));

  iph->ip_hl         = sizeof(ip) >> 2;
  iph->ip_v          = 4;
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);
  iph->ip_id         = htons(54321);
  iph->ip_off        = 0;
  iph->ip_ttl        = 255;
  iph->ip_p          = IPPROTO_ICMP;
  iph->ip_sum        = 0;
  iph->ip_src.s_addr = 0;
  iph->ip_dst.s_addr = inet_addr("192.168.1.103");
  iph->ip_sum        = Checksum(reinterpret_cast<const uint16_t*>(iph), iph->ip_hl << 2);

  memset((char*) icmph, 0, sizeof(icmph));
  icmph->type             = ICMP_ECHO;
  icmph->code             = 0;
  icmph->un.echo.id       = htons(1);
  icmph->un.echo.sequence = htons(1);
  icmph->checksum         = Checksum(reinterpret_cast<const uint16_t*>(icmph), sizeof(icmphdr));

  sockaddr_in sin;
  memset(&sin, 0, sizeof(sin));
  sin.sin_family      = PF_INET;
  sin.sin_addr.s_addr = inet_addr("192.168.1.103");

  std::cout << "sending...\n";
  DisplayRaw(datagram, ip_len);
  int bytes = sendto(sd, datagram, ip_len, 0, (sockaddr*) &sin, sizeof(sin));
  assert(bytes == ip_len);

  unsigned char rdbuf[sizeof(ip) + sizeof(icmphdr)];

  bytes = recv(sd, (char*) rdbuf, ip_len, 0);
  std::cout << "received...\n";
  DisplayRaw(rdbuf, bytes);
}


uint16_t Checksum(const uint16_t* buf, size_t nbytes)
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


void DisplayRaw(const unsigned char* buf, const size_t bufSize)
{
  for (size_t i = 0; i < bufSize; ++i)
  {
    std::cout << std::hex << std::setw(2) << std::setfill('0')
              << (int)buf[i] << " ";
  }
  std::cout << std::dec << std::endl;
}

```

Please note that if you want to send data along with your ping request, you need to append it after the ICMP header.  This data should be included when computing the ICMP header checksum, and obviously the length of the data plus the respective lengths of the IP and ICMP headers should be placed in the IP header.

P.S.  It doesn't hurt to also blank-out the IP header with zeroes; but I did not do that above.

---


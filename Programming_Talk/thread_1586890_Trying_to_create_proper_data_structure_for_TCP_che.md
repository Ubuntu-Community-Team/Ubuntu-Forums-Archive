---
title: "Trying to create proper data structure for TCP checksum verification in C/pcap"
date: 2010-10-02
forum: Programming Talk
---

### Post by 2Real on 2010-10-02
Hi, I'm trying to write a simple program that parses packets and prints out the relevant information. I am having trouble getting the TCP checksum verification working. What I'm supposed to do is create a pseudo TCP header and pair that with the TCP header and data and pass it to a checksum function to be verified. However, the checksum function is no verifying that data I sent to it and I cannot figure out what I'm doing wrong.

Here is the pastie of the relevant functions

[http://pastie.org/1195772](http://pastie.org/1195772)

If you need any more information, let me know. 

Any help would be appreciated since I've been stuck on this for a few days.

Thanks,

---

### Post by dwhitney67 on 2010-10-02
Here's the checksum algorithm that I have used; I believe it works.  If it doesn't, please let me know.
```

uint16_t headerChecksum(const uint16_t* data, unsigned int nbytes)
{
  uint32_t sum = 0;

  for (; nbytes > 1; nbytes -= 2)
  {
    sum += *data++;
  }

  if (nbytes == 1)
  {
    sum += *(unsigned char*) data;
  }

  sum  = (sum >> 16) + (sum & 0xFFFF);
  sum += (sum >> 16);

  return ~sum;
}

```

P.S.  uint16_t and uint32_t are available via stdint.h

---

### Post by 2Real on 2010-10-02
> **dwhitney67 said:**
> Here's the checksum algorithm that I have used; I believe it works.  If it doesn't, please let me know.
```

uint16_t headerChecksum(const uint16_t* data, unsigned int nbytes)
{
  uint32_t sum = 0;

  for (; nbytes > 1; nbytes -= 2)
  {
    sum += *data++;
  }

  if (nbytes == 1)
  {
    sum += *(unsigned char*) data;
  }

  sum  = (sum >> 16) + (sum & 0xFFFF);
  sum += (sum >> 16);

  return ~sum;
}

```

P.S.  uint16_t and uint32_t are available via stdint.h

I already have a checksum algorithm which is, [http://pastie.org/1195802](http://pastie.org/1195802). 
I know that that algorithm works. I just can't figure out what I'm doing wrong with constructing the series of data that needs to be sent to it for a TCP checksum verification.

---

### Post by dwhitney67 on 2010-10-02
Well, here's the code I have tinkered with in the past.  C++ is my preferred language, thus sorry if I'm not more accommodating.

```

/*
# Copyright (C) 2008-2009 David M. Whitney (aka "dwhitney67")
#
# This program is free software: you can redistribute it and/or modify it under 
# the terms of the GNU General Public License as published by the Free Software 
# Foundation, either version 3 of the License, or (at your option) any later 
# version.
#
# This program is distributed in the hope that it will be useful, but WITHOUT 
# ANY WARRANTY; without even the implied warranty of MERCHANTABILITY or FITNESS 
# FOR A PARTICULAR PURPOSE. See the GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License along with 
# this program. If not, see <http://www.gnu.org/licenses/>.
*/

#include "IpDataDisplayer.h"

#include <Socket/TCPClientSocket.hpp>
#include <Socket/SocketUtility.h>

#include <string>
#include <iostream>
#include <iomanip>
#include <stdexcept>
#include <cstdlib>
#include <cstring>
#include <cassert>
#include <unistd.h>


typedef std::basic_string<unsigned char> RawData;

RawData BuildTcpDatagram(const std::string& servAddr, unsigned short servPort, unsigned int seqnum, const RawData& msg);


int main(int argc, char** argv)
{
  const std::string    servAddr = (argc > 1 ? argv[1] : "127.0.0.1");
  const unsigned short servPort = (argc > 2 ? atoi(argv[2]) : 9000);
  unsigned int         seqnum   = (argc > 3 ? atoi(argv[3]) : 1);

  const unsigned char  data[]   = { 0xCA, 0xFE, 0xBA, 0xBE };
  const RawData        msg(data, sizeof(data));

  std::cout << "TCP client, using servAddr = " << servAddr << std::endl;
  std::cout << "TCP client, using servPort = " << servPort << std::endl;

  try
  {
    // Build the raw IP/TCP message
    RawData rd = BuildTcpDatagram(servAddr, servPort, seqnum, msg);

    // Create the socket
    socketpp::TCPClientSocket sock(PF_INET, SOCK_RAW);

    // We no longer need root privileges
    setuid(getuid());

    // Send the raw data
    sock.connect(servAddr, servPort);
    sock.send((const char*) rd.data(), rd.size());

    std::cout << "\nThis data was sent...\n"
              << IpDataDisplayer(IpDataDisplayer::TCP, rd)
              << std::endl;
  }
  catch (std::exception& e)
  {
    std::cerr << "Exception: " << e.what() << std::endl;
    return 1;
  }
}


RawData BuildTcpDatagram(const std::string& servAddr, unsigned short servPort, unsigned int seqnum, const RawData& msg)
{
  // Obtain the destination and source addresses to be inserted into the IP header
  sockaddr_in dst_sin;
  sockaddr_in src_sin;

  int dst_rtn = socketpp::fillAddress(PF_INET, servAddr.c_str(), servPort, &dst_sin);
  int src_rtn = socketpp::fillAddress(PF_INET, "127.0.0.1", 1234, &src_sin);
  assert(dst_rtn == 0 && src_rtn == 0);

  // this buffer will contain IP header, TCP header, and payload. we'll point an ip
  // header structure at its beginning, and a TCP header structure after that to write
  // the header values into it.
  unsigned char* datagram = new unsigned char[sizeof(ip) + sizeof(tcphdr) + msg.size()];

  // setup offsets to mark our header and data regions
  ip* iph    = reinterpret_cast<ip*>(datagram);
  int ip_len = sizeof(ip) + sizeof(tcphdr) + msg.size();

  iph->ip_hl         = sizeof(ip) >> 2;       // 5 words (20 bytes), but could be more!
  iph->ip_v          = 4;                     // IPv4
  iph->ip_tos        = 0;
  iph->ip_len        = htons(ip_len);         // the total length of the datagram
  iph->ip_id         = htons(54321);          // the value doesn't matter here
  iph->ip_off        = 0;
  iph->ip_ttl        = 255;
  iph->ip_p          = IPPROTO_TCP;
  iph->ip_sum        = 0;                      // set to 0; compute checksum later
  iph->ip_src.s_addr = src_sin.sin_addr.s_addr;
  iph->ip_dst.s_addr = dst_sin.sin_addr.s_addr;
  //iph->ip_src.s_addr = inet_addr(servAddr.c_str());
  //iph->ip_dst.s_addr = inet_addr("127.0.0.1");

  // compute checksum for the IP header (this is optional)
  iph->ip_sum = socketpp::headerChecksum(reinterpret_cast<uint16_t*>(iph), iph->ip_hl << 2);

  // now obtain our other data pointers
  tcphdr*        tcph = reinterpret_cast<tcphdr*>(datagram + (iph->ip_hl << 2));
  unsigned char* data = datagram + (iph->ip_hl << 2) + sizeof(tcphdr);

  // assign the message data
  memcpy(data, msg.data(), msg.size());

  // we'll now fill in the TCP header values
  tcph->source  = htons(0);
  tcph->dest    = htons(servPort);
  tcph->seq     = htonl(seqnum);
  tcph->ack_seq = htonl(0);
  tcph->res1    = 0;
  tcph->doff    = sizeof(tcphdr) >> 2;
  tcph->fin     = 0;
  tcph->syn     = 0;
  tcph->rst     = 0;
  tcph->psh     = 0;
  tcph->ack     = 0;
  tcph->urg     = 0;
  tcph->res2    = 0;
  tcph->window  = htons(TCP_MAXWIN);
  tcph->check   = 0;
  tcph->urg_ptr = htons(0);

  // now compute the TCP checksum
  uint16_t*    buffer     = 0;
  unsigned int bufferSize = socketpp::buildPseudoHdrBuffer(src_sin.sin_addr.s_addr, dst_sin.sin_addr.s_addr,
                                                           IPPROTO_TCP,
                                                           reinterpret_cast<uint8_t*>(tcph), sizeof(tcphdr),
                                                           msg.data(), msg.size(),
                                                           &buffer);

  tcph->check = socketpp::headerChecksum(buffer, bufferSize);

  RawData rd(datagram, datagram + ip_len);

  delete [] datagram;
  delete [] buffer;

  return rd;
}

```

Here's the rest of the code; the headerChecksum() function was provided earlier...
```

/////////////////////////////////////////////////////////////////////////////////////////////////
//
//  Function:  buildPseudoHdrBuffer
//
///////////////////////////////////////////////////////////////////////////////////////////////
unsigned int buildPseudoHdrBuffer(unsigned int src_addr, unsigned int dst_addr, unsigned int protocol,
                                  const uint8_t* hdrData, unsigned int hdrBytes,
                                  const uint8_t* msgData, unsigned int msgBytes,
                                  uint16_t** buffer)
{
  struct PseudoHeader pseudoHdr;

  pseudoHdr.s_addr   = src_addr;
  pseudoHdr.d_addr   = dst_addr;
  pseudoHdr.reserved = 0;
  pseudoHdr.protocol = protocol;
  pseudoHdr.length   = htons(hdrBytes + msgBytes);

  unsigned int   bufSize = sizeof(struct PseudoHeader) + hdrBytes + msgBytes;
  unsigned char* buf     = new unsigned char[bufSize];
  int            offset  = 0;

  memcpy(buf + offset, &pseudoHdr, sizeof(struct PseudoHeader)); offset += sizeof(struct PseudoHeader);
  memcpy(buf + offset, hdrData, hdrBytes); offset += hdrBytes;
  memcpy(buf + offset, msgData, msgBytes);

  *buffer = reinterpret_cast<uint16_t*>(buf);

  return bufSize;
}


/////////////////////////////////////////////////////////////////////////////////////////////////
//
//  Function:  fillAddress
//
///////////////////////////////////////////////////////////////////////////////////////////////
int fillAddress(int domain, const char* address, unsigned short port, struct sockaddr_in* sin)
{
  if (address == 0)
  {
    memset(sin, 0, sizeof(sockaddr_in));

    sin->sin_family      = domain;
    sin->sin_addr.s_addr = htonl(INADDR_ANY);
    sin->sin_port        = htons(port);
  }
  else
  {
    addrinfo hints;

    memset(&hints, 0, sizeof(hints));
    hints.ai_family = domain;

    addrinfo* host_info = 0;

    if (getaddrinfo(address, 0, &hints, &host_info) != 0  ||
        !host_info || !host_info->ai_addr || host_info->ai_family != domain)
    {
      if (host_info) freeaddrinfo(host_info);
      return -1;
    }

    memcpy(sin, host_info->ai_addr, sizeof(sockaddr_in));
    sin->sin_port = htons(port);

    freeaddrinfo(host_info);
  }
  return 0;
}

```

I forgot about this...
```

  /**
   * @struct PseudoHeader
   * @ingroup socketpp
   * @brief Pseudo Header used when computing UDP/TCP header checksums.
   */
  struct PseudoHeader
  {
    unsigned int   s_addr;
    unsigned int   d_addr;
    char           reserved;
    unsigned char  protocol;
    unsigned short length;
  };

```

---


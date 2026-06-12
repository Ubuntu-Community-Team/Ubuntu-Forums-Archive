---
title: "[python] decoding raw TCP packets"
date: 2009-11-06
forum: Programming Talk
---

### Post by pokerbirch on 2009-11-06
I have previously used libpcap/pcapy for packet sniffing but am currently investigating using raw sockets instead so that i don't have to depend on pcapy. Currently using the following code to sniff incoming TCP packets:

```

#!/usr/bin/python

from select import select
import socket
from impacket import ImpactDecoder

class Sniffer(object):
    def __init__(self):
        proto = socket.getprotobyname('tcp')
        sock = socket.socket(socket.AF_INET, socket.SOCK_RAW, proto)
        sock.setsockopt(socket.IPPROTO_IP, socket.IP_HDRINCL, 1)
        self.sockets = [sock]
        self.decoder = ImpactDecoder.IPDecoder()
        self.start()

    def start(self):
        """start the main loop"""
        while len(self.sockets) > 0:
            recv = select(self.sockets, [], [], 30)[0] # 30 sec timeout
            if len(recv) > 0:
                sck = recv[0]
                packet = sck.recvfrom(4096)[0]
                if len(packet) == 0:
                    # socket closed remotely
                    self.sockets.remove(sck)
                    sck.close()
                else:
                    # packet received - decode
                    packet = self.decoder.decode(packet)
                    print packet

```
This works fine, but i now have a dependency on the impacket library. I'm not very familiar with networking and packet structures - is there any way i can decode these packets with pure python code? If i attempt to print the raw packet before passing it to IPDecoder, it messes up the Terminal. I'm assuming it is binary data or something?

---

### Post by pokerbirch on 2009-11-07
Problem resolved by looking at the source of ImpactDecoder.py and ImpactPacket.py.

---


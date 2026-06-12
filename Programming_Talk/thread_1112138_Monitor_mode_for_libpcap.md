---
title: "Monitor mode for libpcap??"
date: 2009-03-31
forum: Programming Talk
---

### Post by remy06 on 2009-03-31
Hi guys,

I'm required to do some sniffing of packets in wireless "monitor" mode as part of a project.

After some research around and gathering some info here,more or less we will be coding in C/C++ and Qt.I've found out that we can use libpcap for packet capture in linux and it has been used in many popular packet sniffers(seems to be the only source arnd for packet capture).

However,after going through its man page,it seems that it only support capturing in promiscuous mode.From what I understand from the parameter here:
```
pcap_t *pcap_open_live(const char *device, int snaplen,int promisc, int to_ms, char *errbuf)
```

So the question is am I actually able to use libpcap to capture packets in monitor mode?How can it be done?

Thanks in advanced.

---

### Post by remy06 on 2009-04-01
bump

---

### Post by tturrisi on 2009-04-02
Yes, you can capture while in monitor mode.
I suggest looking at the Wireshark documentation, which implements the use of libpcap.  Or see the Kismet documentation.

---


---
title: "Pcap and Libpcap Installation Trouble"
date: 2013-01-25
forum: New to Ubuntu
---

### Post by dansofe0r on 2013-01-25
Hello everyone! I'm new and beginning to learn network protocol concepts. 
I am trying to compile a program written in C that has a pcap.h include. When I try to compile it I get the following message: 

fatal error: pcap.h: No such file or directory
compilation terminated.

I have installed libpcap0.8 using the Ubuntu Software Center, but that hasn't worked. I also tried to download a tar.gz file from the libpcap website, but cannot copy it into the usr/include folder (if it even belongs in there, lol.) 

So what I would like is to know a simple to understand method of using pcap.h so that my program will compile correctly. Thank you!

---

### Post by jorok_tupur on 2013-01-26
> **dansofe0r said:**
> fatal error: pcap.h: No such file or directory
compilation terminated.

I have installed libpcap0.8 using the Ubuntu Software Center, but that hasn't worked. I also tried to download a tar.gz file from the libpcap website, but cannot copy it into the usr/include folder (if it even belongs in there, lol.)

You need to install the development library and header files for libpcap0.8.

Type this in terminal:
```
sudo apt-get install libpcap0.8-dev
```

---

### Post by dansofe0r on 2013-01-26
Thank you very much! Problem resolved. :)

---


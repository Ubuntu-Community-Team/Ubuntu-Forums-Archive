---
title: "capture communication from ethernet card, in hexa form"
date: 2011-07-26
forum: Programming Talk
---

### Post by mathio on 2011-07-26
Hello,

I have a problem with capturing communication from my ethernet network card. I need to get packets in hexa form to be able to work with these packets(frames)- analyse them.. and send some of these packets to server...
I'm trying to use tshark- command version of wireshark to capture communication. The problem is, that as I'm dumping communication with an linux command 

sudo tshark -x | awk '{print $2 $3 $4 $5 $6 $7 $8 $9 $10 $11 $12 $13 $14 $15 $16 $17}' | egrep 'http|ARP|Data|html|TCP|UDP|DNS|TTL' -v

I get an output- only hexa frame. But the part of command awk takes from 2nd to 17th row from standard output and in the last line of packet there are some characters that doesn't belong to that packet.
Is there any possibility to get these packets in hexa form in proper form? (without writing redundant characters in the last line of packet)
Or any other way to capture packets from ethernet card? I found one C program based on libpcap library, but I had an problem with this library- eighter I found bad source code or the library that I found wasn't correct. Or if you'd know about any C linux program, to capture communication, it'd be very helpful for me. 

Thanks for any help

---


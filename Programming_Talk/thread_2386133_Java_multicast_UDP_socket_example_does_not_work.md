---
title: "Java: multicast UDP socket example does not work"
date: 2018-03-01
forum: Programming Talk
---

### Post by erotavlas on 2018-03-01
Hi,
I'm learning how to use multicast UDP in Java language. I just studied the examples [here]("https://docs.oracle.com/javase/tutorial/networking/datagrams/broadcasting.html"). However, after that I downloaded the codes and executed them, they work only if I run the multicast client and the multicast server in the same PC.
Hence, I tried to run multiple instance of the client and one instance of the server into a LAN network it did not work. Finally, I deeply studied the code and take a look on the web and I found that it is correct.
My client is on GNU/linux ubuntu mate 16.04 LTS 64 bit while I tried to run other clients with same and different OS (also Windows).
I think that is not something related to OS configuration (on GNU/linux via ifconfig I saw multicast enabled), but it should be a problem of my local network. I configured the router in order to allow IGMP proxy and IGMP spoofing and I also disabled the firewall.
Then I used wireshark in order to capture the IGMP and UDP packages. I could see the client in my PC that send IGMP request to join the multicast group (address) and UDP data to the group while I could not receive any package.
What can I do?
My final goal is to test the code across Internet instead on my local LAN. Could an ISP block my multicast traffic?
Thank you

P.S.
I'm using reserved multicast IP [https://www.iana.org/assignments/multicast-addresses/multicast-addresses.xhtml#multicast-addresses-9](https://www.iana.org/assignments/multicast-addresses/multicast-addresses.xhtml#multicast-addresses-9)
netstat -gn show that my network interface has joined the multicast group

---


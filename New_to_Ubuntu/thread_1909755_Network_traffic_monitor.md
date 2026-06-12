---
title: "Network traffic monitor"
date: 2012-01-15
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-01-15
Greetings beings of the Linux universe

I come from a distant world seeking your assistance. I am looking for a way to monitor my network traffic.

Attached is a crazy picture I drew which accurately represents my home network. Don't ask why it has to be this way... it just does.

I don't suppose anyone knows a way of monitoring the network traffic eh? From my "Linux Box" in the top right. Maybe something that could show the traffic passing through each switch?

Thank you so nice planet Ubuntu.

(P.S. We're all running ubuntu 11.10, except the PC which is Windows 7 ofc.)

(P.P.S. Do you like my pretty drawing? I think it's awesome)

---

### Post by Dangertux on 2012-01-15
> **Drowz0r said:**
> Greetings beings of the Linux universe

I come from a distant world seeking your assistance. I am looking for a way to monitor my network traffic.

Attached is a crazy picture I drew which accurately represents my home network. Don't ask why it has to be this way... it just does.

I don't suppose anyone knows a way of monitoring the network traffic eh? From my "Linux Box" in the top right. Maybe something that could show the traffic passing through each switch?

Thank you so nice planet Ubuntu.

(P.S. We're all running ubuntu 11.10, except the PC which is Windows 7 ofc.)

(P.P.S. Do you like my pretty drawing? I think it's awesome)

Hi...Umm... What's with the beings talk? lol 

Anyways welcome and I think the best way to monitor all network traffic both ingress and egress would be on the switch nearest your internet connection via a span port and something like tshark, wireshark or tcpdump. That would do the trick.

Hope this helps, live long and prosper :-)

---

### Post by Drowz0r on 2012-01-15
> **Dangertux said:**
> Hi...Umm... What's with the beings talk? lol 

Anyways welcome and I think the best way to monitor all network traffic both ingress and egress would be on the switch nearest your internet connection via a span port and something like tshark, wireshark or tcpdump. That would do the trick.

Hope this helps, live long and prosper :-)

Hey buddy.

Would I be able to monitor what is going where from that location? For instance what is going to which machine? Essentially I want to see where the heavy use on the network is residing... through the magic of technology.

---

### Post by Dangertux on 2012-01-15
> **Drowz0r said:**
> Hey buddy.

Would I be able to monitor what is going where from that location? For instance what is going to which machine? Essentially I want to see where the heavy use on the network is residing... through the magic of technology.

If it's just switching that is occuring and not NAT'ing on those far switches then yes you should be able to. If there is some type of NAT'ing going on you would need multiple monitors at each "switch"

If that makes sense.

---


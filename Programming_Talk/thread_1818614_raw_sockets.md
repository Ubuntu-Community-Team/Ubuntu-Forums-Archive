---
title: "raw sockets"
date: 2011-08-05
forum: Programming Talk
---

### Post by chuchi on 2011-08-05
Hi friends!!! I am studying computer science and I have to develop a sniffer for one of my subjects, using the Linux sockets. This sniffer has to capture all the packets in the network from/to other hosts. Can you give me any reference please??

thank you very much!!!!

---

### Post by schauerlich on 2011-08-05
> **chuchi said:**
> Hi friends!!! I am studying computer science and I have to develop a sniffer for one of my subjects, using the Linux sockets. This sniffer has to capture all the packets in the network from/to other hosts. Can you give me any reference please??

thank you very much!!!!

[http://www.google.com/search?client=safari&rls=en&q=c+socket+programming+tutorial&ie=UTF-8&oe=UTF-8](http://www.google.com/search?client=safari&rls=en&q=c+socket+programming+tutorial&ie=UTF-8&oe=UTF-8)

I could link you to the individual results, but... meh.

---

### Post by chuchi on 2011-08-05
Hi thanks!! Sorry, I forgot to say that I manage to program sockets, but only to capture data, in the transport layer. But I find it difficult to develop a program to sniff all the packets in the network. 

I found this example in the web: [http://security-freak.net/raw-sockets/sniffer_eth_ip_tcp_data.c](http://security-freak.net/raw-sockets/sniffer_eth_ip_tcp_data.c)

But it doesn't capture all the packets, it only captures the packets from/to my computer.

thank you very much!!!!

---

### Post by chuchi on 2011-08-05
What about this? If I use ETH_P_ALL instead of ETH_P_IP, I can sniff all the packets, but i get "segmentation fault"!!!! why?

---

### Post by cgroza on 2011-08-05
> **chuchi said:**
> What about this? If I use ETH_P_ALL instead of ETH_P_IP, I can sniff all the packets, but i get "segmentation fault"!!!! why?
Try compiling your code with the -g flag and run gdb on that executable. See what gdb tells you. (assuming you are using C or C++)

---

### Post by Wim Sturkenboom on 2011-08-05
> **chuchi said:**
> What about this? If I use ETH_P_ALL instead of ETH_P_IP, I can sniff all the packets, but i get "segmentation fault"!!!! why?
Without seeing the code that is impossible to say (and no, I don't want to see it). One thing might be memory allocation where you don't check if it's actually allocated.

As said by cgroza, use gdb to debug.

---

### Post by chuchi on 2011-08-07
I'm not very sure, but I think the seg fault raises when I try to print a packet which is not an IP packet, i.e, when type ID is not ETH_P_IP.....

Because if I change the protocol to ETH_P_ALL, then I get all the packets, but when ETH_P_IP, i only get packets from/to my computer, but I there is no seg fault.

What is the difference between ETH_P_ALL and ETH_P_IP?? Why can't I capture all the packets with ETH_P_IP, in spite of put my card network to promiscuous mode (ifconfig wlan0 promisc)

Thank you very much!!

---

### Post by chuchi on 2011-08-09
I solved the problem. but now i have to deal with this: I capture the  entire packet, but I want to capture the data in the tcp packet. This  code shows the data packet, but with a few bytes before the data. For  example, a client sends a tcp packet with this data "hello server", and  in this picture I show you the output.

This sentence must be changed:

```


data = (packet + sizeof(struct ethhdr) + ip_header->ihl*4 +sizeof(struct tcphdr));


```

But how can i do it? 

thank you very much!!!

---

### Post by dwhitney67 on 2011-08-09
> **chuchi said:**
> 
But how can i do it? 


I wouldn't assume that all of the characters you want to print are "printable".

Maybe something like this could be of help:
```

  for (size_t i = 0; i < msgSize; ++i)
  {
    printf("%c ", (isprint(msg[i]) ? (char)msg[i] : '*'));
  }

```

---


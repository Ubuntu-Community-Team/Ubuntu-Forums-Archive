---
title: "unable to sniff TCP packets"
date: 2014-10-07
forum: Programming Talk
---

### Post by IAMTubby on 2014-10-07
Hello,
 I wrote a simple client-server program using TCP sockets, where the client sends a message to the server and the server responds with the current date. 
However, I would like to see my packets being sent using a command line tool. I was expecting that when I run the client, I would be able to see the packets on running a tool like tcpdump; but that's not happening.

Please advise me on how I can get to see the packets.

Thanks

---

### Post by tgalati4 on 2014-10-08
*tcpdump* requires sudo privileges and a network card that allows permissive packet sniffing.  Not all cards allow that.  What is your network card?

---

### Post by IAMTubby on 2014-10-08
> **tgalati4 said:**
> *tcpdump* requires sudo privileges and a network card that allows permissive packet sniffing.  Not all cards allow that.  What is your network card?
Hi,
 I just ran these two commands. Are these helpful?

```

IAMTubby@IAMTubby-Inspiron-3542:~$ lspci | awk '/net/ {print $1}' | xargs -i% lspci -ks %
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)
	Subsystem: Dell Device 0651
	Kernel driver in use: r8169
	Kernel modules: r8169

```

```

IAMTubby@IAMTubby-Inspiron-3542:~$ lspci | grep -i net
06:00.0 Network controller: Qualcomm Atheros QCA9565 / AR9565 Wireless Network Adapter (rev 01)
07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 07)

```

---

### Post by tgalati4 on 2014-10-09
Do you get any traffic?

> 
gates@GNAS ~ $ sudo tcpdump -n -i eth0
08:45:10.534462 ARP, Request who-has 10.10.1.38 tell 10.10.20.130, length 46
08:45:10.536231 ARP, Request who-has 10.10.6.4 tell 10.10.5.86, length 46
08:45:10.575137 ARP, Request who-has 10.10.4.152 tell 10.10.1.22, length 46
08:45:10.575166 IP 10.10.5.123.17500 > 255.255.255.255.17500: UDP, length 103
08:45:10.576264 IP 10.10.5.123.17500 > 10.10.255.255.17500: UDP, length 103
08:45:10.582251 ARP, Request who-has 10.10.4.155 tell 10.10.1.14, length 46
08:45:10.585976 ARP, Request who-has 10.10.4.30 tell 10.10.1.32, length 92
^C
386 packets captured
465 packets received by filter
0 packets dropped by kernel


You see some entries in dmesg for entering "promiscuous" mode.

> gates@GNAS /var/log $ dmesg | tail
[682721.745167] [drm] Setting output timings on SDVOB failed
[714235.340663] [drm] Setting output timings on SDVOB failed
[719751.862383] [drm] Setting output timings on SDVOB failed
[726044.024185] [drm] Setting output timings on SDVOB failed
[761865.065856] [drm] Setting output timings on SDVOB failed
[763867.151471] [drm] Setting output timings on SDVOB failed
[792888.558980] [drm] Setting output timings on SDVOB failed
[799950.697016] [drm] Setting output timings on SDVOB failed
[849239.740395] device eth0 entered promiscuous mode
[849244.511450] device eth0 left promiscuous mode


You will need to research the differences between the driver that you are using *r8168* and the actual card that you have RTL8101.  I don't have that hardware, so I can't comment on the compatibility with promiscuous mode.

You do get points for using *awk* and *xargs* in the same script.

---

### Post by IAMTubby on 2014-10-09
> **tgalati4 said:**
> Do you get any traffic?
No I did not, it just keeps waiting for something to happen when I run the command sudo tcpdump -n -i eth0

tgalati4, Please find attached my server and client files. Are you saying that running these programs are supposed to give some traffic on running tcpdump?

---

### Post by tgalati4 on 2014-10-09
Yes, you should get a continuous stream of packets until you hit Control-C.  My guess is that your network card does not support "promiscuous" mode.  This assumes that your computer is attached to a switch that has some traffic on it.  If you have no other machines or are running direct-connect, then you might not get any traffic.  But that is not likely.

Do some research on the *r8169* module and the RTL8101E network card.

---

### Post by fugu2 on 2014-10-11
in your echoc program, you never specify the ip addr of the server, so it doen't know where to send the packets```
server_addr.sin_addr.s_addr = inet_addr("10.11.12.13");
```if your sending them over the loopback adaptor, then you'll need have tcpdump look at the "-i lo" initerface. INADDR_ANY is not very specific and you'd do better to use somthing different for testing purposes at least.

---

### Post by IAMTubby on 2014-10-11
> **tgalati4 said:**
> Yes, you should get a continuous stream of packets until you hit Control-C.  My guess is that your network card does not support "promiscuous" mode.  This assumes that your computer is attached to a switch that has some traffic on it.  If you have no other machines or are running direct-connect, then you might not get any traffic.  But that is not likely.

Do some research on the *r8169* module and the RTL8101E network card.
tgalati4, thanks for that.
I was however looking at the wrong interface. My ifconfig says that I should be looking at wlan0, I was however looking at eth0(which is default for tcpdump if no interface is mentioned) . Once I key in the command, sudo tcpdump -i wlan0, I do get to see the stream of packets. Maybe I should've gone in with a command like sudo tcpdump -i any, which would look at any(all of) the interfaces.

> **fugu2 said:**
> if your sending them over the loopback adaptor, then you'll need have tcpdump look at the "-i lo" initerface.
fugu2, thank you for touching on **-i lo**. I noticed that when I'm transferring packets through UDP, I have to look at -lo interface(sudo tcpdump -i lo udp). Actually I just did -i any and then got to know that it's coming from -lo. I'm surprised because ifconfig shows me my ip address for wlan0. Please can you tell me why we're looking at -lo?

EDIT : Okay, I went back and read a bit about -lo(actually, your reply is pretty clear, but anyways!). I understand that -lo is loopback adaptor, basically when you're running client and server on the same machine. Thanks once again.
So I'm basically going to use -lo if in the same machine and eth0/eth1/wlan0 if on different machines. Actually, I'll just take the easy route and use s**udo tcpdump -i any (udp)** always :) 

Thanks tgalati4, fugu2. Marking the thread as solved.

---


---
title: "PPPoE connection between 2 computers"
date: 2012-02-13
forum: New to Ubuntu
---

### Post by snare91 on 2012-02-13
I am relatively new to Linux. I have a desktop, a laptop and a serial cable (the one with 9 pins). I've been asked to set up a PPPoE connection between the 2 computers - I need to implement a server-client chat program to send data packets or files.
 How should I go about handling this problem? Any help will be greatly appreciated!

---

### Post by sadaruwan12 on 2012-02-13
Well I don't know about a PPPOE connetion but to set up data transmission between two computers you need to get LAN cable which has been crimped using the cross method these cables are known as cross over cables.

[Refference]("http://en.wikipedia.org/wiki/Ethernet_crossover_cable")

Once you get a cross over cable you can connect the two computers through there LAN or network ports and configure them to in the same IP range.

Ex: PC 1 192.168.1.3 then PC 2 192.168.1.4

like that and see if data is transmitted throght the cable to the othe PC.

This is the normal mathod we use to create a small 2 way network between 2 pc's.

---

### Post by lkraemer on 2012-02-13
If you don't want to use a Crossover Cable, you can just use two Ethernet Patch Cables and an Ethernet Hub.
You local Goodwill Store or Re-sale shops should have a used Ethernet Hub for low cost.

Crossover Cable wiring is as Shown in the JPG.

lk

---

### Post by varunendra on 2012-02-14
> **snare91 said:**
> I have a desktop, a laptop and a serial cable (the one with 9 pins). I've been asked to set up a PPPoE connection between the 2 computers - I need to implement a server-client chat program to send data packets or files.
Do you mean PPP over serial ports?

I don't know how you can establish a PPPoE over a serial interface, since the protocol is meant to be implemented over an 'Ethernet' interface, hence the name - **P**oint-to-**P**oint **P**rotocol _**o**ver **E**thernet_. But as far as a simple and 'direct' communication is concerned, I hope these may be helpful:
[http://linux.koolsolutions.com/2008/04/10/how-to-test-serial-ports-under-debian-linux/](http://linux.koolsolutions.com/2008/04/10/how-to-test-serial-ports-under-debian-linux/)
[http://help.lockergnome.com/linux/Text-PCs-serial-connection--ftopict487870.html](http://help.lockergnome.com/linux/Text-PCs-serial-connection--ftopict487870.html)

Is it some sort of a test or project assigned to you? Please tell us the things that are necessary (non-optional) to involve, and hopefully we could suggest the best way to achieve the goal.

Some interesting reads:
[http://ppp.samba.org/README.html](http://ppp.samba.org/README.html)
[http://tldp.org/HOWTO/PPP-HOWTO/](http://tldp.org/HOWTO/PPP-HOWTO/)
[http://tldp.org/HOWTO/Serial-HOWTO.html](http://tldp.org/HOWTO/Serial-HOWTO.html)

---

### Post by snare91 on 2012-02-19
Well, yes it is a part of a bigger project - this is just something which i wanted to for checking the feasibility of what we actually want to do. 

I'll try to rephrase myself better (sorry, I didn't make much sense in my first post). 
Overall, I have to implement PPPoE and TCP/IP on a hardware platform. The idea behind doing so is that the hardware platform will receive data from a device via PPP/PPPoE and then send the data to the server using an internet connection - thats where TCP/IP comes in. 

I've been working on programming sockets and I've been able to make them work properly. I tested them on the LAN and they work seamlessly. 
What I don't understand is that (wrt the OSI model) - my client-server chat program runs on the Application layer. The presentation/session aren't really relevant here. The transport layer is TCP since my sockets are sending streams and not packets. And then since all network addresses are in IPv4 format, the Network layer protocol is IP. The desktops that are connected are using a crossover serial cable (basically the physical layer is replaced by a serial cable instead of an ethernet cable). Then how can I make sure that the data that is being sent is being sent using PPP? I couldn't think of any way to control the Datalink layer protocol. 

Any help will be greatly appreciated.

---

### Post by varunendra on 2012-02-20
> **snare91 said:**
> I've been working on programming sockets and I've been able to make them work properly. I tested them on the LAN and they work seamlessly. 
What I don't understand is that (wrt the OSI model) - my client-server chat program runs on the Application layer. The presentation/session aren't really relevant here. The transport layer is TCP since my sockets are sending streams and not packets. And then since all network addresses are in IPv4 format, the Network layer protocol is IP. The desktops that are connected are using a crossover serial cable (basically the physical layer is replaced by a serial cable instead of an ethernet cable). Then how can I make sure that the data that is being sent is being sent using PPP? I couldn't think of any way to control the Datalink layer protocol.

I have just started studying these things (the OSI model), and and am far-far away from socket programming yet. So most of above is much above my level. Sorry.

I hope for some expert to step in and answer your post. I am interested too.

---

### Post by snare91 on 2012-02-20
Okay, as an alternative approach. You know, those dialiers, from which we can connect to our ISP using PPP? I don't use such a connection, can't we use those dialers in such a way that it establishes a PPP connection, but instead of contacting the ISP's server, it connects to another machine on a LAN? And will that machine have to run a separate server software to allow the connection, or can it be as simple as setting a data communication channel between them?

---


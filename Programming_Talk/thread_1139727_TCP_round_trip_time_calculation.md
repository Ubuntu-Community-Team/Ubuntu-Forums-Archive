---
title: "TCP round trip time calculation"
date: 2009-04-27
forum: Programming Talk
---

### Post by doorman on 2009-04-27
This is a "language-neutral" question, as I'm currently stuck with the concept...

Given two computers, I have to calculate the round trip time, which, in itself, is not a big deal. My problem is the following: apart from the rtt, I also have to calculate (or, better, find out) the time it took the packet to transfer from one computer to the other (i.e. I have to calculate only one side of the trip, not including the return trip time). This seems pretty easy, although it's not as it seems: the computer A could send the start trip time along with the packet, and comp B could calculate the difference between the time received and the time sent... Well, my question is: how can I sync the two computers' time clocks?

The obvious answer is to sync both of them with a time server on the net prior to start communication. But what if the computers sit in a closed network without a time server available?

---

### Post by Arndt on 2009-04-27
> **doorman said:**
> This is a "language-neutral" question, as I'm currently stuck with the concept...

Given two computers, I have to calculate the round trip time, which, in itself, is not a big deal. My problem is the following: apart from the rtt, I also have to calculate (or, better, find out) the time it took the packet to transfer from one computer to the other (i.e. I have to calculate only one side of the trip, not including the return trip time). This seems pretty easy, although it's not as it seems: the computer A could send the start trip time along with the packet, and comp B could calculate the difference between the time received and the time sent... Well, my question is: how can I sync the two computers' time clocks?

The obvious answer is to sync both of them with a time server on the net prior to start communication. But what if the computers sit in a closed network without a time server available?

You can install a time server yourself, on the local net. It's not crucial that the time is the true wall clock time, I suppose, as long as time differences are reliable.

---

### Post by doorman on 2009-04-27
> **Arndt said:**
> You can install a time server yourself, on the local net. It's not crucial that the time is the true wall clock time, I suppose, as long as time differences are reliable.

Well, I can't :( The program I must write can only be run twice - one instance per computer. I am no allowed to run any other software on any other machine on the LAN.

Bearing this in mind, I thought maybe it is plausible the computer A to simulate a time server, but that's not going to work as explained below:

At a time ***t0*** ( where *t0* denoted the beginning of the process, suppose *t0 = 0* ), A sends the current time to B. B receives the time with a delay of ***dT1*** ms ( suppose *dT1 = 5* ). At a time ***t1*** ( where *t1 > t0 + dT*, suppose *t1 = 15* ), A sends a packet to B in which the value of *t1* is incorporated. B receives it ***dT2*** ms after A sent it ( suppose *dT2 = 10* ). Now, from A's point of view the current time is *t_A_now = t1 + dT2 = 15 + 10 = 25*, while from B's point of view the current time is *t_B_now = t1 - dT1 + dT2 = 15 - 5 +10 = 20*

Because of the time shift, I still won't be able to calculate the one-way trip time, as, obviously, there is a time difference between the two clocks :(

If this seems too confused, well, it is. Please, feel free to ask for clarification if one is needed.

---

### Post by dwhitney67 on 2009-04-27
If you have access to both systems, and you know that their clocks are in sync, then a raw IP message can be sent from A to B with the data containing the current time of system A.  System B can compute the time delta of when it received the message against the time contained within the message.

Similarly, B can reply to A with its current time, and then A can perform the time-delta calculation.

If the clocks are not in sync, then you get them in sync by placing a server on B that sets the system time with the time data sent from A.  Subsequent messages from A can then be used to compute the time-delta.

---

### Post by doorman on 2009-04-27
> **dwhitney67 said:**
> If the clocks are not in sync, then you get them in sync by placing a server on B that sets the system time with the time data sent from A.  Subsequent messages from A can then be used to compute the time-delta.

As I said in my previous post, I can't bring up a time server on neither machines. And, as I tried to explain, if I set one machine's time based on the other's time, I still would have a time gap between the two machines (because of the time needed to transfer a packet from A to B) and wouldn't know how to calculate that difference (i.e., if A sends the time to B, B can't know when A actually sent it, just as A can't know when B actually received it)

---

### Post by The Cog on 2009-04-27
I don't think it is possible.

I once heard of a company that was selling in-line boxes for measuring the one-way latency of packets. Because packet latencies are in the millisecond or microsecond range, you need really good clock sync. These boxes used inbuilt receivers to get the time from GPS satellites, and added timestamps to passing packets. Very expensive. And, in my opinion, pointless. It is the RTT that affects application delay. If the one-way latency was so significant, it wouldn't be so hard to measure.

---


---
title: "Need help with 'netstat' command"
date: 2013-05-31
forum: New to Ubuntu
---

### Post by siddharth007 on 2013-05-31
Hi everyone.I just did this ```
netstat -s
```

The netstat threw up these statistics on my terminal
```
Ip:
    90508 total packets received
    0 forwarded
    0 incoming packets discarded
    90508 incoming packets delivered
    76534 requests sent out
Icmp:
    36 ICMP messages received
    0 input ICMP message failed.
    ICMP input histogram:
        destination unreachable: 36
    36 ICMP messages sent
    0 ICMP messages failed
    ICMP output histogram:
        destination unreachable: 36
IcmpMsg:
        InType3: 36
        OutType3: 36
Tcp:
    **2060 active connections openings**
    **170 passive connection openings**
    136 failed connection attempts
    70 connection resets received
    4 connections established
    67485 segments received
    57701 segments send out
    579 segments retransmited
    0 bad segments received.
    2209 resets sent
Udp:
    23830 packets received
    36 packets to unknown port received.
    0 packet receive errors
    18324 packets sent
UdpLite:
TcpExt:
    799 TCP sockets finished time wait in fast timer
    9 packets rejects in established connections because of timestamp
    2016 delayed acks sent
    Quick ack mode was activated 493 times
    274 packets directly queued to recvmsg prequeue.
    103275 bytes directly received in process context from prequeue
    42205 packet headers predicted
    74 packets header predicted and directly queued to user
    4013 acknowledgments not containing data payload received
    6280 predicted acknowledgments
    10 times recovered from packet loss by selective acknowledgements
    200 congestion windows recovered without slow start after partial ack
    82 timeouts after SACK recovery
    1 timeouts in loss state
    12 fast retransmits
    2 retransmits in slow start
    426 other TCP timeouts
    498 DSACKs sent for old packets
    18 DSACKs sent for out of order packets
    76 DSACKs received
    627 connections reset due to unexpected data
    16 connections reset due to early user close
    4 connections aborted due to timeout
    TCPDSACKIgnoredNoUndo: 5
    TCPSackShifted: 1
    TCPSackMerged: 3
    TCPSackShiftFallback: 173
IpExt:
    InMcastPkts: 51
    OutMcastPkts: 31
    InBcastPkts: 4737
    OutBcastPkts: 65
    InOctets: 67623752
    OutOctets: 10400185
    InMcastOctets: 8495
    OutMcastOctets: 4751
    InBcastOctets: 518246
    OutBcastOctets: 7747


``` 

In the output i saw something like active and passive connections openings (marked with bold). These numbers seem to be very high.Please help me understand what these numbers mean.Is my system vulnerable or is it already compromised?? I am really worried.

---

### Post by prodigy_ on 2013-05-31
> **siddharth007 said:**
> These numbers seem to be very high.
Not really.

> **siddharth007 said:**
> Is my system vulnerable or is it already compromised?? I am really worried.
/sigh Computers are about 1000 times better protected than 30 years ago, yet users are about 1000 times more worried. :)

---

If your system is acting abnormally, you could check it with [RKhunter](https://help.ubuntu.com/community/RKhunter). Otherwise you should be fine.

---


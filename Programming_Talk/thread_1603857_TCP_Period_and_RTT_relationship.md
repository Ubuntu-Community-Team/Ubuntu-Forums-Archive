---
title: "TCP Period and RTT relationship"
date: 2010-10-23
forum: Programming Talk
---

### Post by statty on 2010-10-23
This is a programming neutral question as I want to grasp the concept of it first. I was just wondering if anyone might know the following: 
Can anyone define a relationship between the period of a TCP sawtooth waveform and RTT? Is there an equation representing this? 
Thanks.

---

### Post by Zugzwang on 2010-10-23
Dear OP, please explain what these abbreviations mean. I only know "TCP" as "Transmission Control Protocol" and RTT as "Round trip time", but then I have no clue what a TCP sawtooth waveform should be. TCP is high up in the network stack hierarchy, so it doesn't have to do with physical layer stuff such as waveforms of the network line voltages or the like. Or why should the round-trip time (which is a low-level layer thing) have anything to do with TCP?

---

### Post by statty on 2010-10-23
TCP increases and decreases its window size creating a sawtooth affect when transmitting data. The period of time of the waveform is the time it takes the window size to reach its maximum size.

---


---
title: "Problems with SCTP and Multi-streaming"
date: 2007-09-07
forum: Programming Talk
---

### Post by MietitoreDAnime on 2007-09-07
Hi 
we are two students of university of Naples Federico II; we are working on an Traffic generator (D-ITG), and we are implementing the support for SCTP multi-streaming for this software. We are using the Linux Distribution UBUNTU 7.04 with the Kernel version 2.6.20-16 and the lksctp libraries version 1.0.6-2. We have some problem when we try to generate three streams on the same association with variable packet size (in particular with exponential distribution for packet size). In particular during the transmission the sender get blocked on the sctp_sendmsg(), but with constant packet size there is no problem, even with high values of packet size. Is there any problem in lksctp libraries with ubuntu and this configuration? 
 
thanks for help 
sorry for our bad english 
Diana Luigi 
Ercoli

---


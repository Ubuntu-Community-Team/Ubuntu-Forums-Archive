---
title: "Multiplexing 2 Streams to Tx over Wireless &amp; Demulteplexing on Rx to Individual O/P"
date: 2011-01-24
forum: Programming Talk
---

### Post by jskandhari on 2011-01-24
I am a newbie to Linux Programming Need to Know HOW to Go about the Linux Programming of DATA FUSION

Need to Multiplex ( Mux ) two Data Streams broadcast over Wireless and then Demultiplex (DeMux )on the Receiving side and give output on Individual O/p Screens.
: DETAILS ::

My main PROJECT is,
1) First Stream :: GPS Stream
2) Video Stream :: Conversion of Analog Signal to Digital ( Using Compression Divx :: Not an issue )

Tx : Merging the Two Streams ( Mux ) and then Transmitting over Wireless as a Single Stream.
Rx : DeMux the Stream and Display GPS Data on Different O/P Screen and Video Stream on Different O/P Screen.

Thanks ...
#Will Look into the Programming Sections Also thanks

::Boundaries::
For now A Terminal on Both Ends can perform the Function with a OS in the Later Stages it will be embedded.

Newibie Kindly Help So that I can Help Others

---

### Post by Tony Flury on 2011-01-25
Assuming by wireless you mean a  wifi connection - then you would open a socket to the destination and send your data down that socket. For your problem I would actually open two sockets to the same end point (server) but use two different ports - and have the reciever end listen to both ports - thus saving your application the hassle of having to multiplex and de-mutiplex the data.

If by Wireless you mean some form of generic radio device (i.e. not network wifi connection) then you will need device drivers on both transmitter and receiever to allow you to read and write from your radio device. Also if your driver does not present itself as a network type service (which it might not), you will have to think about how to establish connections, do flow control, acknowledgement, error detection/correction/recovery etc.

If you are new to programming and communications - i hope yours is a wifi connection.

---


---
title: "what's a union i c/c++, when to use"
date: 2009-01-11
forum: Programming Talk
---

### Post by monkeyking on 2009-01-11
by wiki
```
In computer science, a union is a data structure 
that stores one of several types of data at a single location. 
```

I've never used these.
But I'm now working on a project that use unions extensively, not written by me.


But I don't really see why they should be used,
Has anyone ever found these usefull?

---

### Post by skirkpatrick on 2009-01-11
I especially use unions when writing device drivers or communication protocols.  Here's a good example:

Say I want to talk to a device over a serial port.  The protocol utilizes a packet structure and supports several types of messages.  The piece of my code that handles the low-level portion of the communication shouldn't have to know about the higher-level data structures.  For instance, it just wants to receive a byte of data and store it.  The packet verification section of code doesn't need or want to know about the various message types.  Now you can either cast pointers to an address to various data structures or you can encapsulate it into one data structure as such:
```

struct MSG_1
{
   int          x;
   float        y;
};

struct MSG_2
{
   char         ErrorMsg[20+1];
};

struct PACKET
{
   int          Length;
   int          MsgType;
   union
   {
      struct MSG_1      Msg1;
      struct MSG_2      Msg2;
   } Payload;
};

union BUFFER
{
   char            RawData[1];
   struct PACKET   Packet;
};

BUFFER          RcvBuffer;

```

The size of a union is the size of the largest element in it.  Therefore, even though RcvBuffer.RawData is defined as only 1 byte long, RcvBuffer itself is as big as a PACKET.  I can store received bytes via RcvBuffer.RawData[index] even if index has a value larger than one.  I can also access the final data using RcvBuffer.Packet.Payload.Msg1.

To put it simply, unions are used when a section of memory can be interpreted in several different ways depending on the context.

---


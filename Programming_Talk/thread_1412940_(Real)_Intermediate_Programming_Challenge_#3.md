---
title: "(Real) Intermediate Programming Challenge #3"
date: 2010-02-21
forum: Programming Talk
---

### Post by dwhitney67 on 2010-02-21
I'm not good at providing challenges, but the previous ones I've seen have been centric about numerical stuff (or making change into dollars!), so I thought that a real world application would be in order... well, at least real to me.

The task is real simple...

You are going to provide the data from an Unmanned Aerial Vehicle (UAV) so that it can be displayed on Coronel Klink's video screen.

Using the KLV (Key-Length-Value) format, develop an application, that sends via a UDP socket, the following information:

1.  Checksum (key =1) (length = 16 bits)
2.  Direction of Heading, in degrees (Key = 1) (length = 16 bits)
3.  Pitch (key = 2) (length = 16 bits)
4.  Roll (key = 3) (length = 16 bits)
5.  True Airspeed (key = 4) (length = 8 bits)
6.  Indicated Airspeed (key = 5) (length = 8 bits)

The values for items 2-6 are not important; just think of them as numbers, given the size specified.  For item 1, the checksum is the 16-bit sum the bytes of the values of items 2-6.

Once the data has been assembled, format it into Network Byte Order (Big Endian) and send all of it via a UDP socket to a remote destination (eg. 192.168.1.10, port 9000).

You can read more about KLV from the [Wiki Pages]("http://en.wikipedia.org/wiki/KLV").

---

### Post by GregBrannon on 2010-02-22
Words that don't belong in this challenge (to me):

Intermediate,
Real world, and
Real simple.

Maybe someday my perspective will change.

---

### Post by Reiger on 2010-02-22
This is intermediate in that:

(a) It is really clearly defined and scoped (no second guessing intentions and expectations: there is a proper yardstick of correct behaviour) There's no 3rd party incompatibility/malformed input/etc. to take into account.


This is simple in that:

(b) It is mostly straightforward if you use 3rd party libs or higher level languages that do most of the hard work for you; and it does not require too much understanding of complex algorithms or similar.


This is real world in that:

(c) It is not atypical: you are basically developing a tool to read/write some more or less propietary (binary) file format.

---

### Post by Queue29 on 2010-02-22
> **GregBrannon said:**
> Words that don't belong in this challenge (to me):

Intermediate,
Real world, and
Real simple.

Maybe someday my perspective will change.

+1

Here's a good intermediate challenge: [http://www.cs.utexas.edu/~scottm/cs307/Assignments/BabyNames.html](http://www.cs.utexas.edu/~scottm/cs307/Assignments/BabyNames.html)

You even end up with something that's relatively fun to play with.

---


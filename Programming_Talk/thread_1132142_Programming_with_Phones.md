---
title: "Programming with Phones"
date: 2009-04-21
forum: Programming Talk
---

### Post by num on 2009-04-21
Hello,

Does anyone know any tutorials or articles in regards to programming with phones? By phones are land line phones in United States. Looking for information of what comes out from a phone line, how do I integrate and pull the information out the line, such as phone number and be able to make calls. Can anyone please help me?

---

### Post by jinksys on 2009-04-29
What platform?  The easiest solution is use a modem and some API to make calls and receive numbers.  The harder solution is to implement the hardware yourself, you can find the necessary info here: [http://www.textfiles.com/phreak/](http://www.textfiles.com/phreak/)

---

### Post by lisati on 2009-04-29
Are we talking about stuff like Caller-ID information here? If so, some of the links at the [Wikipedia article]("http://en.wikipedia.org/wiki/Caller_ID") might be of some interest.

EDIT: Be careful that, legally speaking, you aren't treading on anyone's toes.

---

### Post by UBForty on 2009-05-01
It seems you want to get the Caller ID information from an analog telephone line. Note that Caller ID standards vary from country to country, but the US one is supported by most software.

There is plenty of open source code for that available.

Search for:

- GNU Telephony Server, aka Bayonne
- Callweaver (PBX) and Unicall (its telephony interface library)
- Freeswitch (PBX) and OpenZap (its telephony interface library)

---


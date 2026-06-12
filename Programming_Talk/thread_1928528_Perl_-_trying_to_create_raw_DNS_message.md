---
title: "Perl - trying to create raw DNS message"
date: 2012-02-20
forum: Programming Talk
---

### Post by compiz addict on 2012-02-20
Hello! I'm trying to send a raw DNS message in Perl.
I'm doing this for educational purposes, so don't tell me there's a quicker way to do this; I know there's a quicker way to do this.

This is the portion of my code that sends a DNS message:

```
print $sock pack('s',0xABCD);#Transaction ID
print $sock pack('s',0x0000);#Flags
print $sock pack('s',0x0001);#1 entry in question section
print $sock pack('s',0x0000);#0 entries in answer
print $sock pack('s',0x0000);#0 entries in authority
print $sock pack('s',0x0000);#0 additional
print $sock pack('c',0x09) . "noteforge" .pack('c',0x02) . "ca" . pack('c',0x00);
print $sock pack('s',0xFF);
print $sock pack('s',0x0001);
```

When I send this over to, say, Google's DNS ( 8.8.8.8 ), I don't get a response back. Infact, the socket is closed right away. I'm assuming my DNS message is malformed, and I wouldn't be even slightly surprised if so.

So, what am I missing? Most of the flags I didn't quite understand, so maybe I need to give some of them a value (I just have that entire section zeroed out as you can see).

---

### Post by myrtle1908 on 2012-02-23
Couldn't you look at the source for ```
Net::DNS::Packet
``` to see how it constructs messages?

---

### Post by Tony Flury on 2012-02-24
It is also entirely possible that Google does not accept DNS entires from uknown sites, and it operates a whitelist system.

---


---
title: "Bitwise Operations: Getting Rightmost Octet"
date: 2009-04-01
forum: Programming Talk
---

### Post by Peasantoid on 2009-04-01
How would I go about retrieving the rightmost octet from an arbitrary-length bitstring? For example:
```
01100100 11010110
[some operation]
00000000 11010110
```
I know how to join octets together, just not how to extract them. I've been fooling around with this for a while now but haven't had any success. What bitwise operation (if any) would I use for this purpose?

(I'm using C for this, but any language is welcome so long as the solution is applicable.)

Update: Okay, turns out the C++ STL has this thing called the "bitset". Shoulda done more research. :(

---

### Post by slavik on 2009-04-01
in C:

```

a = 32134243; /* some number */
b = a & 0xFF; /* b will be the least significant byte from a */

```

---

### Post by Peasantoid on 2009-04-02
Hey thanks, your solution is way better! :)

Now that I think about it, it seems totally obvious...

---


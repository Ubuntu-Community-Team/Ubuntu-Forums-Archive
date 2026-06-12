---
title: "C Addressing Q."
date: 2008-02-12
forum: Programming Talk
---

### Post by Jaguar0616 on 2008-02-12
Here's a piece of C code:


```
int n = 1;
printf("n is stored at %u ",&n);
```


Using gcc on a 32 bit machine with 512M of RAM, this prints out 3 billion and something.

So how do you get an address of > 3 billion when there's only ~512 million bytes? Apparently I'm missing something.

Thank you!

---

### Post by CptPicard on 2008-02-12
[http://en.wikipedia.org/wiki/Virtual_memory](http://en.wikipedia.org/wiki/Virtual_memory)

---

### Post by Zwack on 2008-02-12
As CptPicard said...

The address that you see is not the physical memory location.  Think of it like a phone number...  You imagine that a phone number is tied to a particular phone, after all, you dial that number on your phone, and THAT phone rings...

In reality there is a layer between the two that redirects requests.  So you dial a phone number and the exchange looks up where that number really is and then connects to that.  A bit like DNS, you type in a name, DNS looks up the IP address, and you get to the Ubuntu forums...

Except in this case the memory management in the kernel looks up the address that you gave it and then translates that to the real location.

I hope that this helps, clarify,

Z.

---

### Post by Jaguar0616 on 2008-02-12
Thanks Zwack

---


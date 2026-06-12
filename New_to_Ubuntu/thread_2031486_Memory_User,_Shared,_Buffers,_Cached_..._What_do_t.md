---
title: "Memory: User, Shared, Buffers, Cached ... What do they mean?"
date: 2012-07-22
forum: New to Ubuntu
---

### Post by vasa1 on 2012-07-22
I'm using "Indicator Multiload" on Ubuntu 12.04. The Memory tab has the following components:
[LIST]
[*]User
[*]Shared
[*]Buffers
[*]Cached
[*]Free
[/LIST]Can someone please explain those terms, other than Free, or point to some reading on them?

---

### Post by Redblade20XX on 2012-07-23
User: 
How much memory is allocated/used by the current user.

Shared: (Not exactly 100% sure on this one,lol)
How much memory is being shared by multiple users currently logged in on the
computer.

Or how much memory is currently shared between processes.

Buffers:
How much memory is currently used by a program that requires some sort of 
buffer.

Cached:
How much memory is currently allocated to programs that aren't in current usage of the CPU but may likely be called on. 

You probably will want to look up this in an operating system design book, a book on kernels or a process scheduling one.

- Red

---

### Post by philinux on 2012-07-23
> **vasa1 said:**
> I'm using "Indicator Multiload" on Ubuntu 12.04. The Memory tab has the following components:
[LIST]
[*]User
[*]Shared
[*]Buffers
[*]Cached
[*]Free
[/LIST]Can someone please explain those terms, other than Free, or point to some reading on them?

[http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm](http://www.linuxhowtos.org/System/Linux%20Memory%20Management.htm)

---

### Post by vasa1 on 2012-07-23
Thanks, Redblade20XX & philinux!
This bit is good to know: "*The reason Linux uses so much memory for disk cache is because the RAM is wasted if it isn't used. Keeping the cache means that if something needs the same data again, there's a good chance it will still be in the cache in memory. Fetching the information from there is around 1,000 times quicker than getting it from the hard disk*". (from the linuxhowtos link)

---


---
title: "C programming: can't do char [ ] = char *"
date: 2010-10-29
forum: Programming Talk
---

### Post by mongooseman1128 on 2010-10-29
I'm fairly new to C and am pretty confused why a particular line of code isn't working. On compile, I get an "incompatible types in assignment" error. the offending line is
```
packet.req.uri_req.uri = uri;
```

packet.req.uri_req.uri is defined in a header file with 
```
char uri[512];
```
I don't think this changes anything, but packet is a struct, req is an union, uri_req is a struct and uri is the char uri[512] cited above.

the "uri" on the right side is a char *
Is there some silly beginner mistake I'm making?
Thanks in advance for any advice.

---

### Post by Tony Flury on 2010-10-29
presumably you are trying to copy the contents of the the string uri into the packet.req.uri_req.uri ?

If so you have to use strncpy (or strcpy) - you can't copy strings in C by assigning pointers.

---

### Post by mongooseman1128 on 2010-10-29
ahhh... that makes sense. Thanks Tony!

---


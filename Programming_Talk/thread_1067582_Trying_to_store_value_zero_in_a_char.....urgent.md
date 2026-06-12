---
title: "Trying to store value zero in a char.....urgent"
date: 2009-02-12
forum: Programming Talk
---

### Post by pankbiet on 2009-02-12
Hi

I am trying to store value 0 in char. I am doing this:

I have a char array having value 65 (e.g. 'A' )at some places. I have to put a NULL, e.g. 0 in those places.....like this
(assuming abc[5] was 'A')

abc[5]=(char)(0);

Then i convert the whole char array into a string:

xyz=new String(abc);

The recipient expects the xyz to be a UTF8String. But it is rejecting xyz saying invalid format......Any help?......Quick replies will be highly appreciated.

---

### Post by pankbiet on 2009-02-12
Forgot to add that i am working in java

---

### Post by eye208 on 2009-02-12
> **pankbiet said:**
> Hi

I am trying to store value 0 in char. I am doing this:

I have a char array having value 65 (e.g. 'A' )at some places. I have to put a NULL, e.g. 0 in those places.....like this
(assuming abc[5] was 'A')

abc[5]=(char)(0);

Then i convert the whole char array into a string:

xyz=new String(abc);

The recipient expects the xyz to be a UTF8String. But it is rejecting xyz saying invalid format......Any help?......Quick replies will be highly appreciated.
String xyz = new String(abc).replace('A', '\0');

---

### Post by slavik on 2009-02-12
why does this look like homework?

---


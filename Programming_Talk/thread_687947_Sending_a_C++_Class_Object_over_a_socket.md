---
title: "Sending a C++ Class Object over a socket?"
date: 2008-02-04
forum: Programming Talk
---

### Post by earobinson on 2008-02-04
If I write my own C++ class and then I want to send an object over a socket is there any way to do it?

for example if my class had 2 string objects how would I go about sending that class over a tcp/ip connection?

Thanks.

---

### Post by CptPicard on 2008-02-04
You essentially have to write your own serializer as far as I know. For trivial objects you can just write sizeof(your_type) bytes from your_type *ptr into the socket, for more complex objects you have to figure out some sort of order to do the same to the object tree that your serialized object is the root of.

I would go about this by borrowing a page from Java's playbook -- make an abstract class Serializable with a virtual method that takes your socket. Then just inherit from this and implement for every object that you want serializable.

---

### Post by Wybiral on 2008-02-04
On two different computers, since the internal representation might differ, the best bet would be to send the members individually, then reconstruct the class on the receiving end (send the strings as plain character arrays over the network, then assign them to the appropriate members in the class). In other words, serialize (as CptPicard suggested).

---

### Post by aks44 on 2008-02-04
The language itself has no way to do it easily.

This is quite a delicate topic, the exact way to do it strongly depends on your application-level network protocol (eg. is it text or binary based?).

I'm afraid that I can't answer the question precisely without more information on your exact protocol. As far as I'm concerned I usually go for binary protocols rather than text ones, but this is mainly because I tend to handle lots of binary data blobs.

Anyway you'll have to (de)serialize each and every relevant member variable separately, preferably wrapping the whole class (de)serialization in member functions (which could possibly be part of a base interface class, for more flexibility).


The real question here is: *which format would you choose if you had to save that info to a file, and read it back?* Sockets are nothing more than streams, the only difference at the level that interests us is that contrary to files you can't seek on sockets.



EDIT: lol I can't believe I'm that slow, there was no answer when I started answering. :D

Regarding CptPicard's suggestion "*For trivial objects you can just write sizeof(your_type) bytes from your_type *ptr into the socket*", keep in mind that different computers may not:
- use the same endianness
- have the same alignment requirements
- use the same code page (so it's important to send strings in a well defined encoding, UTF-8 is the most logical)
- use the same internal representation for floating point numbers, maybe also for integers (!!)

That's why I said that it's a very delicate topic, which depends on the whole chosen protocol. I strongly advise against simply pushing the data bytes on the network without any additional care, this is just asking for trouble. :)

---

### Post by earobinson on 2008-02-04
ok, so in that case I dont know how to send to strings across the tcpip ports (because they are both variable size, how do I send them in the same message?)\

an example would be great

---

### Post by aks44 on 2008-02-04
You have two ways of doing that:

1) push the string characters on the network, and rely on a specific string terminator (just like C-strings rely on a null terminator). The problem with that approach is that you can hardly preallocate a buffer, so you'll probably end up reallocating much memory needlessly (quite inefficient).

2) my preferred method: first push the string length then the string characters. This way on the receiving side, you'll first read the length, allocate the appropriate buffer, then fill it with the string data. It is usually way more efficient.

Don't forget to ensure beforehand that the string you're transferring is correctly encoded, so that there is no ambiguity on the receiving side.


BTW, those two methods can always be applied to any variable-sized data. Method 1 usually requires markers to be inserted before and/or after the data itself, while method 2 is more straightforward.

---

### Post by earobinson on 2008-02-04
> **aks44 said:**
> You have two ways of doing that:

1) push the string characters on the network, and rely on a specific string terminator (just like C-strings rely on a null terminator). The problem with that approach is that you can hardly preallocate a buffer, so you'll probably end up reallocating much memory needlessly

2) my preferred method: first push the string length then the string characters. This way on the receiving side, you'll first read the length, allocate the appropriate buffer, then fill it with the string data.


Don't forget to ensure beforehand that the string you're transferring is correctly encoded, so that there is no ambiguity on the receiving side.

any sample code of both ways (I guess Im having problems with If I push out the strings "foo" and "bar", ill end up with "foobar" and how do I know where the first string ends and the second one starts)

Thanks

I can think of complicated ways of doing it, I just wana keep it simple.

---

### Post by aks44 on 2008-02-04
Let's say you have two std::string objects, s1 and s2.

First, write s1.length() to the network (hton will help to ensure correct byte ordering), then the data pointed by s1.c_str() (you'll probably want to exclude the null terminator). Repeat for s2.

When reading, first read the size into a temporary variable (see ntoh to revert the byte ordering), allocate a correct buffer (think about adding 1 byte for the null terminator), read the bytes and fill the buffer, and finally make sure you put a null byte at the end of the buffer (to prevent later overflows). Repeat for s2.


Sorry I won't put any actual code, it's been long time since I last used low level network APIs, all I deal with is high level stream abstractions (so that I can handle sockets, files and memory buffers the same way). I hope the description I made is enough to get you started though. :)

---

### Post by earobinson on 2008-02-04
Its a start thanks, if anyone has any code they can post that would be great, I would love to be able to deal with it at a higher level

---

### Post by hod139 on 2008-02-04
Professor ([Dave Hollinger]("http://cgi2.cs.rpi.edu/%7Ehollingd/")) at RPI has some sample code from his undergraduate operating systems course.  
[http://www.cs.rpi.edu/~hollingd/opsys/code/](http://www.cs.rpi.edu/~hollingd/opsys/code/)

The example socket code is here
[http://www.cs.rpi.edu/~hollingd/opsys/code/fifosock/](http://www.cs.rpi.edu/~hollingd/opsys/code/fifosock/)

---

### Post by public_void on 2008-02-05
For transferring data over a network look at [RFC4506]("http://tools.ietf.org/html/rfc4506.html"). It describes how to transfer data between computer with different architectures. For strings it states that a 4 bytes size is put first, followed by the null terminated string that is padded. Heres the diagram:

```
            0     1     2     3     4     5   ... 
         +-----+-----+-----+-----+-----+-----+...+-----+-----+...+-----+ 
         |        length n       |byte0|byte1|...| n-1 |  0  |...|  0  | 
         +-----+-----+-----+-----+-----+-----+...+-----+-----+...+-----+ 
         |<-------4 bytes------->|<------n bytes------>|<---r bytes--->| 
                                 |<----n+r (where (n+r) mod 4 = 0)---->| 
                                                                  STRING
```

---


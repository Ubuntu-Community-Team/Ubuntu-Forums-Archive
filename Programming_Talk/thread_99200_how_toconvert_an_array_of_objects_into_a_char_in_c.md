---
title: "how toconvert an array of objects into a char* in c++?"
date: 2005-12-05
forum: Programming Talk
---

### Post by jerome bettis on 2005-12-05
hi

i'm working on a basic client / server application here, the client has
something like this to be sent:

```
struct request {
    int x, y;
    char buffer[1024];
}

struct request *requests = new struct request[10000];
``` 
requests has to be converted to a char *, and transmitted across a socket. actually not all of the requests, just the ones that are <= count.
 
```
char* buf = to_char_star(requests[0] .. requests[count]);
socket->send(buf, sizeof(buf);
``` 
how do i cast the array of requests into a char*? i tried using reinterpret_cast but it wasn't working or i wasn't using it right.

once the server gets it, it will just write the char* to a binary file. later, the server will send the client the contents of the file over
the socket, and the client can cast the char * back to restore the object array.

thanks for any help   :cool:

---

### Post by por on 2005-12-05
tips:

- your class (or struct) should code the methods for data serialisation (what you try to achive with the casts vice versa). read a tutorial on programming in C++.
- use stl (standard template library) to get an iterator
- use boost for even more templates, e.g. ones that allow you to implement correct multi threading, something that only few client/server apps can do without.
- use beepcore (beepcore.org) or another suitable framework to implement the communication protocol

good luck

---

### Post by thumper on 2005-12-05
Instead of having methods in your struct for serialisation, have functions outside the class (as specified in one of Herb's books).

If using C++, use streams to serialise your structs.  Also if you are not going to use all 1000 (or other magic number) of your structs, don't create them.  Use a vector (or other container as needed).

---

### Post by LordHunter317 on 2005-12-05
[QUOTE=jerome bettis]how do i cast the array of requests into a char*?[/quote]You don't.  You can't do it (safely) in C, you can't do it (safely) in C++.

Write a stream operator for your class that outputs the data you want:```
std::ostream&
operator<<(std::ostream& lhs, const request& rhs);
``` You can then use normal iostream operations to get the data.  Your function would probably look something like:```
{
    lhs << rhs.x << rhs.y << buffer;
    return lhs;
}
```or similar.

Several notes (some have been already said, I apologize if I repeat any):[list][*]Use a std::vector, not an array.  Arrays are evil.  If you're really implementing deque behavior, then use std::deque[*]Hide your class data.  It shouldn't be public unless the whole world needs read and write access.  Even then, it probably shouldn't be public.  Only expose what you must.[*]Use std::string, not C-style char-arrays as strings.[/list]

---

### Post by jerome bettis on 2005-12-05
thanks for your help guys

first off, regarding what looks like bad c++ code, it has to be done this way. all of this data is coming from the kernel, i can't use vectors or std::string or class in the kernel.  i tried using a linked list, but the dynamic storage overhead was actually a concern. 

this sucks, i know, but it's really just because of a bad system design.  i could have done it like this or got involved with C socket programming (shudder).  this design is really bad, but i'm getting points for getting something working, and not necessarily the best possible design that would take too long to implement.

i like the stream operator idea, however each elements buffer has \0 which would inadvertantly terminate the large char* i'm streaming them all into.  this is a big problem that i don't think can be solved.  any ideas?

i'd like to avoid iterating through the array and removing each buffer's null chararcter.  if i have to iterate through it, i might as well just send one at a time, which would be ok, but sending the whole thing at once would be much better.

thanks again

---

### Post by thumper on 2005-12-06
Instead of using the operator << to write your char array, use the write method on the stream itself, so...
```
stream.write(req.buffer, 1024);
```will write 1024 chars to the buffer, nulls and all.

You can still use vectors with this style of programming BTW.

---

### Post by LordHunter317 on 2005-12-06
[QUOTE=jerome bettis]first off, regarding what looks like bad c++ code, it has to be done this way. all of this data is coming from the kernel, i can't use vectors or std::string or class in the kernel.[/quote]This is code in the kernel or that structure is in the kernel?  If the former, you can't write C++ anyway so stop trying.  If the latter, then wrap all your access to the struct inside a class.  

> i like the stream operator idea, however each elements buffer has \0 which would inadvertantly terminate the large char* i'm streaming them all into. this is a big problem that i don't think can be solved.  any ideas?You can do as thumper suggested and have the overriden operator<< use write() for the char.

A better solution if you're streaming a bunch out would be to write it to a stringstream, and then use that to get your char*.  So, something like:```

#include <sstream>
#include <vector>

int
main() {
    std::vector<request_wrapper> wrappers;

    // Load it up.

    std::stringstream str_builder;
    for (std::vector<request_wrapper>::const_iterator i=wrappers.begin(); i!=wrappers.end(); ++i) {
        str_builder << *i;
    }

    const char* output = str_builder.str().c_str(); 
}
```

Whether you'll still need to use write() in the operator<< is dependent on how you lay your structure out.  I highly recommend you either wrap the structure in a class with proper OO functionality, or write some sort of factory method(s)/implicit casts to convert from one to the other.  Composition is probably better than using a factory here though, due the memory management issues.

---

### Post by jerome bettis on 2005-12-06
[quote=LordHunter317]This is code in the kernel or that structure is in the kernel? If the former, you can't write C++ anyway so stop trying. If the latter, then wrap all your access to the struct inside a class. [/quote]

haha no this code is not in the kernel.  the user level program does an ioctl( ) on the driver to get the array.  it would have been ideal to eliminate this user program and stay in the kernel, but kernel programming is very difficult and i don't have the time to get my hands too dirty with that.  i _hate_ C, but i can live with c++.

> You can do as thumper suggested and have the overriden operator<< use write() for the char.

A better solution if you're streaming a bunch out would be to write it to a stringstream, and then use that to get your char*. So, something like:```

#include <sstream>
#include <vector>

int
main() {
    std::vector<request_wrapper> wrappers;

    // Load it up.

    std::stringstream str_builder;
    for (std::vector<request_wrapper>::const_iterator i=wrappers.begin(); i!=wrappers.end(); ++i) {
        str_builder << *i;
    }

    const char* output = str_builder.str().c_str(); 
}
``` 
Whether you'll still need to use write() in the operator<< is dependent on how you lay your structure out. I highly recommend you either wrap the structure in a class with proper OO functionality, or write some sort of factory method(s)/implicit casts to convert from one to the other. Composition is probably better than using a factory here though, due the memory management issues.

right i got all that but here's the problem.

char *big_char_star = serialize_all_requests(request_array);

big_char_star will look something like this:
int,int,small_char\0int,int,small_char\0int,int,small_char\0\0

when i try to send it over the socket, it will see that first \0 and stop right there - not at the \0 for the big_char_star like it should.

i guess the real question here is not how to serialize these individual objects, (i'm past that) but rather how to serialize a whole bunch of them into one and not have the \0 be a problem.

right now i'm just sending them over the socket individually.  not ideal and a little slower, but it works ok for now.

---

### Post by LordHunter317 on 2005-12-06
> **jerome bettis]right i got all that but here's the problem.

char *big_char_star = serialize_all_requests(request_array) said:**
> Not if you use a stringstream like I suggest.  Even if they didn't strip out the invidiual outputs, you can use write() like thumper suggested to not even put the NUL in the stringstream.

Seriously, if you need a StringBuilder in C++ (which you do), use stringstream.  

[quote]when i try to send it over the socket, it will see that first \0 and stop right there - not at the \0 for the big_char_star like it should.Actually, if you're using read(), write(), send(), or recv() for your I/O, it won't.  They take a void* pointer and total length, and don't care about the contents.  Otherwise, how would I send a byte of zero down the line?  If they stopped at ASCII '\0', such a thing would be impossible.

---

### Post by thumper on 2005-12-07
A frequent idiom for sending data of unknown length down through sockets is to prefix the buffer with four bytes (int) length.

So you read the first four bytes, this gives you the length of the rest of the data that has been sent, let's call it buff_size.

You then read buff_size bytes from the socket.  This is now a large char array.  You then feed this into your builder on the other end.

If you are sending the entire 1024 bytes of the char* in your request structure, then recreating the data at the other end is fairly trivial.  Also your **big_char_star** does not contain what you think above.

Despite all the talk of streaming stuff, I would be tempted to write simple packing and unpacking specifically (as long as you don't have to have human readable stuff over the socket).  If you are going to do that though remember to use the host to net conversion functions for your integral values.

---

### Post by LordHunter317 on 2005-12-07
[QUOTE=thumper]Despite all the talk of streaming stuff, I would be tempted to write simple packing and unpacking specifically (as long as you don't have to have human readable stuff over the socket).[/quote]He still wants to send multiple packages in a single call, so you still end up needing stringstream or similar to concatonate them all together before transmission.

---

### Post by jerome bettis on 2005-12-07
[quote=LordHunter317]Not if you use a stringstream like I suggest. Even if they didn't strip out the invidiual outputs, you can use write() like thumper suggested to not even put the NUL in the stringstream.

Seriously, if you need a StringBuilder in C++ (which you do), use stringstream.  [/quote]

excellent, i'll give this a shot when i get home.  right now i'm just sending them one at a time, this is sllooooooooooooooowwww.  if i can send just one big packet it would be 10x faster.

> Actually, if you're using read(), write(), send(), or recv() for your I/O, it won't. They take a void* pointer and total length, and don't care about the contents. Otherwise, how would I send a byte of zero down the line? If they stopped at ASCII '\0', such a thing would be impossible.

you're right, i worded my last post wrong.  i said when i send it over, it will stop - but it all gets sent.  the problem is casting the char* back to a struct request.  the cast stops at the first \0.

[quote=thumper]A frequent idiom for sending data of unknown length down through sockets is to prefix the buffer with four bytes (int) length.
 
 So you read the first four bytes, this gives you the length of the rest of the data that has been sent, let's call it buff_size.
 
 You then read buff_size bytes from the socket. This is now a large char array. You then feed this into your builder on the other end.[/quote]

i like that idea actually.  but i'm using the SendBuf(char*, size_t) method in the socket lib so the size is sent with the data.
 
> If you are sending the entire 1024 bytes of the char* in your request structure, then recreating the data at the other end is fairly trivial. Also your **big_char_star** does not contain what you think above.

if i send one at a time yes, it's very trival.  can you explain how i'm wrong about big_char_star?  i'm curious.

> Despite all the talk of streaming stuff, I would be tempted to write simple packing and unpacking specifically (as long as you don't have to have human readable stuff over the socket). If you are going to do that though remember to use the host to net conversion functions for your integral values.

yeah that would be ideal.  i could do compression and stuff in there, that's excellent but will have to wait till later (time is running out!!  :o)

---

### Post by thumper on 2005-12-08
[quote=jerome bettis]i like that idea actually. but i'm using the SendBuf(char*, size_t) method in the socket lib so the size is sent with the data.[/quote]
What makes you think that the SendBuf actually sends the size of the buffer down the socket first?  The normal behaviour for a method like that is just to send **x** bytes down the socket starting at the pointer location you gave it.
[quote=jerome bettis]if i send one at a time yes, it's very trival. can you explain how i'm wrong about big_char_star? i'm curious.[/quote]You mention above that
[quote=jerome bettis]big_char_star will look something like this:
int,int,small_char\0int,int,small_char\0int,int,sm all_char\0\0[/quote] and I suppose that it could, however not if you are writing 1024 characters to the string stream like was suggested.  Also commas are not really a good one the wire delimiter.

Do you really need to worry about imbedded nulls?  If you do, then the only real way to send your char* buffers is to send all 1024.  If not, then you can delimit it and use the null terminator to terminate the string.  You mention that worrying about calculating the length of the string is a problem, but I'll say that spending the time calculating the length of the string would probably be quicker than sending it all down a socket 8)  Don't optimize prematurely.

Using streaming operators as mentioned above is a clean way to emit human readable strings.  Often it is also the simplest way.  Working with custom packing and unpacking gives more flexability, but also you have more rope to shoot yourself in the foot with.  You are much more likely to have a bug in custom data packing than with streams.
[quote=LordHunter317]He still wants to send multiple packages in a single call, so you still end up needing stringstream or similar to concatonate them all together before transmission.[/quote] Using this method does not mean you cannot concatonate them together.
```
// work out how many to send
//create buffer big enough (1024*sizeof(char) + 2 * sizeof(int)) * count + sizeof(int)
// iterate over list
// send buffer

```

---

### Post by LordHunter317 on 2005-12-08
Hence, a similar method.  I just loathe non-stream based representations for I/O unless I'm doing asynchronous I/O with callbacks (I had bad experiences with a custom application on VMS).  IF you want ot used a fixed buffer and add them in the array, that's cool too.

  Even then, I'd still do internal formatting of the data for a single I/O request with a streamstring, StringBuilder (Java/C#) or other similar representation.

---


---
title: "Can I send a C struct to a socket?"
date: 2007-11-15
forum: Programming Talk
---

### Post by raul_ on 2007-11-15
I'm trying to send a struct to a DGRAM socket. Here's what i'm doing:

client (sends struct)

```

n = sendto(socket_fd,(const char*)&mypdu,sizeof(mypdu),0,
    		(struct sockaddr *)&server_addr,sizeof(server_addr));

```

server

```

n=recvfrom(socket_fd,buffer,sizeof(mypdu),0,
				(struct sockaddr *)&from,&fromlen);

```

but in the client, i initialized one of the fields with 100, and in the server end, that field has the value 3 =\

Can I send the whole struct without sending it field by field?

---

### Post by kknd on 2007-11-15
You will have to serialize the thing to send, and the receiver will need to reassemble the thing, very painfull.

---

### Post by aks44 on 2007-11-15
You shouldn't send a whole struct at a time, in fact you shouldn't even send integers (int) "as-is".


The problem with structs is that depending on the compiler, on the OS, on the architecture, ... there are different padding conventions that apply.


As an example:

```
struct Foo
{
  char foo;
  int bar;
};
```

sizeof(struct Foo) is not guaranteed to (and in real world will almost never) be equal to sizeof(char)+sizeof(int) due to those padding issues.


Moreover, depending on the CPU architecture there are problems of endianness too (most or least significant byte first?).


The rule of thumb being:
- send structs field by field
- if you have to transfer integers, use hton / ntoh functions (aka. Host To Network / Network To Host) which correctly convert byte order.

Or, use plain text protocols.

---

### Post by raul_ on 2007-11-15
Thanks. 

Very painful indeed :)

---

### Post by slavik on 2007-11-15
I would memcopy the struct into a buffer and send the buffer :)

---

### Post by j_g on 2007-11-15
Listen to aks44.

I'll just add that, even if you use datatypes that you're sure all of your networked devices regard as the same bitsize (for example, I can't think of a current architecture that doesn't consider "char" to be 8 bits), same byte order (again, "char" and "unsigned char" relieve you of that worry), or padding, you absolutely, absolutely cannot send any "pointer" to another machine. For example, assume you have the following two struct definitions:

```
struct Something {
   char buf[8];
}

struct SomethingPtr {
  struct Something *something;
}
```

You can't do something like sending these two structs:

```
mySomething = {"text"};
MySomethingPtr = {&mySomething};
```

The mySomething address on one machine is going to be completely different on the other machine. You have to do something people often call "flattening the struct". You replace that pointer field with something that indicates to the other machine that it needs to reinsert a pointer to the mySomething struct you previously sent over.

You may want to take a look at how Microsoft's COM "marshalls" data between processes. There are examples of flattening structs there.

---

### Post by dwhitney67 on 2007-11-15
> **kknd said:**
> You will have to serialize the thing to send, and the receiver will need to reassemble the thing, very painfull.

This is the correct way to do things. although I would not describe it as "painful".  It's just another opportunity to code more.

Aks44 was also correct in that endianess (sp?) is a factor.  If you are transferring data from an Intel architecture to a PPC (power PC) architecture, then you will need to accommodate that the bytes in the words are swapped.  M$'s .NET and CORBA handle this automagically.  You can also do it yourself with minor effort.

Back to the serialize/unserialize procedure... you will need to perform a deep-copy of your structure into a buffer, and if applicable, indicate the size of the buffer and sizes of any variable-length fields within the same buffer.

Once this buffer is sent across the wire, the recipient should be able to parse through the received buffer to reconstruct the original data structure.

---

### Post by raul_ on 2007-11-15
this code is to work between Linux ix86 systems, so I don't think I have that sort of problems. I'm glad to say that it was fairly painless. My structure has mostly char* fields, one int (a cast to (const char*) did the trick), and I created a function to convert a list to a string, so I can send it in a buffer. 

It's nice to have so many good responses in a relative short amount of time, in a subject that has almost anything, if anything at all, to do with Ubuntu :)

Thanks

---

### Post by raul_ on 2007-11-15
marked it as solved :guitar:

---

### Post by giggs on 2010-06-13
Hello,
 
Can I have the source code please ? I am also having the same problem. I am not familiar with serialization . 

My structure is something like this :

struct SecurityEventNotice
{
      int id;
      int timestamp;
      char *description;
      char *source;
}

I need to pass this entire structure through a socket and also the server should be able to unmarshall it.

Can anyone help ?? :)

---

### Post by dwhitney67 on 2010-06-13
> **giggs said:**
> 
Can anyone help ?? :)

Can please show that you have at least made a minor attempt to solve this issue on your own.

Serialization involves stuffing your data into a buffer of chars, in a fashion that makes it easy to retrieve at a later time (via de-serialization).

I recommend that you define/implement two functions; one that serializes the other that de-serializes.  When you send the serialized data through the socket, you will need to know how many bytes are in the buffer you wish to send.  Your serialize() function should keep track of this number, and return it.

---


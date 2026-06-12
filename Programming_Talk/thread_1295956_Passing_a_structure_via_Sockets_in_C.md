---
title: "Passing a structure via Sockets in C"
date: 2009-10-20
forum: Programming Talk
---

### Post by codingfreak on 2009-10-20
Hi

I got a simple structure with a int variable and a chat variable. I like to know how can I pass the structure from client to server using sockets ??

**NOTE:** Both client and Server do know about the variables in the structure and I want to pass values of each variable in the structure from Client to Source.

---

### Post by dwhitney67 on 2009-10-20
Don't think of it as passing a structure between the client and server; instead think of it as passing a series of bytes between them.

In your case, an int is 4-bytes, and a chat [sic] is one-byte, thus for a total of 5 bytes.  Unless you go out of your way though, the compiler will probably align this structure on a word-boundary, thus making the structure 8-bytes long.  There's a way to overcome this.

Here's a synopsis...

```

#pragma pack(1)   // this helps to pack the struct to 5-bytes

struct Foo
{
  int  value;
  char letter;
};

#pragma pack(0)   // turn packing off


int main()
{
   ...

   struct Foo foo = {10, 'a'};

   sendto(sock, &foo, sizeof(foo), 0, (struct sockaddr*) &sin, sizeof(sin));

   ...
}

```
The receiving code would look something like:
```

#pragma pack(1)

struct Foo   // of course, this would be better suited in a header file
{
   int  value;
   char letter;
};

#pragma pack(0)

int main()
{
   ...

   struct Foo foo;

   recvfrom(sock, &foo, sizeof(foo), 0, (struct sockaddr*) &sin, sizeof(sin));
}

```
Assuming you are dealing with more complex structures, such as those that may have for instance a char*, then you would need to learn the concept of serialization and deserialization.

Serialization means taking each field of the structure and packing it into a buffer, so that the data is represented as a stream of bytes.  The recipient of the data would have to deserialize this data back into its original form.

You appear to not be at this stage yet, but when you do reach it, your application will need the assistance of functions such as memset() and memcpy() for setting up, and then ingesting, the buffer stream.

There is also another concept that you should be aware of; Big Endian vs. Little Endian formatting.  Most data transmissions across a network are sent using Network-Byte-Order, or Big Endian, format.  Thus typically for short and int values, these are converted to NBO using htons() and htonl(), respectively.  Upon receiving the data, the opposite functions are used:  ntohs() and ntohl().

If for now you are sending data from one Intel machine to another, you do not have to worry about Endianess.  If however you will be sending data to say, a PowerPC machine, or other other unknown machine, then you must employ the NBO concept for the data.

Anyhow, that's enough for you to digest for now!  Dealing with sockets is difficult at first, but gets easier with experience.  Just remember to write modular code so that you do not have a thousands lines in your main() function.

---

### Post by Arndt on 2009-10-20
> **dwhitney67 said:**
> Don't think of it as passing a structure between the client and server; instead think of it as passing a series of bytes between them.

In your case, an int is 4-bytes, and a chat [sic] is one-byte, thus for a total of 5 bytes.  Unless you go out of your way though, the compiler will probably align this structure on a word-boundary, thus making the structure 8-bytes long.  There's a way to overcome this.

Here's a synopsis...

```

#pragma pack(1)   // this helps to pack the struct to 5-bytes

struct Foo
{
  int  value;
  char letter;
};

#pragma pack(0)   // turn packing off


int main()
{
   ...

   struct Foo foo = {10, 'a'};

   sendto(sock, &foo, sizeof(foo), 0, (struct sockaddr*) &sin, sizeof(sin));

   ...
}

```
The receiving code would look something like:
```

#pragma pack(1)

struct Foo   // of course, this would be better suited in a header file
{
   int  value;
   char letter;
};

#pragma pack(0)

int main()
{
   ...

   struct Foo foo;

   recvfrom(sock, &foo, sizeof(foo), 0, (struct sockaddr*) &sin, sizeof(sin));
}

```
Assuming you are dealing with more complex structures, such as those that may have for instance a char*, then you would need to learn the concept of serialization and deserialization.

Serialization means taking each field of the structure and packing it into a buffer, so that the data is represented as a stream of bytes.  The recipient of the data would have to deserialize this data back into its original form.

You appear to not be at this stage yet, but when you do reach it, your application will need the assistance of functions such as memset() and memcpy() for setting up, and then ingesting, the buffer stream.

There is also another concept that you should be aware of; Big Endian vs. Little Endian formatting.  Most data transmissions across a network are sent using Network-Byte-Order, or Big Endian, format.  Thus typically for short and int values, these are converted to NBO using htons() and htonl(), respectively.  Upon receiving the data, the opposite functions are used:  ntohs() and ntohl().

If for now you are sending data from one Intel machine to another, you do not have to worry about Endianess.  If however you will be sending data to say, a PowerPC machine, or other other unknown machine, then you must employ the NBO concept for the data.

Anyhow, that's enough for you to digest for now!  Dealing with sockets is difficult at first, but gets easier with experience.  Just remember to write modular code so that you do not have a thousands lines in your main() function.

If you know that the client and the server use the same C compiler and the same architecture, the packing thing will work, but pragma pack isn't standard, is it? And even if two architectures/compilers have the same byte order, they may have different ideas of the size of a 'long', for example (not relevant in this small problem, of course).

---

### Post by codingfreak on 2009-10-20
I even heard that pragma is not really portable enough ..... ??

One more doubt is -- Does it makes any sense if your structure has a pointer variable and you pass it to another machine via sockets ... since the receiver end don't understand the memory location to which the pointer variable points to ...

---

### Post by dwhitney67 on 2009-10-20
> **codingfreak said:**
> I even heard that pragma is not really portable enough ..... ??

Then find what is!  Or just send an unpacked structure; it doesn't really matter.  All that matters is how the data is interpreted upon receipt.

Frankly, if I were you, I would get the necessary experience on how to use sockets on a single-platform before worrying about cross-platform development.

> 
One more doubt is -- Does it makes any sense if your structure has a pointer variable and you pass it to another machine via sockets ... since the receiver end don't understand the memory location to which the pointer variable points to ...

Yes it matters.  The receiving system won't be able to do any constructive with the pointer's address.  Read my first post again with regards to serialization of data.

P.S.  Some software developers that abhor programming use the SDL-net library for their multi-platform networking needs.

---

### Post by codingfreak on 2009-10-21
[U]
@[/U][dwhitney67]("http://ubuntuforums.org/member.php?u=322753") - Using pragma worked out with flying colors.

But it seems there is some dependencies in using pragma when the client and server architectures are different.

You are saying about serialization and Deserialization. But I have a doubt about it. If the structure is complex with different datatypes .. even with arrays ... then we have to do serialization for each and every member individually on client side and deserialize it back again individually .... As a result we have to  write  serialize/deserialize functions for each and every possible type into a structure on both client and server side??

---

### Post by Arndt on 2009-10-21
> **codingfreak said:**
> [U]
@[/U][dwhitney67]("http://ubuntuforums.org/member.php?u=322753") - Using pragma worked out with flying colors.

But it seems there is some dependencies in using pragma when the client and server architectures are different.

You are saying about serialization and Deserialization. But I have a doubt about it. If the structure is complex with different datatypes .. even with arrays ... then we have to do serialization for each and every member individually on client side and deserialize it back again individually .... As a result we have to  write  serialize/deserialize functions for each and every possible type into a structure on both client and server side??


It's been done before. See for example this page: [http://en.wikipedia.org/wiki/Serialization](http://en.wikipedia.org/wiki/Serialization). For some reason it doesn't mention Sun RPC and XDR, so also see [http://en.wikipedia.org/wiki/External_Data_Representation](http://en.wikipedia.org/wiki/External_Data_Representation) and look for Sun RPC (which may be obsolete now, it was long since I used it).

---

### Post by dwhitney67 on 2009-10-21
> **codingfreak said:**
> 
You are saying about serialization and Deserialization. But I have a doubt about it. If the structure is complex with different datatypes .. even with arrays ... then we have to do serialization for each and every member individually on client side and deserialize it back again individually .... As a result we have to  write  serialize/deserialize functions for each and every possible type into a structure on both client and server side??

As I joked about earlier, some "programmers" abhor programming.  Go figure.

If you don't want to perform serialization/deserialization, you could always add tons of bloat to your data by using XML.

---

### Post by codingfreak on 2009-10-21
> **dwhitney67 said:**
> As I joked about earlier, some "programmers" abhor programming.  Go figure.

If you don't want to perform serialization/deserialization, you could always add tons of bloat to your data by using XML.

But any general idea on how to do serialization and deserialization of data ... ??

I am really not intrested in XML stuff in C ...

@Arndt was saying about SunRPC and XDR .... does he mean RPC mechanism ??

---

### Post by dwhitney67 on 2009-10-21
> **codingfreak said:**
> But any general idea on how to do serialization and deserialization of data ... ??

I'm not going to candy-coat it... serialization and deserialization of data is not trivial, and for this reason (and perhaps many more), XML was invented.

Here's an example, and if you look carefully, I cut corners by not checking for all error conditions.
```

#include <stdlib.h>
#include <string.h>
#include <netdb.h>
#include <assert.h>

struct Data
{
   unsigned int age;
   char*        first_name;
   char*        last_name;
};


size_t serialize(const struct Data* data, unsigned char** buf)
{
   if (!data) return 0;

   const size_t fn_size   = data->first_name ? strlen(data->first_name) : 0;
   const size_t ln_size   = data->last_name ? strlen(data->last_name) : 0;
   const size_t data_size = sizeof(data->age) + sizeof(size_t) + fn_size + sizeof(size_t) + ln_size;

   *buf = calloc(1, data_size);

   if (*buf)
   {
      size_t offset = 0;

      // age
      unsigned int tmp = htonl(data->age);
      memcpy(*buf + offset, &tmp, sizeof(tmp));                offset += sizeof(tmp);

      // length of first name and the first name itself
      tmp = htonl(fn_size);
      memcpy(*buf + offset, &tmp, sizeof(tmp));                offset += sizeof(tmp);
      memcpy(*buf + offset, data->first_name, fn_size);        offset += fn_size;

      // length of last name and the last name itself
      tmp = htonl(ln_size);
      memcpy(*buf + offset, &tmp, sizeof(tmp));                offset += sizeof(tmp);
      memcpy(*buf + offset, data->last_name, ln_size);
   }

   return data_size;
}


struct Data* deserialize(const unsigned char* buf, const size_t bufSize)
{
   static const size_t MIN_BUF_SIZE = 12;  // min size of buffer includes age, zero-length first/last names

   struct Data* data = 0;

   if (buf && bufSize >= MIN_BUF_SIZE)
   {
      data = calloc(1, sizeof(struct Data));

      if (data)
      {
         size_t tmp = 0;
         size_t offset = 0;

         // get the age
         memcpy(&tmp, buf + offset, sizeof(tmp));
         tmp = ntohl(tmp);
         memcpy(&data->age, &tmp, sizeof(data->age));
         offset  += sizeof(data->age);

         // get the first name's length
         memcpy(&tmp, buf + offset, sizeof(tmp));
         tmp = ntohl(tmp);
         offset  += sizeof(tmp);

         if (tmp > 0)
         {
            // get the first name
            data->first_name = calloc(1, tmp + 1);
            memcpy(data->first_name, buf + offset, tmp);    // missing error checks!!!
            offset  += tmp;
         }

         // get the last name's length
         memcpy(&tmp, buf + offset, sizeof(tmp));
         tmp = ntohl(tmp);
         offset  += sizeof(tmp);

         if (tmp > 0)
         {
            // get the last name
            data->last_name = calloc(1, tmp + 1);
            memcpy(data->last_name, buf + offset, tmp);    // missing error checks!!!
         }
      }
   }

   return data;
}

int main()
{
   struct Data data1;

   data1.age        = 20;
   data1.first_name = strdup("Chuck");
   data1.last_name  = strdup("Roast");

   unsigned char* buf     = 0;
   size_t         bufSize = serialize(&data1, &buf);
   struct Data*   data2   = deserialize(buf, bufSize);

   // Verify serialization/deserialization worked as expected.
   assert(data2 != 0);
   assert(data1.age == data2->age);
   assert(strcmp(data1.first_name, data2->first_name) == 0);
   assert(strcmp(data1.last_name,  data2->last_name)  == 0);

   free(data1.first_name);
   free(data1.last_name);
   free(data2->first_name);
   free(data2->last_name);
   free(data2);

   return 0;
}

```

> 
I am really not intrested in XML stuff in C ...

Up2U.

> 
@Arndt was saying about SunRPC and XDR .... does he mean RPC mechanism ??
RPC = Remote Procedural Call; I suppose this could be used to transfer data from client to server?

---

### Post by Arndt on 2009-10-21
> **dwhitney67 said:**
> I'm not going to candy-coat it... serialization and deserialization of data is not trivial, and for this reason (and perhaps many more), XML was invented.



If all you want to do is reinvent ASN1, you probably don't need all the odd corners of XML, like namespaces, comments, processing instructions, attributes.

I suppose it happens quite often that two programs which agree on a data format for sending data between them have that format be a small subset of XML, rather than doing full-fledged XML parsing.

If you want to write your own, I think one of the first design decisions is which major type to use: one where the type of the data accompanies the data, or one where it doesn't (and sender and receiver have to know what is being passed). ASN1 is of the former kind, I think.

When I mentioned Sun RPC, I was thinking of the rpcgen program which generated serializing code given a typed structure definition. I suppose it could be used without identifying specific remote calls specifically. But since I don't find it when I google a little on the subject, it's probably been obsolete the last 10 years.

---

### Post by VertexPusher on 2009-10-21
Why reinvent the wheel?

[http://tpl.sourceforge.net/](http://tpl.sourceforge.net/)
[http://s11n.net/c11n/](http://s11n.net/c11n/)

---

### Post by codingfreak on 2009-10-26
I wonder why serialization hasn't been included within C standard .... when this is really very important in various cases.

---

### Post by mikka_22 on 2010-06-02
Hi, i'm using your serialize and deserialize functions...but i dont know what's next..in the client im trying to send the serialized struct over a socket like this:

caract_arch car_arch;
unsigned char* buf = 0;


scanf("%s", longitud);
scanf("%s", nombre_arch);

car_arch.longitud = malloc (strlen(longitud) + 1);
strcpy(car_arch.longitud,longitud);
car_arch.nombre_arch = malloc (strlen(nombre_arch) + 1);
strcpy(car_arch.nombre_arch,nombre_arch);
car_arch.tiempo = malloc (strlen(tiempo) + 1);
strcpy(car_arch.tiempo,tiempo);

tam_buf = serialize(&car_arch, &buf);
if(send(s,&buf,tam_buf,0) < 0)

where car_arch is:

typedef struct arch
{
	char *longitud; //4
	char *nombre_arch; //100
	char *tiempo;
}caract_arch;

and in the server side im doing this:

n = recv(ssock,&buf,sizeof(buf),0);
data_arch = deserialize(buf, sizeof(buf));

i dont know what is wrong but when i make a debug inside the deserialize function is like sizeof(buf) is returning me 0. Please help me, i dont know if im sending in the right way the serialized strut. Thanks a lot in advance.

---

### Post by mikka_22 on 2010-06-02
the serialize and deserialize functions im refering are the ones that posted dwhitney67. Please help me. I dont know how to send the serialized strut over the socket. Thanks a lot for ur attention. (Sorry 4 my english, its not good)

---

### Post by dwhitney67 on 2010-06-02
You need to understand how buffering works, and also learn how to index into a buffer.  Adjusting the start point of a buffer is no different than playing with the offset of a pointer.

Here's some code to help you with serializing and deserializing:
```

typedef struct arch
{
   char* longitud;
   char* nombre_arch;
   char* tiempo;
} caract_arch;


size_t serialize(const caract_arch* arch, char* buf)
{
   size_t bytes = 0;

   memcpy(buf + bytes, arch->longitud, strlen(arch->longitud) + 1);
   bytes += strlen(arch->longitud) + 1;

   memcpy(buf + bytes, arch->nombre_arch, strlen(arch->nombre_arch) + 1);
   bytes += strlen(arch->nombre_arch) + 1;

   memcpy(buf + bytes, arch->tiempo, strlen(arch->tiempo) + 1);
   bytes += strlen(arch->tiempo) + 1;

   return bytes;
}


void deserialize(const char* buf, caract_arch* arch)
{
   size_t offset = 0;

   arch->longitud = strdup(buf + offset);
   offset += strlen(buf + offset) + 1;

   arch->nombre_arch = strdup(buf + offset);
   offset += strlen(buf + offset) + 1;

   arch->tiempo = strdup(buf + offset);
}


int main()
{
   caract_arch arch_original;
   caract_arch arch_copia;

   arch_original.longitud    = strdup("100 metros");
   arch_original.nombre_arch = strdup("Juan Pacheco");
   arch_original.tiempo      = strdup("4 segundos");

   char   buffer[1024] = {0};
   size_t bufLen = serialize(&arch_original, buffer);

   deserialize(buffer, &arch_copia);

   printf("arch_copia.longitud    = %s\n"
          "arch_copia.nombre_arch = %s\n"
          "arch_copia.tiempo      = %s\n",
          arch_copia.longitud, arch_copia.nombre_arch, arch_copia.tiempo);

   // should deallocate all strings

   return 0;
}

```
When you send the data from the client to the server, send the buffer array, and of course specify the number of bytes in that buffer that you want to send.  Something like:
```

...

char buffer[1024] = {0};

size_t bytes = serialize(&arch_original, buffer);

send(socket_sd, buffer, bytes, 0);

...

```
The server on the other hand needs to receive/deserialize the data:
```

...

char buffer[1024] = {0};

ssize_t bytesRcvd = recv(client_sock_sd, buffer, sizeof(buffer), 0);

deserialize(buffer, &rcvd_arch);

...

```
Be careful if you are using TCP, for the buffer may be sent in one or more packets; thus you may not get it all in one recv().

---

### Post by mikka_22 on 2010-06-02
Thanks a lot for you very fast reply :) really im very grateful!, about what you said:
You need to understand how buffering works, and also learn how to index into a buffer. Adjusting the start point of a buffer is no different than playing with the offset of a pointer.
Could you please recommend some link to read about this please? 

And about this:
Be careful if you are using TCP, for the buffer may be sent in one or more packets; thus you may not get it all in one recv()

could you please give any clue about what i can do to handle this? do you have some tutorial about sockets in unix where i can read about this issue? Thanks a lot for your help!.

---

### Post by dwhitney67 on 2010-06-02
> **mikka_22 said:**
> Thanks a lot for you very fast reply :) really im very grateful!, about what you said:
You need to understand how buffering works, and also learn how to index into a buffer. Adjusting the start point of a buffer is no different than playing with the offset of a pointer.
Could you please recommend some link to read about this please? 

And about this:
Be careful if you are using TCP, for the buffer may be sent in one or more packets; thus you may not get it all in one recv()

could you please give any clue about what i can do to handle this? do you have some tutorial about sockets in unix where i can read about this issue? Thanks a lot for your help!.

A lot of folks seem to like this tutorial/guide that covers socket programming:
[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

As for other facets of the C language, you will need to learn it the way I did... through experience.  Of course, feel free to read the K&R book, or some other C programming manual.

---

### Post by mikka_22 on 2010-06-02
thank u very much!! =) you really helped me! im going to read the tuto thx a lot!! =)

---


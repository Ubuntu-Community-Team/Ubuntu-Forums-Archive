---
title: "Write binary in 32 bit from a 64 bit  C program"
date: 2012-09-19
forum: Programming Talk
---

### Post by achuthpnr on 2012-09-19
Hi,

This may be a strange question, but here it is. I am writing a C program for 64 bit compilation which gives lots of binary output files (mainly entire C structures with double precision numbers). In 64 bit computer I can read and process data  without any problem. But, I cannot read the data from a 32 bit computer (because it is in 64 bit). 

Is there any way to convert the 64 bit binary file to 32 bit? or 
directly print the data in 32 bit binary from the 64 bit program? or 
read 64 bit data from a 32 bit computer?

Any place where I could find the guidance to accomplish this will be great. 

Thanks.

---

### Post by Bachstelze on 2012-09-19
How is the "data" stored, and how are you reading it?

---

### Post by achuthpnr on 2012-09-19
I write the  struct using fwrite in binary form. When I read the file, I read it in to a similar struct, reconstructing the entire data.

---

### Post by Bachstelze on 2012-09-19
Well, you shouldn't do that. Read and write each field separately.

---

### Post by spjackson on 2012-09-19
Can you post your struct and any relevant type definitions? It may be possible to write it in a way that works on both platforms.

---

### Post by achuthpnr on 2012-09-19
The struct is something like

```

struct index {     
double x,y,z;     
float x0,y0,z0;     
char a,b,c,d;     
unsigned long int buy,sell;
};
```

---

### Post by spjackson on 2012-09-19
> **achuthpnr said:**
> The struct is something like

```

struct index {     
double x,y,z;     
float x0,y0,z0;     
char a,b,c,d;     
unsigned long int buy,sell;
};
```
If you use long long int instead of long int on both platforms then the overall size (56 bytes) is the same and the offsets are the same. That should work.

---

### Post by ofnuts on 2012-09-19
> **spjackson said:**
> If you use long long int instead of long int on both platforms then the overall size (56 bytes) is the same and the offsets are the same. That should work.
In the general case you can also have alignment problems. I would expect 64-bit integers in the 64-bit code to be laid out on 8-byte boundaries, while the 32-bit code would only align them to 4-byte boundaries (by default of course)(but I have no 64-bit compiler to check).

But nothing that cannot be fixed with proper ordering of structure members (biggest first), proper use the the stdint.h types, padding bytes, and     "__attribute__((packed))" (in that order).

---

### Post by trent.josephsen on 2012-09-19
It will most likely still break if you try to recompile it for a different OS, for a different platform, using a different compiler, or with different compiler options. Writing a struct to a file is probably the least robust serialization method you can use. Bachstelze's suggestion is smarter.

---

### Post by ofnuts on 2012-09-19
> **trent.josephsen said:**
> It will most likely still break if you try to recompile it for a different OS, for a different platform, using a different compiler, or with different compiler options. Writing a struct to a file is probably the least robust serialization method you can use. Bachstelze's suggestion is smarter.
The ultimate smart solution is to define the file format as a stream using the ASN.1 language, and use ASN.1 compilers to generate the code to produce and parse it. Now, we all make compromises and cut corners, and structs can be manageable with  a modicum of discipline and some decent unit testing.

---

### Post by trent.josephsen on 2012-09-19
> **ofnuts said:**
> The ultimate smart solution is to define the file format as a stream using the ASN.1 language, and use ASN.1 compilers to generate the code to produce and parse it.
False Hubris. The opposite of an impractically fragile method is not an impractically robust one.

---

### Post by ofnuts on 2012-09-20
> **trent.josephsen said:**
> False Hubris. The opposite of an impractically fragile method is not an impractically robust one.I do agree that both methods are on symmetrical sides of the spectrum, but having used both (across OS/2 16-bit, Windows NT, and PowerPC AIX in one case of the structs solution) I don't find them that impractical, even including the change in endianness... And Bachstelze's suggestion implies that you have different code on each platform so you need a way to make sure all these versions are kept in sync.

---

### Post by albandy on 2012-09-20
A little trick could be to compile it at 32 bit:

gcc -m32 -o program program.c

and run only the 32bit version.


Also check stdint.h
[http://pubs.opengroup.org/onlinepubs/007904975/basedefs/stdint.h.html](http://pubs.opengroup.org/onlinepubs/007904975/basedefs/stdint.h.html)

---

### Post by achuthpnr on 2012-09-20
> **albandy said:**
> A little trick could be to compile it at 32 bit:

gcc -m32 -o program program.c

and run only the 32bit version.


Also check stdint.h
[http://pubs.opengroup.org/onlinepubs/007904975/basedefs/stdint.h.html](http://pubs.opengroup.org/onlinepubs/007904975/basedefs/stdint.h.html)


This is what I ended up doing. But there is a huge amount of data, that came from a 64 bit compilation. I need somehow to make it readable in 32 bit platform to save my time finding a 64 bit machine to work with.

---

### Post by achuthpnr on 2012-09-20
> **ofnuts said:**
> In the general case you can also have alignment problems. I would expect 64-bit integers in the 64-bit code to be laid out on 8-byte boundaries, while the 32-bit code would only align them to 4-byte boundaries (by default of course)(but I have no 64-bit compiler to check).

But nothing that cannot be fixed with proper ordering of structure members (biggest first), proper use the the stdint.h types, padding bytes, and     "__attribute__((packed))" (in that order).

This is what is happening - there is a difference in the file size in both platform.

---

### Post by spjackson on 2012-09-20
> **achuthpnr said:**
> This is what I ended up doing. But there is a huge amount of data, that came from a 64 bit compilation. I need somehow to make it readable in 32 bit platform to save my time finding a 64 bit machine to work with.
I had assumed that might be the case. Most of the advice in this thread has been to throw away your existing file structure and use a new one.

If you were starting with a clean slate, this might be the best policy. If you suspect that you might need to port to many different platforms in the future, then you may need to bite that bullet.

If all you need to do is have a structure that is compatible with your existing 64-bit structure that works on 32-bit, I maintain that this should be possible. You need to make sure that the members are the same size (e.g. use long long) and, if necessary, conditionally compile extra padding to handle alignment issues. The structure you posted before did not need any alignment handling. I think that it is easier to deal with alignment when going from 64-bit to 32-bit than it is to go the other way.

But maybe I'm just mad to believe that it may be possible.

---

### Post by trent.josephsen on 2012-09-20
> **spjackson said:**
> Most of the advice in this thread has been to throw away your existing file structure and use a new one.
Not at all. My advice was to *write an algorithm to serialize the data* rather than *relying on how your implementation lays out structs in memory*. If you don't want to lose the data that's been stored by the 64-bit program, then it's perfectly reasonable to write an algorithm that encodes and decodes *that binary structure*, without depending on implementation-defined behavior. Nobody has said OP should ditch his current file structure, just that he should program it portably.

---


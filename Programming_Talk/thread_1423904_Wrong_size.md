---
title: "Wrong size?"
date: 2010-03-07
forum: Programming Talk
---

### Post by quanganht on 2010-03-07
Yet another stupid question from me :(
I have a structure, like this:
```
struct IndexEntry
{
	unsigned char type;
	unsigned short parent;
	unsigned long startblock;
	unsigned int blockoffset;
};

```

The actual size should be 15 bytes, but when I use sizeof() to print out the size, it reports 24! What happened?

---

### Post by MadCow108 on 2010-03-07
the compiler may align your structures to certain memory boundaries to speed up memory access

there are flags to tell the compiler not to do that
I think it is __attribute__((packed)) for gcc
but better check it on the compilers attribute site

you can also archive smaller packing by placing the less than word sized entries together so that not each one needs padding.
```

// pseudocode 4 byte word size
struct 12byte {
char a; // 3 byte padding
int b; // 4 byte
char c; // 3 byte padding
};

struct 8byte {
char a;
char c; // 2 byte padding
int b;
}

// here  a packed structure:
struct 6byte {
char a;
int b;
char c;
} __attribute__((packed));

```

---

### Post by Zugzwang on 2010-03-07
MadCow108 is perfectly right. I just want to add that you cannot rely on an "int" being 4 bytes and "long" being 8 bytes (actually, long is 4 bytes on a 32-bit GCC). There are the datatypes "int32_t" and "int64_t" that have a guaranteed size, but that's non-standard extension of the language. You can use google to find out more.

---

### Post by pbrane on 2010-03-07
Edit: too slow!

Different types or objects have different alignment requirements. Don't assume that the sum of the individual objects sizeof()'s will equal the sizeof the struct. 

Have a look at data alignment for your processor type.

---

### Post by quanganht on 2010-03-07
Thanks you guys very much. I will try uintX_t.

---

### Post by PX9 on 2010-03-07
There is a great article about data alignment - [Data alignment: Straighten up and fly right](http://www.ibm.com/developerworks/power/library/pa-dalign/). After you read it you will fully understand why is this happens.

---

### Post by dwhitney67 on 2010-03-07
> **quanganht said:**
> Thanks you guys very much. I will try uintX_t.

Using the uintX_t (or intX_t) won't make a difference unless you pack the structure as MadCow108 indicated.

Another flavor of packing, which might not be portable:
```

#include <stdint.h>

#pragma pack(1)

struct SevenBytes
{
   uint8_t  oneByte;
   uint16_t twoBytes;
   uint32_t fourBytes;
};

#pragma pack(0)

```

---

### Post by Lux Perpetua on 2010-03-08
> **Zugzwang said:**
> There are the datatypes "int32_t" and "int64_t" that have a guaranteed size, but that's non-standard extension of the language.If I understand correctly, they're standard in C99.

---

### Post by Tony Flury on 2010-03-08
quanganht : unless you are working on a very very memory limited system - like a mini embedded system, why are you worried specifically about a few extra bytes of padding around a structure - unless you are generating millions of them.

---

### Post by nvteighen on 2010-03-09
> **Tony Flury said:**
> quanganht : unless you are working on a very very memory limited system - like a mini embedded system, why are you worried specifically about a few extra bytes of padding around a structure - unless you are generating millions of them.

+1

Really, having a 24 bytes size struct is not such a big deal in a desktop computer. What should bother you is the usefulness of your structure, rather than the details of how it is laid on memory. So, if those 24 bytes is what you really need, just use them and forget it.

You should worry about this stuff only in the case of embedded programming or other limit cases.

---

### Post by Some Penguin on 2010-03-09
> **Tony Flury said:**
> quanganht : unless you are working on a very very memory limited system - like a mini embedded system, why are you worried specifically about a few extra bytes of padding around a structure - unless you are generating millions of them.

If the way the structures were packed and if the byte orderings were consistent across somebody's target platforms, it'd be easier to write very succinct, very quick (if brittle!) code for loading and storing fixed-length structures.  One could simply specify the memory address of a structure and treat it as a char* for a read() call to populate or a write() call to send.

However, C doesn't provide such guarantees, so unless you're not needing to trade data between heterogeneous systems, you at least need to care about sizes and orderings if you're going with a binary format.

---

### Post by Lux Perpetua on 2010-03-09
> **nvteighen said:**
> +1

Really, having a 24 bytes size struct is not such a big deal in a desktop computer. What should bother you is the usefulness of your structure, rather than the details of how it is laid on memory. So, if those 24 bytes is what you really need, just use them and forget it.

You should worry about this stuff only in the case of embedded programming or other limit cases.There's another possibility: I think the OP probably wanted to represent binary data directly as a C struct. For example, imagine reading some raw data from a disk. That might be a piece of filesystem metadata which has a specific format and might be represented informally as a struct, and one might try to take that to the next step by fread()ing the data directly into a literal C struct. Unfortunately, there's nothing in ANSI C that lets you do this, since you can't make any guarantees about how a struct with a particular declaration will actually be laid out in memory; there's no way (in ANSI C) to make sure it matches the actual data format.

---

### Post by nvteighen on 2010-03-10
> **Lux Perpetua said:**
> There's another possibility: I think the OP probably wanted to represent binary data directly as a C struct. For example, imagine reading some raw data from a disk. That might be a piece of filesystem metadata which has a specific format and might be represented informally as a struct, and one might try to take that to the next step by fread()ing the data directly into a literal C struct. Unfortunately, there's nothing in ANSI C that lets you do this, since you can't make any guarantees about how a struct with a particular declaration will actually be laid out in memory; there's no way (in ANSI C) to make sure it matches the actual data format.

Yes, you're right. But anyway, you can always create a function which segmentally reads that data and uses the struct's interface to fill that same struct. It's longer, but that is guaranteed to succeed!

---


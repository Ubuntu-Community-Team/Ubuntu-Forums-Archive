---
title: "Read from a specific memory address or offset"
date: 2008-07-26
forum: Programming Talk
---

### Post by loganwm on 2008-07-26
I've got a binary file loaded into memory, and I know which data inside the file I'm attempting to access, and I need to know how I can read the data of a specific address in memory.

I know where the file is loaded into memory (in a byte array) but I want to read at a specific offset from there?

any help?

---

### Post by ceclauson on 2008-07-26
If I'm understanding you correctly, it sounds like you just want to cast the pointer to char pointer (or whatever unit you know the offset in terms of), and then use the array access operator to get the data.  This would be the idea:

```

void* rawPointer = getFileAddress();  //address in raw pointer
int dataOffset = getDataOffset(); //number of bytes into the file of the data
                                  //you need
char* addressAsCharP = (char*) rawPointer; //cast to char*
char data = addressAsCharP[dataOffset];    //get the data

```

I'm sort new to C myself, but I'm pretty sure this is right.

I'm assuming, of course, that you're programming in C or C++.  If it's asm, of course you'd just add the base address to the offset, and access the memory there.

Are you using objcopy? Is it a C/C++ project?  This info might help people to help you better.

Hope this was helpful,
-Cooper

---

### Post by nvteighen on 2008-07-26
(Ignore if your project is not in C)
Is there any reason not to use a (FILE *) pointer? You can use it to open binary files using fopen(const char *filename, "rb")... Then you'll probably have to use fread() to read.

It would be much easier, I think... unless you're doing something very low-level...

---

### Post by mike_g on 2008-07-26
In C you would generally us fseek:

[http://www.cplusplus.com/reference/clibrary/cstdio/fseek.html](http://www.cplusplus.com/reference/clibrary/cstdio/fseek.html)

the second paramater is the byte offset, the third sets the position to seek from: either the start, current pos, or nd of the file.

---

### Post by loganwm on 2008-07-26
> **nvteighen said:**
> (Ignore if your project is not in C)
Is there any reason not to use a (FILE *) pointer? You can use it to open binary files using fopen(const char *filename, "rb")... Then you'll probably have to use fread() to read.

It would be much easier, I think... unless you're doing something very low-level...

It's a simple emulator (very simple) so I'd say it is pretty low level.

I can't get on my work station quite yet but I'll test the theories and get back to you guys asap.

---

### Post by era86 on 2008-07-26
> **loganwm said:**
> I've got a binary file loaded into memory, and I know which data inside the file I'm attempting to access, and I need to know how I can read the data of a specific address in memory.

I know where the file is loaded into memory (in a byte array) but I want to read at a specific offset from there?

any help?

If I am understanding this question, you have the data loaded in memory and you want to read a specific segment of data using an offset.  I'm assuming the offset is in bytes, so just cast the buffer to a char * and access the offset?

:confused::confused: Or I could be completely off... ;)

---

### Post by loganwm on 2008-07-26
I found a much simpler way to do it using the hex offset of the data as the array index:
Ex:
memoryblock[0x14A]

I just need to figure out reading the bits at an address and changing em and I can begin implimenting opcodes.

---

### Post by era86 on 2008-07-26
You can set a different pointer to point to that address and read from there.  Does the data correspond to a specific type?  You could do a typecast and read the data from a struct, etc.

char * mp = &memoryblock[0x14A];
Type * tp = (Type *)mp;

Or something like that.  Not sure exactly.. ;)

---

### Post by loganwm on 2008-07-26
Any ideas as to how I can view the data that I obtained from an address in binary form (ex: 10010011) and change it in that form?

basically convert back and forth on the fly.

---

### Post by mike_g on 2008-07-26
In C you could open the file with fopen using "r+b" to read and write to a binary file. Like:
```
FILE *fp = fopen("filename", "r+b");
```
To read data in use fread, and to write use fwrite. And, as I said before fseek will help you move to where you want to get.

Edit: as for the binary/hex thing, they are just different representations for the same thing.

---

### Post by era86 on 2008-07-26
> **loganwm said:**
> Any ideas as to how I can view the data that I obtained from an address in binary form (ex: 10010011) and change it in that form?

basically convert back and forth on the fly.

You can type cast the data using pointers.  Remember, the data in the buffer doesn't change.  It doesn't actually convert.  You can use pointers to view the data differently.

---

### Post by mike_g on 2008-07-26
You should really cast the data to a char array, otherwise you can get endian problems.

---

### Post by loganwm on 2008-07-26
The entire ROM file is read into a char array named "memblock"

I access my specific data at specific offsets using memblock[offset] which returns the data.

I understand that all representations are the same, but I just want a simple way to view the individual bits.

---

### Post by mike_g on 2008-07-26
maybe something like:
```
void PrintBin(unsigned char byte)
{
    unsigned char mask = 128;
    for( ; mask; mask >>= 1)
    {
         putchar( (byte&mask)? '1': '0');
    }
}
```

---

### Post by loganwm on 2008-07-26
if that shows me the individual bits, is there an applicable method to use the bits as a numeric/hex/data/etc entry?

ex:
char mybyte = [enter bits as a number]

---

### Post by mike_g on 2008-07-27
Apparentluy theres an 0b specifier for binary in the GNU C language extensions. [http://gcc.gnu.org/onlinedocs/gcc/Binary-constants.html](http://gcc.gnu.org/onlinedocs/gcc/Binary-constants.html)
I have never used it myself. Using it might break your code if you try compile it with another compiler.

---

### Post by dribeas on 2008-07-27
> **loganwm said:**
> Any ideas as to how I can view the data that I obtained from an address in binary form (ex: 10010011) and change it in that form?

basically convert back and forth on the fly.

They are the same data, just two ways of presenting (as with hex/decimal). There are no builtin facilities for that, afaik. If it is for a user interface (the user has to type a string containing '0's and '1's then it is quite easy to create a couple of functions for the conversion by using bitwise operations ( & ).

If it is just to write constants inside your code, use hex, which is easy to convert mentally back and forth to binary.

---


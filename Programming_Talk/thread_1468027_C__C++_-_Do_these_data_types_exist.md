---
title: "C / C++ - Do these data types exist"
date: 2010-05-01
forum: Programming Talk
---

### Post by FinalShot on 2010-05-01
I come from windows, so I don't really know the differences.

[LIST]
[*]Byte
[*]Word
[/LIST]
If not, what is the equivalent types on linux.

---

### Post by MadCow108 on 2010-05-01
These types are non standard so it depends on the context what they mean.

what comes closest to a byte is the char (or int8_t)
char is defined to be the smallest addressable unit and has size 1.
This is a byte in almost all cases.

A word is more ambiguous. It is often the size of the dataword of the processor. In that case the size_t (unsigned) or ptrdiff_t (signed) types comes closest.
They are 4byte in 32 bit computers and 8 byte on 64 bit computers.

But often a word is just 4 byte, in that case it would be int32_t

To be sure what they mean in windows check to what they typedef to in the compiler/headers used to compile your windows program.

---

### Post by Quikee on 2010-05-01
A Word type in Windows as I remember should be 2 bytes long actually which means it is something like uint16_t.

---

### Post by MadCow108 on 2010-05-01
you seem to be correct.
here is a table of the windows types:
[http://msdn.microsoft.com/en-us/library/aa383751(VS.85).aspx](http://msdn.microsoft.com/en-us/library/aa383751(VS.85).aspx)
what I though of was the DWORD

unfortunately it is not listed in C99 exact width datatypes,so you should not copy the exact typedefs listed on that page but replace them with those in the stdint.h header

---


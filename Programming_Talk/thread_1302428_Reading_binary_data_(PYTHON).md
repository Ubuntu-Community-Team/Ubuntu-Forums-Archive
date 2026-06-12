---
title: "Reading binary data (PYTHON)"
date: 2009-10-27
forum: Programming Talk
---

### Post by cguy on 2009-10-27
Hi!
I am implementing the Shannon-Fano compression algorithm in Python and I am really confused on how to read a file as it is stored on the disk, byte by byte.

Does this chunk of code read properly?
```
def readSymbols():
    global totalSymbols
    totalSymbols = 0
    while oFileHandle.read(1) != '\n':
        oFileHandle.seek( oFileHandle.tell() - 1 )
        symbol = oFileHandle.read(1)
        totalSymbols += 1
        if symbol in distinct:
            distinct[symbol] += 1
        else:
            distinct[symbol] = 1
    return
```

--

How do I properly write in binary mode?
My current code
```
FileHandle.write( str(N) )
```
is wrong.

eg: if N==13 it will appear as 2 bytes on the disk: 1 and 3

---

### Post by lisati on 2009-10-27
I don't know a lot of Python, but suspect that "str" is converting to ASCII.

---

### Post by Bachstelze on 2009-10-27
For reading, just use read(), then ord() to convert to ASCII (decimal):

```

firas@itsuki ~ % dd if=/dev/urandom of=random.bin bs=1024 count=1
1+0 records in
1+0 records out
1024 bytes transferred in 0.000149 secs (6871948 bytes/sec)
firas@itsuki ~ % cat binread.py
f = open("random.bin", mode="r")
for i in range(10):
        char = f.read(1)
        print "%sth char is %s, ASCII code is %s" % (i, char, ord(char))

firas@itsuki ~ % python binread.py
0th char is ?, ASCII code is 63
1th char is &#65533;, ASCII code is 140
2th char is u, ASCII code is 117
3th char is &#65533;, ASCII code is 161
4th char is {, ASCII code is 123
5th char is &#65533;, ASCII code is 150
6th char is ?, ASCII code is 63
7th char is U, ASCII code is 85
8th char is G, ASCII code is 71
9th char is &#65533;, ASCII code is 172
```

For writing, You want chr():

```
firas@itsuki ~ % cat ascii.py
import sys

a = input("ASCII code? ")
sys.stdout.write(chr(a))
print
firas@itsuki ~ % python ascii.py
ASCII code? 35
#
```

---

### Post by cguy on 2009-10-27
But I have to write in the compressed file the array of distinct symbols and the number each symbol appears.
What if symbol "a" appears 300 times? 300 is not in the 0-256 range so I can convert it with chr.

It can be represented on two bytes, but how will I read these two bytes? How will I know that they go together to form the number 300 and that they don't represent two distinct numbers?

---

### Post by cguy on 2009-10-27
Oh I missed a thing:
the number of appearances of a symbol should be represented on 32 bits.

How can I write and read a number on 32 bits to/from a binary file?

EDIT:
I think I got it:
I transform the number into binary and then pad zeros to the left until the representation is on 32 bits. Then I take each 8 bit group, find out how much it is in decimal and the write its ascii in the file.

---

### Post by lisati on 2009-10-27
I think I blinked and missed something here. Surely the point of using a data compression algorithm is to "translate" a source data file into a form which uses *less* disk space: converting the binary data into ASCII can make it use *more* space. A binary value in the range 0x00 to 0xff (please excuse the "C" style representation) will use no more than 8 bits if preserved in binary, but will use up to 24 bits if represented in ASCII.

---

### Post by wmcbrine on 2009-10-27
1. Open the file in binary mode.

```
open(filename, "b")
```

This may not matter in Ubuntu, but it will in Windows.

2. Use the struct module to handle things other than characters.

```
import struct
# read an unsigned little-endian 4-byte integer from file "f"
rawnum = f.read(4)
num = struct.unpack('<I', rawnum)[0]
```

This looks verbose, but becomes less so when you read multiple values at once.

3. I have no idea what you're trying to do in the code in the first post.

---


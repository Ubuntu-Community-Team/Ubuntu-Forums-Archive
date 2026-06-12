---
title: "Python binary/hex output is wrong when written to file"
date: 2012-06-21
forum: Programming Talk
---

### Post by theLured on 2012-06-21
Hello, my hex output seems to be wrong when I output to file.

I'm trying to convert a string to it's hex value(not the literal value)
So I want to convert something like this '5ABB78FF2C' to its hex '\x5A\xBB\x78\xFF\x2C'

Here's my code
```
import binascii

hex_string = 'A1B2C3D4'
# Convert to actual hex
hex_string = binascii.a2b_hex(hex_string)

print repr(hex_string)
print
hex_file = open('hex-output.bin', 'wb')

hex_file.write( hex_string )
hex_file.close()
```

The result of running the program
```
$ ./tester.py
'\xa1\xb2\xc3\xd4'

$ hexdump hex-output.bin
0000000 b2a1 d4c3
0000004
```

I want hexdump to look like this
```
$ hexdump hex-output.bin
0000000 a1b2 c3d4
0000004
```

I'm not sure what's happening, but writing to the file seems to be swapping the hex around.
repr() shows the correct order that I want.

Any ideas?

---

### Post by Tony Flury on 2012-06-21
> **theLured said:**
> Hello, my hex output seems to be wrong when I output to file.

I'm trying to convert a string to it's hex value(not the literal value)
So I want to convert something like this '5ABB78FF2C' to its hex '\x5A\xBB\x78\xFF\x2C'

Here's my code
```
import binascii

hex_string = 'A1B2C3D4'
# Convert to actual hex
hex_string = binascii.a2b_hex(hex_string)

print repr(hex_string)
print
hex_file = open('hex-output.bin', 'wb')

hex_file.write( hex_string )
hex_file.close()
```

The result of running the program
```
$ ./tester.py
'\xa1\xb2\xc3\xd4'

$ hexdump hex-output.bin
0000000 b2a1 d4c3
0000004
```

I want hexdump to look like this
```
$ hexdump hex-output.bin
0000000 a1b2 c3d4
0000004
```

I'm not sure what's happening, but writing to the file seems to be swapping the hex around.
repr() shows the correct order that I want.

Any ideas?

What happens when you read the data back out of the file - is it in the right order ? could it be that hexdump is swapping something when displaying ?

---

### Post by theLured on 2012-06-21
Yes, I believe you are right.
If I view it in ghex, the data looks like 'a1 b2 c3 d4'

I can also use 'hexdump -C' to get the proper output.
Thanks!!

```
$ hexdump hex-output.bin 
0000000 b2a1 d4c3                              
0000004

$ hexdump -C hex-output.bin 
00000000  a1 b2 c3 d4                                       |....|
00000004
```


I assumed I made a mistake in my code, but it's just the way hexdump displays it.

Thank you!!!!

---

### Post by ofnuts on 2012-06-21
> **theLured said:**
> 
I assumed I made a mistake in my code, but it's just the way hexdump displays it.

By default hexdump list data by packets of two bytes interpreted as integers, and you are on a little-endian system (least significant byte at the lowest address).

---


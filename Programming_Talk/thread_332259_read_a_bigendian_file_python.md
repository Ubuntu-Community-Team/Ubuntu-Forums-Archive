---
title: "read a bigendian file python"
date: 2007-01-05
forum: Programming Talk
---

### Post by Hairy_Palms on 2007-01-05
hi, im trying to read a 4 byte integer from a binary file, only trouble is, the file is in bigendian format and no matter what i try i cant seem to make python read it big endian, 

does anyone know how to read big endian files in python

---

### Post by gpolo on 2007-01-05
is there any chance you can send me this big-endian file ? or a sample big-endian file ?

---

### Post by gpolo on 2007-01-05
well, if it is just an 4 bytes integer you could do this:

from struct import unpack
file = open('file', 'rb')

be_int = file.read(4)

le_int = unpack('>L',  be_int)  # > for big endian, < for little endian

---

### Post by Hairy_Palms on 2007-01-05
im willing to bet you have a bigendian file on your computer :) any mp3 is big endian, (or at least the metadata is)

---

### Post by gpolo on 2007-01-05
it gets complicated to read variable lenght data in big endian format while im using a little endian machine, but if you know the lenght of data, like int 4 bytes it is a lot easier. Did you try the solution I told you ?

---

### Post by Hairy_Palms on 2007-01-05
i get a > global name 'unpack' is not defined error :( is there something i need to import?

---

### Post by gpolo on 2007-01-05
first line: from struct import unpack

---

### Post by Hairy_Palms on 2007-01-05
ah yeah sorry, my bad missed it :)

still get an erro though,

>  File "basictreeview (copy).py", line 312, in add_event
    self.import_meta_info(lotsafiles.pop())
  File "basictreeview (copy).py", line 268, in import_meta_info
    title = self.import_id3v2_title(data)
  File "basictreeview (copy).py", line 216, in import_id3v2_title
    le_int = unpack('>',last)
struct.error: unpack str size does not match format
thx 4 ur help btw


the code is this 

> f = open(data, "rb")	
	from struct import unpack
	f.seek(6)
	x = 0
	last = f.read(4)
	le_int = unpack('>',last)
	print last

---

### Post by gpolo on 2007-01-06
that is why I asked you to send me the file, I just can't guess at what position your integer would be.

---

### Post by Hairy_Palms on 2007-01-06
it is an mp3 file, its always at the same place because of the specification, cant really send an mp3 file

read from the ver start of the file

first 3 bytes always = "ID3"
next 2 bytes will be "0n 00" where n is a number from 1 to 4
next byte needs to be read as binary for flags
next 4 bytes are the size of the metadata, in this case its "00 00 08 67" which when read big endian is 2151 (right) in little endian is 1728577536 (not right)
ive verified in a hex editor too

---

### Post by gpolo on 2007-01-06
i didn't know it was a mp3 file ;) I thought you were just joking when you told me about them

---

### Post by dwblas on 2007-01-06
I'm pretty sure you can use Python's array to do that: from [http://effbot.org/librarybook/array.htm](http://effbot.org/librarybook/array.htm)```
# File: array-example-4.py

import array

def little_endian():
    return ord(array.array("i",[1]).tostring()[0])

if little_endian():
    print "little-endian platform (intel, alpha)"
else:
    print "big-endian platform (motorola, sparc)"

##----------  FYI  - to find out what any system is
# File: sys-byteorder-example-1.py

import sys

# available in Python 2.0 and later
if sys.byteorder == "little":
    print "little-endian platform (intel, alpha)"
else:
    print "big-endian platform (motorola, sparc)"
```With the array, the "i"=integer=32 bits = 4 bytes on an intel 32 bit machine.  I have a note that says that '>u2' is  big-endian, unsigned integer, 2 bytes.  Check the docs for all the options.   [http://docs.python.org/lib/module-array.html](http://docs.python.org/lib/module-array.html)  Also, an array file read is```

import array
a1 = array.array('H')                                                           
fp = file(filename, 'rb')   ## the binary part is necessary if you don't know already                                
a1.fromfile(fp, 1)  ## the '1'=read one array's  length=2 bytes in this case, "H'=short int
```
I think you can also use something like:
import struct
(Integer,) = struct.unpack('l', f.read(4))
but I have never used it so don't know about endian-ness of it

And I didn't check this for typos so you'll have to correct any errors

---


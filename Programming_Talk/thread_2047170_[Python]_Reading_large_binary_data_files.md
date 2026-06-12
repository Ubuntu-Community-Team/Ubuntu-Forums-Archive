---
title: "[Python] Reading large binary data files"
date: 2012-08-24
forum: Programming Talk
---

### Post by Erdaron on 2012-08-24
I am working on a data analysis script that is supposed to read in a large (hundreds of megabytes) data file. The data are encoded as a single row of unsigned 16-bit integers (uint16 ieee-le).

For example, the following successfully reads a single value:
```
>>> struct.unpack_from('H', '\xae\x7f')
(32686,)
```

I am trying to figure how to read the whole file. Numpy has a function numpy.fromstring() that can correctly interpret a string, but I can't seem to actually read in the whole file. If I open the file and the use the .read() method (without a buffer size - so it should read everything), it stops after just a few hundred bytes (whereas the whole file, in this case, is 250 MB).
```
>>> f1 = open('T_03.dat')
>>> a1 = f1.read()
>>> len(a1)
488
>>> a1
'\x98}\xb9}\x11~b~Z~\xcf~&\x7f\x92\x7f\x9c\x7f\x01\x80^\x80\x8c\x80\xa3\x80M\x81\x14\x81\x82\x81\xa5\x81\xd1\x81\x00\x82(\x82!\x82L\x82C\x82\x96\x82\x95\x82\xab\x82;\x82c\x82,\x82V\x82Z\x82-\x82\xfd\x81\xc5\x81\x10\x82\x04\x82\xd7\x81\xff\x81\x1f\x82B\x82?\x82e\x82>\x82]\x82\r\x82\x1b\x82\xf2\x81\x04\x82\xcf\x81\xb3\x81\xc7\x81\x96\x81p\x81\x18\x81+\x81\xb5\x80r\x80#\x80\x12\x80\xe8\x7f\x85\x7fB\x7f>\x7f\x85~:~\'~\xdc}\xb7}\n}\x10}\xae|h|\x1e|\r|\xd1{\xbc{\xb3{\xcd{\xcb{\xd3{\xd8{\xe1{\xe5{\x04|:|\x9b|u|\xe9|\xeb|3}\r}m}]}\xcc}\xed}N~n~\x97~\xaa~\xc4~\x14\x7f+\x7f\x8b\x7f\xe4\x7f\xea\x7f1\x80I\x80r\x80X\x80\xa6\x80n\x80<\x80c\x80F\x80?\x80!\x80\xd4\x7f\x87\x7fE\x7f\x1f\x7f(\x7f\xf0~\n\x7f\x13\x7f\x01\x7f\xe5~\xea~-\x7f,\x7f\x15\x7f\x16\x7f5\x7fa\x7f\xad\x7f\x94\x7f\xc3\x7f\x12\x80\xfd\x7f"\x80\xc7\x7f\xd8\x7f\xcf\x7fn\x7f\xc4\x7f\xb7\x7fc\x7fZ\x7f=\x7f\x1e\x7f\xd8~\x0b\x7f\xa3~q~\x90~\x83~\xef}\xec}\xe5}i}?}\x05}F}\xe9|\xc8|\xc5|\x88|G|\x87|\x96|r|\x81|\xf0|\x01}$}\xaa}\xd6}\xd0}\xdf}\x80~\x9c~\xfa~\xe1\x7f\r\x80\x87\x80\n\x81\xbf\x81\r\x82/\x82\xab\x82+\x83A\x83\xd9\x83}\x84}\x84\xf2\x84j\x85\xf2\x85\x06\x86[\x86\x9b\x86\xf9\x86E\x87\x8c\x87\xe1\x87V\x88W\x88\xbb\x88\xb3\x88\xf3\x88\'\x89E\x89/\x895\x89\x14\x89\x14\x89\xe3\x88\xe4\x88\xa7\x88Z\x881\x88\xf4\x87\xb0\x87p\x87\x18\x87k\x86\xfd\x85\xd9\x85b\x85{\x85\xae\x84w\x84\xe0\x83\xa6\x837\x83\xb7\x82\xb6\x82\xad\x82r\x82R\x82\xe2\x81\xed\x81\xed\x81\r\x82\xe8\x81'
```
At this point I am stuck. I'm not really sure what his happening that is causing Python to stop reading the file and how to get around that.

---

### Post by Erdaron on 2012-08-24
Never mind, I'm an idiot. Apparently I just needed to add the binary flag 'b' to the .read() method. The correct call to read the file:

```
>>> f1 = open('T_03.dat', 'rb')
>>> a1 = f1.read()
>>> len(a1)
256000000
```

'rb' opens the file to read as binary.

All is well.

---

### Post by MadCow108 on 2012-08-24
if the file are really just binary uint16's you can read it in directly with numpy.fromfile or if saved from numpy with numpy.load
you can also memory map it with mmap (or numpy.memmap, or numpy.load) which is very useful if you only access part of the data, saves you a bunch of copying (assuming its saved in the correct endianness) and makes memory management easier (on 64 bit cpu's you can just memory map terabytes of data and let the kernel do the memory management)

---

### Post by Erdaron on 2012-08-24
Of course. Thank you :). It's embarrassing that I somehow overlooked its function, even though I found its cousin.

---


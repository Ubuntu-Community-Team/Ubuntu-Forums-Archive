---
title: "Python 3 map and lambda help"
date: 2013-04-13
forum: Programming Talk
---

### Post by fret669 on 2013-04-13
Hello,

I am trying to build an eeprom programmer. I have data from the eeprom in a text file, but need to convert the characters in this file to a bin file.
I have successfully done this with a code snippet I found online, but it is written for python 2. My larger application to read, erase, and burn the eeprom is written in python 3.
I have read about changes to lambda and map in python 3 (which I was not familiar with to begin with) :confused: , but cannot see what needs to be changed to make this work.

```


out_file = open("newBin.bin","w")
in_file = open("temp.tmp","r")
lines = in_file.readlines()

for line in lines:
    bytes = map(lambda x:int(x,16), line.split())
    for b in bytes:
        out_file.write(chr(b))

```

This returns a bunch of useless data to my bin file, and makes it about 30kb larger that it should be.
Any help is much appreciated. Thank you.

---

### Post by schragge on 2013-04-13
Try to open out_file in binary mode and write bytes into the file rather than characters
```

out_file = open("newBin.bin", "wb")
in_file = open("temp.tmp")
lines = in_file.readlines()

for line in lines:
    out_file.write(bytes([int(b, 16) for b in line.split()]))

```

---

### Post by fret669 on 2013-04-13
Worked like a charm. Thanks a ton. :P

---


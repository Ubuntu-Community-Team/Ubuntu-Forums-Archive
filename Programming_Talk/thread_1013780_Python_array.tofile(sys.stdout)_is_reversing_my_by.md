---
title: "Python: array.tofile(sys.stdout) is reversing my bytes for no good reason"
date: 2008-12-17
forum: Programming Talk
---

### Post by Drostie on 2008-12-17
Hey guys. I have a python script that looks generally like this:

```
bytearray = array.array('B')

# (In here is code that adds stuff to the bytearray. 
# It's not important for this post, I don't think.)

#debug info to stderr
for item in bytearray:
    sys.stderr.write(str(item) + ", ")
sys.stderr.write("\n")

#output to stdout
bytearray.tofile(sys.stdout)
```

But here's what it looks like in practice:

```
$ cat md5 | ./hash2bin.py > f
160, 15, 191, 71, 192, 111, 71, 193, 18, 16, 143, 201, 153, 36, 112, 61,
$ hexdump f
0000000 0fa0 47bf 6fc0 c147 1012 c98f 2499 3d70
0000010
```

Do you see the problem here? The bytearray.tofile method is reading two elements of the array at a time for no good reason, and is appending them to the file in reverse order. Looking in the array.array reference, I see a bytearray.byteswap() method, but that changes nothing.

What the heck is happening here? And why do I have to hack around it? (Is bash's greater-than-symbol acting up or something?)

---

### Post by unutbu on 2008-12-17
```
hexdump f
```

shows output which reads well from left to right on big endian systems. 
```

hexdump -C f 
```
or ```

xxd f 
```

shows output which reads well from left to right on little endian systems.

Intel-based systems are little endian systems.

There is nothing wrong with the data in f. It is just a bunch of 0's and 1's as far as hexdump is concerned. "hexdump f" chose to interpret those 0's and 1's using the wrong byte ordering and hence the garbled output.

See
[http://en.wikipedia.org/wiki/Endianness](http://en.wikipedia.org/wiki/Endianness)
[http://www.noveltheory.com/TechPapers/endian.asp](http://www.noveltheory.com/TechPapers/endian.asp)

---

### Post by Drostie on 2008-12-17
Ah, I hadn't thought that hexdump would do a big-endian reinterpretation of binary files by default. My mistake.

Thank you so much!

---


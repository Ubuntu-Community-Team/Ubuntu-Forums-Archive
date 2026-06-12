---
title: "Python writing hex/bytes to file"
date: 2010-12-06
forum: Programming Talk
---

### Post by v1rati on 2010-12-06
Hi,

Right now I'm trying to write a list of hex values (strings) to a disk file in Python 3.1.
```
['AB', 'EC', 'CD', 'AB', 'ED', 'EB', 'DB', 'AB', 'EC']
```

I tried adding \x before each one and then writing it to file, but it's writing it literally as '\xAB\xEC\xCD\xAB\xED\xEB\xDB\xAB\xEC'.

What do I need to do to write it as bytes?

Thanks.

---

### Post by Vaphell on 2010-12-06
[http://linux.byexamples.com/archives/478/python-writing-binary-file/](http://linux.byexamples.com/archives/478/python-writing-binary-file/)

---

### Post by wmcbrine on 2010-12-07
You might want to post more of your code to illustrate exactly what you've tried.

---

### Post by v1rati on 2010-12-07
> **Vaphell said:**
> [http://linux.byexamples.com/archives/478/python-writing-binary-file/](http://linux.byexamples.com/archives/478/python-writing-binary-file/)
I tried that an it spat out:
```
TypeError: must be bytes or buffer, not str
```
> **wmcbrine said:**
> You might want to post more of your code to illustrate exactly what you've tried.
```
bitlist = ['AB', 'EC', 'CD', 'AB', 'ED', 'EB', 'DB', 'AB', 'EC']
for bit in bitlist:
    bitstring += r'\x' + bit
bitout = open('bitout', 'wb')
bitout.write(bitstring)
```

---

### Post by DaithiF on 2010-12-07
the binascii module can help:
```

import binascii
bitlist = ['AB', 'EC', 'CD', 'AB', 'ED', 'EB', 'DB', 'AB', 'EC']
bytes = binascii.a2b_hex(''.join(bitlist))
bitout.write(bytes)
```

---

### Post by ssam on 2010-12-07
if those byte represent values you may find [http://docs.python.org/library/struct.html](http://docs.python.org/library/struct.html) useful

---

### Post by wmcbrine on 2010-12-08
> **v1rati said:**
> ```
bitlist = ['AB', 'EC', 'CD', 'AB', 'ED', 'EB', 'DB', 'AB', 'EC']
for bit in bitlist:
    bitstring += r'\x' + bit
bitout = open('bitout', 'wb')
bitout.write(bitstring)
```So, what you're doing here is creating strings that start with a literal backslash. These are *not* then evaluated into byte values. (Think about it -- at what point would that happen?)

You might try something more like this:

```
for bit in bitlist:
    bitstring += chr(int(bit, 16))
```

---


---
title: "Quick problem from a python noob"
date: 2009-05-19
forum: Programming Talk
---

### Post by shipitkthx on 2009-05-19
Ok im just getting started learning python, i've been going through the tutorial from Python.org

In of the examples i'm trying to use read() and readline() and both of them return the following:

```
>>> f.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python3.0/io.py", line 1728, in read
    decoder.decode(self.buffer.read(), final=True))
  File "/usr/lib/python3.0/io.py", line 666, in read
    self._unsupported("read")
  File "/usr/lib/python3.0/io.py", line 322, in _unsupported
    (self.__class__.__name__, name))
io.UnsupportedOperation: BufferedWriter.read() not supported
>>> f.readline()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "/usr/lib/python3.0/io.py", line 1817, in readline
    while self._read_chunk():
  File "/usr/lib/python3.0/io.py", line 1563, in _read_chunk
    input_chunk = self.buffer.read1(self._CHUNK_SIZE)
AttributeError: 'BufferedWriter' object has no attribute 'read1'
```

I've searched everywhere for this and I can't figure it out. Help?

---

### Post by regomodo on 2009-05-19
#

---

### Post by Tony Flury on 2009-05-19
you need to open the file first :

[http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files](http://docs.python.org/tutorial/inputoutput.html#reading-and-writing-files)

Edit : 

There is something else going on here - so context would be useful : 

if f is not defined you get the error :
```

>>> f.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'f' is not defined

```

If f is defined (for example a string) - but not a file - then the error is :
```

>>> f.read()
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
NameError: name 'f' is not defined

```

I have experimented a bit with other things, closed files, files open for writing etc, but i cannot reproduce the error that you get.

---

### Post by Bodsda on 2009-05-19
This bit confuses me
```
AttributeError: 'BufferedWriter' object has no attribute 'read1'
```

that error should only occur if your trying to use 
```
something.read1()
```

which he isnt.

Although, this may be worth a read [http://bugs.python.org/issue4579](http://bugs.python.org/issue4579)

---

### Post by Tony Flury on 2009-05-19
Reading that - it looks like he is using python 3 - my installation is 2.5 (or is it 2.6) - and that he has opened the file for writing - and not reading.

---


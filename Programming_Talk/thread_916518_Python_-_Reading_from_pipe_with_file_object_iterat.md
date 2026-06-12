---
title: "Python - Reading from pipe with file object iterator"
date: 2008-09-11
forum: Programming Talk
---

### Post by Endolith on 2008-09-11
I've got syslog writing to a named pipe, and I'm trying to read it line-by-line in Python.  This works, printing out each line as it comes:

```
f = open("test_pipe")
while True:
    line = f.readline()
    print line,
```The [recommended method]("http://docs.python.org/lib/bltin-file-objects.html") is to use a file as an interator, but this does not work.  It dumps out all the lines at once only when I restart syslog (presumably because it's sending an EOF):

```
f = open("test_pipe")
for line in f:
    print line,
```Whyyyy?


According to [PEP 234 - Iterators]("http://www.python.org/dev/peps/pep-0234/"), these are equivalent:

A:```
while 1:
    line = file.readline()
    if not line:
        break
    ...
```B:```
for line in iter(file.readline, ""):
    ...

```C:```
for line in file:
    ...
```So I really don't understand why A and B work on a pipe that has been sent newlines and then flushed, while C only works when the pipe has been closed.

---

### Post by Endolith on 2008-09-12
Aha.   The last method does return values without closing the file, but only if I've sent a large number of lines.  This behaves the same way (doesn't work):

```
for line in file("pipe"):
    print line,
```

I guess open() uses the file() type, so there isn't much difference here.

Is this some kind of pre-buffering problem?  This doesn't work, either:

```
for line in file("pipe","r",1):
    print line,
```

Where 1 is buffering:

```
If the buffering argument is given, 0 means unbuffered, 1 means line
buffered, and larger numbers specify the buffer size.

```

It also doesn't work if I open both for reading and writing with 1.

Nor does this:

```
for line in f.readlines():
    print line,
```

even though this should be equivalent to 

```
for line in iter(f.readline, ""):
    print line,
```

which does work.

---

### Post by Endolith on 2008-09-12
Actually, no.  ```
for line in f.readlines()
``` would read in the whole file first (or a large chunk of the file?), and *then* split it into a list with an element for each line, while ```
for line in iter(f.readline(), "")
``` reads in one character at a time until it hits a new line, which iter then makes into the first item in a list?  Then it keeps reading until it hits a newline to make the next element, and so on, until it hits the EOF, which will cause readline() to return "", at which point it quits.  If the EOF doesn't exist yet (pipe not closed), and it's read all the characters but not found a newline yet, it just sits and waits?

So that would explain why I'm seeing this.  So does "for line in f:" mean "read in the entire file and then split into a list with an element for each line"?

---

### Post by days_of_ruin on 2008-09-12
> **Endolith said:**
> I've got syslog writing to a named pipe, and I'm trying to read it line-by-line in Python.  This works, printing out each line as it comes:

```
f = open("test_pipe")
while True:
    line = f.readline()
    print line,
```The [recommended method]("http://docs.python.org/lib/bltin-file-objects.html") is to use a file as an interator, but this does not work.  It dumps out all the lines at once only when I restart syslog (presumably because it's sending an EOF):

```
f = open("test_pipe")
for line in f:
    print line,
```Whyyyy?



Maybe you are not closing the file properly in the program that writes to it.

---

### Post by Endolith on 2008-09-12
> **days_of_ruin said:**
> Maybe you are not closing the file properly in the program that writes to it.

I don't have any control over the program that writes to the pipe, and it's a pipe, so it's not supposed to be closed, is it?  Programs continuously write to a pipe without closing it.

---

### Post by ghostdog74 on 2008-09-15
See [here](http://groups.google.com.sg/group/comp.lang.python/search?hl=en&group=comp.lang.python&q=named+pipe+question&qt_g=Search+this+group)  similar

---

### Post by Endolith on 2008-09-15
> **ghostdog74 said:**
> See [here]("http://groups.google.com.sg/group/comp.lang.python/search?hl=en&group=comp.lang.python&q=named+pipe+question&qt_g=Search+this+group")  similar

Yes, I've read that.  It's helpful, but doesn't answer my question.

---

### Post by tmcg on 2008-09-17
I entered the same problem today. The reason seams to be that the next method on files uses an internal buffer (see python doc for file.next()) and only returns if the pipe is closed.
The following simple custom iterator using file.readline() internaly works fine for me:
```
class FileIterator:
    def __init__(self, file):
        self.file = file

    def __iter__(self):
        return self

    def next(self):
        l = self.file.readline()
        if l=='':
            raise StopIteration
        return l


f = file('pipe', 'r')
for l in FileIterator(f):
    print l,
f.close()

```

---

### Post by Endolith on 2008-09-17
> **tmcg said:**
> I entered the same problem today. The reason seams to be that the next method on files uses an internal buffer (see python doc for file.next())

[http://www.python.org/doc/2.5/lib/bltin-file-objects.html](http://www.python.org/doc/2.5/lib/bltin-file-objects.html)

> In order to make a for loop the most efficient way of looping over the lines of a file (a very common operation), the next() method uses a hidden read-ahead buffer. As a consequence of using a read-ahead buffer, combining next() with other file methods (like readline()) does not work right.

> and only returns if the pipe is closed.

Or if there's enough data to fill the buffer?

> The following simple custom iterator using file.readline() internaly works fine for me:

Yeah, we really shouldn't have to implement our own classes for this, though.  Seems like a bug of shortsightedness to me.  I'm going to file a bug and see if it sticks.

---

### Post by tmcg on 2008-09-18
Following doc and PEP 234 the file iterator is intended to allow fast reading of files. To achive this it uses a buffer reading larger blocks at one.
If you want to read lines from a pipe as soon as they are present you need to read byte by byte to check for newline (as readline() does). However this would slow down reading usual files.
Hence the only bug I can see is that file iterator completely block until the pipe is closed. But even if this is fixed it would be unsuitable due to the use of a buffer.
A nice solution would be to be able to turn of the buffer or to adjust its size.

---

### Post by Endolith on 2008-09-18
> **tmcg said:**
> Following doc and PEP 234 the file iterator is intended to allow fast reading of files. To achive this it uses a buffer reading larger blocks at one.

I don't think that's right.  The file iterator is intended to simplify and "pythonify" reading from files, not speed it up.  The speed up and internal hidden buffer are merely implementation details that the high-level programmer doesn't have to worry about.

> If you want to read lines from a pipe as soon as they are present you need to read byte by byte to check for newline (as readline() does). However this would slow down reading usual files.

I'm not sure that's necessarily true.  Certainly the underlying C routines can be optimized depending on the type of file being read from.  Reading a pipe "character by character" shouldn't be any slower than reading in a buffer, should it?  Aren't pipes stored in memory?  Isn't memory read in chunks anyway, depending on the hardware?

Python emphasizes having a minimalist command set: "There should be one-- and preferably only one --obvious way to do it."  The "for line in f" construct is The One Pythonic Way to iterate through files, and the older ways like xreadlines that do the same thing are deprecated.

As Python is a very high-level language, there's no reason to presume that a construct for iterating through the lines of a file will have a hidden internal read-ahead buffer.  This is not implicit in the command; it's just an optimization to the C implementation added to make the code go faster, on the assumption that it would be reading actual physical files with data already in them.  But this assumption does not work for other file-like objects like pipes that are not pre-filled with data, so I would consider this to be a bug.  Details like this should be handled automatically by the low-level subsystems, not by the programmer.

> Hence the only bug I can see is that file iterator completely block until the pipe is closed. But even if this is fixed it would be unsuitable due to the use of a buffer.

That's the way pipes are supposed to work, if I understand correctly.  Until the pipe is closed, it should expect more data, and so should block and wait for more.  It should only stop iterating when it reaches the end of the file, which is equivalent to the sending program closing the pipe(?)
 
> A nice solution would be to be able to turn of the buffer or to adjust its size.

Why can't the underlying C implementation test what kind of file object it's looking at and optimize accordingly?  Read already-existing files with a fast buffer, and read unclosed pipes character by character?  As long as the outcome is to iterate through the lines of the file-like object, and this is what the programmer has asked for, then it's behaving correctly.

---

### Post by Endolith on 2008-09-18
[http://bugs.python.org/issue3907](http://bugs.python.org/issue3907)

---

### Post by Endolith on 2008-09-24
Fixed in future versions: [http://bugs.python.org/issue3907](http://bugs.python.org/issue3907)

---


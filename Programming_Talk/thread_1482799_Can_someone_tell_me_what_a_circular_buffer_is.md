---
title: "Can someone tell me what a circular buffer is?"
date: 2010-05-14
forum: Programming Talk
---

### Post by s3a on 2010-05-14
Can someone tell me what a circular buffer is in a summarized and general form? (I believe buffer is a temporary storage location to store data in but I don't know what the circular part means)

Any input would be greatly appreciated!
Thanks in advance!

---

### Post by mmix on 2010-05-14
[http://en.wikipedia.org/wiki/Circular_buffer](http://en.wikipedia.org/wiki/Circular_buffer)

[http://www.boost.org/doc/libs/1_43_0/libs/circular_buffer/doc/circular_buffer.html](http://www.boost.org/doc/libs/1_43_0/libs/circular_buffer/doc/circular_buffer.html)

---

### Post by soltanis on 2010-05-14
[http://lmgtfy.com/?q=circular+buffer](http://lmgtfy.com/?q=circular+buffer)

Also called a "ring buffer", it's a buffer with a fixed size that "wraps around", so that if you attempt to write past the end of the buffer, it is written back to the front.

Take this example of a 6 byte buffer:

```

| 0 | 1 | 2 | 3 | 4 | 5 |
  ^-- write pointer

```

If I write 4 bytes it behaves as a normal buffer:

```

| a | b | c | d |   |   |
                  ^-- write pointer

```

Now if I write 4 more bytes, the two bytes that go past the end are written back to the front:

```

| g | h | c | d | e | f |
          ^-- write pointer

```

---


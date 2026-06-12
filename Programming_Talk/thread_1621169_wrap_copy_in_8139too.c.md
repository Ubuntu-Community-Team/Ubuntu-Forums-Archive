---
title: "wrap copy in 8139too.c"
date: 2010-11-13
forum: Programming Talk
---

### Post by tapas_mishra on 2010-11-13
I came across a function wrap_copy on [http://lxr.free-electrons.com/source/drivers/net/8139too.c](http://lxr.free-electrons.com/source/drivers/net/8139too.c)
Can some one help to understand what it is doing.
What I  interpret  it is that some how the person is tying to copy
payload from DMA to sk buffer.Is this interpretation correct?
What exactly are we trying to achieve via wrap_copy function call?

---

### Post by VernonA on 2010-11-15
The function is copying a block of data into a circular array. In other words, data is copied in at position 'offset', and if it reaches the end of the target array, copying carries on at position 0. The code first looks to see if the amount of data to copied will fit between 'offset' and the end of the array. If it does, fine, a simple copy will suffice. Otherwise, the first chunk of data must be copied at offset, and what's left goes in at 0.

---

### Post by tapas_mishra on 2010-11-15
Hi,
many thanks for your reply.I understood the explanation given by you.
 Can you give me some link which you recommend I should be reading for such stuff or some thing that you recommend me to search and understand.

---

### Post by VernonA on 2010-11-15
This is a pretty common programming technique, so a Google for "ring buffer" or "circular buffer" will give you plenty of sites. To start with try [http://en.wikipedia.org/wiki/Ring_buffer]("http://en.wikipedia.org/wiki/Ring_buffer") on Wikipedia.

---


---
title: "Socket programming: Read unknown byte size"
date: 2008-09-08
forum: Programming Talk
---

### Post by rustybar on 2008-09-08
Hi,

I like to read some binary data using tcp. However, the size of these binary data varies and thus I cannot specify a fixed size of the data in my receiver size. Is that a way to read unknown size data?

Thanks.

---

### Post by tinny on 2008-09-08
What language are you developing with?

Does the application at the other end of the socket close the socket once it is done?

Or perhaps you can assume that if you have not received any data for X milliseconds then the message has been sent.

What do you know about the other application? Are you in control of its source?

---

### Post by rustybar on 2008-09-08
I'm using C to do the socket programming. 

The source will keep on pumping the data as long as you are connected to it and I can't control it.

The data can come as fast as at a sampling rate of 10 times per sec (10Hz) and at different size (but are small like a few Kb and varies about it).

The data is in binary format. Each time I want to write each individual data received into a file.

---

### Post by tinny on 2008-09-08
I would imagine that this sort of continuous stream data would be sent in frames. Each frame could be a sample, the frame would have a fixed header that states how many data bytes follow the header.

[Header][Data bytes][Header][Data bytes] etc....

This is just a guess (this is how id do it).

---

### Post by rustybar on 2008-09-09
emm.. no. the bytes sent are pure data without any header as they do provide logging of data at their side. Just that the streaming is for live updates.

---

### Post by Tony Flury on 2008-09-09
rustybar - are you in control of the s/w at the source?

If so i would suggest modifying the source code of the sender to include frame type structure as per tinny's suggestion.

Nearly ever communications protocls uses one of three possible methods : 
[LIST]
[*]Variable length with a header that contains a measure of the length of data
[*]Fixed length
[*]Variable length with some sort of unique start and end of frame markers
[/LIST]

---

### Post by Zugzwang on 2008-09-09
I'd strongly second Tony.

Since you are using TCP, data might get delayed (but arrives with guarantee). So in your setting, you have absolutely no way of chunking your data accordingly since you don't have control information about the data sizes and timing can't be used (reliably) either.

If data may get lost and the maximum data size is small enough, you might want to consider using UDP at the source.

---

### Post by The Cog on 2008-09-10
You want to put the separate chunks into separate files, or just stream it all into one file?

The former is easy. When you read a socket, it tells you how many bytes were read into the buffer and you just write that many bytes from the buffer to file.

The latter is not possible unless you read the stream contents and can somehow identify the boundaries between messages. Normally, a TCP stream of separate messages will use length headers or unique end-of-message markers to allow the reader to identify boundaries. This is neede because a TCP stream is "unformatted". Data written in separate write() calls will sometimes turn up in the same size chunks in the read() calls the other end, but it's not guaranteed. Chunks can be merged (especially if the first chunk encounters a network delay), chunks can be split, or both can happen.

Imagine trying to read separate records from a binary file on disk. The problem is the same. If the data doesn't contain the info needed to find the boundaries then the protocol design is faulty. Just hoping that the read()s will match the sizes of the write()s is unreliable and WILL produce occasional errors.

---


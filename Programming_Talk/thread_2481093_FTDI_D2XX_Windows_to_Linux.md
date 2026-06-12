---
title: "FTDI D2XX Windows to Linux"
date: 2022-11-18
forum: Programming Talk
---

### Post by tbnrc on 2022-11-18
Hi folks,

I've got a really simple application using FTDI's D2XX driver to run a USB UART in async bit bang mode to continuously read incoming data.

It's just always polling for a minimum number of incoming bytes, if quantity is met read entire receive buffer into memory, repeat.

My issue is that I originally wrote this in Windows. Each loop is completed in 2 milliseconds or less, with about 0.01% of loops straying out of range into the 2-2.5 millisecond zone. This was effectively perfect for my application.

However, I'm using Ubuntu on my server, which is where this application is meant to run. The problem is that using the exact same code, Linux is significantly slower. Effectively 1% of loops exceed 2 milliseconds, and I've seen peaks as high as 10 milliseconds. Even more oddly, when these peaks happen, it is usually in a pattern like below (in microseconds):

1500
1490
1550
5000
500
430
450
50
1500
1400

So on average a loop takes 1.5 milliseconds, but there will be times when there's a big lag spike on one sample, and a handful of subsequent samples go way faster than average before returning to normal.

I'm currently playing with the kernel. I tried the stock low latency kernel from the repository, but it didn't seem to have a clear effect.  It might have reduced the total number of loops that timeout from 1% to 0.7%, but it's not clear. I'm building a modified kernel with some optimizations for the Intel CPU I'm using, but I'm not optimistic.

I've read there's an ASYNC_LOW_LATENCY flag you can throw onto a serial port to improve performance, but the FTDI doesn't have a /dev/ttyUSB device associated with it when using the D2XX driver so I don't know how to proceed with that.

Does anybody know what it is about Linux that makes it slower than Windows reading this UART and is there anything I can do about it? Minimizing timeouts is kind of mission critical to me. I've even set real time priority for the thread running this code on a dedicated core and I am not seeing any improvement.

Any help would be appreciated.

---


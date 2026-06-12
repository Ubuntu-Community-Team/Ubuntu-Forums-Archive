---
title: "developing a server like Apache"
date: 2010-09-02
forum: Programming Talk
---

### Post by jamesbon on 2010-09-02
I have learned module programming on Linux Kernel and I can write a character device driver.
I want to learn how servers are developed on Linux such as an Apache server.What do I need to be able to do to be able to develop some thing like Apache.I am looking for relevant tutorials what I got from my search results were not very good results for example I got an article from slashdot.
[http://ask.slashdot.org/article.pl?sid=07/08/23/1447220](http://ask.slashdot.org/article.pl?sid=07/08/23/1447220).
If some one can point me to some tutorial where I should begin with or what exactly should I be searching then that would be great.

---

### Post by lordhaworth on 2010-09-02
The web security tutorials here are nice intro into some concepts:
[http://code.google.com/edu/courses.html](http://code.google.com/edu/courses.html)

The examples involve web servers (including a basic one with source code you can look at/test) and security is a major component of designing one. There are also some exercises.

I would also try 
[http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/](http://ocw.mit.edu/courses/electrical-engineering-and-computer-science/)

There are course notes on security and lots of other bits there.

I imagine someone will come along with something mre advanced shortly, but these will provide something to think about in the mean time

---

### Post by dwhitney67 on 2010-09-02
Undoubtedly you will require knowledge of socket programming.  Here's a popular reference:
[http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html](http://beej.us/guide/bgnet/output/html/singlepage/bgnet.html)

---

### Post by phrostbyte on 2010-09-02
The main "APIs" involved are POSIX threads and sockets.

---

### Post by myrtle1908 on 2010-09-02
Also nice to have an understanding of HTTP and the underlying TCP and IP protocols.

[http://en.wikipedia.org/wiki/Internet_Protocol_Suite](http://en.wikipedia.org/wiki/Internet_Protocol_Suite)

As an aside, you may be best starting with writing a basic HTTP server in a scripting language like perl or python (just to nail down the concepts) then move onto implementing the server and relevant protocols for real in a lower level lang like C.

---

### Post by Bachstelze on 2010-09-03
> **myrtle1908 said:**
> Also nice to have an understanding of HTTP and the underlying TCP and IP protocols.

[http://en.wikipedia.org/wiki/Internet_Protocol_Suite](http://en.wikipedia.org/wiki/Internet_Protocol_Suite)

As an aside, you may be best starting with writing a basic HTTP server in a scripting language like perl or python (just to nail down the concepts) then move onto implementing the server and relevant protocols for real in a lower level lang like C.

Or you could use your Python one for real. ;) With a web server, you'll be I/O bound way before the languages start making a difference performance-wise.

---

### Post by jamesbon on 2010-09-03
Thanks all for the links and tips.

---


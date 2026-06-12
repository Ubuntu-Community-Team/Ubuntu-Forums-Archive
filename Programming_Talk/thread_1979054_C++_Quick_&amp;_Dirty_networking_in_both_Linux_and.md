---
title: "C++ Quick &amp; Dirty networking in both Linux and Windows?"
date: 2012-05-12
forum: Programming Talk
---

### Post by compiz addict on 2012-05-12
There has been so many times where I would find this useful. What I want to do is write a server, which will request a plain-text file and receive/write it, and a client, which will send the plain-text file upon request.

What would be the best and least time consuming way to do this? Could someone post an example?

---

### Post by dwhitney67 on 2012-05-12
Quick & Dirty, and that runs under Windoze and Linux? -- well, use Java, not C++.

---

### Post by compiz addict on 2012-05-12
> **dwhitney67 said:**
> Quick & Dirty, and that runs under Windoze and Linux? -- well, use Java, not C++.

Unfortunately I already have a functioning program written in C++ that I'd hate to have to write again.
EDIT: Is there a way to compile my C++ program with a Java program inside it? Then I would probably do that.

---

### Post by 11jmb on 2012-05-12
> **compiz addict said:**
> Is there a way to compile my C++ program with a Java program inside it? Then I would probably do that.

The other way around is easier. JNI can link native code. What is it that you wrote in c++ that you don't want to re-write?

---

### Post by Some Penguin on 2012-05-12
> **compiz addict said:**
> There has been so many times where I would find this useful. What I want to do is write a server, which will request a plain-text file and receive/write it, and a client, which will send the plain-text file upon request.


Your description sounds very backwards.  Requests are normally initiated by clients...

> 
What would be the best and least time consuming way to do this? Could someone post an example?

You could use an embedded HTTP server like [http://code.google.com/p/mongoose/]("http://code.google.com/p/mongoose/") or an FTP server like [http://sourceforge.net/projects/cftpserver/]("http://sourceforge.net/projects/cftpserver/") although that might be overkill.  If the point is to learn about low-level networking code, searching for a BSD sockets tutorial would be a good bet.

---

### Post by 11jmb on 2012-05-12
To answer your original question, you can try boost::asio.

[http://www.boost.org/doc/libs/1_37_0/doc/html/boost_asio/overview.html](http://www.boost.org/doc/libs/1_37_0/doc/html/boost_asio/overview.html)

Boost is a great extension to c++, and the asio library supports networking on many popular platforms.

---


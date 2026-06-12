---
title: "Perl"
date: 2007-02-09
forum: Programming Talk
---

### Post by neugen on 2007-02-09
Is it possible to write a web server or a ftp server using perl ?

---

### Post by stoffe on 2007-02-09
Yes, from scratch using sockets if you are into bondage or, easier, by using one of the many modules available, such as:

* [http://search.cpan.org/~rwmj/Net-FTPServer-1.122/](http://search.cpan.org/~rwmj/Net-FTPServer-1.122/)
* [http://search.cpan.org/~gaas/libwww-perl-5.805/lib/HTTP/Daemon.pm](http://search.cpan.org/~gaas/libwww-perl-5.805/lib/HTTP/Daemon.pm)
* Just search CPAN...

But, if you *should* do it depends on why you want to do this, and why any regular server won't do it for you. Testing, specialized local setup and stuff like that may be valid reasons, but wanting to run a web hotel probably isn't. ;)

---

### Post by yaaarrrgg on 2007-02-09
Yes... you can probably write a web server in just a few lines (just a server socket that listens on port 80).

Although not sure it will be as  high performance or as secure as other open source tools  already written and tuned to do this.  Still it's a good way to learn abuot the underlying protocols.

---

### Post by phossal on 2007-02-10
As everyone else has mentioned, it's entirely possible to write a server in perl. Tiny web servers have been written in perl countless times. I believe the book, "Programming Perl" (published by O'Reilly) has an example. You can certainly find a few on the web. 

I still enjoy using perl a lot, although it's fallen out of favor since Python's rise to popularity. However, I think the downside of perl, as noted by the language's author in the above referenced book, is that sockets are heavily C-dependent. It would be tough to write a decent server in perl (There are all kinds of different servers. They don't all listen on port 80, and they don't all serve web content. Think of MySQL server, for example) that was very portable, or that wouldn't be much better written in a different language entirely. 

It might be fun though. ;)

---


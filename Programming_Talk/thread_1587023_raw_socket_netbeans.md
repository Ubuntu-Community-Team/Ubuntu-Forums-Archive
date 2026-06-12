---
title: "raw socket netbeans"
date: 2010-10-02
forum: Programming Talk
---

### Post by pythonsyntax on 2010-10-02
How can i do raw sockets in netbeans would it be safer to do it with pcap.h?

---

### Post by pythonsyntax on 2010-10-03
Someone got to now something.

---

### Post by pythonsyntax on 2010-10-03
?

---

### Post by r-senior on 2010-10-04
Do you mean "how do I work with TCP/IP sockets in Java?"? It's not really a question of working with sockets in Netbeans.

The classes you need are in the java.net package:

[http://download-llnw.oracle.com/javase/6/docs/api/java/net/package-summary.html]("http://download-llnw.oracle.com/javase/6/docs/api/java/net/package-summary.html")

... and there's a tutorial here:

[http://download.oracle.com/javase/tutorial/networking/sockets/]("http://download.oracle.com/javase/tutorial/networking/sockets/")

I'm not sure what you mean by "safer" with pcap? The java.net sockets implementation should work cross-platform.

---

### Post by pythonsyntax on 2010-10-04
I am talking about netbeans in C. Or do i have to be in main root for it?

---

### Post by dwhitney67 on 2010-10-04
Netbeans is an IDE.  You should drop it from your discussion because there are many IDEs and regular editors that are all capable of building C, C++, Java, or other languages.

Now, please confirm what you need assistance with:  is it with typical BSD sockets or with BSD sockets in which the socket type is setup as SOCK_RAW?  The latter requires root-privileges to create, and most often is not used because of the complexity in managing the TCP/UDP/IP stacks.

Before replying, you should read this: [http://en.wikipedia.org/wiki/Berkeley_sockets](http://en.wikipedia.org/wiki/Berkeley_sockets)

---


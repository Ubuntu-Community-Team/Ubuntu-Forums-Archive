---
title: "Moving files between servers using Ruby on Rails"
date: 2009-04-29
forum: Programming Talk
---

### Post by Miss Brightside on 2009-04-29
Hi
We're developing an application that works like this:
1. The user clicks on the button
2. The server generates a file
3. The file must be moved to another server

i'm currently learning ruby on rails, so if you guys have a hint about how to do this or about file administration on ruby, it would be really appreciated!

thanks in advance

---

### Post by Tibuda on 2009-04-29
Can you explain more what you want?
You can connect to FTP in ruby.

See
[http://www.ruby-forum.com/topic/141835](http://www.ruby-forum.com/topic/141835)
[http://www.ruby-doc.org/stdlib/libdoc/net/ftp/rdoc/index.html](http://www.ruby-doc.org/stdlib/libdoc/net/ftp/rdoc/index.html)

---

### Post by soltanis on 2009-04-30
Utilize FTP, as above poster has said, or you may consider using SFTP if the transfer is going to be done to a server not on the local network.

Other possibilities are mounting the foreign server as an NFS volume (ugh...don't do that), or using samba fileshares.

FTP/SFTP is really the best option here. I'm sure Ruby has the appropriate packages (or whatever they're called, I don't use it) for using those protocols.

---


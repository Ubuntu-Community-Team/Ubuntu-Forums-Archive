---
title: "Java: Recommended FTP library and security question"
date: 2009-06-22
forum: Programming Talk
---

### Post by mikazo on 2009-06-22
Hi,

I am writing a Java applet that I would like to show a representation of the file structure on my web server. I figured the best way to do this would be through FTP communication between the applet and the server.

I would like to know if anyone has used / can recommend a good Java FTP library? Also, what are the security issues regarding having my FTP username and password used in a Java applet?

Thanks.

---

### Post by froggyswamp on 2009-06-22
If only to show the files - you can use a servlet on the server side that can read your directories structure and a simple HTML on the client side, thus no need for a client in form of an Applet+FTP libs and no need to put your nick/password there.
I don't know though whether you can use server-side Java on that server.

---

### Post by mikazo on 2009-06-22
As far as I know, I can't run servlets, and I'd like to be able to upload/download files from my applet, as well as show maybe an image preview, and have the ability to add tags to files

---

### Post by Reiger on 2009-06-22
I am not quite sure:
[list="1"]
[*]You have a world-readable directory from which the WWW server serves your applet
[*]That directory also acts as your own authenticated-FTP directory???
[/list]

So anyone can circumvent built-in security mechanisms of the FTP server by using the WWW server to serve anything it can read? Do you actually have an FTP server?

Might as well go for anonymous FTP with disabled write access to the directory: then there isn't a need for storing passwords anywhere anymore and you are about as secured.

---

### Post by mikazo on 2009-06-22
Users would only have access to my applet by first logging in through PHP/MySQL (about 15 users, none of whom are very tech-savvy)

---

### Post by morningboat on 2009-06-23
You can have a look at this CrossFTP applet: [http://www.crossftp.com/features.htm#webcrossftppro](http://www.crossftp.com/features.htm#webcrossftppro)
It can be customized to show the default FTP site, etc.

---

### Post by hoboy on 2009-06-23
> **mikazo said:**
> Users would only have access to my applet by first logging in through PHP/MySQL (about 15 users, none of whom are very tech-savvy)

Try this link

[http://commons.apache.org/net/](http://commons.apache.org/net/)

---

### Post by froggyswamp on 2009-06-23
Your main problem is the inability to program on the server-side, hence you're trying to do workaround and rely on the client-side which means asking for troubles. You might invest a lotta time into the applet just to realize that the user can simply decompile and read your nick/password.
Also, for a Java fan creating an applet and putting on a webpage might be cool, but it's not good for users.

> Users would only have access to my applet by first logging in through PHP/MySQL (about 15 users, none of whom are very tech-savvy)
then nevermind..

---

### Post by mikazo on 2009-06-23
I know plenty of server-side programming, enough to make such functionality in PHP or Perl (and the server functionality to do so). I just thought it might be easier and faster to work with Java. If the whole idea is flawed from a security perspective, then maybe I'll bite the bullet and put in the extra work in.

Thank you for the links, those who posted some.

---


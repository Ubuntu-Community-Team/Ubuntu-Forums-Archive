---
title: "Why do some programs connect to localhost (127.0.0.1)?"
date: 2011-03-24
forum: Programming Talk
---

### Post by billdotson on 2011-03-24
I was starting up GNUcash in Windows 7 and Comodo firewall says that it was trying to connect to 127.0.0.1 on some port. Why would a program like GNUcash (or any program I guess) need to or want to connect to localhost? I'm assuming since it is localhost it isn't a security issue but I'm curious anyway.

---

### Post by Grey on 2011-03-25
It's a fairly common thing in the *nix world to write your programs in two parts.  One part is a server, and one part is a client.  Even X11 (your display server), functions that way.  This allows a program to clearly separate the functional side from the UI side.

That being said, I don't use GNUCash.  So I can't say for sure.  But perhaps it allows you to centralise your book-keeping and by default, it connects to your local computer.

---

### Post by billdotson on 2011-03-29
Well, I was using GNUCash on Windows and my firewall said it was trying to connect to 127.0.0.1 and asked me if I wanted to allow or block.

I assume if anything is connecting to 127.0.0.1 it isn't doing anything harmful (by that I mean sending your private information to somewhere else or something, I guess it could still be a virus or something) so I allowed GNUCash access. 

I haven't really figured out how to operate the Comodo Firewall in Windows 7. About all I know how to do is get it to nag me anytime an unauthorized program tries to connect to something. I haven't figured out how to tell it to accept all localhost by default.

---

### Post by nvteighen on 2011-03-29
In Unix-like environments, programmmers try to achieve the maximum interoperability among programs, so that you could automate more stuff by combining the funcionality of different programs.

There are several ways to do this, according to your needs; the server-client model being one of them. The server-client model allows you to code functionality that can be retrieved by different clients. For example, a server-client model can give much better control on how to synchronize multiple parallel access to some data. Also, if the program uses an openly documented protocol, this opens a very easy way to create new clients for that server.

---


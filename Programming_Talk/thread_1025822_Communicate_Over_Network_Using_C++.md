---
title: "Communicate Over Network Using C++"
date: 2008-12-30
forum: Programming Talk
---

### Post by nebu on 2008-12-30
How do I send an integer array over a local network using C++...

i know the IP of the computer i want to send the data to...

---

### Post by catchmeifyoutry on 2008-12-30
Sockets is what you're looking for.
Google for "C++ sockets linux" and you'll find tons of tutorials.

---

### Post by open_source_sux on 2009-01-28
Google doesn't solve everything wise guy. I've probably looked at 4 or 5 of these so called tutorials out there.  There's confusing BSD, Linux, Unix, Windows and C/C++ socket tutorials out there that all don't do anything but confuse. Searching for api functions brings up the above mentioned 4 operating systems in google searches and you have to consider C or C++ tutorials. 4 OS x 2 different syntaxes = 8.  8 ways of socket programming and all I want to do is learn how to do it in Ubuntu(Linux) in C++.
    But seriously, where can I learn how to create TCP/IP packets using C++(NOT C) and send them through a socket (unmodified by any OS behaviors) under Ubuntu 8.04 or later? And also receive a genuine response from a server that accepts a genuine TCP/IP packet sent from Ubuntu in c++ etc etc.  Beej's network guide is hardly helpful to me from what I have experienced reading through it and trying out his code.  Neither is Mixter's denial of service tutorial.  Both tutorials have bugs in their code or just don't work on Ubuntu.  Heck. Mixter has "PREFER UNIX" in his #defines.  
     I already have learned about TCP and IP headers, flags, checksums, options, ACK, SYN, three way foot shake, source address,  etc. etc.  whatever, but now the question is implementation with all the hairy details.  Theory only goes so far and so does Google.  This problem probably points right at all the nice, useful documentation made available for anyone who wants to learn huh? wait. what useful documentation?

---

### Post by cszikszoy on 2009-01-29
> **open_source_sux said:**
> Google doesn't solve everything wise guy. I've probably looked at 4 or 5 of these so called tutorials out there.

Do you really expect anyone to take you seriously?  Go to your local book store and find a book!  As someone already said sockets is what you're looking for.  Even if going to the book store is too much work, amazon returned some 248 books if you search "bsd socket".  It won't matter too much, winsock or bsd socket API.  Winsock has most of its roots in the BSD socket API.

---


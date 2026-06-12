---
title: "connecting to domain printer during a domain user session"
date: 2008-08-20
forum: New to Ubuntu
---

### Post by GigabyteMe on 2008-08-20
Hi,

my ubuntu box is part of AD domain [thanks to Likwise!], I have added my domain user account to ubuntu admin group in the[etc/group] file.

I can successfully connect to the print server and browse for printers, however; while installing the ppd I am prompted for a password and not one seems to work; not the ubuntu admin [ the one created during installation], not the domain user, I even created a password using [sudo psswrd] and it did not work!

the message I keep receiving is [password for DOMAINUSER on localhost?]

help!!

---

### Post by GigabyteMe on 2008-10-15
Adding the user account to lpadmin group did the trick.

thanks anyways!!

---


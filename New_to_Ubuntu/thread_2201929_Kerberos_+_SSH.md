---
title: "Kerberos + SSH"
date: 2014-01-26
forum: New to Ubuntu
---

### Post by heatseeker2 on 2014-01-26
Hi,

See if someone can lend me a hand with a simple problem . I'm tinkering with Kerberos and I doubt arises in trying to " kerberizing " SSH (OpenSSH ) . My disposal the following virtual scenario:


- Machine 1: Debian router ( caronte.hades.org ) -> Contains NTP server for time synchronization .
- Machine 2: Ubuntu Server ( minos.hades.org ) -> Contains the Kerberos server , SSH and DNS.
- Used 3: Ubuntu Desktop ( orfeo.hades.org ) -> Contains the Kerberos and SSH client side .


What I intend to do is a simple ssh connection authenticated by kerberos as follows : maquina3 to machine2 . Taking into account:


- There is ssh as principal ( host / minos.hades.org ) in the kerberos server ( machine 2) and corresponding keytab service.
- A user ( mortadelo ) as principal in the kerberos server as the local user of the machine 2 .
- I enabled GSSAPI both server and client files by setting respectively ( " sshd_config " on the server and " ssh_config " on the client ) .


And now this. From the client ( machine 3) generated the ticket for mortadelo with " kinit mortadelo " without any problem and when I connect ( ssh- v [email]mortadelo@minos.hades.org[/email] ) to server ( machine 2) pa asked me to try the local password ... The error log shows the following:


debug1 : Unspecified GSS failure . Minor code May Provide more information
Server krbtgt / DIAL - UP.TELESP.NET.BR @ HADES.ORG not found in Kerberos database


I do not understand that this entry refers to . It's as if he did not understand that I want to connect minos.hades.org , moreover, is what helped me the initial ticket ...


What am I doing wrong?

---


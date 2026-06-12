---
title: "Weird gproftpd problem"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by django0909 on 2008-06-28
Hi all, searched the forums for an answer but can't seem to find one.

I have gproftpd set up on a HH install. I can connect internally, via [ftp://user@192.168.x.xxx](ftp://user@192.168.x.xxx) - so there is no problem with any login credentials. When I try and connect externally, my client hangs when it tries to list the directory. I have no idea what is happening and any clues as to why it is hanging or what is going on would be appreciated greatly.

Thanks all, if you require any more info give me a shout :)

-django

EDIT: Apparently I need to shut off passive mode. How is this done in gproftpd?

---

### Post by django0909 on 2008-06-28
Or perhaps not. Turning off passive mode gives:

501 Invalid number of arguments: //
425 Unable to build data connection: Invalid argument: //

Any ideas at all guys? I'm using Fire FTP on the remote machine and gproftpd 8.3.2 on the client. I really need it to populate the directory list... :(

---


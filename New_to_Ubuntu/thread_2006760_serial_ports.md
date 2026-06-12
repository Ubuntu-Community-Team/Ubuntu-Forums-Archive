---
title: "serial ports"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by ab8cl on 2012-06-19
I have a program that runs in wine.  If started as a user/administrator(I'm the only user of this computer) the program runs but can't use the serial ports "doesn't have permission".
is the error I see.  So I run it as root and everything works fine.  I installed the program as just me the administrator/user and saw I had this problem so I then removed it and re0installed it as root.   Then ran it (in wine) as a normal user but still can't use the serial port unless ran as root.  HOw do I get "permission" use serial ports, I think is the ? so that I don't have to run the program as root.

thanks 
KP

---

### Post by HiImTye on 2012-06-19
[http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure](http://www.winehq.org/docs/wineusr-guide/misc-things-to-configure)
this should work

---

### Post by lkraemer on 2012-06-20
You also need to VERIFY that the loggedinuser has permission to use the
Serial Ports with the Terminal (CLI Command):
```

groups

```

My groups are:
> 
larry@debian:~$ groups
larry dialout cdrom floppy sudo audio dip video plugdev netdev bluetooth scanner vboxusers
larry@debian:~$

and dialout is for the Serial ports & Modem.

ie. Manage "Users & Groups"

lk

---

### Post by ab8cl on 2012-06-20
Awsome answers and I needed them both !  It's working like a well oiled machine.

Thanks again,
Keith

---


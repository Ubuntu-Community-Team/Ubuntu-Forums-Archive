---
title: "gdesklets doesn't work"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by m994301009 on 2008-06-28
So, i've just installed gdesklets, and it doesn't work, when opening it from the launch icon, it just goes away after a bit, but running from the terminal I get this error:
```

Unhandled error! Something bad and unexpected happened. ===

[EXC]
in /usr/bin/gdesklets: line 393 <module>
in /usr/bin/gdesklets: line 268 parse_command
in /usr/bin/gdesklets: line 177 __open_profile
in /usr/bin/gdesklets: line 167 __client_daemon
in /usr/lib/gdesklets/main/client.py: line 208 set_remove_command
in /usr/lib/gdesklets/main/client.py: line 38 __send
in /usr/lib/gdesklets/utils/xdr.py: line 75 recv
[EXC]/usr/lib/gdesklets/utils/xdr.py

[---]   70     chunk = ""
[---]   71     while (True):
[---]   72         try:
[---]   73             length = ord(s.recv(1))
[---]   74         except:
[ERR]>  75             raise XDRError
[---]   76 
[---]   77         if (length): chunk += s.recv(length)
[---]   78 
[---]   79         flag = s.recv(1)
[---]   80         if (flag == _CONT): continue
[---]   81 

```
OR (and it seems totally random which one I get)
```

Starting gdesklets-daemon...
Cannot establish connection to daemon: connection timeout
The log file might help in solving the problem.

```
And I can't find the log file, so could anyone tell me where it is?

---

### Post by cpetercarter on 2008-06-28
Have you tried re-installing gdesklets and gdesklets-data using Synaptic Package Manager?

---

### Post by saratchandra on 2008-06-28
Try screenlets instead. Download the latest version from [http://www.getdeb.net/](http://www.getdeb.net/) They are better than desklets imo.

---

### Post by cariboo on 2008-06-28
You may want to have a look here:

[https://bugs.launchpad.net/](https://bugs.launchpad.net/)

Search for gdesklets to see if anyone is having the same problem. In a lot of cases there may be a work around.

Jim

---

### Post by m994301009 on 2008-06-28
Yup, I found the bug, no fix ATM though, it seems to be an issue with x86_64 computers mostly. Time to try screenlets.

---


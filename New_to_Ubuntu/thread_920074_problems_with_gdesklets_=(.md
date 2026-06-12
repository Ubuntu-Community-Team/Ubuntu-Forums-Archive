---
title: "problems with gdesklets =("
date: 2008-09-14
forum: New to Ubuntu
---

### Post by zloygame on 2008-09-14
I have Ubuntu 8.04, I was using this tutorial - [http://www.howtoforge.com/gnome_gdesklets](http://www.howtoforge.com/gnome_gdesklets)

When I succesfully install gdesklets and gdesklets-data, when I try to launch it a window with the name gDesklets pops out, then it freezes, and then I have to forcr quit it. 
Whats the problem? Is there a newer version of dgesklets that I should use? O_o

---

### Post by Tatty on 2008-09-14
Try running gdesklets from a terminal and see if it produces an error message.

---

### Post by zloygame on 2008-09-14
just tried to run it in a terminal.
when i typed in "gdesklets" a whole bunch of stuff was registring or smth, and then it stopped on "connecting to DAEMON" and then nothing happened :(((

---

### Post by Tatty on 2008-09-14
Hmm, i just tried installing gdesklets too and it crashed like yours giving the following terminal output:

```
Connecting to daemon [    ###      ]
==========================================================[09/15/08-04:17:22]===
Registering new control "/usr/lib/gdesklets/Controls/System".


Connected to daemon in 2835 milliseconds.

==========================================================[09/15/08-04:17:22]===
=== Unhandled error! Something bad and unexpected happened. ===

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


Is this the same error that yours ends with?

Can anyone else confirm this?

---

### Post by zloygame on 2008-09-14
close enough, but mine doesnt even connect lol. it times out =)

---

### Post by zloygame on 2008-09-14
This is what i get =)
> mazafaker@mazafaker-desktop:~$ gdesklets
Starting gdesklets-daemon...
Cannot establish connection to daemon: timeout!
The log file might help you solving the problem.


---

### Post by Tatty on 2008-09-15
Have you tried looking at the log file?

---


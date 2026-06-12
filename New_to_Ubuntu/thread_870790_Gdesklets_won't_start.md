---
title: "Gdesklets won't start"
date: 2008-07-26
forum: New to Ubuntu
---

### Post by Jarovit on 2008-07-26
I've been trying to get Gdesklets working, using the package in the default repository, but it just won't start. If it start it via the applications->accesories menu, it opens a blank window, that goes grey in a few seconds, than shuts down in a half a minute. If I start it with the terminal, I get this:

```
zero0ne@ARTEMIS:~$ gdesklets
Starting gdesklets-daemon...
Connected to daemon in 202 milliseconds.

==========================================================[07/26/08-13:31:25]===
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


zero0ne@ARTEMIS:~$ 


```
 
Any ideas?

---

### Post by Jarovit on 2008-07-26
bump

---

### Post by m_ad on 2008-07-26
If nobody can help you, try the package "screenlets," same thing with actually more screenlets/desklets :)

---

### Post by wishyjr on 2008-07-26
hmm never seen that one. try re-installing using synaptic. Also, can you start gDesklets using the icon in the main menu?

---

### Post by bobbob94 on 2008-07-26
I had problems with Gdesklets under Compiz, and switched to Screenlets, which work just fine.

---

### Post by m_ad on 2008-07-26
that's why I suggested Screenlets :)

AND there is many more screenlets available on gnome-look.org

---

### Post by Cpl.Punishment on 2010-12-28
Been a while since this post, but I like screenlets alot. I am on Ubuntu 10.10 and was unable to get gdesklets to work.

---

### Post by Redjack8 on 2010-12-31
ive added this in other areas...  just in case, if your error is the tiling error ...  try this link - im a total ubuntu noob and it took me about a minute or two... its just editing one line in a file...worked fine for me...

[http://forum.linuxmint.com/viewtopic.php?f=90&t=32554#p187551](http://forum.linuxmint.com/viewtopic.php?f=90&t=32554#p187551)

redjack

---


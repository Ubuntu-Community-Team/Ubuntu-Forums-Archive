---
title: "I can install anything from the USC"
date: 2013-02-24
forum: New to Ubuntu
---

### Post by OhGojira on 2013-02-24
Hello, and thanks in advance.
Whenever I try to download and install something from 
Ubuntu software center, i can't...
It does download it, but can install it
i always get this:

```

installArchives() failed: Setting up install-info (4.13a.dfsg.1-10ubuntu2) ...
/etc/environment: line 1: acquire::http::proxyfalse: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 install-info
Error in function: 
Setting up install-info (4.13a.dfsg.1-10ubuntu2) ...
/etc/environment: line 1: acquire::http::proxyfalse: command not found
dpkg: error processing install-info (--configure):
 subprocess installed post-installation script returned error exit status 127

```


Thanks.

---

### Post by gordintoronto on 2013-02-28
Do you connect to the Internet through a proxy?

---

### Post by matt_symes on 2013-02-28
Hi

Welcome to the forums :D

Press alt + F2 and type this into it.

```
gedit /etc/environment
```

Copy and paste the text from gedit into your next post.

Kind regards

---

### Post by OhGojira on 2013-03-19
Thank you for the reply.

I type in what you said matt and i got this:

acquire::http::proxy"false"

should i change it to true or something?

---

### Post by OhGojira on 2013-03-19
Well i just went into the terminal and typed in:

```
sudo [COLOR=#000000][FONT=Ubuntu Mono]gedit /etc/environment[/FONT][/COLOR]
```

and deleted the text that was inside and it now works XD 

thank you very much :) :)

OhGojira

---

### Post by matt_symes on 2013-03-20
Hi

@OP

In your case this was the solution, however this is **not** a general solution (deleting the contents of /etc/environment) to fix these errors for **any other people** searching for a solution to USC problems.

Kind regards

---


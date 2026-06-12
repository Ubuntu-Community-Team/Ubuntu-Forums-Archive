---
title: "Apache Installation From Source"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by Flash Gordon on 2008-06-09
I installed Ubuntu last week and have never used a Unix command line beforehand. I asked a friend what I could do to learn and he suggested I install Apache from the source code. I believe I successfully installed it, however it will not run. Here is my directory

:  theflash@theflash-desktop:/usr/local/apache2/bin$ 

From here I typed the command

:  ./apachectl start

yet I get this error

:  (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80

I do not know any vi or vim, but apparently I need to direct apache towards an IP. Is there any other information needed to solve this issue?
Thanks

---

### Post by stchman on 2008-06-09
> **Flash Gordon said:**
> I installed Ubuntu last week and have never used a Unix command line beforehand. I asked a friend what I could do to learn and he suggested I install Apache from the source code. I believe I successfully installed it, however it will not run. Here is my directory

:  theflash@theflash-desktop:/usr/local/apache2/bin$ 

From here I typed the command

:  ./apachectl start

yet I get this error

:  (13)Permission denied: make_sock: could not bind to address 0.0.0.0:80

I do not know any vi or vim, but apparently I need to direct apache towards an IP. Is there any other information needed to solve this issue?
Thanks

Apache is in the repos so there is no need to build it.

There are better ways to learn the command line than to start building software.  Google command line Ubuntu and there are lots of tutorials.

---

### Post by annda on 2008-06-09
i agree with stchman: start somewhere easier. this is a nice start i think:
[http://linuxcommand.org/](http://linuxcommand.org/)

and apache is especially tricky, because you have to know what files go where and what permissions they need.

---


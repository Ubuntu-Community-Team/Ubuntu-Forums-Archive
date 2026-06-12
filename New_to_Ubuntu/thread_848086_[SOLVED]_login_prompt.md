---
title: "[SOLVED] login prompt"
date: 2008-07-03
forum: New to Ubuntu
---

### Post by ub007 on 2008-07-03
Hiya,

I started with a mail server installation & at the moment reached the prompt:
fmaster@ubuntu:~$
i need to get back to my previous prompt :david@ubuntu$

tried
-fmaster@ubuntu:~$login
*YOu must exec "login" from yhe lowest level "sh"

-fmaster@ubuntu:~$sh
$login
*YOu must exec "login" from yhe lowest level "sh"


$bash

[email]fmaster@ubuntu:~$logout,exit,..does[/email]nt seem to work
fmaster@ubuntu:~$sudo -s
password
fmaster is not in sudoers file...

what could be wrong here?

Cheers
David

---

### Post by mcduck on 2008-07-03
"exit" should log you out.

---

### Post by ub007 on 2008-07-03
it doesnt :(

---

### Post by jspolen on 2008-07-03
try "su david"

---

### Post by ub007 on 2008-07-03
rather strange,i rebooted n tried the exit command,it worked fine!!!thanks

---


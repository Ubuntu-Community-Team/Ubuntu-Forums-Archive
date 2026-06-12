---
title: "Get current user in C/C++?"
date: 2005-05-03
forum: Programming Talk
---

### Post by Kimm on 2005-05-03
I am writing an application that would need root permission, I only want the program to ask for the password if you are not logged in as root however, so, I am woundering if there is any way that I can know what user is logged in?

---

### Post by HungSquirrel on 2005-05-03
If there's a way to execute shell commands from C, you could have your program execute the **whoami** Unix command.  There's probably a much better way to do this, though.

Edit:  Scroll down to the C on *Nix post at this link.
[http://lineman.net/node/271](http://lineman.net/node/271)

---

### Post by lao_V on 2005-05-03
you can check to see if the userid is 0 or not. something like:

```
 if [ -eq $UID 0]
```

---

### Post by Kimm on 2005-05-03
HungSquirrel, that C on *Nix post worked perfectly ^^ thank you!

lao_V, I dont quite understand what you mean... is that C code??

---

### Post by Teren on 2005-05-03
[QUOTE=Kimm]HungSquirrel, that C on *Nix post worked perfectly ^^ thank you!

lao_V, I dont quite understand what you mean... is that C code??[/QUOTE]
 That's SH

---

### Post by Kimm on 2005-05-03
oh, I see, I never realy use SH...

---


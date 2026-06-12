---
title: "allowing a certain program to have root privileges"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by adobrakic on 2008-05-27
How do i allow ClamTk (virus scanner) to have root privileges, without actually logging into root? I wanna do this, because when i try to update signatures, it tells me i need to be root. 

I went to terminal and did 
gksu clam

but that did nothing.

any suggestions?

---

### Post by scorp123 on 2008-05-27
What do you need a virus scanner for??

---

### Post by sayakb on 2008-05-27
Try 
```
gksudo clam
```

---

### Post by scorp123 on 2008-05-27
> **LinuxIsInnovation said:**
> Try 
```
gksudo clam
``` @OP: If you really really insist on using a virus scanner (you don't need one IMHO) you should read about "visudo": ```
man visudo
``` ... That's the command used to manipulate the "sudoers" file. You could add the "clam" command so that it won't ask your for a password when you execute it via "sudo" (yes, that can be done). I'd suggest you use Google and search around for examples regarding "sudoers" and "visudo". If done correctly it would make it a lot easier for you I guess (e.g. not having to type the password all the time, etc.)

---


---
title: "Error... complete nube"
date: 2008-11-27
forum: New to Ubuntu
---

### Post by numberattic101 on 2008-11-27
hi im getting an error i looked all over and could not find a solution on fixing it that i could understand.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

is my error can someone please explain in an easy way on how i can manually unless i tried it correctly. went to applications > accessories > terminal and typed it in there and got this

dpkg: requested operation requires superuser privilege

if anyone got an answer to this it would be great.

using ubuntu 8.10
got this error from trying to download compiz, synaptic package manager, update manager and so on. ty for ur help

---

### Post by Shwefty on 2008-11-27
Whenever you see something that says you need "super user privileges" in the command line, that means you have to type "sudo" before it.

So, what you should type into Terminal is:

```
sudo dpkg --configure -a
```

It'll prompt you for your password.

---


---
title: "dpkg was interrupted, you must manually run dpkg..."
date: 2008-10-26
forum: New to Ubuntu
---

### Post by mr2v6 on 2008-10-26
Hello,
While I was trying to play a dvd on totem, this message appeared.

dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I am not sure what I need to do.  When I tried synaptic, I get the same message.  I really don't want to reinstall ubuntu 8.04.  

Any help would be appreciated.

thanks,
MR2v6

---

### Post by BackBack on 2008-10-26
Just type in sudo dpkg --configure -a into the terminal, that should fix it

---

### Post by Nepherte on 2008-10-26
The error already suggets what you have to do:
```
sudo dpkg --configure -a
```

---

### Post by acidsolution on 2008-10-26
type 
```
sudo dpkg --configure -a

```

---

### Post by lswest on 2008-10-26
Just to be a bit more detailed in a description:

The error occurs when dpkg is interrupted (computer freezes, you cancel an install, PC crashes, etc.) and it suggests you run "dpkg --configure -a" to fix it.

Running it like that alone won't do it, you'll need to run it as a super user (thus the sudo everyone above has added) and this is because you were running dpkg as a super user, therefore it doesn't add that into the error message.  Basically if you get an error message when running a program as a super user, expect to run any fixes as a super user (since you'll likely need those permissions to fix certain files).

Linux is (unlike windows) very helpful with its error messages, generally reading them will give you a good idea of how to fix them (or else google will help you find the solution to this problem, there are hundreds of these threads asking for help with this specific problem, for example).

Just some extra info you may or may not want/need/find useful.

---


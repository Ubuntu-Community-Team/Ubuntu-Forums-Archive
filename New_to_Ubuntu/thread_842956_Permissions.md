---
title: "Permissions"
date: 2008-06-27
forum: New to Ubuntu
---

### Post by MONKEY4SALE on 2008-06-27
So i downloaded and installed PlaneShift but i have a problem, when I try to run/uninstall I get an error, of:

Failed to execute child process "/opt/
PlaneShift/psclient" (Permission denied)

but im running on the only account I made, and as far as I can tell, it is impossible to log in as root from the login screen.

---

### Post by Journeyman on 2008-06-27
you can run as root using gksudo <program> (gksudo is for gui apps) also if you type sudo -i or sudo -s it will give you a root prompt

---

### Post by MONKEY4SALE on 2008-06-27
tried gksudo, asked for my pword,I entered it, and then nothing happened....

and when doing sudo -s:

/opt/PlaneShift/psclient: line 5: cd: /root//opt/PlaneShift: No such file or directory
chmod: cannot access `psclient.bin': No such file or directory
/opt/PlaneShift/psclient: line 8: /root/psclient.bin: No such file or directory
/opt/PlaneShift/psclient: line 8: exec: /root/psclient.bin: cannot execute: No such file or directory

---

### Post by Journeyman on 2008-06-27
I miss read your first post, thinking you where installing it, running it as root wouldn't be good in the first place. so back to fixing your problem.

try this
```
 sudo chmod -R a+rx /opt/Planeshift 
```

that should correct the permissions.  if that doesn't do ```
 sudo chmod -R a+rwx /opt/Planeshift 
```

---

### Post by MONKEY4SALE on 2008-06-27
now the perms work, but the program doesnt, nothing happens when I click on it.

thanks for helping, now I need to figure out the odd non-working....

---

### Post by BrownieBoy on 2009-10-03
> **Journeyman said:**
> I miss read your first post, thinking you where installing it, running it as root wouldn't be good in the first place. so back to fixing your problem.

try this
```
 sudo chmod -R a+rx /opt/Planeshift 
```

that should correct the permissions.  if that doesn't do ```
 sudo chmod -R a+rwx /opt/Planeshift 
```

Worked for me, although it's capital "S" in PlaneShift, i.e.:

```
 sudo chmod -R a+rx /opt/PlaneShift 
```

---

### Post by cervantes_ on 2009-10-22
am having a similar problem but for me it won't let me drag and drop the fire fox icon on to the desktop cause it says i don't have permission but am the only user

---


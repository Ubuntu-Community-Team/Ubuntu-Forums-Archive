---
title: "Emacs, Tramp, SSH"
date: 2008-04-19
forum: Programming Talk
---

### Post by raashell on 2008-04-19
I'm learning Emacs and I just figured out how to connect to a remote host to edit files with tramp.  I have two issues that I hope someone here can answer, or point me in the right direction:

1-  Can I change a files permissions remotely in Emacs, or do I have to do it through another secure shell?

2-  Every time that I save, I have to enter my password on the remote server.  How can I save this in a config file?

Any help would be greatly appreciated-- my eyes hurt from Googling and scanning the Tramp manual.

John

---

### Post by raashell on 2008-04-20
Bump

---

### Post by simonbonner on 2008-05-16
Hey raashell,

Had the same problem, and the only note on the web I could find was yours. 

I realized that the problem was in using scp, which seems to open a new connection every time, rather than ssh, which will maintain a connection. I changed the default connection method, and it now works properly.

You can modify the variable from the menu 'Options > Customize Emacs > Specific Option' and then selecting tramp-default-method. Change the default method from scp to ssh and then click on 'Set for Current Session' and 'Save for Future Sessions' to make it take effect now and foreever.

Hope that helps...

---

### Post by st14n on 2008-06-19
> **simonbonner said:**
> 
I realized that the problem was in using scp, which seems to open a new connection every time, rather than ssh, which will maintain a connection. I changed the default connection method, and it now works properly.

You can modify the variable from the menu 'Options > Customize Emacs > Specific Option' and then selecting tramp-default-method. Change the default method from scp to ssh and then click on 'Set for Current Session' and 'Save for Future Sessions' to make it take effect now and forever.


Thanks, that was the solution for me as well. However, I prefer putting 
```
(setq tramp-default-method "ssh")
``` directly into my .emacs file.

For i nice guide on the pros and cons with this, look at the documentation for the tramp default method within Emacs.
```
C-h i s tramp <RET> <RET> s default method <RET> <RET>
```

---


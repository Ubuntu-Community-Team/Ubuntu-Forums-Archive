---
title: "Running GUI applications on a remote computer"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by andriy.kostyuk on 2008-06-22
As far as I know, one can run graphic-interface applications on a remote computer.
I tried the following
1. ssh [email]myname@somehost.xx[/email]
2. After entering my password I logged in and could do everything in command line interface, as if I am using the terminal connected to the computer "somehost".
3. But if I try to run a GUI program 

$ mozilla &

(for example)
I get the message 

  Can't open display

--
What should I do?

Thanks in advance.

---

### Post by Xerp on 2008-06-22
Enable Desktop sharing, or use software such as NoMachine.

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)
[http://www.nomachine.com/](http://www.nomachine.com/)

---

### Post by _sphinx_ on 2008-06-22
I think you should do:
```

ssh -X myname@somehost.xx

```

---

### Post by acidsolution on 2008-06-22
You can use vncviewer from the computer which u want do remote.
but before doing that you have to enable vnc-server on the remote computer .
to enable vncserver first intall vncserver 
you can either tight vnc-server from the repository

---

### Post by ezramorris on 2008-06-22
I agree with _sphinx_. Unless you <need> to see the entire desktop, using ssh -X is quicker and more secure.

---

### Post by andriy.kostyuk on 2008-06-22
> **_sphinx_ said:**
> I think you should do:
```

ssh -X myname@somehost.xx

```
Thank you very much! 
It works. :)

---


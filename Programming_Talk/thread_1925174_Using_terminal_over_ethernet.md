---
title: "Using terminal over ethernet"
date: 2012-02-14
forum: Programming Talk
---

### Post by godart on 2012-02-14
Hi everyone,

I am developing an embedded application with qt (c++), i was wondering that is there a way to sending commands to terminal over the ethernet ?

Thanks in advance,

---

### Post by deathadder on 2012-02-14
I'm not entirely sure what you're looking for, but you can run remote commands over SSH. You could probably use libssh2 to do that with, although I've never used it myself.

[http://www.libssh2.org/](http://www.libssh2.org/)
[http://www.libssh2.org/examples/](http://www.libssh2.org/examples/)
[http://www.libssh2.org/docs.html](http://www.libssh2.org/docs.html)

---

### Post by godart on 2012-02-14
> **deathadder said:**
> I'm not entirely sure what you're looking for, but you can run remote commands over SSH. You could probably use libssh2 to do that with, although I've never used it myself.

[http://www.libssh2.org/](http://www.libssh2.org/)
[http://www.libssh2.org/examples/](http://www.libssh2.org/examples/)
[http://www.libssh2.org/docs.html](http://www.libssh2.org/docs.html)

Thanks, i guess this will work for me. But i want to explain what i want. In my embedded application, i have installed the angstrom which is one of the distributions of linux. And i have ethernet interface. I want to use this interface to run commands in the linux operating systems terminal. Because, i am not supposed to use keyboard or mouse :)

---

### Post by dwhitney67 on 2012-02-14
> **godart said:**
> Thanks, i guess this will work for me. But i want to explain what i want. In my embedded application, i have installed the angstrom which is one of the distributions of linux. And i have ethernet interface. I want to use this interface to run commands in the linux operating systems terminal. Because, i am not supposed to use keyboard or mouse :)

You would use the Ethernet interface if you want to access remote (external) systems.  If you merely want to run system commands on the local device, then use system() library function or use a similar function that Qt may offer.

Usage of the system() function has absolutely nothing to do with a terminal, and neither what you have previously described.  If you want your device to securely communicate with external systems, then the SSH-protocol would be helpful.

---


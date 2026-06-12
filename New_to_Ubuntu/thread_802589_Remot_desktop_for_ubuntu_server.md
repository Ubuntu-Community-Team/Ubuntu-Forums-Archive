---
title: "Remot desktop for ubuntu server"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by jamisonwalter on 2008-05-21
I am in the process of building a faceless Ubuntu server and I am new to linux.  I know that I can install ubuntu server and have the computer running fine in the closet, but if I need to change any configurations or anything else that requires access to the computer, is there an easy way to access the server from another computer using something like remote desktop to avoid having to lug a keyboard, mouse, and monitor to the server?

---

### Post by HermanAB on 2008-05-21
Yup.  It is called SSH.

You have to install the OpenSSH package, start the sshd service then log in from another machine.  SSH can also do X forwarding, so you can run graphical programs on the remote server without having X on the remote machine.

Cheers,

Herman

---


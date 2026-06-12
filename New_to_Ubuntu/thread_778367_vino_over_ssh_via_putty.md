---
title: "vino over ssh via putty"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by OmahaVike on 2008-05-02
hey all.  would appreciate any comments or suggestions on this one.

been a long time dapper user, and used to have a vnc/ssh/putty connection to my home machine while at work.

since moving to hardy, i see that vino is the built in default.  has anyone solidified a vino connection over ssh using putty?

thanks in advance!

---

### Post by bluefrog on 2008-05-13
you can always forward ports for vnc or whatever in ssh.
for vnc, on your computer
ssh -L 5901:localhost:5900 user@IP (of course an ssh server must be running on the distant pc)

then in vnc, on your computer, you connect to localhost:1.

Oh you are using Putty.
If memory serves putty has all you need to initiate such a connection (the ssh port forwarding part)

---

### Post by bodhi.zazen on 2008-05-13
See also :

[uwiki]VNCOverSSH[/uwiki]

---


---
title: "[SOLVED] how to stup shared folders in virtualbox?"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by kamitsukai on 2008-05-03
Hi, im running windows xp sp3 in virtualbox on ubuntu 8.10 how do i setup shared folders? i have gone in the virtualbox settings and selected ubuntu home directory to be shared but then you have to run commands in the xp? it's been ages since ive done this so what commands and where lol:)

thanks in advance

---

### Post by NIT006.5 on 2008-05-03
Unfortunately I'm not on the machine where I've got virtualbox set up at the moment (that's at work) but I've never had to run any commands. As far as I remember, once you've set the folder to be shared, you just browse to it under networks in XP... you should find \\VBOXSRV\foldername - and then map that share. (provided that guest additions are installed in the virtual OS).

---

### Post by kestrel1 on 2008-05-03
NIT006.5 is correct or you can use the 'net use' command from a dos box, but you do need the guest additions installed.

---

### Post by kamitsukai on 2008-05-03
thnx

---


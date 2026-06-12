---
title: "Fix SSH through FTP"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by dolphin194 on 2012-05-11
I have messed something on my server computer up, and now I cannot connect with SSH. I only have access to the machine through FTP, and am wondering if I can issue commands through FTP, or an alternate method.

I do not have physical access to the machine.

It is running Ubuntu Server 10.04.

---

### Post by Lisiano on 2012-05-11
FTP stands for File Transfer Protocol so as the name states, it only supports transfering files, you can use FTP over SSH though.
If you are renting a server then maybe their tech support could help you restore SSH.
If it's a corporate server, you'll have to find someone willing to go to where the server is and make that person fix SSH or go yourself.

How exactly did you fubar your SSH server? If you tweaked something user-specific (Like a shell) then it's easy enough to fix I reckon.

---


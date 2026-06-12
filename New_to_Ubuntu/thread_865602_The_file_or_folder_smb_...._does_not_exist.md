---
title: "The file or folder smb:// .... does not exist"
date: 2008-07-20
forum: New to Ubuntu
---

### Post by scootre on 2008-07-20
Hi guys

Issue:
kubuntu 8.04 Desktop with Samba installed.  If I try to get to a shared folder from another Ubuntu (8.04.1 server AMD64) machine I get the error from its kubuntu desktop:
"The file or folder smb://<machine>/PUBLIC does not exist"

I've found a few posts here and on other forums with people having the same issue.  The common fix I have found suggest editing /etc/samba/smb.config  and commenting out the line:  msdfs proxy = no

Problem is... I cannot find any such line in smb.conf to comment out?!?

$ sudo more /etc/samba/smb.conf |grep msdfs
also returns nothing.

The issue seems to be with the host machine itself because even if I try to navigate to that folder via Samba locally I get the same error.  I can however open the directory normally, via GUI or command line, and add and remove files and folders without any problems.

---

### Post by stmiller on 2008-07-20
If you are using KDE 3, start kcontrol from the terminal and:

kControl Center -> Internet & Network -> Samba -> Advanced Tab -> VFS

And uncheck “Host msdfs”.

That should do it...

---------

If you are using KDE4, go to system settings>sharing> and put in your network samba username/password. Now samba browsing will work with Konqueror/Dolphin.

---

### Post by scootre on 2008-07-22
Hi mate

Thanks for your reply.  Unfortunately, it's still not working.  Even after restarting Samba and then later restarting the entire machine.

---

### Post by scootre on 2008-07-24
OK... so no other takers?  Anyone?  Bueller?

---


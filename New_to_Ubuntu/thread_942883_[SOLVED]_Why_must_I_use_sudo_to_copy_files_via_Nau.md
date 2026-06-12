---
title: "[SOLVED] Why must I use sudo to copy files via Nautilus???"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by akelsall on 2008-10-09
Just installed Ubuntu 8.04 and have a question about copying files via Nautilus. I set up one user that has complete privileges to do anything (basically, the equivalent of root), and another that does not have admin privileges. Let's say the user names are root and newb.

I created several partitions on my HD, one of those being /computer. If I launch Nautilus without using sudo (as either "newb" or "root"), I can NOT copy files over to the /computer partition. 

If I log into the desktop as user "root" and launch Nautilus from a term window (sudo nautilus &), I **AM** able to drag&drop files to /computer. 

If I log into the desktop as user "newb", I have to use the syntax "gksudo nautilus &" to allow me to drag&drop files into the /computer partition. 

So, my questions are:

1. Why must I use the sudo command to drag&drop files via Nautilus?

2. Why am I able to use just sudo when logged in as user "root", but must use "gksudo" when logged in as user "newb"?

Thanks,

Andy

---

### Post by drs305 on 2008-10-09
Here are two good references which answer your questions:
[RootSudo]("https://help.ubuntu.com/community/RootSudo")

[GraphicalSudo]("http://www.psychocats.net/ubuntu/graphicalsudo")

I'd planned on giving you a brief synopsis but the wife just called me to dinner ... ;-)

---

### Post by bwang on 2008-10-09
The sudo prevents you from  accidentally messing up your system. The root account is disabled in Ubuntu, and the admin account is not a root account. Read more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Zill on 2008-10-09
Logging in as root is contrary to the Ubuntu security model.  Sudo is used by specified users to enable superuser permissions when necessary.

[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

Your directory /computer is, presumably, "owned" by root and the user will therefore need to use sudo from a terminal or gksudo from the GUI to allow any files in this directory to be modified.

---

### Post by akelsall on 2008-10-09
Great links! That clears it up perfectly. Thanks to everyone for the info!

Andy

---


---
title: "Nautilus and samba shares authentication"
date: 2008-07-15
forum: New to Ubuntu
---

### Post by hp3 on 2008-07-15
I try to mount a samba share, and I can, but all my files are created with the user nobody on the server.  I give my user name and password. but still nobody is used on the server as my user name.  I also noticed that 
When I share folder with Nautilus and reboot my system, I have to share them again.  I have posted this before but got no answers.

I have found a program called smbclient, when I use this, all my files are created correctly on the server.  But using the command line for all my file work is hard and I hope this is due to some misunderstanding 
and that it can be fixed.

---

### Post by bobnutfield on 2008-07-15
You will have to edit your samba.conf file.  Here is a link to an extensive tutorial on Samba, with some working examples..

[http://us4.samba.org/samba/docs/man/Samba-Guide/]("http://us4.samba.org/samba/docs/man/Samba-Guide/")

---


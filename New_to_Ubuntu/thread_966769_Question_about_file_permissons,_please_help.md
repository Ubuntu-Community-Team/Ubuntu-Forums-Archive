---
title: "Question about file permissons, please help"
date: 2008-11-01
forum: New to Ubuntu
---

### Post by Ice Dragon on 2008-11-01
Hey all, I have a server running Ubuntu with several samba shares which all my windows computers use regularily.

The problem is when I copy a file from a windows computer onto the samba share on the linux computer its locked to anyone except that computer when viewing it on the linux server logged in as administrator.

I want these files to be accessable to everyone by default when they are copied and the ones i want restricted ill manually set. Its a bit annoying to have to command prompt and chown everything i copy.

---

### Post by cmnorton on 2008-11-03
I believe you have to map your users to that share using smbpasswd, and the user or users have to be a real user or users on the Linux system. 

So, if this is a share for the use of a group of people, you could create a login for that group, and map those users to it. If this is a share for one person, then create and individual account for that person and map to Windows account name, including domain name to the linux account name.

---

### Post by movrshakr on 2008-11-03
I have exactly this same problem and have not been able to resolve it.  The issue revolves around the owner and group names applied to file as they are put onto the linux server, and around the permissions applied to the file.  How does the linux server know what owner and group names to give a new file, and what permissions to give it, so that ANY user with access to that shared folder can fully access the files there?

Watching closely for the answer to this.

---


---
title: "Samba Troubles"
date: 2014-03-04
forum: New to Ubuntu
---

### Post by jacob25 on 2014-03-04
I've installed Samba (today, so I should have the latest version), and got it working with (supposedly) the root folder, but I can only access the /home/USER folder (replace USER with your account name).

I however, want full access to every file.

I am on a Windows 7 machine, and my server is running Ubuntu 12.04

---

### Post by coldcritter64 on 2014-03-04
> **jacob25 said:**
> I've installed Samba (today, so I should have the latest version), and got it working with (supposedly) the root folder, but I can only access the /home/USER folder (replace USER with your account name).

I however, want full access to every file.

I am on a Windows 7 machine, and my server is running Ubuntu 12.04

Why the need for "full acess to every file" ? 

Messing with ownership and permissions of system files for something like this can lead to disaster for your installation. Keep sharing to the home folder whereever you can. Be VERY careful altering any system files ownership or permissions; the sudoers file for instance, if altered, can render the system unusable -- no sudo=no way to administer the installation. That is only one example amongst many, especially if chown or chmod are used recursively, reinstallation is often the best way to fix the extreme mess ups they can cause.
Take care !

---

### Post by jacob25 on 2014-03-04
Yeah, I realized after setting up a few more things that it probably would be best just to put the files in my home directory, and move then elsewhere using PuTTY...

---


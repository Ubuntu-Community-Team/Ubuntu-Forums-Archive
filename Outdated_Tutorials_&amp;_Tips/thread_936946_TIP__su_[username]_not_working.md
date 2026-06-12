---
title: "TIP:  su [username] not working"
date: 2008-10-03
forum: Outdated Tutorials &amp; Tips
---

### Post by michaelkahl on 2008-10-03
On my Ubuntu Eee installation I borked something.  All of a sudden I couldn't use su [username] to change over to another account in the CLI.  I searched and searched.  Nothing came up for me on google or in forum searches.  Usually I just found information about the root account being disable and how to enable it.  
If you broke su like I did then hopefully this tip will help someone.

Below is the output from the ls command before the fix was applied.

$ ls -l /bin/su
-rwxr-xr-x 1 root root 25540 2008-08-22 16:07 su (green lettering)

I realized that these permissions were improper(after checking on another system).  So I changed permissions accordingly.

$ sudo chmod 4755 /bin/su

The chmod command above turned on SUID.  4=SUID 7=rwx(owner) 5=r-x(group) 5=r-x(everyone else)
Below you can see the correct output that I received after changing permissions.
$ ls- l /bin/su
-rwsr-xr-x 1 root root 25540 2008-08-22 16:07 su (redbox, white lettering)

  
Now the su command works properly.  So if you break it, here's how to fix it.

---


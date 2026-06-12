---
title: "Sudoer and Admin"
date: 2008-12-05
forum: Programming Talk
---

### Post by hosseinyounesi on 2008-12-05
Hi,
How I can get that a user is system admin or a sudoer ?

Thanks a lot

---

### Post by cl333r on 2008-12-05
System->administration->Users and groups

---

### Post by geirha on 2008-12-05
Add a user to the admin group to allow that user to use sudo.

---

### Post by dwhitney67 on 2008-12-05
> **hosseinyounesi said:**
> Hi,
How I can get that a user is system admin or a sudoer ?

Thanks a lot

A sudoer can be given some system admin rights, but denied others, or be given complete system admin rights (and thus have equivalent privileges to 'root').

In either case, when a sudoer or root are running an application, their user-id is 0.  In C or C++, this can be determined using the getuid() C library call.  In shell scripting, a call to 'id -u' will also provide this information.

---

### Post by hosseinyounesi on 2008-12-05
Thanks. I get users lists in my program, and now I want to know that the user is admin, sudoer or an usual one. Is there any way to d this in C++ or Python ?

---

### Post by dwhitney67 on 2008-12-05
> **hosseinyounesi said:**
> Thanks. I get users lists in my program, and now I want to know that the user is admin, sudoer or an usual one. Is there any way to d this in C++ or Python ?
There is only one true admin account:  root.

A sudoer can be looked up in /etc/sudoers.

All users can be found in /etc/passwd.

Any users not having the name 'root', and not found in /etc/passwd are not legitimate accounts.

P.S.  To peruse the /etc/sudoers file, your application will need to be run with root-privileges.

---

### Post by hosseinyounesi on 2008-12-05
How about the super user in ubuntu ?
What this line says ?
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
It means that all admin of the system(including superusers) are allowed to sudo ?! How can I get admins ?

Another question :
Is there any system call to use visudo in C++ ? (except using system())

Thanks

---

### Post by Reiger on 2008-12-05
That seems like there is a group called Admin. You can use the Users & Groups management applet (Users and Groups on Kubuntu) to add users to this group.

What this line means is that ALL members of 'admin' are allowed ALL superuser rights.

---

### Post by dwhitney67 on 2008-12-05
> **Reiger said:**
> That seems like there is a group called Admin. You can use the Users & Groups management applet (Users and Groups on Kubuntu) to add users to this group.

What this line means is that ALL members of 'admin' are allowed ALL superuser rights.
I believe the OP wants to do user lookups programatically, not by hand.

---

### Post by dwhitney67 on 2008-12-05
> **hosseinyounesi said:**
> How about the super user in ubuntu ?
What this line says ?
# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
It means that all admin of the system(including superusers) are allowed to sudo ?! How can I get admins ?

Another question :
Is there any system call to use visudo in C++ ? (except using system())

Thanks

I was just perusing /etc/group.  In that file, you should be able to determine if a user belongs to the admin group.

P.S.  Based on your questions, I would think that you are attempting to "re-invent the wheel".  Why are you not using code already developed by the Gnome to access user privileges and/or insert new users as sudoers?

---

### Post by mssever on 2008-12-05
Due to the flexibility of sudo, to find out if a user has sudo access, you need to look it up in the context of the specific command you want to run with sudo. That means understanding and correctly parsing sudoers. Examining a user's group might work in some cases, but it won't work in all cases, especially if the user has tweaked their sudoers file.

In short, unless this problem has already been solved, solving it would be non-trivial. Your best bet might be to simply try to run as root and see if that fails.

@dwhitney67:
Small correction: Any account with a uid of 0 has root privileges, regardless of its name, though I wouldn't be surprised if some programs examine the username rather than the uid to determine what privileges they have.

---

### Post by dwhitney67 on 2008-12-05
> **mssever said:**
> ...

@dwhitney67:
Small correction: Any account with a uid of 0 has root privileges, regardless of its name, though I wouldn't be surprised if some programs examine the username rather than the uid to determine what privileges they have.
I did not make a mistake; perhaps you misunderstood my post.  Both getuid() and 'id' will return 0 for scripts or applications that are executed by the 'root' account or by a sudoer (who is running the command using sudo).

---

### Post by mssever on 2008-12-05
> **dwhitney67 said:**
> I did not make a mistake; perhaps you misunderstood my post.  Both getuid() and 'id' will return 0 for scripts or applications that are executed by the 'root' account or by a sudoer (who is running the command using sudo).
I was referring to this:
> **dwhitney67 said:**
> Any users not having the name 'root', and not found in /etc/passwd are not legitimate accounts.

---

### Post by dwhitney67 on 2008-12-05
> **mssever said:**
> I was referring to this:
 Originally Posted by dwhitney67  View Post
Any users not having the name 'root', and not found in /etc/passwd are not legitimate accounts.

Sorry if the quote (that is, my quote) does not show properly...

What I was stating is that if I were to give you a user-account, say "foo", then it is obviously not "root"; if "foo" does not appear in /etc/passwd, then obviously I have given you a bogus account.  Substitute "bogus" with "legitimate" and then maybe you will understand what I was stating.

---

### Post by mssever on 2008-12-06
> **dwhitney67 said:**
> Sorry if the quote (that is, my quote) does not show properly...

What I was stating is that if I were to give you a user-account, say "foo", then it is obviously not "root"; if "foo" does not appear in /etc/passwd, then obviously I have given you a bogus account.  Substitute "bogus" with "legitimate" and then maybe you will understand what I was stating.
OK. I understand you now.

---


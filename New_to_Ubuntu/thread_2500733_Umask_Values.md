---
title: "Umask Values"
date: 2024-09-10
forum: New to Ubuntu
---

### Post by jmkmx on 2024-09-10
Hello forum,


What would be the umask value for giving a file rwx rights to the user, group and others?

I know 000 does the following:

```
[TABLE="width: 1"]
[TR="bgcolor: #202325"]
[TD]000[/TD]
[TD]File:rw-rw-rw-[/TD]
[TD]Directory:rwxrwxrwx[/TD]
[/TR]
[/TABLE]

```
 
But I could not find a way to grant execute rights while using the umask mode.

---

### Post by 1fallen on 2024-09-10
umask is subtractive, not prescriptive: permission bits set in umask are removed by default from modes specified by programs, but umask can't add permission bits. touch specifies mode 666 by default (the link is to the GNU implementation, but others behave in the same way; this is specified by POSIX), so the resulting file ends up with that masked by the current umask: in your case, since umask doesn't mask anything, the result is 666.


The umask acts as a set of permissions that applications cannot set on files. It's a file mode creation mask for processes and cannot be set for directories itself. Most applications would not create files with execute permissions set, so they would have a default of 666, which is then modified by the umask.


More Info: [https://www.cbtnuggets.com/blog/technology/system-admin/umask-file-permissions-a-crash-course](https://www.cbtnuggets.com/blog/technology/system-admin/umask-file-permissions-a-crash-course)

My session now is:
```
umask
0007
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> umask -S
u=rwx,g=rwx,o=

```
Or
```
&#9472;> umask 027
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;>
&#9474;~ 
&#9492;&#9472;> umask -S
u=rwx,g=rx,o=

```

That link has a lot of good info to digest.

---

### Post by jmkmx on 2024-09-12
Thanks for the thorough explanation...

---

### Post by 1fallen on 2024-09-12
Your Welcome, hope that answers most of your questions with umask

---


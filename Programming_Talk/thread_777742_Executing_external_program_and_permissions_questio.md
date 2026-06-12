---
title: "Executing external program and permissions question"
date: 2008-05-01
forum: Programming Talk
---

### Post by jakev383 on 2008-05-01
I'm trying to set up some tasks on my internal web server to be called from a web page. The PHP script calls my C program, and my question is this:
If I call an external program in a C program, for example
```

system("mv /etc/testfile /backup/");

```
and compile the program as root but then change the ownership of the compiled program to www-data so as to be executed by the apache process, will it still perform the mv command with root privileges?  I need to be able to run these commands with root privileges unfortunately, and do not want to add sudo privileges to www-data or anything else as obtrusive as that.

Thanks in advance!

---

### Post by mssever on 2008-05-01
Programs are executed with as the user that called them, unless they explicitly change their owner (and have permission to do so) or are setuid. So the only way to run mv as root is to call it as root (such as via sudo). You could make it setuid, but that would be a really bad idea.

You have several options. One is to use visudo to allow just the sudo permission that's appropriate (and disable passwords in that case since you'll presumably be running non-interactively).

Another option is to do all the work from within your own language, and use whatever permissions modification is available there.

The third option is to modify the permissions of all affected files so that www-data has the proper permissions.

---

### Post by jakev383 on 2008-05-01
I'm using C to write the programs but have never attempted something like this before.
How does an application like Webmin and the likes perform these actions without using sudo?  I'm trying to do this without using sudo, so any suggestions are appreciated.
Thanks!

---

### Post by nanotube on 2008-05-01
> **jakev383 said:**
> I'm using C to write the programs but have never attempted something like this before.
How does an application like Webmin and the likes perform these actions without using sudo?  I'm trying to do this without using sudo, so any suggestions are appreciated.
Thanks!

i think the easiest thing for you to do would be to give www-data user  write access to the /backup directory.

---

### Post by mssever on 2008-05-02
> **jakev383 said:**
> I'm using C to write the programs but have never attempted something like this before.
How does an application like Webmin and the likes perform these actions without using sudo?  I'm trying to do this without using sudo, so any suggestions are appreciated.
Thanks!

I've never used Webmin, so I don't know how it works. I have heard, though, that it keeps its configuration separate, and then somehow merges it in as appropriate. The best way to find out how Webmin works would be to examine their code/docs.

Apache starts as root (some of its tasks must run as root), then it drops its privileges as soon as it can. That's actually a common design pattern, and might be the way Webmin works (that's just a guess).

---


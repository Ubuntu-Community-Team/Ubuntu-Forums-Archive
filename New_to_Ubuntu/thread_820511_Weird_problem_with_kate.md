---
title: "Weird problem with kate"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by linuxnovice on 2008-06-06
Hi,

I just installed Kubuntu Hardy Heron. Whenever, I use kate to open any file I get these messages on the konsole:
trying to create local folder /home/ss/.kde/share/apps/kate/sessions: Permission denied
trying to create local folder /home/ss/.kde/share/apps/kate/sessions: Permission denied
trying to create local folder /home/ss/.kde/share/apps/kate/sessions: Permission denied

I never got these messages on Gutsy, so was just wondering what was going on.

Thanks.

---

### Post by django0909 on 2008-06-06
Kate is trying to create a sessions folder in a place which it doesn't have permission to do so. If you run Kate as root does it do the same? I'm not suggesting thats a good idea of course but it would prove me to be correct.


You can read about Sessions here:[HTML]http://www.alweb.dk/blog/anders/kate_named_sessions[/HTML]


Good luck!

---

### Post by Cypher on 2008-06-06
Please run
```

ls -l ~/.kde/share

```
and show us the output..

---

### Post by linuxnovice on 2008-06-06
> **Cypher said:**
> Please run
```

ls -l ~/.kde/share

```
and show us the output..

The output is:
total 32
drwx------  2 ss ss 4096 2008-06-05 18:19 applnk
drwx------ 26 ss ss 4096 2008-06-05 22:09 apps
drwx------  6 ss ss 4096 2008-06-06 10:44 config
drwx------  2 ss ss 4096 2008-06-05 18:19 locale
drwx------  6 ss ss 4096 2008-06-05 22:02 mimelnk
drwx------  2 ss ss 4096 2008-06-05 18:19 services
drwx------  2 ss ss 4096 2008-06-05 18:19 servicetypes
drwx------  2 ss ss 4096 2008-06-05 21:24 wallpapers

I am ss the user and it seems that I have all the 3 permissions for all the files here....

I do not get the same message when I run as root, however, I do get some other "errors". The reason for the quotes is because, the messages call it an error but it still runs properly. Here are the errors I get when I run as root,
Error: "/var/tmp/kdecache-ss" is owned by uid 1000 instead of uid 0.
Error: "/tmp/kde-ss" is owned by uid 1000 instead of uid 0.
Error: "/tmp/ksocket-ss" is owned by uid 1000 instead of uid 0.

Thanks.

---

### Post by linuxnovice on 2008-06-06
Just found something. This thing does not happen with kwrite but only with kate.

---

### Post by txcrackers on 2008-06-07
Try this:
```
sudo chown -R ss.ss .kde/*
```
What this does is set the owner of everything in the KDE directory - *and sub-directories* - to your user.

My supposition is that when you were "sudo'd" to root, you ran Kate, which re-set the user/rights for the Kate-specific config and rc files.

---

### Post by linuxnovice on 2008-06-07
> **txcrackers said:**
> Try this:
```
sudo chown -R ss.ss .kde/*
```
What this does is set the owner of everything in the KDE directory - *and sub-directories* - to your user.

My supposition is that when you were "sudo'd" to root, you ran Kate, which re-set the user/rights for the Kate-specific config and rc files.

Hey, thanks that worked. But I still dont understand why that did not happen when I was using kwrite.

---


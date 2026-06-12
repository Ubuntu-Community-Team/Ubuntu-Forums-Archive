---
title: "What users do vsftpd and samba operate as/ will this work?"
date: 2009-10-30
forum: Programming Talk
---

### Post by sp0tz on 2009-10-30
So, I've got a functional fileserver which runs samba and vsftpd. I've just gotten vsftpd to work with anonymous logins. Apparently you need a root directory that is NOT writable by the ftp user, and a subdirectory that is. I've already got smb running quite well in one directory though, and I'd like to keep what functionality I have. What I'd like to have is:



/home/foo
the directory that users are dropped into when logging in via smb or ftp. Read/Write permissions for smb, but only read permission for ftp.

and

/home/foo/bar
read/write permissions for ftp as well as smb.



And if it's not wise to have share directories in /home/ I can move them elsewhere. So, is it possible to do this? To have whatever user samba masquerades as, as well as ftp logins with credentials have read and write permissions, but not the anonymous ftp user? My biggest concern is that I'm going to get the (OOPS: Child Died) or (Refusing to run with anonymous writable root) errors when I try to login anonymously with vsftpd.


Any insight on this, even just the usernames that smb and anonymous ftp logins use, would be helpful. Thanks!



P.S. I'm not entirely above disallowing anonymous ftp users to write, but as an aspiring network tech I'd like to figure this stuff out.

---


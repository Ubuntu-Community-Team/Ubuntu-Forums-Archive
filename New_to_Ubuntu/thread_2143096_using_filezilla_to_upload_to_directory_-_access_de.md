---
title: "using filezilla to upload to directory - access denied"
date: 2013-05-07
forum: New to Ubuntu
---

### Post by sniper8752 on 2013-05-07
I am trying to upload files to my /var/www folder, but it won't let me, via Filezilla.  I logged in with my root user account.  If I am logged in as root via FTP, shouldn't I be able to do anything (like upload files to a directory, in this case)?  Anyway, I know this is not the best way to solve this, but I did a "sudo chmod 777 www" to the directory so I could put the files.  Is there a better, more secure alternative to doing it this way?

---

### Post by alphacrucis2 on 2013-05-07
It would be much better to set up an ftp account with the appropriate access rights rather than logging in as root.

---

### Post by Moose on 2013-05-07
> **alphacrucis2 said:**
> It would be much better to set up an ftp account with the appropriate access rights rather than logging in as root.
+1. If there's a will there's a way. But this guy's solution is much easier. c:

---

### Post by sniper8752 on 2013-05-07
so what would i have to do... create a new user, and add him to a ftp group, and then limit the access controls?  i know this may be asking for a bit much.

---

### Post by sandyd on 2013-05-07
What FTP Server are you using on the server?

---


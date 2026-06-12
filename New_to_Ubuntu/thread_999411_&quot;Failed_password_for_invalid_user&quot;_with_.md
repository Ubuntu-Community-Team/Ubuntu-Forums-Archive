---
title: "&quot;Failed password for invalid user&quot; with ssh/scp/rsync"
date: 2008-12-01
forum: New to Ubuntu
---

### Post by John Chambers on 2008-12-01
My ubuntu (Hardy Heron) system's ssh, scp and rsync commands work fine for the initial uid that I installed.  But I've added several other uids, and incoming ssh/scp/rsync connections fail for all of them. They fail the same way.  For example, ssh asks for the password three times, and then says "Permission denied (publickey,password)."  Meanwhile, the tail end of /var/log/auth.log says:

Dec  1 20:55:48 minya sshd[3436]: Failed none for invalid user lwv from 192.168.1.101 port 51824 ssh2
Dec  1 20:55:50 minya sshd[3436]: pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=ap101  user=lwvFailed password for invalid user
Dec  1 20:55:52 minya sshd[3436]: Failed password for invalid user lwv from 192.168.1.101 port 51824 ssh2
Dec  1 20:56:03 minya last message repeated 2 times
Dec  1 20:56:03 minya sshd[3436]: PAM 2 more authentication failures; logname= uid=0 euid=0 tty=ssh ruser= rhost=ap101  user=lwv

So it seems that sshd is calling the PAM library, which is rejecting the login.  So far, I haven't found any clues.  Googling for "Failed password for invalid user" gets lots of hits, but they all seem to be talking about defending against attackers doing thousands of logins.  In this case, I'm trying to break into my own machine from another of my own machines (or my wife's).  The effect has been to block using the new machine as a server, since the valid users can't get in.

Anyone know what I might have done wrong, or how I could diagnose and fix this problem?

---

### Post by spiderbatdad on 2008-12-01
have you set AllowUser or AllowGroup in sshd_config? do you have an sshlogin group?

Of course don't forget the server must be restarted after changes to the config file.

---

### Post by John Chambers on 2008-12-01
> **spiderbatdad said:**
> have you set AllowUser or AllowGroup in sshd_config? do you have an sshlogin group?

Funny thing; I'd seen the terms "AllowUser" and "AllowGroup" in my googling, but I totally failed to those strings in any of the Help or man stuff.  "man -k AllowUser" finds no match, and neither does anything else I tried.

So they have something to do with sshd_config ... That seems to refer to a file /etc/ssh/sshd_config ... Found the AllowUsers, added the "lwv" ... Tried a login from another machine ... It failed exactly the same way.

So what else do I need to know to make it work? I still haven't seen the string "AllowGroup" anywhere; do I need to add it?  It isn't needed for my first uid (which is in the AllowUser list).

I might add that for the uid mentioned, I did a su - lwv", and it worked the first time.  So I do know the password, and the login daemon accepts it.

---

### Post by spiderbatdad on 2008-12-01
AllowGroup sshlogin

for example could be added to the file under AllowUser
then run ```
sudo adduser lwv sshlogin
sudo adduser anyone_else sshlogin #if you want to add anyone_else
``` So then you edit sshd_config to look like:
```
AllowUser Your_username lwv anyone_else
AllowGroup sshlogin
```

Then restart the server```
sudo /etc/init.d/ssh restart
```

Your admin account is automatically part of the sshlogin group, but still include your username if you want to login with it, and use things like xforwarding. Of course the other uids will be limited to permissions you set. If you have mutltiple users, you might consider setting their /home to 0750...

Edit: I appear to be wrong about the admin account. You will also need to add that account to the sshlogin group. This helps with security as well; that is requiring name and group login privileges.

---

### Post by spiderbatdad on 2008-12-01
ACK! of course you will have had to have created the group. lol```
sudo addgroup sshlogin
```then proceed with adding users to the group
[https://help.ubuntu.com/8.04/serverguide/C/user-management.html](https://help.ubuntu.com/8.04/serverguide/C/user-management.html)

---


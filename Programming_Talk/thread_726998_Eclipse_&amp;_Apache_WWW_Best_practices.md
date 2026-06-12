---
title: "Eclipse &amp; Apache WWW Best practices"
date: 2008-03-17
forum: Programming Talk
---

### Post by Preserved_Killick on 2008-03-17
I've just managed to set up Apache and would like to add/ edit files within www directory using Eclipse...which I can't, unless I start Eclipse as sudo. However, since the WWW directory is read-only unless I'm running as a root user, I'm predicting endless issues doing any website development to all files within my www folder.  This is purely for development. 

I'm thinking the answer it to change permissions on my www directory so I can access files as my normal user?

Would this be best?  How would I do this? 

Any better suggestions?

-Jeff

---

### Post by themusicwave on 2008-03-17
I think you have 2 options.

1) Use chmod to set the permission for www to allow write access.
2)Tell Apache to look elsewhere for web stuff, in a directory that you can write files into.

Either one should work.  Theoretically, these would both leave your system vulnerable.  However, I think that the attacker would only be able to mess with that one directory.  It should be a minimal risk.

I used option 1 on my system.  I also only start Apache when I am working on any web stuff.  Otherwise I turn it off.  This is probably a good idea for you as well.

I could be totally wrong about this, so perhaps others will enlighten us both.

---

### Post by SanderVermolen on 2008-03-17
I'd say a better solution is to add yourself to the apache group. That way you will be able to edit the files (also in Eclipse), but you will not corrupt the Apache install, or reduce security. 

You can change the groups you are in by using the usermod command (or the graphical "users and groups" program in the administration menu. Just don't forget to log in and out after you have changed anything, otherwise the changes will not have any effect.

---

### Post by Preserved_Killick on 2008-03-17
Sander,

I'm not sure I follow. I have two users, (under users & groups) myself and root. I don't see an apache group to add myself to? 

I must have installed Apache as root? 

I'm clearly new here feeling this out as I go..

-Jeff

---

### Post by themusicwave on 2008-03-17
I think perhaps he is suggesting that you create a new group called Apache.  Then you set the www directory to allow users of group apache to have read,write and maybe execute privileges to the folder.

---

### Post by mssever on 2008-03-17
If you installed via the repository, you should have a user www-data and group www-data. That would be the one to add yourself to.

I've moved my webroot to a more convenient location, which I own. All Apache cares is that it can read the stuff there. As long as you have sensible writing permissions set, you should be OK.

Also, you can configure Apache to only listen on the IP addresses you think is valid for development:

```
# /etc/apache2/ports.conf
Listen 127.0.0.1:80
```

---

### Post by skeeterbug on 2008-03-18
I use a vhost and point it to a directory in my home. This works on servers and workstations. With a server, I can setup an FTP server where my home is the root of my ftp login. Obviously with a workstation you can work directly with the files.

---


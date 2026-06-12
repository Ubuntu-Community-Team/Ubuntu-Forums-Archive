---
title: "Set Apache permissions by default?"
date: 2008-09-01
forum: New to Ubuntu
---

### Post by hazelwood on 2008-09-01
OK, so I've got an annoying problem here. I set up Apache 2.2.8 on Xubuntu and whenever I drag and drop files from my desktop (or wherever) into var/www I have to go through each file and set the properties from "none" to "read-only," otherwise I get the message "Forbidden You do not have permission to access..." when I navigate to it in my browser. I don't have to mess with it when I use FTP, only when I try to move items locally. Is there some way to set the properties of anything I move into that folder to "read-only" by default?

Thanks in advance.

PS: I'm a complete noob to Linux/Apache.

---

### Post by lovinglinux on 2008-09-01
Please don't follow my method before receiving advice from a security expert.

I installed LAMP here for web development, not to host a web site, so my setup uses a different listening port that is not forwarded from the router. I also disabled Apache and MySQL services from within session manager to avoid running them all the time. When I need, I manually start them with commands.

Anyways, I created a virtual host and changed the configuration of Apache to point to a directory under /home/me/www

You can see how to do this at [https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP#Virtual%20Hosts](https://help.ubuntu.com/community/ApacheMySQLPHP?action=show&redirect=LAMP#Virtual%20Hosts)

Don't know if this will help you, but I installed Joomla CMS, which requires writing permissions on several folders and files and everything is working this way.

---


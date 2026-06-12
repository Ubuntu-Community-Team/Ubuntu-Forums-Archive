---
title: "ODBC to M$ Access"
date: 2008-10-11
forum: New to Ubuntu
---

### Post by edpatterson on 2008-10-11
Greetings,

This is try 2. I believe my original post went to the bit bucket, if this is a duplicate I apologize. 

I am trying to connect to an Access database on a Windows 2003 server from a Ubuntu server (no gui, so no responses beginning with 'click' please).

Here is what I have:

Ubuntu Server(s) with Squid, Apache, MySQL
Windows Server 2003 with Access database maintained by BGInfo, Sysinternals user utility

If a user attempts to access a site not allowed by Squid, a static page is displayed. By default a mailto link is provided for the user.

I am trying to take it a step further, change the mailto link to a link to a page on the Apache server. The link will forward the URL and the users IP Address.

Using PHP I would like to connect to the Access database and retrieve the users name.

I setup a System DSN on the Windows box that points to the database but am stuck on how to get PHP from the Ubuntu box to use it.

Any help (spoon feeding, howto's additional documentation) would be greatly appreciated.

Ed

---


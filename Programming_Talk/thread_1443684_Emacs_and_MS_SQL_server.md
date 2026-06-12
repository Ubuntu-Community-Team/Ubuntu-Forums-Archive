---
title: "Emacs and MS SQL server"
date: 2010-03-31
forum: Programming Talk
---

### Post by lykwydchykyn on 2010-03-31
Recently, I've had MS SQL server added to the roster of databases I have to work with at the office.  I've had no luck getting it to work properly with Tora, so I'm wondering if there's a way to work with it in Emacs.

When I try loading sql-ms mode, I just get errors that seem to indicate that it's sending a bunch of switches to osql that the FreeTDS version of osql doesn't understand.

I have sqsh installed and working, and I'm wondering if there's a way to tell sql-ms mode to use sqsh instead? (and yes, I did try symlinking osql to sqsh, that doesn't work).

Alternately, can anyone suggest a comfy way to work with MS SQL server from Linux (that doesn't involve a virtual machine or remote desktop session)?

---

### Post by lykwydchykyn on 2010-04-01
Bump.

I've managed to hack some things together using emacs, sqsh, a python wrapper, and some hacks to allow piping into emacs buffers.

Still, if anyone has wisdom and experience with this I'd like to hear from you.

---

### Post by jvector on 2010-09-28
Hi,
I've nothing to add to what you have already done but I also am in this situation and am lookinginto it; will post if I find any alternatives.

---

### Post by eeperson on 2010-09-28
I can't comment about accessing SQL Server in Emacs.  However, I have used [SQuirreL SQL]("http://squirrel-sql.sourceforge.net/") to access a SQL Server database.  I used on windows but it should work for you since it is cross-platform because it is written in Java.  You will probably also need to download the SQL Server JDBC driver which can be found [here]("http://msdn.microsoft.com/en-us/sqlserver/aa937724.aspx").

---


---
title: "how to connect to sql server from ubuntu hardy"
date: 2008-06-10
forum: New to Ubuntu
---

### Post by new_student on 2008-06-10
how to connect and access data or file from sql server..????? i've been success to join windows domain and sharing folder with windows pc... but when i try to access file from sql server i even can't see the folder file or data on the server....please help me...what should i do.....

---

### Post by Jonas thomas on 2008-06-11
This is sort of my to do list also....
I found this link that looks promising:
[http://www.phpbuilder.com/columns/alberto20000919.php3]("http://www.phpbuilder.com/columns/alberto20000919.php3")

---

### Post by chris_nava on 2008-06-11
:confused: SQL Server is a Database, not a file server...

If you are trying to connect to a windows file server then look into Samba.
Specifically, you will need to install "smbfs" in order to be able to browse windows shares easily.

If you are trying to connect to a database then you will need an "SQL Client" application.  I'm not aware of one for Ubuntu.  However, there are several Java based ones that could do the trick.  [http://www.google.com/search?q=java+sql+client](http://www.google.com/search?q=java+sql+client)

You will also need the JDBC drivers for MS SQL Server.
[http://msdn.microsoft.com/en-us/data/aa937724.aspx](http://msdn.microsoft.com/en-us/data/aa937724.aspx)

---

### Post by acidsolution on 2008-06-11
sql server is not for file sharing 
if you want to connect to mysql of remote computer than this post might help you [http://ubuntuforums.org/showthread.php?t=716183](http://ubuntuforums.org/showthread.php?t=716183)

let me know if this is what you want :)

---


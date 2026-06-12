---
title: "hardy mount remote password protected smb share"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by hp3 on 2008-07-05
I have tried smbclient in a terminal, and I have access to the share

#smbclient //server-name/disk3 -R<myuserid>

works fine, but not in the GUI, and that is more than hard to be without.
How do I do this from the GUI?  ON 6.06 LTS server this works fine.
What is the trick in hardy desktop edition?

---

### Post by bodhi.zazen on 2008-07-05
Either :

Places -> Network -> navigate to share 

Places -> Connect to Server -> enter ip/server name

Open Nautilus ( Places -> Home) enter smb://server/share in the navigation bar ("Location : ")

Then enter user and pw

---

### Post by hp3 on 2008-07-06
I can mount smb shares, but all files are read only when using the GUI tools.  how can I change that?  if I use smbclient from a terminal, I can delete files or create new.

---

### Post by hp3 on 2008-07-08
ok, I have learned some more.
When I connect to the server, my files are created as nobody and the 
the group is wheel. (BSD server), but all windows clients gets correct 
owner and file permissions.  If I mouunt with smbclient I am my self again, and giving my password all is fine.  No password when using nautilus.

I hope some one can help me solve this.

---


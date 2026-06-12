---
title: "smb.conf printers not browsable"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Rebecca@tauri on 2008-06-04
Hello,

I'm printing with CUPS on my samba server. I am having trouble connecting to printers from clients by browsing.

In my smb.conf file I have:

[printers]
browseable = yes 

but when I run testparm and view the dump of service definitions it says:

[printers]
browseable = no

(I have saved the file, tried restarting the server, and testparm does not report any syntax errors)

Any idea what I'm doing wrong?

---


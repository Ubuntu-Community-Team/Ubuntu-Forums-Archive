---
title: "opening ports"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by catroaring on 2008-05-31
is a firewall installed with ubuntu?  if so, how do i open ports?  i work with many artists, and we use Azureus to transfer files.  but since i changed to ubuntu they can not connect to me(they can but its very slow).

---

### Post by sayakb on 2008-05-31
Firewalls can either open or close ports, but cannot make them slow. Ubuntu has it's own firewall k/a IPTables. To configure this firewall and to open a specific port, you can install Firestarter from the repos. After installing firestarter, try to connect again. On doing so, the firestarter icon will go red and the port you were accessing would be listed under Events tab. Right click on the port and select "Allow inbound services on port"
You donot otherwise need firestarter.

---


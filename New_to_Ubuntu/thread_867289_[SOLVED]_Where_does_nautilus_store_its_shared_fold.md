---
title: "[SOLVED] Where does nautilus store its shared folders data?"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by ptn107 on 2008-07-22
When I share a folder through the nautilus sharing extension, where does it save the data that defines those shares?  It's not in /etc/samba/smb.conf or /etc/exports.

---

### Post by Tim Sharitt on 2008-07-22
Each share has a file in /var/lib/nautilus/samba/usershares

---


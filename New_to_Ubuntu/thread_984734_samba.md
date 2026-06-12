---
title: "samba"
date: 2008-11-16
forum: New to Ubuntu
---

### Post by guptavivek34964 on 2008-11-16
:confused::confused::confused::confused::confused::confused::confused:i have installed samba n i can share my docs on lan but they are not visible in windows os

---

### Post by gizmobay on 2008-11-16
You have to create a samba user on the ubuntu side. It's easier if you create a user with the same login and password as windows. For example, #sudo smbpasswd -a windowsuser then enter the windows password. After you do this, I'd restart samba then logout then in onto windows then on windows "my network places" add network then enter /your.i.p./sharedir/

---


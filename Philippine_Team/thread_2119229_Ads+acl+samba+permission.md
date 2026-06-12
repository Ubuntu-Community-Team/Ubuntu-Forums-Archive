---
title: "Ads+acl+samba+permission"
date: 2013-02-23
forum: Philippine Team
---

### Post by jmbalanag on 2013-02-23
mga sirs/maams. paano po iconfigure ang samba + ADS + permissions +ACL para sa subfolders?

mga ilang araw na ako nagbabasa sa forums kaso wala kasi ako mahanap na tuts para sa "ADS+ACL+SAMBA+PERMISSION"

Member na po ng domain and Ubuntu (12.04) File Server ko, kaso pag gumagawa ako 
ng new share sa samba, read permission lang lahat ng AD user ko.
Gusto ko sana ng ganitong set up:

Main Folder (all AD Users have read access)
-Subfolder 1 (all have read access, but only user 1 have write access)
-Subfolder 2 (all have read access, but only user 2 have write access)
-Subfolder 3 (all have ready access except for user 1 and user 2, user 3 has write access.

Sana po may makatulong. Salamat.

Note (my set up): 
1. Samba security = ADS
2. Ubuntu 12.04 (Server) already joined in the Domain and is already a Member in the Active Directory

---


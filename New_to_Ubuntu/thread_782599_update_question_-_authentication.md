---
title: "update question - authentication???"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Loki*PI on 2008-05-05
I launch Update Mgr.  It says to update two update mgr updates.  Says they are from GNOME.  When I go to install them I'm warned they cannot be authenticated. 

This appears to be an official update of a basic component of the OS.  Why can it not be authenticated?  Has someone hacked in an distributing malware through update mgr?  This seems rather odd.

Thanks for your insights.

Loki

---

### Post by subzero316 on 2008-05-05
may be a 3rd pary s/w update...

---

### Post by vishzilla on 2008-05-05
Go to System>Admin>Software Sources. List down all of the 3rd party repo you have enabled from the '3rd Party' tab

---

### Post by Loki*PI on 2008-05-05
Only thing enabled is medibuntu.org/gutsy free non-free

---

### Post by vishzilla on 2008-05-05
In software sources, check the Authentication tab, you will have two keys from Ubuntu
1. Ubuntu Archive
2. Ubuntu CD
and one from Medibuntu
3. Medibuntu packaging team.

If you don't have the medibuntu signing key, download it using this, from the terminal
```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```

---

### Post by Loki*PI on 2008-05-05
Thank you very much that seems to clear it up.  Undoubtedly something I should have done previously.  

Thanks again.

---


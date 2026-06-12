---
title: "General input/output error when saving to network drive"
date: 2012-04-21
forum: New to Ubuntu
---

### Post by Boyntonstu on 2012-04-21
I can save a text editor file over the LAN, no problem.

LibreOffice fails and gets General input/output error.

Does LibreOffice need tweaking?

---

### Post by bodhi.zazen on 2012-04-21
Can you post the exact error message ?

And we need more details - is the network drive samba ? nfs ? sshfs ? other ?

If all else fails, run libreoffice from the command line and see what error message it is throwing.

---

### Post by derekshaw on 2012-12-03
can't open/save ODF format documents on NFS-mounted shares:
  "general input/output error while..." 

```
which soffice
vi /path/to/soffice
```
find and comment out the SAL_ENABLE_FILE_LOCKING code (so it looks like this):
```
# file locking now enabled by default
#SAL_ENABLE_FILE_LOCKING=1
#export SAL_ENABLE_FILE_LOCKING
```

[LIST]
[*]above example is for libreoffice 3.5.
[*]different versions of open/libreOffice have different contents for soffice -- GIYF
[*]this has reset to the default (file locking enabled) a couple of times on my system since I found the fix on google (updates to LO, I assume).  Eventually I'll make enough time to figure out how to persist the changes.
[/LIST]

---


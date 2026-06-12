---
title: "paano magshare ng cd/dvdrom ng ubuntu"
date: 2009-04-15
forum: Philippine Team
---

### Post by Script Warlock on 2009-04-15
gusto sana share ang dvdrom drive sa server....right clicking the drive won't enable the sharing at eto yung display   

'net usershare' returned error 255: net usershare add: cannot share path /media/cdrom0 as we are restricted to only sharing directories we own.
	Ask the administrator to add the line "usershare owner only = False" 
	to the [global] section of the smb.conf to allow this.> 

---

### Post by loell on 2009-04-15
try mo e share sa superuser level mode, sudo nautilus , then redo the process.

---

### Post by Script Warlock on 2009-04-15
so need to add something sa smb config pala..just like that hahahahahah iba talaga to mga nauna sa amin:lolflag:

ok na ho boss loell as what u said, solve....ty boss

---


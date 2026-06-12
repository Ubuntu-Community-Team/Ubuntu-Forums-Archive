---
title: "Garbled DOS file names from shared Ubuntu directory"
date: 2008-11-19
forum: New to Ubuntu
---

### Post by Frogbarf on 2008-11-19
I am using my Ubuntu box as a file server via a shared directory. The machines that access this are both Win98, one of them Win98SE, the other the original release, both updated just before MS discontinued Win98 support.

32-bit software running on the Win98 machines works just fine, but I still use a few pieces of old 16-bit software dating from Win3.1 days. These don't know about long file names, which only came in with Win95.

Whenever one of these 16-bit programs accesses the shared directory, many of the file & directory names are garbled. 

Examples:

dos&wfwg comes out as DU38X4~0
! comes out as _2X68Q~6
!_SOFTWA comes out as _1UQCB~H
16-BIT comes out okay

Presumably this is because Samba is generating DOS file names on the fly and gets confused by the exclamation point and underscore even though these characters are within the first 127 characters even in Unicode.

Does anyone have the faintest idea what is happening? If so, is there any way I can coerce Samba into generating short file names using the algorithms used in 32-bit versions of Windows?

:confused:

---


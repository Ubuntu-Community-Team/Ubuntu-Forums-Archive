---
title: "Start Recovery and Finish ?"
date: 2017-03-21
forum: New to Ubuntu
---

### Post by Bob_Reksten on 2017-03-21
Hi,

This morning to open any LIbre Office file I must accept and click on "start recovery" and then finish to open it, and even if I open the same file several times!
Can someone please send me a 'fix"?
Thanks
Garoolgan-17

---

### Post by ajgreeny on 2017-03-21
Having managed to open that apparently corrupt file you probably need to save it again, immediately without making any other edits to it, but for safety I suggest you save it under another name, so that the original is still around if it is needed (no idea why it should be needed if it's corrupt but it is another safety valve for you).

Once saved with its new name, hopefully it will now open properly for you.

If this is happening for all LO files that you open I think it is likely your LO configuration that is corrupt so try renaming the folder **~/.config/libreoffice** as **~/.config/libreoffice-backup**.

---


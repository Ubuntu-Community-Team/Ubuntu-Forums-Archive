---
title: "Mounting errors?"
date: 2013-02-28
forum: New to Ubuntu
---

### Post by joemartin on 2013-02-28
[COLOR=#333333]Is there a fix for this mounting error message??? using mate desktop.  Thanks again for the knowledge.

[/COLOR]

---

### Post by slickymaster on 2013-02-28
Do you actually have a floppy drive installed in your computer? Is there a floppy interface enabled in the BIOS even if there's no actual drive in the machine?

---

### Post by joemartin on 2013-02-28
> **slickymaster said:**
> Do you actually have a floppy drive installed in your computer? Is there a floppy interface enabled in the BIOS even if there's no actual drive in the machine?


There is no floppy drive on pc.

I had a dual boot with windoze 7....

With gparted I deleted windoze 7 drive and expanded Linux's.  Since then I get this error.  I have also noticed i/o buffer errors when shutting down????.  Assuming they are related?

---

### Post by slickymaster on 2013-02-28
As you don't have such a drive you can always edit your **/etc/fstab** file. In this file there should be a line that references the floppy disc. So at a terminal window, run ```
gksudo geany /ect/fstab
``` and just put a # in front of that line.

---


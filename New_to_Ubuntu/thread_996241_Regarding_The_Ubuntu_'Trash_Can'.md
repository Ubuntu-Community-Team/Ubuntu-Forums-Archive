---
title: "Regarding The Ubuntu 'Trash Can'"
date: 2008-11-28
forum: New to Ubuntu
---

### Post by azurepancake on 2008-11-28
Recently, I've made a very large download off the Internet, about 2GBs in size. It was a .ISO file in which I used and thought I was done with. I then went and deleted the file from a CLI, using the remove (rm) command. I have not cleared my trash since then.

Suddenly, I have realized that I need this file once more and it would be great if I could simply remove it from my trash, back to my home directory. I don't blame the OS for this, it was my fault that I deleted it, but when I check the trash, this file does not appear to exist.

I wonder, is there something I don't know about how data is removed from the hard drive? Maybe it was because the file was too large? I have tons of free disk space. Or perhaps it was because I deleted the file using the remove command?

If anyone could shed a little light on this, I'd greatly appreciate it!

Thank you for reading :)

---

### Post by Billybob97060 on 2008-11-28
I think generally the way it works is that whenever you delete something over a certain size it just automatically deletes it as if you emptied the trash because the trash can is only set to hold a certain amount of data

---

### Post by azurepancake on 2008-11-28
Ah, yes. That is what I feared!

Oh well, guess I'll download it again. Thank you very much for sharing your knowledge!

---

### Post by hessiess on 2008-11-28
the rm command deletes files bypassing the trashcan alltogether.

---

### Post by skillllllz on 2008-11-28
If you use rm, it's gone. The trashcan is a feature of the window manager, not a feature of linux itself. When you execute rm, you are instructing linux to remove the file completely, no "if's," "and's," or "but's." Exercise caution when using the CLI; some commands can and will do ireprable damage to the OS and/or your personal data.

---


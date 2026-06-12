---
title: "Vista suddenly unable to access ext3 partitions?"
date: 2008-06-17
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-06-17
A month or two ago, I installed the 'FS-Drive' program that allowed Vista to read and write to ext3 partitions. However, that program has suddenly stopped working--now, Vista insists that I need to format the drives to access them. How can I access the ext3 partitions again on Vista?

---

### Post by Pjotr123 on 2008-06-17
Strictly speaking, that's something that doesn't belong here....

Furthermore, it's unwise to let contaminated Windows touch your shiny clean Linux partitions. Windows viruses and other malware now can sink their claws in the Ubuntu partition.

---

### Post by Inxsible on 2008-06-17
> **Jaded Misanthrope said:**
> A month or two ago, I installed the 'FS-Drive' program that allowed Vista to read and write to ext3 partitions. However, that program has suddenly stopped working--now, Vista insists that I need to format the drives to access them. How can I access the ext3 partitions again on Vista? Ar these external drives or internal?

It is most likely that there was an unclean shutdown under Ubuntu. Start up Ubuntu and do a clean unmount of those drives before trying it in Vista.

See if that works for you?

---

### Post by Jaded Misanthrope on 2008-06-17
Unwise or not, I have stored the vast majority of my files on one of the partitions that I now cannot access. Accessing them with Vista would be *very* useful.

They're internal drives, yes. I'll try your suggestion now.

---

### Post by fiddledd on 2008-06-17
Have a look here:

[http://freshmeat.net/projects/ext2ifs/](http://freshmeat.net/projects/ext2ifs/)

---

### Post by Inxsible on 2008-06-17
> **Jaded Misanthrope said:**
> Unwise or not, I have stored the vast majority of my files on one of the partitions that I now cannot access. Accessing them with Vista would be *very* useful.

They're internal drives, yes. I'll try your suggestion now.you could also just try re-installing ext2ifs. I had noticed that it wouldn't access the drives and re-installing almost always seemed to work.

---


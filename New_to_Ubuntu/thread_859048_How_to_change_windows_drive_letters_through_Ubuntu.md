---
title: "How to change windows drive letters through Ubuntu?"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by sharks on 2008-07-14
How to change windows drive letters through Ubuntu?

---

### Post by hyper_ch on 2008-07-14
edit the windows registry

---

### Post by sayakb on 2008-07-14
Ubuntu does not use drive letters, so you may not be able to change them on Ubuntu. You can use programs like Partition Magic in windows to change the drive letters.

---

### Post by coffeecat on 2008-07-14
Do you mean to change 'E:' say, to 'F:' because, as the previous posters say, this is probably not possible from Linux. The Windows drive letter convention is peculiar (in more than one sense of the word) to Windows, so there is no need for Unix-type systems to be able to change them - I guess.

Or do you mean to change the Windows partition label? That's quite possible. You can relabel both NTFS and FAT32 partitions from Linux. If that's what you mean, post back and I'll tell you how.

---

### Post by Vivaldi Gloria on 2008-07-14
> **sharks said:**
> How to change windows drive letters through Ubuntu?

There's already an administrative tool called "Computer Management" in windows XP which you can use to change drive letters.

If you cannot see the admin. tools then right click the start menu and enable admin tools from the settings (properties?).

Why do you want to use ubuntu to change it when it's something about windows registry and there is a already a tool in windows?

---

### Post by SpEcIeS on 2008-07-14
format c: /u

---

### Post by coffeecat on 2008-07-14
> **SpEcIeS said:**
> format c: /u

Yes, but that will do an unconditional (destructive) format, won't it? Is that what you meant?

---

### Post by SpEcIeS on 2008-07-14
:biggrin: Yes. That is what it would do alright. One could try out **fdisk**.

---


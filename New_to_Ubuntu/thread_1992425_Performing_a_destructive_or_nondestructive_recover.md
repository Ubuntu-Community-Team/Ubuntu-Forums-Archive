---
title: "Performing a destructive or nondestructive recovery of windows"
date: 2012-05-31
forum: New to Ubuntu
---

### Post by Maleekw1 on 2012-05-31
I was wondering what performing either a destructive or nondestructive recovery of windows xp would do to my ubuntu partition.

---

### Post by strask on 2012-05-31
> **Maleekw1 said:**
> I was wondering what performing either a destructive or nondestructive recovery of windows xp would do to my ubuntu partition.

I don't know what you mean by destructive or nondestructive recovery of windows. I assume that you mean taking some steps to restore data from a backup; what tools would you be using to perform this restore?

---

### Post by irv on 2012-05-31
I believe if you do a restore from the windows CD it will end up only booting into windows. You will need to boot a live Ubuntu CD to fix your grub menu. Be careful. Do some searching and reading before you do this.

---

### Post by deadflowr on 2012-05-31
You'll only hurt your Ubuntu partition if you decide to reinstall your XP across the whole disk. The ubuntu partition will otherwise remain isolated, hence the term partition. If you boot through grub you will need to follow irv's advice and fix grub with a livecd.

---


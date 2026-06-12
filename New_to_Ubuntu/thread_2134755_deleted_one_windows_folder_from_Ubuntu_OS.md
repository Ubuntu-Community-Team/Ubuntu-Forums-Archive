---
title: "deleted one windows folder from Ubuntu OS"
date: 2013-04-12
forum: New to Ubuntu
---

### Post by susanvarghese on 2013-04-12
Hello to All,
I have 2 partitions in my laptop, Vista and Ubuntu 10.04 LTS.
I can access my windows drive through Ubuntu.
I was working on Ubuntu and wanted to copy some files from windows, for which I mounted the WIN drive. By mistake while searching for the file, I deleted the "Desktop" folder.
Is there any way to recover it?
When I unmounted the Win drive, it asked me if I would like to empty the trash, but I clicked "Dont empty trash". So I know its there, but I dont know where to locate it and replace it back.
Kindly help.
Thanks


Susan

---

### Post by black veils on 2013-04-12
perhaps there is a **.Trash-1000** folder on the windows partition, where you can find your deleted desktop?

or your files could be in the ubuntu **filesystem** **/root/.local/share/Trash/files** you will need to open the file manager with root privileges using the command ```
gksudo nautilus

```
i'm not sure how it works for your sort of situation, but it wont hurt to look.

---


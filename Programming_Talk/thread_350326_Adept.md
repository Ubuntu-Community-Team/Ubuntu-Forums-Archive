---
title: "Adept"
date: 2007-01-31
forum: Programming Talk
---

### Post by Clouseau on 2007-01-31
I installed Adept in and used it for awhile and now when I click it, I get the following msg:
Failed to execute child process "kdesu" (No such file or directory)

What does this mean and how do I rectify this? I have tried uninstalling Adept and reinstalling it and get the same message. Please advise. Thanks :)

---

### Post by Jucato on 2007-01-31
Did you install Adept on Ubuntu/GNOME? If yes, try to edit your menu entry for Adept, and check if it says something like "kdesu adept_manager" (on Edgy) or "kdesu adept" (on Dapper). If you are on GNOME, change "kdesu" to "gksudo".

---

### Post by Clouseau on 2007-02-01
Where do I find the menu? Is it on the Applications or do I do this via the Terminal?

---

### Post by Jucato on 2007-02-03
Sorry for not replying ASAP. The menu is the K Menu. Right-click on the K Menu icon and select the Menu Editor.

---

### Post by Clouseau on 2007-02-06
But I am using Ubuntu. Where can I access it on Ubuntu? It worked before and then poof, I get this msg.

---

### Post by Jucato on 2007-02-06
Ah ok...  you're using Ubuntu and installed Adept?

If you are using Ubuntu, go to Applications -> Alacarte Menu Editor. Look for the entry for Adept, and if it says "kdesu adept_manager", change it to "gksudo adept_manager". Basically, kdesu isn't installed on Ubuntu, which uses gksudo.

---

### Post by DopeFish on 2007-02-12
I've had the exact same problem as Clouseau, followed your tips and after clicking on Adept it just said: Starting... and nothing happend.

What could be the problem?

---

### Post by tokh on 2007-03-16
> **Jucato said:**
> Did you install Adept on Ubuntu/GNOME? If yes, try to edit your menu entry for Adept, and check if it says something like "kdesu adept_manager" (on Edgy) or "kdesu adept" (on Dapper). If you are on GNOME, change "kdesu" to "gksudo".

thank you so much !!!

---


---
title: "Is it a possible bug in the Trash?"
date: 2008-06-29
forum: New to Ubuntu
---

### Post by Victor Dolirio on 2008-06-29
Hi,

I'm having a strange problem with my trash directory, when I access the directory in graphical mode by trash:///, i'm seeing a recent directory that i've been deleted (ps. the current user don't have permissions to remove it), but when I access the directoy ~/.local/share/Trash/files to try to remove by using sudo, this directory don't exists!!! wow, what can I do?? I've restarted my computer, but this problem persist!

tanx all.

---

### Post by Victor Dolirio on 2008-06-29
I'm using Ubuntu 8.04...

---

### Post by iaculallad on 2008-06-29
On Hardy:

For User's Trash:

```
/home/your_user_name/.local/share/Trash
```

For Root's Trash:

```
~/.local/share/Trash
```

When in Gutsy:

```
~/.Trash
```

---

### Post by Victor Dolirio on 2008-06-29
this problem happen in my user's local trash, this mean, ~/.local/share/Trash. But, what I must to do? I want to remove this "ghost" directory...

---

### Post by iaculallad on 2008-06-29
Had you tried:

```
sudo rm -rf ~/.local/share/Trash/files/*
```

---

### Post by Victor Dolirio on 2008-06-29
Yes, i've tried this.

I don't be sure if the problem is that I can't remove files in ~/.local/share/Trash/files or if the problem is that the symbolic path trash:/// that is used by navigator in graphical enviroment is showing incorrectly this files... I'm sayng that because if I do ls within ~/.local/share/Trash/files on console, nothing is displayed, only in navigator, when I click in the trash icon or trying access trash:///. :s

---


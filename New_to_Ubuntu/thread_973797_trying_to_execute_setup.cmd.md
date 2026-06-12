---
title: "trying to execute setup.cmd"
date: 2008-11-07
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-07
I have a folder on my desktop. Its an application i want to install or am trying too. hldstart-v1.4.2 in this folder is a file "setup.cmd" I'm guessin i need to execute this file to install the app. anyone know how i can do this. I tried to use sudo in terminal but i don't know what i'm doing yet. Only been on ubuntu for 2 days kubuntu 1 day for a grand total of 3 days. But i like it.

Thanks for the help. Sorry if i sound retarded.

---

### Post by pgorillaman on 2008-11-07
Setup.cmd is usually a shell script to install on Windows. Look for a similarly named script that ends in .sh. So maybe setup.sh. Run this instead. It is very likely that you'll have to run it with sudo. I would guess something like:
```
sudo ./setup.sh
```

---

### Post by glotz on 2008-11-07
Open a terminal. Change the files' permissions to allow execution 
[B]
chmod +x path/to/file[/B] and then run it (probably don't need sudo)

**/path/to/file** (Use TAB to autocomplete the path in terminal)

---


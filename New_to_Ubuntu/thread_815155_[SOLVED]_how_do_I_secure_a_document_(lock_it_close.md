---
title: "[SOLVED] how do I secure a document (lock it closed) on a family computer?"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by Samurai Penguin on 2008-06-01
how do I secure a document (lock it closed) on a family computer? thanks

---

### Post by sayakb on 2008-06-01
You can put it inside a folder, say its inside a folder Mike inside your Documents, then do:
```
sudo chmod -r ~/Documents/Mike/Document.odt
```

Naturally, do +r to grant access again. Does you family know your system's password?

---

### Post by blairm on 2008-06-01
If it's in open office, go to file-save as. In the box where you enter the document's name and location there will be an option to save with password.

When you or anyone else tries to open the document later, they have to enter the password you nominated.

Cheers,

Blair

---

### Post by dje on 2008-06-01
If you are using Hardy Heron right click on the file and select 'Encrypt'

hope that helps,
dje

---


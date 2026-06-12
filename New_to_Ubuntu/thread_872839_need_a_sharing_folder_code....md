---
title: "need a sharing folder code..."
date: 2008-07-28
forum: New to Ubuntu
---

### Post by scartmell on 2008-07-28
in the terminal, i'm in as root, and I did a mkdir "shares" to make the folder in the root directory.

now i need to find a code that will allow me to share this folder (or at least give me the permission to right click>sharing options


thanks.

---

### Post by eightmillion on 2008-07-28
Where did you put this folder? What's the full path?

---

### Post by eightmillion on 2008-07-28
You should just be able to enter this command to be able to right click and share the folder...
> sudo chmod 755 /path/to/folder

---

### Post by scartmell on 2008-07-28
perfect. thanks a bunch.

---


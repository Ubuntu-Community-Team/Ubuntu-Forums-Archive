---
title: "Command to Open Spreadsheet"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by Quarkrad on 2013-08-13
I can launch calc from the terminal by typing **libreofice --calc**.  If I have a spreadsheet called test.ods in my ~/**Documents/Passwords** folder what command would I enter in Terminal to launch it?

---

### Post by DuckHook on 2013-08-13
```
libreoffice -o ~/Documents/Passwords/test.ods
```

---

### Post by Quarkrad on 2013-08-13
Many thanks for speedy reply.

---

### Post by DuckHook on 2013-08-13
Insomnia anyways. Glad I could help.

---

### Post by Cheesemill on 2013-08-13
Another method is to use the xdg-open command. This will open a file with it's default application.
```
xdg-open ~/Documents/Passwords/test.ods
```

---


---
title: "[SOLVED] network manager asking for pasword"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by Nxion on 2008-06-08
Every time I log in to my laptop it asks me for a password for 2 things. One is "nm-applet" the other is "cGmail" which check gmail. I don't know why it is asking for a password. It never used to until recently, Any idea how to set it so it saves a password so it doesnt ask me every time?

---

### Post by ibuclaw on 2008-06-08
Most efficient way I find to fix this is by removing the somehow corrupted keyrings.

Press "**Alt+F2**" and type in
```
nautilus ~/.gnome2/keyrings
```
And remove the entire contents of the folder in the new window (it'll be something like three files named "default" "default.keyring" and "login.keyring".)

Then logout/login. You'll be prompted for a password, but thereafter you shouldn't be prompted again. (Or if you still do, look for a small checkbox with the title like "Do not ask me again" or "Remember".

Regards
Iain

---

### Post by Nxion on 2008-06-09
Thanks tinivole, I will try this tonight.

---

### Post by Nxion on 2008-06-10
Thanks for the info. It fixed it. :)

---


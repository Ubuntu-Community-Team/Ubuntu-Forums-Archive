---
title: "Java 7 oracle"
date: 2013-01-11
forum: New to Ubuntu
---

### Post by nick gentile on 2013-01-11
I am a new user. Update manager tells me i have updates. It will download but not install because it says i have  declined to accept the oracle java 7 agreement terms. How can i fix this

---

### Post by cottfcfan on 2013-01-11
Try running in a terminal:
```
sudo apt-get update && sudo apt-get upgrade
```
It should offer you a license to accept, just answer yes & continue.

---

### Post by nick gentile on 2013-01-11
Where do i type this

---

### Post by sammiev on 2013-01-11
> **nick gentile said:**
> Where do i type this

The command he left in his post needs to be entered in the terminal window.

---

### Post by audiomick on 2013-01-11
You can open a terminal by serching for "terminal" in the dash, or with the key combination ctrl+alt+t

When someone posts commands for you to use in a help thread, it is a good idea to copy and paste them into the terminal to avoid typing errors.

To copy and paste in the terminal, you need to use shift+ctrl+c and shift+ctrl+v respectively, or choose the option out of the edit menu.

---


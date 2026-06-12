---
title: "Password reset"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by ubuntokun on 2008-09-18
I would like to know how to reset my password from booting ubuntu in safe mode please

---

### Post by bodhi.zazen on 2008-09-18
list you user name with 

ls /home

then 

passwd user

where "user" is the user whose password you wish to reset

Then telinit 2

---

### Post by ubuntokun on 2008-09-18
I dont understand exactly what ur saying

---

### Post by oilchangeguy on 2008-09-18
> **ubuntokun said:**
> I dont understand exactly what ur saying

please spell all words, ur is not a word. the poster is giving you a command to enter in the terminal.

---

### Post by mc4100 on 2008-09-18
> **bodhi.zazen said:**
> list you user name with 

ls /home

then 

passwd user

where "user" is the user whose password you wish to reset

Then telinit 2
Same thing, just reworded...
Type what is in the following boxes at a root shell (ie., from Recovery Mode):
```
passwd (type here the username of the user whose password you wish to reset)
```
If you don't know the username, the users on the computer can be shown by typing:
```
ls /home
```

And finally:
```
telinit 2
```

---


---
title: "Really messed up need help"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by Rifts on 2008-04-30
haha alright so I was trying to fix my graphics card driver (not the important part) but in doing so i deleted my xconfig or whatever its called so now i have no ubuntu desktop when i load up ubuntu it just goes to a black screen as if its a huge permanent terminal... lol help

---

### Post by kesman on 2008-04-30
In there, log in with your account and run command:
```

sudo dpkg-reconfigure xserver-xorg

```
it will create you a new configuration file.

---

### Post by Rifts on 2008-04-30
alright so I tried that and it errored saying 
"xserver-xorg is broken or is not installed"

now what =[

---

### Post by Rifts on 2008-04-30
bump

---

### Post by Rifts on 2008-04-30
bump again =[ its gets pushed to page 10 so fast ha

---

### Post by martrn on 2008-04-30
Have you tried 
```
sudo apt-get install dpkg 
sudo apt-get install gkdebconf
sudo apt-get install xserver-xorg

```

Then retry.

---


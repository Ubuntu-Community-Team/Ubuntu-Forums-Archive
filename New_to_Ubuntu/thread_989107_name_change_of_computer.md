---
title: "name change of computer"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by edcouch on 2008-11-21
Hello, could someone please tell me how to change the name of my computer?
I would like it to show up on my lan under a different name.
thanks

---

### Post by Peter09 on 2008-11-21
You need to edit the /etc/hostname file

```
gksudo gedit /etc/hostname
```

---

### Post by slmouradian on 2008-11-21
```
 $ sudo gedit /etc/hostname 
```

Restart, and that should work.

---

### Post by edcouch on 2008-11-21
Thank you very much! Both of you!  it worked great!

---

### Post by lswb on 2008-11-21
Make sure you also change it in the /etc/hosts file.

---


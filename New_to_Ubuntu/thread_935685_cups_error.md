---
title: "cups error"
date: 2008-10-01
forum: New to Ubuntu
---

### Post by 1chad1 on 2008-10-01
I keep getting a message on my system at startup saying printer'lbp3000':'cups missing filter'. so I downloaded the driver from canon but it is in tar.gz and I have no idea how to install it, so can someone please help
chad

---

### Post by iaculallad on 2008-10-01
Try not to enforce security policy on cupsd. Try the command below on your terminal:

```
sudo aa-complain cupsd
```

---

### Post by 1chad1 on 2008-10-01
Nope tried it and no difference but thanks anyhow

---

### Post by jrothwell97 on 2008-10-01
A .tar.gz file is just like a .zip file, so extract it and look for an INSTALL or README file.

---

### Post by 1chad1 on 2008-10-02
ok thanks,I opened it and found a makefile but when I double clicked it nothing happened but getting closer

---


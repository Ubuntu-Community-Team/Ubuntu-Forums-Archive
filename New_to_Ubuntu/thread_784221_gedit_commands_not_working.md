---
title: "gedit commands not working"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by paul.lav on 2008-05-06
hi got another problem

 when i type the command 
```
sudo gedit /etc/samba/smb.conf
```
i get the error message
```
sudo:unable to resolve host ubuntufileserver
```

i have tried installing gedit from the synaptic manager but to no avail.

would someone please tell me what silly mistake i'm making this time.

---

### Post by mc4man on 2008-05-06
Try gksudo gedit .... instead

---

### Post by NilsE on 2008-05-06
Or browse to it with Nautilus and try to edit it

---

### Post by spectrevk on 2008-05-06
What exactly is the difference between sudo and gksudo?

---

### Post by tacutu on 2008-05-06
sudo unable to resolve host:
[http://ubuntuforums.org/showthread.php?t=773851](http://ubuntuforums.org/showthread.php?t=773851)

---

### Post by NilsE on 2008-05-06
> **spectrevk said:**
> What exactly is the difference between sudo and gksudo?
sudo is for command line root permissions and gksudo is for graphical interface root permissions.

---

### Post by bodhi.zazen on 2008-05-06
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---


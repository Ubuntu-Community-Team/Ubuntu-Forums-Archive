---
title: "sorry ubuntu 18.04 has experienced an internal error"
date: 2019-06-08
forum: New to Ubuntu
---

### Post by roshanaryal on 2019-06-08
Hey
I have just switch my pc from windows to ubuntu 18.04
After using some time i got message as 
sorry ubuntu 18.04 has experienced an internal error
How to solve it 
can anyone help me

---

### Post by cruzer001 on 2019-06-08
That is Apport

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

I think all you need is a reset.  It sometimes gets hung on a report.
```
sudo rm /var/crash/*
```

---

### Post by Rubi1200 on 2019-06-08
I've had this on fresh installs too.

Either do as cruzer001 suggests or consider removing the package (unless you want to contribute to bug reports).

And welcome to the forums :-)

---

### Post by Dennis N on 2019-06-08
> How to solve it
can anyone help me 
You can set problem reporting preferences in **Settings > Privacy > Problem Reporting**.
From there, you can suppress the notifications and allow reports to be sent automatically. That's the option I use.

---


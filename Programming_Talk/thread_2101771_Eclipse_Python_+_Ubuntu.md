---
title: "Eclipse Python + Ubuntu"
date: 2013-01-05
forum: Programming Talk
---

### Post by chinye2020 on 2013-01-05
i m new of Phyton,please help..
i have create FirstModule.py using Eclipse,
and how to install this module as Ubuntu service like Window Services?

---

### Post by chinye2020 on 2013-01-05
Oh, use Upstart and those command

$ sudo initctl reload-configuration 
$ sudo start FirstModule.py

Am i Correct?

---


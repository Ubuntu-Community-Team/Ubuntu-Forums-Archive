---
title: "how to enable mod_write php apache"
date: 2010-01-27
forum: Philippine Team
---

### Post by aweblab on 2010-01-27
how to enable mod_write php apache? 
thank you in advance

---

### Post by Samhain13 on 2010-01-30
mod_write? Or rewrite?

Anyway, in the terminal:
```
$ a2enmod
```

That will give you a list that you can enable. When you find the name of the module that you want to enable:
```
$ sudo a2enmod name_of_module
```

For more details:
```
man a2enmod
```

---

### Post by aweblab on 2010-01-30
> **Samhain13 said:**
> mod_write? Or rewrite?

Anyway, in the terminal:
```
$ a2enmod
```That will give you a list that you can enable. When you find the name of the module that you want to enable:
```
$ sudo a2enmod name_of_module
```For more details:
```
man a2enmod
```

Thank you sir Samhain :-)

i got the code how to enable the mod_rewrite 
```
sudo a2enmode rewrite
```and its done! mod_rewrite on apache is enable.

Thank you again sir Samhain13 :-)

---

### Post by Samhain13 on 2010-02-01
No problem. :D

---


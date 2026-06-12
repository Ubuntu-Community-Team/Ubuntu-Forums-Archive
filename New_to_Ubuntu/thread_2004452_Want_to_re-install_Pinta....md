---
title: "Want to re-install Pinta..."
date: 2012-06-15
forum: New to Ubuntu
---

### Post by sillyboy on 2012-06-15
I had to reinstall Ubuntu 10.04. I had Pinta v0.8 installed.  I tried to install it again, and it will not install.

Does anyone know what to do?

Thanks

---

### Post by afixane on 2012-06-16
> **sillyboy said:**
> I had to reinstall Ubuntu 10.04. I had Pinta v0.8 installed.  I tried to install it again, and it will not install.

Does anyone know what to do?

Thanks

Try to purge it :D

---

### Post by sillyboy on 2012-06-16
> **afixane said:**
> Try to purge it :D

How?

---

### Post by hakermania on 2012-06-16
> **sillyboy said:**
> How?

Hello silly, please explain better what the problem is?
Did you install Pinta from Ubuntu Software Center?

Then a solution would be to remove it from there and then click on the install button again, or, as afixane said, to do
```

sudo apt-get purge pinta
sudo apt-get install pinta

```

---


---
title: "Ubuntu 13.04 : Don't suspend on login screen"
date: 2013-05-14
forum: New to Ubuntu
---

### Post by HatoExB on 2013-05-14
Hi,

On my laptop, I have it set so if you close the lid within an account, it won't suspend.  Is there a way to do this even from the login screen?  It seems it's only taking effect on that account.

Sorry for the wierd question, but for me it's "convinient" if disabled.

Thanks. :)

---

### Post by Toz on 2013-05-14
As root, edit the file **/etc/UPower/UPower.conf**
```
gksu gedit /etc/UPower/UPower.conf
```
...and change the last line:
> IgnoreLid=false
...to read:
```
IgnoreLid=true
```

Note: this will disable all lid events on your laptop.

---


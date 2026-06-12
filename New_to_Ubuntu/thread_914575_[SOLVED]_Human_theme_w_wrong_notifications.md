---
title: "[SOLVED] Human theme w/ wrong notifications"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by mevets on 2008-09-08
A while back I messed around with the human theme on my system and seemed to have damaged it. I now have GTK notifications that are from another theme. Clicking on Human in the theme tab does not fix the problem. I was wonder if it was advisable to run a
```

dpkg-reconfigure package_name

```
If this is advisable at all, I cannot figure out what package it would be. Can anyone steer me in the right direction?

---

### Post by panhandle on 2008-09-08
if you are using Hardy, here are the packages:

[http://packages.ubuntu.com/hardy/human-theme](http://packages.ubuntu.com/hardy/human-theme)

---

### Post by graben3 on 2008-09-08
More specifically this one :

[http://mirrors.kernel.org/ubuntu/pool/main/h/human-theme/human-theme_0.18_all.deb](http://mirrors.kernel.org/ubuntu/pool/main/h/human-theme/human-theme_0.18_all.deb)

---

### Post by mevets on 2008-09-08
ah wow, reinstalling the package worked, while running a reconfigure did not. thanks

---


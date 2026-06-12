---
title: "Problem installing phpmyadmin on Ubuntu 12.04 LTS"
date: 2014-01-18
forum: New to Ubuntu
---

### Post by Taufan_Arsyad on 2014-01-18
Hi,

I am new here, and new to Ubuntu as well. I am a converting Windows user.
Anyway, I was installing LAMP for my machine. My steps were similar to [this link]("http://ubuntulife.net/how-to-install-lamp-in-ubuntu-12-04/"). But when I tried to install phpmyadmin, it gave me an error while it tried to configure phpmyadmin.
```
dpkg: error processing phpmyadmin (--configure): subprocess installed post-installation script returned error exit status 10
Errors were encountered while processing:
 phpmyadmin
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I have tried to apply the solution from [this link]("http://www.iasptk.com/ubuntu-debian/15825-ubuntu-fix-broken-package-best-solution"), but the error keeps coming up again. Anyone may help me about this?
Thank you very much in advance, really appreciate it.

Regards.

---

### Post by Taufan_Arsyad on 2014-01-18
Oh my, I am sorry but it seems like it was just a silly mistake by me.
I missed to try this line

```
sudo apt-get update --fix-missing
```
And all works like charm.

Hope this helps for the other guys!

Regards.

---


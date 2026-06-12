---
title: "Can't find packages."
date: 2012-06-16
forum: New to Ubuntu
---

### Post by kramer65 on 2012-06-16
Hello,


I want to install owncloud on an Ubuntu 12.04 installation. The [installation page]("http://owncloud.org/support/install/") says I need to install the following for that:
```
apt-get install apache2 php5 php5-json php-xml php-mbstring php5-zip php5-gd
apt-get install php5-sqlite curl libcurl3 libcurl3-dev php5-curl php-pdo
```
Unfortunately, apt can't find the following packages: php-xml, php-mbstring, and php5-zip.

My question; how can I find these? Or am I doing something wrong?

---

### Post by MG&amp;TL on 2012-06-16
Do you have a reason for manual dependency handling?

Why don't you use:

```
sudo apt-get install owncloud
```?

---

### Post by kramer65 on 2012-06-16
Wait.. is it *that* simple?

Damn, that I didn't think of that! It seems to be installing fine now, so I'll just keep my fingers crossed.

Thanks!

---

### Post by Paqman on 2012-06-16
> **kramer65 said:**
> Wait.. is it *that* simple?


Yup. Package managers are awesome.

---


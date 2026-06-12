---
title: "PEAR error"
date: 2006-04-13
forum: Programming Talk
---

### Post by spahn on 2006-04-13
So, i really want to get going with PEAR...

i have PHP5 installed on Breezy, (i used the package manager to install PEAR) and when i try to install packages via the command line as so:
[PHP]install HTML_Common[/PHP]

i get this error:

[PHP]downloading HTML_Common-1.2.2.tgz ...
Starting to download HTML_Common-1.2.2.tgz (4,240 bytes)
.....done: 4,240 bytes
failed to write /usr/share/php/HTML/.tmpCommon.php[/PHP]


Can anybody get me going in the right direction (any ideas what's wrong, or tips on how to improve)? 

Much thanks (in advance)

---

### Post by clauder357 on 2006-05-20
[QUOTE=spahn]So, i really want to get going with PEAR...

i have PHP5 installed on Breezy, (i used the package manager to install PEAR) and when i try to install packages via the command line as so:
[PHP]install HTML_Common[/PHP]

i get this error:

[PHP]downloading HTML_Common-1.2.2.tgz ...
Starting to download HTML_Common-1.2.2.tgz (4,240 bytes)
.....done: 4,240 bytes
failed to write /usr/share/php/HTML/.tmpCommon.php[/PHP]


Can anybody get me going in the right direction (any ideas what's wrong, or tips on how to improve)? 

Much thanks (in advance)[/QUOTE]
Hi  your command should include the word pear.

Have you tried 

pear install HTML_Common

---

### Post by Corvillus on 2006-05-21
```
sudo pear install HTML_Common
```
should do the trick. You need root privileges to use PEAR, since PEAR packages are not installed in your home directory.

---


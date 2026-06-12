---
title: "package missing in /var/cache/apt/archive folder"
date: 2017-12-31
forum: New to Ubuntu
---

### Post by wrongusername2 on 2017-12-31
I ran ** sudo apt install fdupes**
It said it installed fdupes and gave the name of the deb file as 'fdupes_1.51-1_amd64.deb'

But I do not see the 'fdupes_1.51-1_amd64.deb' in cache folder.


Any idea what happened?

---

### Post by deadflowr on 2017-12-31
apt, as opposed to apt-get, purges the archived files after a successful installation of the package.

---

### Post by wrongusername2 on 2017-12-31
Thanks I was guessing the same :-)

---


---
title: "Apache2, SSL, SVN - 403 Forbidden MKACTIVE"
date: 2008-04-23
forum: Programming Talk
---

### Post by bz029 on 2008-04-23
I am receiving errors when I try to import files into a repository.

svn import svn.test [https://www.grstaff.net:8500/svn/svn.test](https://www.grstaff.net:8500/svn/svn.test) -m "test import"
[authenticate]
svn: MKACTIVITY of '/svn/svn.test/!svn/act/0bdd7457-16e0-413b-839e-c2e306b9b2aa': 403 Forbidden ([https://www.grstaff.net:8500](https://www.grstaff.net:8500))


Please see the pastebin for the rest of the information ... 
[http://www.pastebin.ca/994167](http://www.pastebin.ca/994167)

svn folder = /var/svn
/var/svn = 777
/var/svn owner:group = www-data:www-data
the repository is all lower case, its not the 403 error caused by case sensitivity. =)

Thanks for your help in advance!

---


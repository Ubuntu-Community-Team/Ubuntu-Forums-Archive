---
title: "locally hosting my site"
date: 2013-05-17
forum: New to Ubuntu
---

### Post by jairoh_ on 2013-05-17
Hi everyone i'm new to ubuntu and i just installed xampp and tried the site i made from windows here. I u know how can i gain all the previleges as a user pls post. or if u know a solution to this. tnx
Problems are:

1. I cannot copy/paste or edit files in my www folder.
*first thumbnail*

2. I wasn't able to the my site in the localhost
*second thumbnail*

---

### Post by bluefrog on 2013-05-17
files in /var/www must be readable by the user www-data to be accessible via a browser.
your user must have the right to create in /var/www otherwise you must use sudo to create/paste files in there.

---

### Post by jairoh_ on 2013-05-17
> **bluefrog said:**
> files in /var/www must be readable by the user www-data to be accessible via a browser.
your user must have the right to create in /var/www otherwise you must use sudo to create/paste files in there.
how to add a right to the user?

---


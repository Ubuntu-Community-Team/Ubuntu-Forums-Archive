---
title: "Virtual Directory Listing Deny on apache"
date: 2008-01-01
forum: Other OS Talk
---

### Post by kool_kat_os on 2008-01-01
I have apache 2 on windows xp and I need to make it so it does not show the contents of a directory? ie: if there is a picture at "www.mysite.com/images/mypicture.gif" how do I make it so that if you type in "www.mysite.com/images" it does not show the contents of that folder? Thanks

---

### Post by Bachstelze on 2008-01-02
```
Options -Indexes
```
In .htaccess or in the Apache config.

---


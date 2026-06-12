---
title: "LAMP -- prevent others from accessing public_html"
date: 2008-07-05
forum: New to Ubuntu
---

### Post by JimmyJim on 2008-07-05
I'm using LAMP to work on web dev. projects. I don't want others to be able to access/view my public_html directory to view my work. How can I prevent this?

Thanks in advance.

---

### Post by spiderbatdad on 2008-07-05
you can use .htaccess to set up authentication requirements. You can block forwarding via your router, so that only localhost has access.

---

### Post by JimmyJim on 2008-07-05
> **spiderbatdad said:**
> you can use .htaccess to set up authentication requirements. 

Where is .htaccess located for xampp? I can't seem to find it. Also, what would I add to .htaccess to add authentication requirements?

Thanks

---

### Post by Dr Small on 2008-07-05
Just use chmod.
```
chmod 700 ~/public_html
```

---


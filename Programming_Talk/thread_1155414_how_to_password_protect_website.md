---
title: "how to password protect website?"
date: 2009-05-10
forum: Programming Talk
---

### Post by gfunkera on 2009-05-10
how can i password protect my website with multiple users?

---

### Post by Meson on 2009-05-10
> **gfunkera said:**
> how can i password protect my website with multiple users?

For a quick fix, if you're not the admin, you can use a .htaccess and .htpasswd file.

---

### Post by gfunkera on 2009-05-10
i am the admin..

i dont know wher those files are.. do i have to create them? can i create different ones in different places? how will the user be asked for credentials? do i have to write it in the html?

is there a way to log all accesses to my site and/or login attempts?

---

### Post by yaaarrrgg on 2009-05-10
Are you using apache? If you're not using apache then you'll need a different method. Here's a link that helps create these files:

[http://tools.dynamicdrive.com/password/](http://tools.dynamicdrive.com/password/)

This can be dropped in the directory that you want to protect.

Apache should give you an access log.

This is basic authentication (pops up a prompt).  If you need something fancier, either aesthetically or with more fine-grained logging, it will likely require web programming and a database.

---


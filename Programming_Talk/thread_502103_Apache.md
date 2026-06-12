---
title: "Apache"
date: 2007-07-16
forum: Programming Talk
---

### Post by sugan on 2007-07-16
Hi,

I have installed apache in my system. I have set E: as localhost drive. If I type localhost, it by default lists all the folders in it. I don't want to list all the folders in it. If the folder contains index file, it should display the index page or else it should not list anything.

Solution will be appreciable.

Regards, 
Sugan

---

### Post by the_unforgiven on 2007-07-16
> **sugan said:**
> Hi,

I have installed apache in my system. I have set E: as localhost drive. If I type localhost, it by default lists all the folders in it. I don't want to list all the folders in it. If the folder contains index file, it should display the index page or else it should not list anything.

Solution will be appreciable.

Regards, 
Sugan
Check out the Apache configuration directive "Options":
[http://httpd.apache.org/docs/2.2/mod/core.html#options](http://httpd.apache.org/docs/2.2/mod/core.html#options)

---


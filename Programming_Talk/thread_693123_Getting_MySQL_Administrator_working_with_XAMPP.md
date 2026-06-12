---
title: "Getting MySQL Administrator working with XAMPP"
date: 2008-02-10
forum: Programming Talk
---

### Post by comfixit on 2008-02-10
I did a default installation of XAMPP, everything tests out well.

Now I am trying to connect to the MySQL server through MySQL Administrator.

The default port looks correct. I am using Host: localhost, username: root and password I am leaving blank.

When I try to connect I get an error in MySql Administrator saying that it can't connect to localhost, but when it tries to ping it seems to ping back fine.

Any ideas what changes I might need to make to get it to work?

---

### Post by comfixit on 2008-02-10
Figured it out:

I was using localhost instead of Localhost

When I switched that everything worked fine.

---


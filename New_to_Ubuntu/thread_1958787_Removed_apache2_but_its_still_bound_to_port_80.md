---
title: "Removed apache2 but its still bound to port 80?"
date: 2012-04-14
forum: New to Ubuntu
---

### Post by terrykiwi83 on 2012-04-14
So I have removed apache2 but its still showing as online when I go to [http://localhost](http://localhost)

When I try to start my cherokee web server it won't start as apache is bound to port 80.

how do I get rid of apache?

Cheers

---

### Post by agillator on 2012-04-14
First, how did you remove apache and are you sure it is completely gone? Second, assuming it was running at the time, did you stop it before you removed it? The copy in memory may still be running and that may be the problem. Assuming it is truly removed, i.e. any start up file in /etc/init.d or wherever is also gone, rebooting the computer should take care of the problem.

---


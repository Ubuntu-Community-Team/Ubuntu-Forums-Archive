---
title: "Cant cancel print job"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by jerzydirtracer on 2008-05-13
Hello,  am having a problem canceling a print job, I get a message "cups server error" "there was an error during the CUPS operation: 'client-error-not-possible". It is driving me nuts. It wont let me print what I want, it keeps trying to print what is in the cache. Any ideas? Thanks!

---

### Post by cmnorton on 2008-05-14
The printer might be configured wrong. Check the cups logs /var/logs/cups for errors.

Ubuntu has a pretty good printer interface, but I still prefer to use localhost:631. Just make sure your username is part of lpadmin, so when you give your password when prompted for root's, you'll be able to perform those tasks. 

Obviously using CUPS' web interface is not going to fix this problem; I just find the interface easier to use, and it's a must on RHEL when you have non-standard port numbers.

If worse comes to worse, delete and re-instate the printer definition, and, if that does not work, remove and re-install CUPS.

---

### Post by jerzydirtracer on 2008-05-14
Thanks. I will go over the settings.

---


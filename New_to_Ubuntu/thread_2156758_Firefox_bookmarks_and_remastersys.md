---
title: "Firefox bookmarks and remastersys"
date: 2013-06-23
forum: New to Ubuntu
---

### Post by pghud3 on 2013-06-23
I want to create re-spin of Ubuntu and want to include bookmarks from Firefox when the live medium is booted up.  I will be using remastersys to create the live Cd, How do i get bookmarks to stay when the ISO is created in remastersys?  And will the bookmarks stay if the distro is installed to the hard disk?

---

### Post by Harsh Kumar Narula on 2013-06-24
copy and paste ".mozilla" folder from your home folder to /etc/skel with root privileges. Create distro using remastersys. You are done :)

---

### Post by pghud3 on 2013-06-24
> **Harsh Kumar Narula said:**
> copy and paste ".mozilla" folder from your home folder to /etc/skel with root privileges. Create distro using remastersys. You are done :)

Thanks i will try that, also with it copy over any add-on as well?

---

### Post by Harsh Kumar Narula on 2013-06-24
yes , everything..including browser history... basically it will copy the current 'state' of firefox..

---

### Post by sandyd on 2013-06-24
note that I *think* all the passwords/etc saved in FF will be copied over as well, you might want to be careful if that is the case.

---


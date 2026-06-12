---
title: "Add/Remove Programs and synaptic not working"
date: 2008-05-23
forum: New to Ubuntu
---

### Post by ghuqu on 2008-05-23
I just tried to install 7zip in ADD/Remove and it gives me "Software installation failed" "There has been a problem during the installation of the following pieces of software." The box is blank below that warning. Also, tried to install other progs with the same error message. Then, I went to open synaptic and now that won't even open. I click on the icon and....nothing. I am using HH, by the way.

---

### Post by tnmarktx on 2008-05-23
Assuming nothing has happened to your internet connection.  Maybe try sudo apt-get update in terminal, and then try add/remove programs.

---

### Post by ghuqu on 2008-05-23
I typed that in and this is the message I received:  
sudo: /etc/sudoers is owned by gid 1001, should be 0
Never seen this before, do you know what it means?

And yes, there was nothing wrong with my internet connection

---

### Post by nick_h on 2008-05-23
Have you changed any permissions in /etc?

---

### Post by ghuqu on 2008-05-23
Not that I know of. At least not on purpose.

---

### Post by N.N. on 2008-05-23
See the following thread for a (possible) solution: [http://ubuntuforums.org/showthread.php?t=691604](http://ubuntuforums.org/showthread.php?t=691604).

---

### Post by ghuqu on 2008-05-23
> **N.N. said:**
> See the following thread for a (possible) solution: [http://ubuntuforums.org/showthread.php?t=691604](http://ubuntuforums.org/showthread.php?t=691604).

Actually I did try that...it did nothing for me.

---

### Post by ghuqu on 2008-05-23
> **ghuqu said:**
> Actually I did try that...it did nothing for me.

No wait...it totally worked for me. Thank you everyone.

---

### Post by philinux on 2008-05-23
Never mess with sudoers. :)

---


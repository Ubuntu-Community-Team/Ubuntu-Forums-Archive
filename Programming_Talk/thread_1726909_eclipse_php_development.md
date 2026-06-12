---
title: "eclipse php development"
date: 2011-04-11
forum: Programming Talk
---

### Post by ddmn on 2011-04-11
Hi,
I'm trying php development in eclipse. The problem is eclipse can't create a workspace under /opt/lampp/htdocs. It says the directory is read only. But i guess to deploy my web pages, they need to be saved in htdocs.
How do i go about this?
regards,

---

### Post by eriscae on 2011-05-20
Try as **root** to change the owner:group of /opt/lamp/htdocs to your user and group

[FONT=Courier New][SIZE=3]chown -R your_user:your_group /opt/lampp/htdocs/[/SIZE][/FONT]

---

### Post by madmaxo on 2011-05-20
Or you could create a symbolic link to a folder in your home directory with ln -s

---


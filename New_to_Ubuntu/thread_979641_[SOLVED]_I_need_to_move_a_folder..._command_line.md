---
title: "[SOLVED] I need to move a folder... command line"
date: 2008-11-12
forum: New to Ubuntu
---

### Post by shanep-server on 2008-11-12
How do i go about moving a folder. 

I want to move 

/usr/phpbb3/
to
/var/www/

What is the command line to execute this?

---

### Post by Steve1961 on 2008-11-12
sudo cp -a /usr/phpbb3 /var/www/

---

### Post by ratmandall on 2008-11-12
The above would copy /usr/phpbb3/ to /var/www/
This will move it.
```

sudo mv /usr/phpbb3/ /var/www/
```

---


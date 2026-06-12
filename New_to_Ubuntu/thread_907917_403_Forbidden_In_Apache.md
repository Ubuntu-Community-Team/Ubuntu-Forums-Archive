---
title: "403 Forbidden In Apache"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by abeisgreat on 2008-09-02
so I installed 

sudo aptitude install apache2 php5 mysql phpmyadmin

and I put my item in the /var/www/ dir and I try to access it and it opens a download window for the .php file like if I just opened a local php file normally.

How can I get it to open the file correctly?

---

### Post by lazyart on 2008-09-02
I think you have to allow execution of files in that directory:
```
sudo chmod ugoa+x /var/www
```or, to give permission to all subdirectories as well```
sudo chmod ugoa+x -R /var/www
```

---

### Post by abeisgreat on 2008-09-02
> **lazyart said:**
> I think you have to allow execution of files in that directory:
```
sudo chown ugoa+x /var/www
```or, to give permission to all subdirectories as well```
sudochown ugoa+x -R /var/www
```

I tried the first one and got 

chown: invalid user: `ugoa+x'

---

### Post by lazyart on 2008-09-02
oops.... that should be chmod, not chown.

---

### Post by abeisgreat on 2008-09-02
> **lazyart said:**
> oops.... that should be chmod, not chown.

haha thats what I kinda thought

well I tried it and still no luck

now I go to blahblah/index.php I dont even get the download window

---


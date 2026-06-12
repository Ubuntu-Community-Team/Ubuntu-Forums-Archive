---
title: "Deleting users"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by mr-Kirch on 2008-05-21
okay i got to administrator options>users and groups>unlock>choose user and delete but all there files are still in my computer>how do i get rid of them?

btw can somebody send me an installing wine/steam tutorial..im starting fresh

---

### Post by RiceMonster on 2008-05-21
1) To get rid of those files, run this in a terminal:
```
sudo rm -r /home/user_name_you_want_to_delete
```

2) -[http://appdb.winehq.org](http://appdb.winehq.org). Search there for steam, it's got a great tutorial. 
    -To install wine, run this in a terminal:
```
sudo apt-get install wine
```

---


---
title: "Setting permissions to apache server"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by ben22 on 2008-04-25
Hi,

I need to give 777 rights to a folder to apache. 

```
ben@ben-desktop:~$ chmod www-data=777 -R /home/ben/Desktop/web/myweb/templates_c/
chmod: invalid mode: `www-data=777'
Try `chmod --help' for more information.
```

This seems to be wrong, some help there?

thx,
ben

---

### Post by Kilz on 2008-04-25
> **ben22 said:**
> Hi,

I need to give 777 rights to a folder to apache. 

```
ben@ben-desktop:~$ chmod www-data=777 -R /home/ben/Desktop/web/myweb/templates_c/
chmod: invalid mode: `www-data=777'
Try `chmod --help' for more information.
```

This seems to be wrong, some help there?

thx,
ben

I think its 
```
sudo chmod -R 777 /path/to/folder
```

---

### Post by ben22 on 2008-04-25
> **Kilz said:**
> I think its 
```
sudo chmod -R 777 /path/to/folder
```

how do u define the user in there - this way u would give the the user "ben" not apache the 777 rights, I reckon?

---


---
title: "Pycharm / configuring Wordpress"
date: 2014-01-29
forum: New to Ubuntu
---

### Post by aviv2 on 2014-01-29
issue 1:
I m trying to install pycharm 2.6
when i type ./pycharm.sh
i m getting "failed to clear url cache"

issue 2:
i have installed wordpress on ubuntu 64.
when i try to get in to my site
[http://192.168.16.22/blog/wp-admin/](http://192.168.16.22/blog/wp-admin/)
i get 
There doesn't seem to be a wp-config.php file. I need this before we can get started.
i have [FONT=Courier New]wp-config.php[/FONT] file on vaw/www/blog/wp-admin
i have tried to change permissions to the file.
i have validate that i have php5 on my server.
when i type [http://192.168.16.22/blog/wp-admin/](http://192.168.16.22/blog/wp-admin/)wp-config.php i can see the content of the file.

whats the solution please, 10x.

---

### Post by oldos2er on 2014-01-29
Moved to Absolute Beginners.

---

### Post by mastablasta on 2014-01-30
issue one make sure the file is executable. use 
```
chmod +x filename
``` to make it executable

issue 2

did you cretate a database? what si in wp-config.php ? is it cretae dpropperly?

---


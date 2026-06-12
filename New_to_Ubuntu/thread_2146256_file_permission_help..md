---
title: "file permission help."
date: 2013-05-17
forum: New to Ubuntu
---

### Post by jairoh_ on 2013-05-17
i followed this article ```

[h=4]Adding yourself to the Apache group and modifying permissions[/h] For this example your username will be "youruser", on most Linux  distributions the Apache service runs on the user "wwww-data" and the  group "www-data", we need to include our user "youruser" in to the  "www-data" group to be able to set permissions to the web server files  and have no problems when we have to edit them. 
 
[LIST]
[*]To add "youruser" to the Apache group, open a terminal and type
[/LIST]
 
sudo adduser youruser www-data  
[LIST]
[*]Now we need to change the owner and group of all our web server files to owner "www-data" and group "www-data"
[/LIST]
 
sudo chown -R www-data:www-data /home/youruser/lamp/public_html  
[LIST]
[*]Finally we have to set the correct folder permission so both  APahce and our user can edit the files with no problems, on a terminal  type
[/LIST]
 
sudo chmod -R 775 /home/youruser/lamp/public_htm  [h=4][/h]

```
and en up this one. I cannot edit my site now.
[[IMG]http://img507.imageshack.us/img507/33/permission.png[/IMG]](http://imageshack.us/photo/my-images/507/permission.png/)

i tried some commands for me to enable write/delete/rewrite but nothing happened right ```

jairoh@jairoh-300E4C-300E5C-300E7C:~$ sudo chmod +x  /home/jairoh/lamp/public_html
jairoh@jairoh-300E4C-300E5C-300E7C:~$ sudo chmod +x  /home/jairoh/lamp/public_html
jairoh@jairoh-300E4C-300E5C-300E7C:~$ gksudo chmod +x  /home/jairoh/lamp/public_html
jairoh@jairoh-300E4C-300E5C-300E7C:~$ sudo chmod 644 /home/jairoh/lamp/public_html
jairoh@jairoh-300E4C-300E5C-300E7C:~$ sudo chmod -R 775 /home/jairoh/lamp/public_html



```

i read commands but nothing worked. if u know how to solve this please post tnx.

---

### Post by jairoh_ on 2013-05-17
solved it already. i just use konquer IDE. hehehe

---

